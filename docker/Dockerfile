FROM ubuntu:16.04
MAINTAINER Hiroshi TAEKDA <takeda@gmail.com>

# environment variables
ENV WORKING_FOLDER=/MidiAudioClassification
ENV JN_PORT=8880
ENV UNAME=anuser

# configure
EXPOSE $JN_PORT

USER root
# build
RUN \
apt update && \
apt upgrade -y && \
apt install -y git build-essential && \
apt install -y python3 python3-venv python3-dev ffmpeg gcc && \
echo "Running apt is finished"

WORKDIR $WORKING_FOLDER
RUN \
useradd -m -s /bin/bash -G users,sudo $UNAME && \
id $UNAME && \
chown $UNAME:$UNAME $WORKING_FOLDER && \
ls -al $WORKING_FOLDER && \
echo "Creating user is finished"

USER $UNAME
WORKDIR $WORKING_FOLDER
RUN \
ls -al $WORKING_FOLDER

RUN \
git clone https://github.com/ssashir06/MidiAudioClassification.git . && \
python3 -m venv env  && \
. env/bin/activate  && \
pip install --upgrade pip  && \
pip install numpy matplotlib scipy sklearn hmmlearn simplejson eyed3 pydub  && \
pip install -r requirements.txt  && \
echo "Setting up is finished"


USER $UNAME
# run
CMD \
echo "Start Jupyter... (using port is $JN_PORT)"  && \
cd $WORKING_FOLDER && \
. env/bin/activate && \
cd $WORKING_FOLDER/notebooks  && \
jupyter notebook --ip=0.0.0.0 --port $JN_PORT && \
echo "Jupyter Notebook is ended."

