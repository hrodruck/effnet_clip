# Welcome!

Main idea: 

- start with a dataset of square images
- resize them all to 2 copies: one with about 768x768 px and another with 224x224px
- run effnet (the specific one from stable cascade) on the first set of copies to generate 16x24x24 latents
- run CLIP (original from openai) on the second set of copies to generate 1x512 latents
- train an MLP on the effnet latent such that the output from the MLP matches the CLIP latents
- then, at inference time, you can have an MLP that translates from 16x24x24 effnet latents to 1x512 clip latents, without having to go through pixel or the image modality to perform semantic comparisons!

# Q/D Setup instructions

apt install ffmpeg libsm6 libxext6
apt install nano
apt install g++
create venvs, setup repos
for cascade repo, change numpy to 1.24.4
for img2dataset, change albumentations to 1.2
pip install ipykernel
python -m ipykernel install --user
jupyter notebook