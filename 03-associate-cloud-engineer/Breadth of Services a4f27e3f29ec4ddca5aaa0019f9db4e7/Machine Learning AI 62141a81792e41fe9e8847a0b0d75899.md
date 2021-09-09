# Machine Learning / AI

## Cloud ML Engine

[Vertex AI | Google Cloud](https://cloud.google.com/vertex-ai)

[https://developers.googleblog.com/2017/09/how-machine-learning-with-tensorflow.html](https://developers.googleblog.com/2017/09/how-machine-learning-with-tensorflow.html)

- Regional
- Massively scalable managed service for training ML models & making predictions
- Enables apps and des to use TensorFlow on datasets of any size; endless usecases
- Integrates
    - Google Cloud Storage and Big Query (storage)
    - Cloud Data lab (dev)
    - Cloud Data Flow (preprocessing)
- Supports online & batch predictions
    - prioritizing latency (online)
    - prioritizing job time (batch)
- Or download models & make predictions anywhere
    - Desktop
    - mobile
    - own servers
- HyperTune automatically tines model hyperparameters to avoid manual tweaking
- Training: Pay per hour depending on chosen cluster capabilities (ML training units)
- Prediction: Pay per provisioned node-hour plus by prediction request volume made

## Cloud Vision API

[Vision AI | Derive Image Insights via ML | Cloud Vision API](https://cloud.google.com/vision/)

- Global
- Massive pretrained ML model
- Classifies images into catagories
    - detects objects / faces
    - finds / reads printed text
- Classifies images into thousands of catagories
    - Sailboat
    - Lion
    - Eiffel Tower
- Upload images to point to ones stored in GCS
- Pay per image, based on detection features requested
    - Higher price for OCR of full documents and finding similar images on the web
    - Some features are priced together
        - Labels + SafeSearch
        - ImgProps + Cropping
    - Others are priced individually
        - Text
        - Faces
        - Landmarks
        - Logos

## Cloud Speech API

[Speech-to-Text: Automatic Speech Recognition | Google Cloud](https://cloud.google.com/speech-to-text)

- Global
- Automatic Speech Recognition (ASR) to turn spoken word audio files into text
- Pre-trained ML model for speech in 110+ languages / variants
- Accepts pre-recorded or real-time audio & can stream results back in real time
- Enables voice command and control and transcribing user microphone dictations
- Handles noisy source audio
- Optionally filters inappropriate content in some languages
- Accepts contextual hints
    - Words and names that are likely to be spoken
- Pay for 15 seconds of audio processed

## Cloud Natural Language API

[Cloud Natural Language | Google Cloud](https://cloud.google.com/natural-language/)

- Global
- Analyzes text for sentiment, intent & content classification and extracts info
- Pre trained ML model for determining what text means so you can act on it
- Excellent with speech api, vision API and translation API
- Syntax analysis extracts tokens and sessions, parts of speech and dependency trees
- Entity analysis finds people, places, things, etc, labels them and links to Wikipedia
- Analysis for sentiment (overall), and entity sentiment detect +/- feelings & strength
- Content classification puts each document into one of 700+ predefined catagories
- Charged per request of 1000 characters, depending on analysis type requested

## Cloud Translation API

[Cloud Translation | Google Cloud](https://cloud.google.com/translate/)

- Global
- Translate text among 100+ languages
    - Optionally auto-detects source language
- Pre trained ML model for recognising and translating semantics, not just syntax
- Combine with speech, vision and natural language APIs for powerful workflows
- Send plain text or HTML and receive translation in kind
- Pay per character processed for translation
- Also pay per character for language auto-detection

## Dialogflow

[Dialogflow | Google Cloud](https://cloud.google.com/dialogflow)

- Global
- Build conversational interfaces for websites and apps, messages and IoT devices
- Pre trained ML model and service for accepting, parsing, lexing input & responding
- Enables useful chatbots and other natural user interactions with your custom code
- Train it to identify custom entity types by provided small example dataset
- Can choose from 30+ prebuilt agents as starting template
    - Car
    - Currency (conversion)
    - Dates
- Supports many different languages and platforms/devices
- Free plan has unlimited text interactions and capped voice interactions
- Paid plan is unlimited but charges per request: more for voice, less for text

## Cloud Video Intelligence API

[Video AI - Video Content Analysis | Cloud Video Intelligence API](https://cloud.google.com/video-intelligence/)

- Regional, Global
- Annotates videos in GCS (or directly uploaded) with info about what they contain
- Pre-trained ML model for video scene analysis and subject identification
- Enables you to search a video catalog the same way you search text documents
- "Specify a region where processing will take place" (regulatory compliance)
- Label detection: Detect entities within the video
    - Dog
    - Flower
    - Car
- Shot change detection: detect scene changes in video
- SafeSearch Detection: Detect adult content in video
- Pay per minute of video processed: depending on requested detection modes

## Cloud Job Discovery

[Cloud Talent Solution Job Matching APIs | Solutions | Google Cloud](https://cloud.google.com/solutions/talent-solution)

- Global
- Helps career sites, company job boards, etc to improve engagement & conversion
- Pre-trained ML model to help job seekers search job posting databases
- Integrates with many job / hiring systems
- Lots of features, such as commute distance and recognizing abbreviations / jargon
- Show me jobs with a 30 minute commute on public transportation from my home

"Most job sites rely on keyword search to retrieve content which often omits relevant jobs and overwhelms the job seeker with irrelevant jobs. For example, keyword spelling errors return 0 results, and a keyword search for dental assistant returns any assistant role that offers dental benefits"