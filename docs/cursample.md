In this workshop, you will skip the [CONFIGURE COST AND USAGE REPORTS steps](https://wellarchitectedlabs.com/cost/100_labs/100_1_aws_account_setup/3_cur/) because you are using EventEngine account. If you are doing the lab using your own AWS account, then you can follow those steps.

1. Run this command in your Cloud9 IDE to create and copy sample CUR files. Change `yourname` to your real name
    ```
    CUR_S3_BUCKET=yourname-cur-hourly-billing
    aws s3 mb s3://$CUR_S3_BUCKET --region us-east-1 
    mkdir -p sample

    cd sample
    wget https://wellarchitectedlabs.com/Cost/200_4_Cost_and_Usage_Analysis/Code/Oct2018-WorkshopCUR-00001.snappy.parquet -P "./WorkshopCUR/WorkshopCUR/year=2018/month=10"
    wget https://wellarchitectedlabs.com/Cost/200_4_Cost_and_Usage_Analysis/Code/Nov2018-WorkshopCUR-00001.snappy.parquet -P "./WorkshopCUR/WorkshopCUR/year=2018/month=11"
    wget https://wellarchitectedlabs.com/Cost/200_4_Cost_and_Usage_Analysis/Code/Dec2018-WorkshopCUR-00001.snappy.parquet -P "./WorkshopCUR/WorkshopCUR/year=2018/month=12"

    aws s3 cp . s3://$CUR_S3_BUCKET/cur --recursive

    ## Make sure that the files are already in the correct S3 folder
    aws s3 ls s3://$CUR_S3_BUCKET/cur/WorkshopCUR/WorkshopCUR/year=2018/month=10/
    aws s3 ls s3://$CUR_S3_BUCKET/cur/WorkshopCUR/WorkshopCUR/year=2018/month=11/
    aws s3 ls s3://$CUR_S3_BUCKET/cur/WorkshopCUR/WorkshopCUR/year=2018/month=12/
    ```
    
   From the last 3 commands you should get output similar to this, which means 3 parquet files are successfully copied in S3 bucket:
    ```
    2020-09-08 20:07:42    1486391 Oct2018-WorkshopCUR-00001.snappy.parquet
    2020-09-08 20:07:42    1565532 Nov2018-WorkshopCUR-00001.snappy.parquet
    2020-09-08 20:07:42    1118918 Dec2018-WorkshopCUR-00001.snappy.parquet
    ```
2. Create an S3 bucket for Athena query result for later use. Change `yourname` to your real name

   ```
   ATHENA_RESULT_S3_BUCKET=yourname-curworkshop-athena-result
   aws s3 mb s3://$CUR_S3_BUCKET
   ```
4. Open [S3 Console](https://s3.console.aws.amazon.com/s3/home) and explore the bucket created.
   
    
