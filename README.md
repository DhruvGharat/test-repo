import json
import boto3

s3 = boto3.client('s3')

def lambda_handler(event, context):
    bucket_name = 'your-bucket-name'     # change this to your S3 bucket
    file_name = 'data.json'

    data = {
        "name": "Asmit",
        "age": 21,
        "course": "IT Engineering"
    }

    # Upload JSON to S3
    s3.put_object(
        Bucket=bucket_name,
        Key=file_name,
        Body=json.dumps(data)
    )

    print("✅ Object has been uploaded to S3!")
    return {
        'statusCode': 200,
        'body': json.dumps('File uploaded successfully!')
    }

    
