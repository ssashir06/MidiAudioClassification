# Outline
This project will determine MIDI audio type of midi note by using pyAudioAnalysis.
The notes of MIDI audio are stored to this repository as converted Ogg file.


# Analyze
This project contains some notebook files to analyze the MIDI audio files.

- To create a new working directory, run create_sample_folder.ipynb.
    - A working folder will be created like 'midi_audio_sample20180819013100'.
- To create regression model, run learn_regression.ipynb.
    - Before starting this operation, folder_tag variable has to be changed if you created a new working directory.
- To test regression model, run test_regression.ipynb.
    - Before starting this operation, folder_tag variable has to be changed if you created a new working directory.
    - A test result named 'regression_result.json' will be output in the testing folder.

These notebooks can run by the following operations.

# Create a new environment by using Docker
```bash
docker pull ssashir06/midiaudioclassification
docker run -p 127.0.0.1:8880:8880 ssashir06/midiaudioclassification &
```
And then a Jupyter Notebook URL will be displayed in the console.

- Docker Hub
    - https://hub.docker.com/r/ssashir06/midiaudioclassification/

# Create a new environment by yourself 
## Requirements
- Ubuntu 16.04
- gcc
- ffmpeg
- python3
```bash
sudo apt update
sudo apt install python3 python3-venv python3-dev ffmpeg gcc build-essential
```

## Setup and run
### Pull
```bash
cd ~
mkdir MidiAudioClassification 
cd MidiAudioClassification 
git clone git@github.com:ssashir06/MidiAudioClassification.git
```

### Create venv
```bash
cd ~/MidiAudioClassification
python3 -m venv env
source env/bin/activate
pip install --upgrade pip
pip install numpy matplotlib scipy sklearn hmmlearn simplejson eyed3 pydub
pip install -r requirements.txt
```

### Run Jupyter Notebook
```bash
cd ~/MidiAudioClassification/notebooks
source env/bin/activate # if not activated
jupyter notebook
```
And then a Jupyter Notebook URL will be displayed in the console.
