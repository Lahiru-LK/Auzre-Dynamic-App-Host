CREATE Dynamic APP HOST

01 create Repor

02 Repor Clone 
	
        cmd open 

	i git clone https://github.com/Azure-Samples/php-docs-hello-world 
	ii cd php-docs-hello-world

			how to local run php app
				
				 * open wampsercer
				 * copy paste clone  folder (php-docs-hello-world) ---> C:\wamp64\www
				* admin : localhost/php-docs-hello-world/	

03 Resouse Group

	i Shell Open
		

		01 -- Creat User
							     Lahiru749	           lmsLK@2x
		$ az webapp deployment user set --user-name <username> --password <password> 
		
		
		02 --  Create a resource group 	

					   myresource001php
		$ az group create --name <Resour Group Name> --location "West Europe"


		03 -- Create an Azure App Service plan

						     myappplane001php	                     myresource001php

		 $ az appservice plan create --name <App Serice Plan Name> --resource-group <Resour Group Name> --sku B1 --is-linux


		04 -- Create a web app

							myresource001php           myappplane001php           phpmyapp001
		$ az webapp create --resource-group <Resour Group Name> --plan <App Serice Plan Name> --name <app-name> --runtime "PHP|8.3" --deployment-local-git


		-- Copy  to 'deploymentLocalGitUrl :' 
				
				"https://Lahiru749@phpmyapp001.scm.azurewebsites.net/phpmyapp001.git"

		05 show to apps to php

		-- Copy to '"name": "phpmyapp001.scm.azurewebsites.net",'
				
				"phpmyapp001.scm.azurewebsites.net"

		
		06 Push to Azure from Git (cmd for your project file location)

							https://Lahiru749@phpmyapp001.scm.azurewebsites.net/phpmyapp001.git	
				$ git remote add azure <deploymentLocalGitUrl-from-create-step> 
				$ git push azure master 


		07 Update locally and redeploy the code
			
			i go to index.php 
			ii eddit to  'Hello Azure!' 
			
			-- local cmd --------

			git commit -am "updated output" 
			git push azure master

		08 Resource Delelete

			az group delete --name myResourceGroup
