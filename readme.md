# Mystical Magic 8 Ball Experience - Serverless Application

This project is a serverless implementation of the classic Magic 8 Ball, allowing users to interact with the application via a web interface. The backend is powered by AWS Lambda, while the frontend is hosted on an S3 bucket. The application answers user questions with random responses, creating a fun and interactive experience.

## Project Structure

- **`index.html`**: The main frontend file, providing the user interface for interacting with the Magic 8 Ball.
- **`app.py`**: The Lambda function that processes API requests and returns a random Magic 8 Ball response.
- **`template.yaml`**: The AWS SAM template that defines the serverless architecture, including the Lambda function and API Gateway.

## Getting Started

### Prerequisites

Before you start, ensure you have the following installed:

- AWS CLI configured with your credentials.
- AWS SAM CLI.
- An AWS account with permissions to create Lambda functions, API Gateway, and S3 buckets.

### Deployment Instructions

1. **Clone the Repository**

   Clone the repository to your local machine using the following command:

   ```bash
   git clone https://github.com/AmirMalaeb/magic-8-ball-SAM.git
   cd magic-8-ball-SAM
   ```

2. **Package the Application**
   Package the application using the AWS SAM CLI. Replace your-s3-bucket with the name of an S3 bucket in your account where the deployment artifacts will be stored.  
   
   ```bash
   sam package --template-file template.yaml --output-template-file packaged.yaml --s3-bucket your-s3-bucket
   ```

3. **Deploy the Application**
   Deploy the application using the AWS SAM CLI. This command will create the necessary AWS resources and deploy your application.

   ```bash
   sam deploy --template-file packaged.yaml --stack-name magic-8-ball-stack --capabilities CAPABILITY_IAM
   ```

4. **Obtain the API Endpoint**
    After the deployment is complete, note the API Gateway endpoint URL provided by the Magic8BallApiUrl output in the terminal. This URL will be used in the frontend HTML file to make requests to the backend.


5. **Update the Frontend**
Open the index.html file in a text editor and replace the placeholder API URL in the script section (line 232) with your actual API Gateway URL obtained from the previous step.

6. **Upload the Frontend to S3 (Optional)**
    If you want to host the frontend on S3:
	1.	Create a new S3 bucket in the AWS S3 Console.
	2.	Enable static website hosting on the bucket.
	3.	Upload the index.html file to the bucket.
	4.	Set the file permissions to be publicly readable.
    
    You can then access the frontend through the S3 bucket’s URL.

**Usage**

Once everything is set up, open the index.html file in your browser or access it through the S3 bucket URL. Type your question into the input box, click the Magic 8 Ball, and see what the mystical ball has to say!

**Troubleshooting**

	•	CORS Issues: If you encounter CORS issues when accessing the API, ensure that CORS is properly configured in the API Gateway as outlined in the template.yaml file.
	•	API Not Responding: Ensure that the API Gateway URL in the index.html file is correct and that the Lambda function is successfully deployed.

