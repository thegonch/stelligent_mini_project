# stelligent_mini_project
An automated build of an Apache HTTPD web server on Amazon Linux with a static HTML page, created with AWS resources, and utilizing infrastructure tests.

To execute:
aws cloudformation create-stack --stack-name myteststack --template-body file:////Users//stephengoncher//aws//stelligent_mini_project//webserver_template.json

To validate the template file:
aws cloudformation validate-template --template-boy file:////Users//stephengoncher//aws//stelligent_mini_project//webserver_template.json
