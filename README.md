# stelligent_mini_project
An automated build of an Apache HTTPD web server on Amazon Linux with a static HTML page, created with AWS resources, and utilizing infrastructure tests with Serverspec.

PRE-REQUISITES:
- AWS IAM user with full permissions to CloudFormation and EC2, whose credentials are configured for the AWS CLI
- AWS KeyPair, named MyKeyPair (for the purposes of infrastructure tests), with the private key stored locally under ~/.ssh/MyKeyPair
- Serverspec local install

To execute the creation of the webserver resources, use the full local location of the template file.
```
aws cloudformation create-stack --stack-name <stack_name> --template-body file:////Users//<username>//stelligent_mini_project//webserver_template.json
```

To validate the template file:  
```
aws cloudformation validate-template --template-body file:////Users//<username>//stelligent_mini_project//webserver_template.json
```
  
To verify the server is up and running:
```
aws cloudformation describe-stacks --stack-name <stack_name>
```
  
This will contain the Output of the hostname that can be navigated to in a browser.  You can pull this specifically with:
```
aws cloudformation describe-stacks --stack-name <stack_name> | grep OutputValue
```

To execute the infrastructure tests (once Cloudformation is complete), use the hostname for:
```
HOST=<host_name> rake spec
```

To delete the stack:
```
aws cloudformation delete-stack --stack-name <stack_name>
```
