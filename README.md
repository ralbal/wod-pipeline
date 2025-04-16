# wod-pipeline
Waymo Open Dataset 2025 Machine Learning Pipeline

# Overview
This repo provides a full pipeline from clone to submission generation of the Waymo Open Dataset 2025 Challenges. The goal is to make setup and execution **as plug-and-play as possible**. No guessing, no drama. Run the scripts and let it cook

# Demo 
Here is a demo: [Demonstration](url)

# Workflow

Peek into these shell scripts before running, it's always good to know what the code is doing under the hood. 

1. **setup_pipeline.sh**
2. **convert_data.sh**
3. **run_pipeline.sh**

### Clone Repo (do once)

Go to Sourcetree and clone this repo. or hit the trenches in terminal.

```bash
git clone https://github.com/ralbal/wod-pipeline.git
cd wod-pipeline
```

After cloning, the workflow assumes the current working directory is ```wod-pipeline/```

### Setup Pipeline (~10 minutes)

Script will execute the following

1. Read user input
2. Setup and activate virtual environment
3. Install dependancies and build packages
4. Run test scripts and readiness check

```bash
chmod +x setup_pipeline.sh
./setup_pipeline.sh
```

### Download and Preprocess Data (~10 minutes)

Use ```download_many_blobs_with_transfer_manager``` to programmatically download the tfrecords files (Google Cloud SDK for automation)

> Requires authorization w/ Google Cloud APIs. Users must
 manually download data and maintain matching folder structure until script is completed, user

Refer to [Google Cloud Docs - Downloading Objects](https://cloud.google.com/storage/docs/downloading-objects)

> Script assumes that there is data loaded in the same folder structure as download storage

```bash
chmod +x convert_data.sh
./convert_data.sh
```

### Run Pipeline (~30-45 minutes)

Shell script will execute the following

1. Read user input

2. Run ```preprocessing.py``` to convert and format raw waymo tfrecords

3. Run ```training.py``` to learn patterns from labeled data. 
    - Outs loss, gradients, and updated weights from labeled training dataset.

4. Run ```validation.py``` to monitor training performance. 
    - Outs loss and metrics from labeled validation dataset.

5. Run ```testing.py``` to evaluate model accuracy and precision. 
    - Outs predictions from unlabeled real world data. 

6. Run ```infer.py``` (Optional) to make predictions on new unseen data 
    - (out of scope of the challenge, nice to have. cough cough, I need a new job...)

7. Run ```postprocess.py``` to generate waymo predictions and submissions

```bash
chmod +x run_pipeline.sh
./run_pipeline.sh
```

# FAQ
Raise an issue if it demo is unsuccessful. May be a setup issue.