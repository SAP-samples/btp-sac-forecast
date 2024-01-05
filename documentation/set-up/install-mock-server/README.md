# Install Mock Server

If you don't have access to an SAP backend system (ECC, SAP S/4HANA or SAP on-premise system) but still need OData services with some data, you can use this [mock server application](https://github.com/SAP-samples/cloud-extension-ecc-business-process/blob/mock/README.md). It contains some entities of SAP OData services with sample data.

In essence, these are the steps you need to follow:
1. Install the mock server. There are two options to do that:
   * Using [SAP Business Application Studio](#option-1-install-the-mock-server-using-sap-business-application-studio)
   * Using a [local system](#option-2-install-the-mock-server-using-a-local-system)

2. Create a subaccount in SAP BTP with Cloud Foundry environment enabled and 256 MB of Cloud Foundry runtime.

3. Create a [destination](#create-destination-to-mock-server) to the mock server in the same subaccount as your SAP AppGyver subscription.

> **_NOTE:_** If you used *btp-setup-automator* to create the subaccount in SAP BTP, there's a high probability that the mock server application has been already deployed. 

## Option 1. Install the Mock Server Using SAP Business Application Studio

**Prerequisites:** 
* Configure the entitlement of SAP Business Application Studio in you global account in SAP BTP. See [SAP Help Portal: Getting Started Guide](https://help.sap.com/docs/SAP%20Business%20Application%20Studio/9d1db9835307451daa8c930fbd9ab264/19611ddbe82f4bf2b493283e0ed602e5.html?locale=en-US).
* Enable the Cloud Foundry environment for your subaccount in SAP BTP.

### Create Workspace

1. Open the SAP Business Application Studio. Choose **Create a New Dev Space** and check the **Full Stack Cloud Application** radio button.

2. Open a new terminal.

### Log In to Cloud Foundry in SAP Business Application Studio

**In SAP BTP cockpit:**
1. Navigate to your subaccount and choose **Overview**. Copy the values from the **Org Name** and **API Endpoint** parameters in a text editor of your choice.

2. In the left-hand navidation, choose **Cloud Foundry** &rarr; **Spaces**, copy the Space name and write it in a text editor of your choice.

**In SAP Business Application Studio:**
1. In the tabs, choose **View** and select **Find Command**.

2. Search for **CF Login** and select **CF: Login on to Cloud Foundry**.

3. Enter the Cloud Foundy API endpoint you have copied from SAP BTP cockpit or take the default suggested API endpoint.

4. When prompted, enter your the email and password for your global account in SAP BTP.

5. Select your Cloud Foundry Org, the same you have copied from SAP BTP cockpit. 

6. Then, select the Cloud Foundry Space, the same you have copied from SAP BTP cockpit. 

7. Once you have selected the Org and the Space, log in to Cloud Foundry in SAP Business Application Studio.

**Result:** you have successfully created a workspace and pointed to our desired Cloud Foundry Org and Space.

### Build and Deploy the Mock Server Application

1. In SAP Business Application Studio, choose **Terminal** &rarr; **New Terminal** and navigate to the projects folder using:

   ```bash
      cd projects
   ```

2. Clone the mock server GitHub repository:

   ```bash
      git clone -b mock https://github.com/SAP-samples/cloud-extension-ecc-business-process.git
   ```

3. In the menu, choose **File** and then choose **Open Workspace** from the dropdown menu.

4. To open the project, choose **projects** &rarr; **cloud-extension-ecc-business-process** and then choose **Open**.

5. Replace all content of the file ../srv/csv/OP_API_BUSINESS_PARTNER_SRV-A_BusinessPartner.csv with business sample partner data we use in our project   [OP_API_BUSINESS_PARTNER_SRV-A_BusinessPartner.csv](./OP_API_BUSINESS_PARTNER_SRV-A_BusinessPartner.csv)

6. In the project folder, right-click the **mta.yaml** file and choose **Build MTA Project**.

7. When the project is built successfully, you will see a new **mta_archives** folder in your project with the **Mockserver_1.0.0.mtar** file inside. Right-click that file and choose **Deploy MTA Archive**.

**Next step:** create a [destination](#create-destination-for-mock-server) to the mock server.

## Option 2. Install the Mock Server Using a Local System

### 1. Install Tools
For building and deploying the mock server, you need to install the following tools on your device:

1.  [Node.js](https://nodejs.org/en/download/) - find the latest Node.js version supported by [SAP Cloud Application Programming Model (CAP)](https://cap.cloud.sap/docs/advanced/troubleshooting#node-version).
2. [Git](https://github.com/git-guides/install-git)
3. [Cloud Foundry command line interface (v7 version or later)](https://github.com/cloudfoundry/cli/wiki/V7-CLI-Installation-Guide).
4. [Cloud MTA Build Tool](https://sap.github.io/cloud-mta-build-tool/) - you can install it using Node.js.

     ```cmd
     npm install -g mbt
     ```

### 2. Clone the Repository

1. Open a terminal (on Mac) or a command prompt (on Windows).

2. Clone the mock server GitHub repository:

   ```bash
      git clone -b mock https://github.com/SAP-samples/cloud-extension-ecc-business-process.git
   ```
3. Replace all content of the file ../srv/csv/OP_API_BUSINESS_PARTNER_SRV-A_BusinessPartner.csv with sample business partner data we use in our project   [OP_API_BUSINESS_PARTNER_SRV-A_BusinessPartner.csv](./OP_API_BUSINESS_PARTNER_SRV-A_BusinessPartner.csv)   

### 3. Build the Application

Build your application by using the `mta.yaml` build file. With the `-t parameter`, the file will be created in the specified folder.

   ```cmd
   mbt build -t ./mta_archives

   ```
   
### 4. Log In to Your Subaccount in SAP BTP

1. Set the SAP BTP API endpoint. You can find it in overview of your SAP BTP subaccount:

    ```cmd
    cf api <your-api endpoint>
    ```

2. Log in to your subaccount and select your Cloud Foundry Org and Space:

   ```cmd
   cf login -u <your-user> -p <your-password>
   ```

### 5. Deploy the MTA Archive

You can deploy the application to your subaccount and Space by using the created mtar file:

   ```cmd
   cd mta_archives
   cf deploy Mockserver_1.0.0.mtar
   ```

If the deployment is successful, you will see the following log:

   ```cmd
   Starting application "mock-srv"...
   Application "mock-srv" started and available
   ```

## Create Destination to Mock Server

1. In SAP BTP cockpit, go to your subaccount and navigate to the space where you have deployed the mock server. In the **Applications** section, choose the **mock-srv** application.

2. In the application overview screen, copy the **Application Route** of the mock server.

3. Go back to the subaccount overview and choose **Connectivity** &rarr; **Destination**. Then, choose **New Destination**. 
  1. Enter the following values:

      * **Name** = *[Some destination name depending on your mission]*, in our scenario we will choose Name = cpapp-bupa
      * **Type** = HTTP
      * **URL** = *[URL for your OData entities]* e.g. https://\<The application route of the mock server\>/v2/op-api-business-partner-srv/
      * **Proxy Type** = Internet
      * **Authentication** = NoAuthentication

  2. Choose **New Property** at create the following properties:
       
      * **WebIDEEnabled** = true
      * **HTML5.DynamicDestination** = true
      * **WebIDEAdditionalData** = full_url
      * **WebIDEUsage** = odata_gen

  3. Select the **Use default JDK truststore** checkbox.

  4. Save your settings.

4. Choose **Check Connection**, you should get a `200 OK` message.

## Test the Mock Server

1. Call the **Application Route**.

2. There are couple of options to display the data of the mock server. For example, call the **Open API** endpoint and you will get a Swagger UI where you can test the OData services.
