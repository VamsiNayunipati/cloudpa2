## Building a Wine Quality Prediction Model with Spark on AWS
### Cluster Creation:
1. Login to AWS Account and start the lab
2. Click on AWS Console
3. Search for EMR
4. Click on create cluster and give a name

    ![alt text](image.png)

5. Under Cluster scaling and provisioning, give 1 instance for core and 5 instances for Task
    
    ![alt text](image-1.png)

6. Under Cluster termination and node replacement, click on Manually terminate cluster and Use termination protection.

    ![alt text](image-2.png)

7. Under Security configuration and EC2 key pair, click on create key pair > name the key > select .pem and click on create key and go back and click on Browse and add the key.

    ![alt text](image-3.png)
    ![alt text](image-4.png)

8. Under Identity and Access Management (IAM) roles, for Service role choose EMR_DefaultRole and for Instance profile choose EMR_EC2_DefaultRole.

    ![alt text](image-5.png)

9. Click on Create Cluster
    
    ![alt text](image-6.png)

10. Search for EMR and click on it

    ![alt text](image-7.png)

11. Click on the created cluster
12. Click on Connect to the Primary node using SSM

    ![alt text](image-8.png)

13. Check for the Public IP address - 3.238.28.122 (may be different for others) and search for that IP address in the instances running.

    ![alt text](image-9.png)

### EC2 Instances:
14. Search for EC2 and click on it and then click on instances running.

    ![alt text](image-10.png)
    ![alt text](image-11.png)

15. Click on the instance with the same IP because it is the primary node.
16. Click on security Tab.

    ![alt text](image-12.png)

17. Click on (ElasticMapReduce-master) under Security groups.

    ![alt text](image-13.png)

18. Click on Edit inbound rules

    ![alt text](image-14.png)

19. Click on add rule, Select SSH under Type dropdown and MyIP under Source dropdown and click on save rules

    ![alt text](image-15.png)

20. Search for EMR and click on it

    ![alt text](image-16.png)

21. Click on the cluster and Click on Connect to the Primary node using SSH

    ![alt text](image-17.png)

22. Copy the ssh command

    ![alt text](image-18.png)

23. Open terminal from the .pem save location and run the command copied from above
(delete ~/ if not needed) and run it

    ![alt text](image-19.png)

24. Enter yes for continue connection and once it is successful it connects to EMR

    ![alt text](image-20.png)

### S3 Bucket Creation:
25. Once this is done, go to AWS Console and search for S3 and click on it

    ![alt text](image-21.png)

26. Click on Create Bucket

    ![alt text](image-22.png)

27. Write a bucket name and click on Create Bucket

    ![alt text](image-23.png)
    ![alt text](image-24.png)

28. After the successful creation of bucket, it will be like this

    ![alt text](image-25.png)

29. Click on the created bucket and click on upload files and then upload the require files (Working code and datasets)

    ![alt text](image-26.png)

30. If we click on the uploaded files, then it will show the file location and we need to add this file location in the program and then reupload it
31. Once the upload process is done, go to the EC2 connected terminal and run the command: spark-submit s3://mypa2bucket/training.py (Training code)
32. After training code, run the testing code using same command i.e.,                               spark-submit s3://mypa2bucket/testing.py (Testing code)
33. After the successful execution we will get the testing results.
Note: All the process we did in the EC2 Connected Terminal above is without Docker.
