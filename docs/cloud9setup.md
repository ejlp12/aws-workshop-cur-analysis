## Cloud9 Setup

> Ad blockers, javascript disablers, and tracking blockers should be disabled for the Cloud9 domain, or connecting to the workspace might be impacted.


1. Create a [Cloud9 Environment in us-east-1 region](https://eu-west-1.console.aws.amazon.com/cloud9/home?region=us-east-1)

2. Select Create environment

3. Name it `curworkshop` and set the “Cost-saving setting” to After four hours then take all other defaults

4. When it comes up, customize the environment by closing the **Welcome tab** and **Lower work area**, and opening a new Terminal tab in the main work area: 
    ![](https://reinvent2019.aws-management.tools/mgt306/en/images/intro/c9before.png)
    
    Your workspace should now look like this: 
    
    ![](https://reinvent2019.aws-management.tools/mgt306/en/images/intro/c9after.png)
    
5. We should configure our aws cli with our current region as default. Run this command in your terminal:
    ```
    export AWS_REGION="eu-east-1"
    echo "export AWS_REGION=${AWS_REGION}" >> ~/.bash_profile
    aws configure set default.region ${AWS_REGION}
    aws configure get default.region
    ```
    
6. We will also need to know your AWS account ID and put into a variable `ACCOUNT_ID` to make your job easier later
    ```
    sudo yum install jq -y
    export ACCOUNT_ID=$(aws sts get-caller-identity|jq -r ".Account")
    ```
    
[BACK TO WORKSHOP GUIDE](../README.md)   
