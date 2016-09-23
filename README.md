# SignalFx CloudFormation template

Use this CloudFormation Template to create an IAM Role for Cross Account Access to [SignalFx](signalfx.com).

## Instructions

1.  Login to SignalFx
1.  Go to the **Integrations** page and click on **Amazon CloudWatch**
1.  Click on the **Install** tab and save your **External ID**
1.  Login to the AWS Web Console and go to CloudFormation
1.  Click **Create Stack**
1.  Under "Choose a template", select **Upload a template to Amazon S3** and select the `signalfx.yaml` file from this repository.
1.  On the parameters page, enter a Stack name. I used `SignalFx-Access-Role`.
1.  Here is where you input the "External ID" from step 3 above.
1.  Continue through clicking Next, giving IAM capabilities until the Stack is being created.
1.  Once the stack status is `CREATE_COMPLETE`, click on the **Output** tab.
1.  Copy the **SignalFxRoleArn** and paste it into the SignalFx page.

### AWS CLI style

    aws cloudformation create-stack --stack-name "SignalFx-Access-Role2" \
      --template-body file://./signalfx.yaml --capabilities CAPABILITY_NAMED_IAM \
      --parameters "ParameterKey=SignalFxExternalId,ParameterValue=YOUR_EXTERNAL_ID"

    aws cloudformation describe-stacks --stack-name "SignalFx-Access-Role"


## License

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0 Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
