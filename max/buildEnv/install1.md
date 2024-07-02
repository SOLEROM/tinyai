
## deps
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev \
  libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
  libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev \
  libsndfile-dev portaudio19-dev

## venv

* py tool

curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash

*  .bashrc
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"

## download 
cd <your/project>
git clone --recursive https://github.com/analogdevicesinc/ai8x-training.git
git clone --recursive https://github.com/analogdevicesinc/ai8x-synthesis.git



## venv-training

pyenv install 3.8.11

cd ai8x-training
git checkout main
python -m venv venv --prompt ai8x-training
source venv/bin/activate
pip3 install -U pip wheel setuptools

//pip3 install -r requirements-cu11.txt
pip3 install -r requirements.txt


## venc-Synthesis

cd ai8x-synthesis 
git checkout main
python -m venv venv --prompt ai8x-synthesis
source venv/bin/activate
pip3 install -U pip setuptools
pip3 install -r requirements.txt