           <!-- Module 0 - Lab 0 -->
            <section>
                <section data-markdown>
                    <script type="text/template">
                        ## Attention!
                        #### This guide assumes that you have a spare hardware to execute all of the tasks in the self-paced manner. If you don't have any hardware to run - you may leverage any cloud provider. This guide can be completed with software virtualization only (QEMU), however we would highly recommend KVM-supported hardware. 

                        ---
                        <br>

                        ## Requirements

                        | Requirement     | Minimum Value | Recommended |
                        |----------------- | -------- | -------- | 
                        | CPU    | 2 cores | 4 cores |
                        | MEMORY    | 4 GB | 8 GB    |
                        | Disk Space | 60 GB | 100GB |
                        | Operating System | RHEL, Debian, Ubuntu |  RHEL, Debian, Ubuntu|


                    </script>
                </section>
            </section>

            <!-- Module 1 - Lab 1 -->
            <section>
                <section data-markdown>
                    <script type="text/template">
                        ## Module 1 - Lab 1 : Prepare your Lab Environment using miniONE 
                         
                        ---
                        <br>
                            
                        ## Objective(-s):
                        - Install OpenNebula and Hypervisor using miniONE tool.
                        - Login into the Sunstone interface.
                          
                        ---
                        <br>
                           
                        ### Install OpenNebula and Hypervisor using miniONE tool.

                        ---
                        <br>

                        #### 1.1.1

                        Fill in <a href="https://opennebula.io/get-minione/" target="_blank">this form</a> to get the link to download miniONE.
                        
                        Copy the **minione** to any location on your Linux server that you had allocated for this task. 

                        In this guide we are going to assume that it is stored under the **/deployment** directory.

                        ---
                        <br>
                           
                        #### 1.1.2

                        You supposed to perform the installation with **root** user privileges!

                        Set the password for **oneadmin** user to any string, however in this guide we are going to assume that the  password is set to **Pa$$w0rd**.

                        ```console[]
                        # cd /deployment
                        # bash minione --password 'Pa$$w0rd' --force --yes
                        ```

                        Wait until the script is going to finish (~10m).

                        ---
                        <br>
                           
                        #### 1.1.3

                        Access the Sunstone interface on port 80/tcp and login as **oneadmin**.

                        <img src="./resources/module1_lab1/s3.png" class="img_80_percent">
                            
                        ---
                        <br>
                            
                        ### Congratulations, you've completed the assignment!
                    </script>
                </section>
            </section>

            <!-- Module 2 - Lab 1 -->
            <section>
                <section data-markdown>
                    <script type="text/template">
                        ## Module 2 - Lab 1 : Users, Groups & Permissions
                         
                        ---
                        <br>
                            
                        ## Objective(-s):
                        - Create a Group.
                        - Create a User.
                        - Change an ownership of the VM Template and Image.
                        - Optionally, secure oneadmin user with TOTP 2FA.
                            
                        ---
                        <br>

                        ### Create a Group.

                        ---
                        <br>
						
                        #### 2.1.1
                        
                        Navigate to **System -> Groups** to access the Groups Management screen.
                        
                        <img src="./resources/module2_lab1/s1.png" class="img_80_percent">
                        
                        ---
                        <br>
                        
                        #### 2.1.2
                        
                        From the Groups screen press **Create** to start the wizard. 
                        
                        <img src="./resources/module2_lab1/s2.png" class="img_80_percent">
                        
                        ---
                        <br>
                        
                        #### 2.1.3
                        
                        Name the group **cloud**.
                        
                        Add an administrator user with the name **cloud-admin**. 
                        
                        Set **Authentication Type** to **core**. 

                        Choose the password you wish and press **Next**.
                        
                        <img src="./resources/module2_lab1/s3.png" class="img_70_percent">
                        
                        ---
                        <br>
                        
                        #### 2.1.4

                        Leave **Permissions** as is and press **Next**.
                        
                        <img src="./resources/module2_lab1/s4.png" class="img_80_percent">
                        
                        ---
                        <br>
                        
                        #### 2.1.5
                        
                        Set the **User view** as a **Default view**.
                        
                        Also enable the **User view** and press **Next**.
                        
                        <img src="./resources/module2_lab1/s5.png" class="img_80_percent">
                        
                        ---
                        <br>
                        
                        #### 2.1.6
                        
                        Leave the **System** tab as is and press **Finish**.
                        
                        <img src="./resources/module2_lab1/s6.png" class="img_80_percent">
                        
                        ---
                        <br>
                        
                        #### 2.1.7
                        
                        You should see the newly created group added to the list of groups.

                        Note the **Group ID (#100)**, this may be a different ID in your environment!
                        
                        <img src="./resources/module2_lab1/s7.png" class="img_80_percent">

                        ---
                        <br>

                        ### Create a User.

                        ---
                        <br>
                           
                        #### 2.1.8

                        Navigate to **System -> Users** to access the Users Management screen.
                        
                        <img src="./resources/module2_lab1/s8.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 2.1.9

                        Press **Create** to enter the user creation wizard.

                        <img src="./resources/module2_lab1/s9.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 2.1.10

                        Name the user as **cloud-user**.

                        Set Authentication to **core**.

                        Set the password. In this guide we are going to assume that the password is set to **Pa$$w0rd**.

                        <img src="./resources/module2_lab1/s10.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 2.1.11

                        Set **cloud-users** as the **Primary Group**.

                        <img src="./resources/module2_lab1/s11.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 2.1.12

                        Leave the **Secondary Groups** empty and press **Finish**.

                        <img src="./resources/module2_lab1/s12.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 2.1.13

                        You must end up having two users in the **cloud-users** group.

                        One is **admin** and second is the **regular** user.

                        <img src="./resources/module2_lab1/s13.png" class="img_80_percent">

                        ---
                        <br>
                           
                        ### Change an ownership of the VM Template and Image.

                        ---
                        <br>
                           
                        #### 2.1.14

                        Navigate to **Templates -> VM Templates**. 

                        <img src="./resources/module2_lab1/s14.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 2.1.15

                        Select the **Alpine Linux 3.XX** VM Template from the template list.

                        <img src="./resources/module2_lab1/s15.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 2.1.16

                        Change ownership to:
                        **Owner: cloud-user**
                        **Group: cloud-users**

                        Save changes by clicking the **tick** icon.

                        <img src="./resources/module2_lab1/s16.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 2.1.17

                        Navigate to **Storage -> Images**.

                        <img src="./resources/module2_lab1/s17.png" class="img_80_percent">
                        
                        ---
                        <br>
                           
                        #### 2.1.18

                        Select the **Alpine Linux 3.XX** image.

                        <img src="./resources/module2_lab1/s18.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 2.1.19

                        Change ownership to:
                        **Owner: cloud-user**
                        **Group: cloud-users**

                        Save changes by clicking the **tick** icon.

                        <img src="./resources/module2_lab1/s19.png" class="img_80_percent">

                        ---
                        <br>

                        ### Optionally, secure oneadmin user with TOTP 2FA.

                        ---
                        <br>
                           
                        #### 2.1.20

                        Navigate to **Settings**.

                        <img src="./resources/module2_lab1/s20.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 2.1.21

                        Select **Security** and scroll down to the bottom of the page. Press the **Register authentication App** button.

                        <img src="./resources/module2_lab1/s21.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 2.1.22

                        Take your authentication app that can generate TOTP codes and scan the QR code. Enter the code and press **Add**.

                        <img src="./resources/module2_lab1/s22.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 2.1.23

                        Once added you are going to get prompted to enter the code during the next loging attempt. 

                        <img src="./resources/module2_lab1/s23.png" class="img_80_percent">
                        
                        ---
                        <br>
                           
                        ### Enroll the SSH public key. 

                        ---
                        <br>

                        #### 2.1.24

                        In order to access VMs that are owned by **cloud-user** - you must add a public key. Outside of the test scenario - it must be different from **oneadmin's**!

                        Navigate to **Settings -> Security** while being logged in as oneadmin and copy the public key.

                        <img src="./resources/module2_lab1/s24.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 2.1.25

                        Login as cloud-user and navigate to **Settings -> Security**.

                        Press edit the **SSH public key**.

                        <img src="./resources/module2_lab1/s25.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 2.1.26

                        Paste the key into the field.

                        <img src="./resources/module2_lab1/s26.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 2.1.27

                        Click anywhere outside to save the key.

                        <img src="./resources/module2_lab1/s27.png" class="img_80_percent">


                        ---
                        <br>
                            
                        ### Congratulations, you've completed the assignment!
                    </script>
                </section>
            </section>

            <!-- Module 3 - Lab 1 -->
            <section>
                <section data-markdown>
                    <script type="text/template">
                        ## Module 3 - Lab 1 : Hosts
                         
                        ---
                        <br>
                            
                        ## Objective(-s):
                        - Add a KVM Host.
                        - Disable the **localhost**.
                          
                        ---
                        <br>

                        ### Add a KVM Host.

                        ---
                        <br>
                           
                        #### 3.1.1

                        Navigate to **Infrastructure -> Hosts**.

                        <img src="./resources/module3_lab1/s1.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 3.1.2

                        Press **Create** to start the wizard.

                        <img src="./resources/module3_lab1/s2.png" class="img_80_percent">
                        
                        ---
                        <br>
                           
                        #### 3.1.3

                        Set the IP to **127.0.0.1**.

                        <img src="./resources/module3_lab1/s3.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 3.1.4

                        Add the new host to the **default** cluster.
                        
                        <img src="./resources/module3_lab1/s4.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 3.1.5

                        You now must have two hosts in the list - **127.0.0.1** and **localhost**.

                        <img src="./resources/module3_lab1/s5.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 3.1.6

                        Select **localhost** and press the **Offline** button. 

                        <img src="./resources/module3_lab1/s6.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 3.1.7

                        The host must change the status light from **Green** to **Red**.

                        <img src="./resources/module3_lab1/s7.png" class="img_80_percent">

                        ---
                        <br>

                        ### Tag a Host with a Custom Attribute.

                        ---
                        <br>
                           
                        #### 3.1.8

                        Select the **127.0.0.1** and expand the info card.

                        <img src="./resources/module3_lab1/s8.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 3.1.9

                        Scroll down and add the key **TYPE** with the value **PRODUCTION**.

                        <img src="./resources/module3_lab1/s9.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 3.1.10

                        Press anywhere to save the changes.

                        <img src="./resources/module3_lab1/s10.png" class="img_80_percent">

                        ---
                        <br>
                            
                        ### Congratulations, you've completed the assignment!
                    </script>
                </section>
            </section>


            <!-- Module 4 - Lab 1 -->
            <section>
                <section data-markdown>
                    <script type="text/template">
                        ## Module 5 - Lab 1 : Images & Marketplaces
                         
                        ---
                        <br>
                            
                        ## Objective(-s):
                        - Add a Marketplace.
                        - Import an Image and Template.
                          
                        ---
                        <br>

                        ## Add a Marketplace.

                        ---
                        <br>
                           
                        #### 5.1.1

                        Navigate to **Storage -> Marketplaces**.

                        <img src="./resources/module5_lab1/s1.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 5.1.2

                        Press **Create** to start the Marketplace wizard.

                        <img src="./resources/module5_lab1/s2.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 5.1.3

                        Fill in Name and Description according to your preferences.

                        Make sure to set **Storage Backend** to **OpenNebula Systems**.

                        <img src="./resources/module5_lab1/s3.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 5.1.4

                        Set **Endpoint URL for marketplace** to https://community-marketplace.opennebula.io/.

                        <img src="./resources/module5_lab1/s4.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 5.1.5

                        Make sure that the status light is **green** on the newly added marketplace.

                        **If your new marketplace shows 0 0, then Disable and Enable the marketplace.** 

                        <img src="./resources/module5_lab1/s5.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 5.1.6

                        Logout from **oneadmin** and login as **cloud-user**.

                        <img src="./resources/module5_lab1/s6.png" class="img_60_percent">

                        ---
                        <br>
                           
                        #### 5.1.7

                        Navigate to **Storage -> Apps**.

                        <img src="./resources/module5_lab1/s7.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 5.1.8

                        Search for **NixOS**. Select **NixOS** and press **Import**.

                        <img src="./resources/module5_lab1/s8.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 5.1.9

                        You can set the name for VM Template or Image as desired or leave as is.

                        <img src="./resources/module5_lab1/s9.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 5.1.10

                        Select the **default** datastore from the list and press **Finish**.

                        <img src="./resources/module5_lab1/s10.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 5.1.11

                        Navigate to **Storage -> Images**. 

                        <img src="./resources/module5_lab1/s11.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 5.1.12

                        Wait until the status light of newly important image turns **Green**.

                        <img src="./resources/module5_lab1/s12.png" class="img_80_percent">

                        ---
                        <br>
                            
                        ### Congratulations, you've completed the assignment!
                    </script>
                </section>
            </section>

            <!-- Module 6 - Lab 1 -->
            <section>
                <section data-markdown>
                    <script type="text/template">
                        ## Module 6 - Lab 1 : Virtual Networks 
                         
                        ---
                        <br>
                            
                        ## Objective(-s):
                        - Create a Virtual Network.
                          
                        ---
                        <br>

                        ###	Create a Virtual Network.
                           
                        ---
                        <br>
                           
                        #### 6.1.1

                        Make sure you're signed in as **oneadmin**.

                        <img src="./resources/module6_lab1/s1.png" class="img_50_percent">

                        ---
                        <br>
                           
                        #### 6.1.2

                        Navigate to **Networks -> Virtual Networks**. 

                        <img src="./resources/module6_lab1/s2.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 6.1.3

                        Press **Create** to start the Network wizard.

                        <img src="./resources/module6_lab1/s3.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 6.1.4

                        Name the way you want and make sure the **default** cluster is selected. 

                        <img src="./resources/module6_lab1/s4.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 6.1.5

                        On the **Configuration** tab set the type to **Bridged**. 

                        Toggle the **Use only private host networking**.

                        <img src="./resources/module6_lab1/s5.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 6.1.6

                        Switch to **Addresses** tab. 

                        And press **+ Address Range**.

                        <img src="./resources/module6_lab1/s6.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 6.1.7

                        Set the **First IPv4 address** field to **192.168.0.20**.

                        Set **Size** to **20** and press **Accept**.

                        <img src="./resources/module6_lab1/s7.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 6.1.8

                        Press **Finish** to add the network and close the wizard.

                        <img src="./resources/module6_lab1/s8.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 6.1.9

                        After closing the wizrd you must have two networks. 

                        <img src="./resources/module6_lab1/s9.png" class="img_80_percent">
                            
                        ---
                        <br>
                            
                        ### Congratulations, you've completed the assignment!
                    </script>
                </section>
            </section>

            <!-- Module 7 - Lab 1 -->
            <section>
                <section data-markdown>
                    <script type="text/template">
                        ## Module 7 - Lab 1 : Virtual Machine Templates
                         
                        ---
                        <br>
                            
                        ## Objective(-s):
                        - Clone the VM Template.
                        - Adjust the VM Templates.
                          
                        ---
                        <br>

                        ###	Clone the VM Template.
                           
                        ---
                        <br>
                           
                        #### 7.1.1
                        
                        Login as **cloud-user**.

                        <img src="./resources/module7_lab1/s1.png" class="img_50_percent">

                        ---
                        <br>
                           
                        #### 7.1.2

                        Navigate to **Templates -> VM Templates**.

                        <img src="./resources/module7_lab1/s2.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.1.3

                        Select **Alpine Linux 3.XX** and press **Clone**.

                        <img src="./resources/module7_lab1/s3.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.1.4

                        Make sure that **image cloning** checkbox isn't active and name the VM Template as **App Server**.

                        <img src="./resources/module7_lab1/s4.png" class="img_80_percent">

                        ---
                        <br>
                           
                        ### Clone the Alpine Linux 3.XX template one more time, but this time set the name to DB Server instead.

                        ---
                        <br>
                           
                        #### 7.1.5

                        Now you must have two new VM Templates.

                        <img src="./resources/module7_lab1/s5.png" class="img_80_percent">


                        ---
                        <br>
                           
                        ### Adjust the VM Templates.

                        ---
                        <br>
                           
                        #### 7.1.6

                        Select the App Server VM Template and press **Update**. 

                        <img src="./resources/module7_lab1/s6.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.1.7

                        Change the **Memory** value from **256** to **1024** and proceed ot the **Next** step of the wizard.

                        <img src="./resources/module7_lab1/s7.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.1.8

                        Under the **Storage** tab locate the currently attached disk and press the **edit** button.

                        <img src="./resources/module7_lab1/s8.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.1.9

                        Make sure that **Alpine Linux 3.XX** is selected.

                        <img src="./resources/module7_lab1/s9.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.1.10

                        Change the **Size on instantiate** parameter from **512** to **5120** and press **Finish**.

                        <img src="./resources/module7_lab1/s10.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.1.11

                        You should see that the size has been changed to 5 GB.

                        <img src="./resources/module7_lab1/s11.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.1.12

                        Switch to the **Context** tab.

                        <img src="./resources/module7_lab1/s12.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.1.13

                        Scroll down to the **User inputs** section and create a new input.

                        Name: **DB_HOST**

                        Type: **Text**

                        Either keep "Description" empty or anything you like.

                        **Leave the "Default value" empty!**

                        Toggle the **Mandatory** switch.
                        
                        Press **+ Add**
                        
                        <img src="./resources/module7_lab1/s13.png" class="img_60_percent">
                        
                        ---
                        <br>
                        
                        #### 7.1.14
                        
                        Add another one
                        
                        Name: **APP_DATABASE**
                        
                        Type: **Text**
                        
                        Either keep "Description" empty or anything you like.
                        
                        Default value: **app**

                        Toggle the **Mandatory** switch.

                        Press **+ Add**

                        <img src="./resources/module7_lab1/s14.png" class="img_60_percent">

                        ---
                        <br>
                           
                        #### 7.1.15

                        Add another one
                        
                        Name: **DB_USER**
                        
                        Type: **Text**
                        
                        Either keep "Description" empty or anything you like.
                        
                        Default value: **appuser**

                        Toggle the **Mandatory** switch.

                        Press **+ Add**

                        <img src="./resources/module7_lab1/s15.png" class="img_60_percent">

                        ---
                        <br>
                           
                        #### 7.1.16

                        Add another one
                        
                        Name: **DB_USER_PASSWORD**
                        
                        Type: **Text**
                        
                        Either keep "Description" empty or anything you like.
                        
                        Default value: **appassword**

                        Toggle the **Mandatory** switch.

                        Press **+ Add**

                        <img src="./resources/module7_lab1/s16.png" class="img_60_percent">

                        ---
                        <br>
                           
                        #### 7.1.17

                        Finally add the **optional** **TIMEZONE** input.

                        Name: **TIMEZONE**
                        
                        Type: **Text**
                        
                        Either keep "Description" empty or anything you like.
                        
                        Default value: **UTC**

                        Keep  **Mandatory** switch un-toggled.

                        Press **+ Add**

                        <img src="./resources/module7_lab1/s17.png" class="img_60_percent">

                        ---
                        <br>
                           
                        #### 7.1.18

                        You should have 5 variables in the list. Proceed to the **Next** script of the wizard.

                        <img src="./resources/module7_lab1/s18.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.1.19

                        Leave the **Custom Variables** screen as is and press **Finish**.

                        <img src="./resources/module7_lab1/s19.png" class="img_80_percent">

                        ---
                        <br>

                        ### Perform the same steps except the CONTEXT configuration on the "DB Server" VM Template!

                        ---
                        <br>
                            
                        ### Congratulations, you've completed the assignment!

                    </script>
                </section>
            </section>

            <!-- Module 7 - Lab 2 -->
            <section>
                <section data-markdown>
                    <script type="text/template">
                        ## Module 7 - Lab 2 : Virtual Machines
                         
                        ---
                        <br>
                            
                        ## Objective(-s):
                        - Instantiate the App Server and DB Server.
                        - Install software on App Server.
                        - Install software on DB Server.
                        - Save both Disks as an Image.
                          
                        ---
                        <br>

                        ###	Instantiate the App Server and DB Server.
                           
                        ---
                        <br>
                           
                        #### 7.2.1

                        Naviagte to **Instances -> VMs**.

                        <img src="./resources/module7_lab2/s1.png" class="img_80_percent">
                        
                        ---
                        <br>
                           
                        #### 7.2.2

                        Press **+ Create** to start the VM Instantiation wizard.

                        <img src="./resources/module7_lab2/s2.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.2.3

                        Select the **DB Server** VM Template.

                        <img src="./resources/module7_lab2/s3.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.2.4

                        Keep the **Configuration** tab as is and move on to the **Next** tab.

                        <img src="./resources/module7_lab2/s4_1.png" class="img_80_percent">

                        Same with **Advanced options**. Press **Finish**.

                        <img src="./resources/module7_lab2/s4_2.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.2.5

                        Press **+ Create** once again, but this time select the **App Server** VM Template.

                        <img src="./resources/module7_lab2/s5.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.2.6

                        Keep the **Configuration** tab as is and move on to the **Next** tab.

                        <img src="./resources/module7_lab2/s6.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.2.7

                        Under the **User inputs** tab set the **DB_HOST** to something like **127.0.0.1**. At this point it doesn't matter. Since the value is **Mandatory**, we can't leave it empty.

                        <img src="./resources/module7_lab2/s7.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.2.8

                        Keep the **Advanced options** as is and press **Finish**.

                        <img src="./resources/module7_lab2/s8.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.2.9

                        Make sure that VM's status lights are **Green** and write down the IP address of each. 

                        <img src="./resources/module7_lab2/s9.png" class="img_80_percent">

                        ---
                        <br>

                        ### Install software on DB Server.

                        ---
                        <br>
                           
                        #### 7.2.10

                        Connect to DB Server VM using the **onevm** command:

                        ```console[]
                        # sudo -i -u oneadmin
                        $ ssh root@<DB Server IP>
                        ```
                        
                        Download the DB Prep script.

                        ```console[]
                        # script='https://raw.githubusercontent.com/alpeon/training-files/refs/heads/main/VMs/prep_db.sh'
                        # curl $script -o prep_db.sh
                            % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                                        Dload  Upload   Total   Spent    Left  Speed
                        100   707  100   707    0     0    983      0 --:--:-- --:--:-- --:--:--  1020
                        ```
                            
                        ---
                        <br>
                        
                        #### 7.2.11

                        Launch the script and wait until it's going to finish!

                        ```console[]
                        # bash prep_db.sh
                        ...
                        Installing MariaDB/MySQL system tables in '/var/lib/mysql' ...
                        OK
                        ...
                        Consider joining MariaDB's strong and vibrant community:
                        https://mariadb.org/get-involved/

                        * Caching service dependencies ...                                       [ ok ]
                        * Starting mariadb ...
                        250825 11:13:13 mysqld_safe Logging to syslog.
                        250825 11:13:13 mysqld_safe Starting mariadbd daemon with databases from /var/lib/mysql 
                        ```

                        ---
                        <br>
                        
                        #### 7.2.11

                        Execute mysql select statement to verify that the user was added successfully:

                        ```console[1,11]
                        # mysql -u root -e 'select Host, User,Password from mysql.user;'
                        mysql: Deprecated program name. It will be removed in a future release, use '/usr/bin/mariadb' instead
                        +-----------+-------------+-------------------------------------------+
                        | Host      | User        | Password                                  |
                        +-----------+-------------+-------------------------------------------+
                        | localhost | mariadb.sys |                                           |
                        | localhost | root        | invalid                                   |
                        | localhost | mysql       | invalid                                   |
                        |           | PUBLIC      |                                           |
                        | localhost |             |                                           |
                        | %         | appuser     | *44440582CE6B34610E78D820F219FD95B0F15647 |
                        +-----------+-------------+-------------------------------------------+
                        ```
                        
                        Exit from the DB Server's console.

                        ```console[]
                        # exit
                        ```
                        
                        ---
                        <br>
                        
                        #### 7.2.12
                        
                        Connect to App Server using the **onevm** Command Line:

                        ```console[]
                        $ ssh root@<App Server's IP>
                        ```

                        Download the App Prep script.

                        ```console[]
                        # script='https://raw.githubusercontent.com/alpeon/training-files/refs/heads/main/VMs/prep_app.sh'
                        # curl $script -o prep_app.sh
                        % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                                            Dload  Upload   Total   Spent    Left  Speed
                        100   180  100   180    0     0    205      0 --:--:-- --:--:-- --:--:--   216
                        ```
                        ---
                        <br>
                        
                        #### 7.2.13
                        
                        Run the App Prep script.

                        ```console[1,4,8,10]
                        # bash prep_app.sh
                        ...
                        Executing busybox-1.37.0-r12.trigger
                        OK: 179 MiB in 171 packages
                        ...
                        Cloning into 'app'...
                        ...
                        Resolving deltas: 100% (3/3), done.
                        ...
                        Successfully installed Flask-3.0.3 Jinja2-3.1.4 MarkupSafe-3.0.2 Werkzeug-3.0.4 blinker-1.8.2 click-8.1.7 itsdangerous-2.2.0 mysql-connector-python-9.1.0
                        ```
                        
                        ---
                        <br>
                        
                        #### 7.2.14

                        List the **app** directory.

                        ```console[]
                        # ls -lah app
                        total 15K
                        drwxr-xr-x    4 root     root        1.0K Jul 25 00:19 .
                        drwx------    8 root     root        1.0K Jul 25 00:20 ..
                        drwxr-xr-x    8 root     root        1.0K Jul 25 00:19 .git
                        -rw-r--r--    1 root     root        4.6K Jul 25 00:19 .gitignore
                        -rw-r--r--    1 root     root        1.0K Jul 25 00:19 LICENSE
                        -rw-r--r--    1 root     root        3.0K Jul 25 00:19 app.py
                        -rw-r--r--    1 root     root         139 Jul 25 00:19 requirements.txt
                        drwxr-xr-x    2 root     root        1.0K Jul 25 00:19 templates
                        ```

                        Exit from the App Server's console.

                        ```console[]
                        # exit
                        ```

                        ---
                        <br>

                        ### Save both Disks as an Image.

                        ---
                        <br>

                        ### Attention! We are performing this task assuming that the Hypervisor is set to QEMU thus VMs must be powered down. KVM-based hypervisors can perform this task while the VMs are RUNNING!

                        ---
                        <br>
                           
                        #### 7.2.15

                        Navigate to **Instances -> VMs**.

                        <img src="./resources/module7_lab2/s15.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.2.16

                        Select all your Virtual Machines, from the **VM state** drop-down menu select **Poweroff**.

                        <img src="./resources/module7_lab2/s16.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.2.17

                        Wait until both VMs are powered down.

                        <img src="./resources/module7_lab2/s17.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.2.18

                        Open the info card of the App Server VM and navigate to **Storage** and press the **Save as** icon near the disk.

                        <img src="./resources/module7_lab2/s18.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.2.19

                        Name the new Image as **App Server** and press **Accept**.

                        <img src="./resources/module7_lab2/s19.png" class="img_80_percent">

                        ---
                        <br>
                           
                        ### Perform the same task on the DB Server Virtual Machine, but this time name the Image as "DB Server".

                        ---
                        <br>

                        
                           
                        #### 7.2.20

                        Navigate to **Storage -> Images**.

                        <img src="./resources/module7_lab2/s20.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.2.21

                        Make sure that both newly created Images having the **Green** status light.

                        <img src="./resources/module7_lab2/s21.png" class="img_80_percent">

                       

                        ---
                        <br>

                        ### Congratulations, you've completed the assignment!
                    </script>
                </section>
            </section>

            <!-- Module 7 - Lab 3 -->
            <section>
                <section data-markdown>
                    <script type="text/template">
                        ## Module 7 - Lab 3 : Deploy the Custom Application 
                            
                        ---
                        <br>
                            
                        ## Objective(-s):
                        - Adjust the App Server VM Template.
                        - Adjust the DB Server VM Templates.
                        - Instantiate both VM Templates.
                        - Test Drive an App to make sure it works.
                            
                        ---
                        <br>

                        ###	Adjust he App Server VM Templates.
                            
                        ---
                        <br>
                            
                        #### 7.3.1

                        Navigate to **Templates -> VM Templates**

                        <img src="./resources/module7_lab3/s1.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.2

                        Select **App Server** and press **Update**.
                        
                        <img src="./resources/module7_lab3/s2.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.3

                        Keep the **General** settings as is and press **Next**.

                        <img src="./resources/module7_lab3/s3.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.4

                        Under the **Storage** tab locate the **Alpine Linux 3.XX** disk and press **Edit**.

                        <img src="./resources/module7_lab3/s4.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.5

                        Select the **App Server** Image from the list.

                        <img src="./resources/module7_lab3/s5.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.6

                        Leave **Advanced options** as is.

                        <img src="./resources/module7_lab3/s6.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.7

                        Continue only if you have **App Server** set as the only disk!

                        <img src="./resources/module7_lab3/s7.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.8

                        Swich to **Network** tab and press the **Attach NIC** button. 

                        <img src="./resources/module7_lab3/s8.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.9

                        Keep **Advanced options** as is.

                        <img src="./resources/module7_lab3/s9.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.10

                        Select the **host-only** network from the list.

                        <img src="./resources/module7_lab3/s10.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.11

                        Keep **Network values** as is.

                        <img src="./resources/module7_lab3/s11.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.12

                        Keep **QoS** settings as is and press **Finish**.

                        <img src="./resources/module7_lab3/s12.png" class="img_80_percent">
                        
                        ---
                        <br>
                            
                        #### 7.3.13

                        Make sure that this template now has **two networks**!

                        <img src="./resources/module7_lab3/s13.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.14

                        Navigate to **Context** tab and scroll down to the **Start script** window and add the code below (make sure it looks the same way as on the picture without extra spaces).

                        ```console[]
                        source /root/bin/activate
                        cd /root/app
                        python3 -u app.py &
                        ```

                        <img src="./resources/module7_lab3/s14.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.15

                        Leave **Custom Variables** as is and press **Finish**.

                        <img src="./resources/module7_lab3/s15.png" class="img_80_percent">

                        ---
                        <br>
                            
                        ### Adjust the DB Server VM Template.

                        ---
                        <br>

                        #### 7.3.16
                        
                        Select the **DB Server** VM Template and press **Update**.

                        <img src="./resources/module7_lab3/s16.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.17

                        Under the **Storage** tab locate the **Alpine Linux 3.XX** disk and press **Edit**.

                        <img src="./resources/module7_lab3/s17.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.18

                        Select the **DB Server** Image from the list.

                        <img src="./resources/module7_lab3/s18.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.19

                        Leave **Advanced options** as is.

                        <img src="./resources/module7_lab3/s19.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.20

                        Continue only if you have **DB Server** set as the only disk!

                        <img src="./resources/module7_lab3/s20.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.21
                        
                        Under the **Network** tab locate the **NIC0: vnet** and press the **Edit** button.

                        <img src="./resources/module7_lab3/s21.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.22

                        Keep **Advanced options** as is.

                        <img src="./resources/module7_lab3/s22.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.23

                        Select the **host-only** network from the list.

                        <img src="./resources/module7_lab3/s23.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.24

                        Keep **Network & values** as is.

                        <img src="./resources/module7_lab3/s24.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.25

                        Keep **QoS** as is and press **Finish**.

                        <img src="./resources/module7_lab3/s25.png" class="img_80_percent">

                        ---
                        <br>
                            
                        #### 7.3.26

                        Switch to **Context** tab.

                        ```console[]
                        rc-service mariadb start
                        ```

                        <img src="./resources/module7_lab3/s26.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.3.27

                        Kepp **Custom Variables** as is.

                        <img src="./resources/module7_lab3/s27.png" class="img_80_percent">

                        ---
                        <br>
                           
                        ### Instantiate both VM Templates.

                        ---
                        <br>

                        #### 7.3.28

                        Navigate **Instances -> VMs**.

                        <img src="./resources/module7_lab3/s28.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.3.29

                        Select all VMs and **Terminate hard** from the drop-down menu.

                        <img src="./resources/module7_lab3/s29.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.3.30

                        Wait until all VMs are destroyed and then press **+ Create**.

                        <img src="./resources/module7_lab3/s30.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.3.31

                        Select the **DB Server**.

                        <img src="./resources/module7_lab3/s31.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.3.32

                        Leave **Configuration** as is.

                        <img src="./resources/module7_lab3/s32_1.png" class="img_80_percent">

                        And the **Advanced options** as is and press **Finish**.

                        <img src="./resources/module7_lab3/s32_2.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.3.33

                        Copy the **IP address** of a **DB Server** VM and press **+ Create** once again.

                        <img src="./resources/module7_lab3/s33.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.3.34

                        Select **App Server**.

                        <img src="./resources/module7_lab3/s34.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.3.35

                        Keep **Configuration** as is.

                        <img src="./resources/module7_lab3/s35.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.3.36

                        Paste the copied IP Address from the DB Server to the **DB_HOST** field.

                        <img src="./resources/module7_lab3/s36.png" class="img_80_percent">

                        ---
                        <br>
                           
                        #### 7.3.37

                        Leave **Advanced options** as is and press **Finish**.

                        <img src="./resources/module7_lab3/s37.png" class="img_80_percent">
                        
                        ---
                        <br>
                           
                        #### 7.3.38

                        Wait until the **App Server** is running and copy its IP Address.

                        <img src="./resources/module7_lab3/s38.png" class="img_80_percent">

                        ---
                        <br>
                           
                        ### Test Drive an App to make sure it works.
                        ---
                        <br>

                        #### 7.3.39

                        Go to the OpenNebula's Command Line and execute the following commands. 
                        
                        Make sure to use the IP Address that you've copied in the previous step (in this guide we assusme that the IP is 172.16.100.2)

                        Create the Database to make sure that the connection between the App Server and DB Server is working. 

                        ```console[]
                        $ curl 172.16.100.2:5000/create-db
                        {"message":"Table 'data' created successfully"}
                        ```

                        Insert the dummy data. Execute this command a few times.

                        ```console[]
                        $ curl 172.16.100.2:5000/insert-dummy
                        {"message":"Dummy data inserted successfully"}
                        $ curl 172.16.100.2:5000/insert-dummy
                        {"message":"Dummy data inserted successfully"}
                        ```
                        
                        Now query for the data to finalize the test. 

                        ```console[]
                        $ curl 172.16.100.2:5000/get-data
                        [{"data1":"2025-08-25 13:21:25","data2":"31","id":1},{"data1":"2025-08-25 13:21:26","data2":"64","id":2}]
                        ```

                        ---
                        <br>
                            
                        ### Congratulations, you've completed the assignment!
