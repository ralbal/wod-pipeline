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
