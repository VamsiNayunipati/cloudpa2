## Building a Wine Quality Prediction Model with Spark on AWS
### Cluster Creation:
1. Login to AWS Account and start the lab
2. Click on AWS Console
3. Search for EMR
4. Click on create cluster and give a name
5. Under Cluster scaling and provisioning, give 1 instance for core and 5 instances for Task
6. Under Cluster termination and node replacement, click on Manually terminate cluster and Use termination protection.
7. Under Security configuration and EC2 key pair, click on create key pair > name the key > select .pem and click on create key and go back and click on Browse and add the key.
8. Under Identity and Access Management (IAM) roles, for Service role choose EMR_DefaultRole and for Instance profile choose EMR_EC2_DefaultRole.
9. Click on Create Cluster
10. Search for EMR and click on it
11. Click on the created cluster
12. Click on Connect to the Primary node using SSM
13. Check for the Public IP address - 3.238.28.122 (may be different for others) and search for that IP address in the instances running.


### EC2 Instances:
14. Search for EC2 and click on it and then click on instances running.
15. Click on the instance with the same IP because it is the primary node.
16. Click on security Tab.
17. Click on (ElasticMapReduce-master) under Security groups.
18. Click on Edit inbound rules
19. Click on add rule, Select SSH under Type dropdown and MyIP under Source dropdown and click on save rules
20. Search for EMR and click on it
21. Click on the cluster and Click on Connect to the Primary node using SSH
22. Copy the ssh command
23. Open terminal from the .pem save location and run the command copied from above (delete ~/ if not needed) and run it
24. Enter yes for continue connection and once it is successful it connects to EMR


### S3 Bucket Creation:
25. Once this is done, go to AWS Console and search for S3 and click on it
26. Click on Create Bucket
27. Write a bucket name and click on Create Bucket
28. After the successful creation of bucket, it will be like this
29. Click on the created bucket and click on upload files and then upload the require files (Working code and datasets)
30. If we click on the uploaded files, then it will show the file location and we need to add this file location in the program and then reupload it
31. Once the upload process is done, go to the EC2 connected terminal and run the command: spark-submit s3://mypa2bucket/training.py (Training code)
32. After training code, run the testing code using same command i.e.,                               spark-submit s3://mypa2bucket/testing.py (Testing code)
33. After the successful execution we will get the testing results.

**Note:** All the process we did in the EC2 Connected Terminal above is without Docker.

