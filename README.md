#Sample AWS Lambda function for Alexa
This is my take on a simple [AWS Lambda]  function that demonstrates how to write a skill for the Amazon Echo using the Alexa SDK. This is based on Amazon's ReindeerGames example. More on Amazon's lambda functions here - http://aws.amazon.com/lambda

## Setup
To run this  skill you need to do two things. The first is to deploy the example code in lambda, and the second is to configure the Alexa skill to use Lambda.

### AWS Lambda Setup
1. Go to the AWS Console and click on the Lambda link. Note: ensure you are in us-east or you won't be able to use Alexa with Lambda.
2. Click on the Create a Lambda Function or Get Started Now button.
3. Skip the blueprint
4. Name the Lambda Function "Cat_Facts_Trivia-Skill".
5. Select the runtime as Node.js
5. Go to the the src directory, select the index.js file and then create a zip file, make sure the zip file does not contain the src directory itself, otherwise Lambda function will not work.
6. Select Code entry type as "Upload a .ZIP file" and then upload the .zip file to the Lambda
7. Keep the Handler as index.handler (this refers to the main js file in the zip).
8. Create a basic execution role and click create.
9. Leave the Advanced settings as the defaults.
10. Click "Next" and review the settings then click "Create Function"
11. Click the "Event Sources" tab and select "Add event source"
12. Set the Event Source type as Alexa Skills kit and Enable it now. Click Submit.
13. Copy the ARN from the top right to be used later in the Alexa Skill Setup

### Alexa Skill Setup
1. Go to the [Alexa Console](https://developer.amazon.com/edw/home.html) and click Add a New Skill.
2. Set "CatFactsTrivia" as the skill name and "cat facts" as the invocation name, this is what is used to activate your skill. For example you would say: "Alexa, tell cat facts to start a new game"
3. Select the Lambda ARN for the skill Endpoint and paste the ARN copied from above. Click Next.
4. Copy the Intent Schema from the included IntentSchema.json.
5. Add a Custom Slot Type. The name of the type is 'LIST_OF_ANSWERS' while the values for the type are the values in the LIST_OF_ANSWERS file.
6. Copy the Sample Utterances from the included SampleUtterances.txt. Click Next.
7. [optional] go back to the skill Information tab and copy the appId. Paste the appId into the index.js file for the variable APP_ID,
   then update the lambda source zip file with this change and upload to lambda again, this step makes sure the lambda function only serves request from authorized source.
8. You are now able to start testing your sample skill! You should be able to go to the [Echo webpage](http://echo.amazon.com/#skills) and see your skill enabled.
9. In order to test it, try to say some of the Sample Utterances from the Examples section below.
10. Your skill is now saved and once you are finished testing you can continue to publish your skill.

## Examples
    User: "Alexa, tell cat facts to start a new game"
    Alexa: "Cat Facts Trivia. I will ask you 5 questions..."
