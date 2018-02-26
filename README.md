1. ###### Clone deepo repository
```
git clone https://github.com/ufoym/deepo.git ~/deepo
cd ~/deepo/generator
```

2. Make Docker file with PyTorch and TensorFlow
python generate.py Dockerfile2 jupyter pytorch tensorflow python==3.6 --cpu-only

3. Build the image
docker build -t deepo .

4. Clone this repo to ~/simple-cifar-10 folder
git clone https://github.com/surukuntu/simple-cifar-10.git ~/simple-cifar-10

5. Start the container
docker run --rm --name nn -it -p 8888:8888 -p 6006:6006 -v ~/simple_cifar_10:/data deepo

if you want to keep the bash history
touch .nn_bash_history
docker run --rm --name nn -it -p 8888:8888 -p 6006:6006 -v ~/.nn_bash_history:/root/.bash_history -v ~/simple_cifar_10:/root/simple_cifar_10 deepo

6. Start the jupyter notebook inside the container
cd ~/simple_cifar_10
jupyter notebook --ip=0.0.0.0 --no-browser --allow-root

7. Connect to notebook from browser 
http://0.0.0.0:8888/tree