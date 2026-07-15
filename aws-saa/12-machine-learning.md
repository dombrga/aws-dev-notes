## amazon sagemaker
1. fully managed ML service or ds, engineers, devs to build, clean, train and deploy ML models.
2. store and share data without provisioning own servers.
3. to simply ml workflows, models, frameworks.
4. concepts
  1. sagemaker studio - web-based. Offers suitde of IDE.
  2. Containers - docker containers for build and runtime tasks. offers prebuils images.
  3. sagemaker domain - to organize resources like efs vols, authorized users, apps and diff vpc configs.
  4. Endpoints - where model is deployed. Specify model variant, etc.

**Exam tip**: sagemaker allow you to host own ML models to use.

5. amazon sagemaker automated ml
  1. sagemaker canvas - use ml to generate predictions without writing code. Chat with LLMs. For example, predicting customer churn.
  2. sagemaker jumpstart - offers pretrained, open source models to get started with ml.

**exam tip:** sagemakers runs on ec2 instances that you dont control. Use Saving plans to save cost.

6. example. Need to use ML algo to build and train models for online shopping platforn.
7. might need ML background to leverage sagemaker.

## amazon rekognition
1. aws computer vision product that automates recognition of pictures and videos using DL and neural nets.
2. understand and label whats in pics and vids.
3. create collection containing stored faces for detection.
4. to find objects, people (face recog or celebrity matching),
5. use cases
  1. content moderation - so apps and websites are family friendly. Common exam scenario.
  2. celebrity recog.
  3. face detection and analysis - recognize faces, detect emotions, clothing acces, eye positions.
  4. streaming video events detection
6. confidence scores - indicates likelihood.
7. scenario 1: content moderation
  1. rekognition can analyze images or videos in S3.

**exam scenario:** need a solution to prevent photo/vid with undesired content from being uploaded to web app. You dont want to involve training ml model.