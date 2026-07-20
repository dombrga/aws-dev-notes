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

## amazon polly
1. service to turn text into speech.
2. different languages.
3. voice options:
  1. generative engine - largest model. humanlike
  2. neural -
  3. long form - humanlike, better at expressing emotion than neural.
  4. standard tts - default, natural sounding
4. use cases
  1. read news sites to you
  2. elearning platforms to read lessons
  3. accessibility apps.
5. documents and lexicons
  1. input can be plaintext or SSML.
  2. ssml gives you more control over generated speech.
  3. pronunciation lexicons

## amazon translate
1. automate language translation.

## amazon lex
1. service for building conversational interfaces for apps using voice and text. For no ML experience.
2. powers Alexa.
3. build natural language chatbots on-demand.
4. NLU and ASR.

## amazon connect
1. ai-powered contact center.
2. integrates with other CRM software.
3. receiving customer calls, engage customers.
4. commonly used with Lex.

## amazon comprehend
1. managed, serverless service for NLP to understand meaning and sentiment of text.
2. use cases: detect if customers have positive or negative experience with staff.
#### amazon comprehend medical
3. detects and returns useful info from unstructured clinical text.
4. doctor notes, discharge summaries, test results, etc.
5. uses NLP.

## amazon forecast
1. managed service to produce time series forecast using ML algorithms.
2. automatically learns your data and select right ML algo.
3. used by Amazon.com for forecasting sales data.
4. no longer available to new customers.
5. thousand of iot sensors, historical values.

## amazon kendra
1. to create intelligent search service powered by ML and NLP.
2. enterprise search applications can bridge different silos of info, like s3 buckets, file servers, etc.

## amazon textract
1. managed service to extract typed text, handrwritten from scanned documents.
2. pdf, jpg, etc