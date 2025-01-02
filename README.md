# Welcome!

Main idea: 

- start with a dataset of square images
- resize them all to 2 copies: one with about 768x768 px and another with 224x224px
- run effnet (the specific one from stable cascade) on the first set of copies to generate 16x24x24 latents
- run CLIP (original from openai) on the second set of copies to generate 1x512 latents
- train an MLP on the effnet latent such that the output from the MLP matches the CLIP latents
- then, at inference time, you can have an MLP that translates from 16x24x24 effnet latents to 1x512 clip latents, without having to go through pixel or the image modality to perform semantic comparisons!

Download jupyter notebook to see some results! If it's only to view it, you can just upload the file to google colab

# Q/D Setup instructions

- clone https://github.com/Stability-AI/StableCascade, place the notebook from this repo into the StableCascade folder
- download sbu captions following instructions from https://github.com/rom1504/img2dataset/blob/main/dataset_examples/SBUcaptions.md
- apt install ffmpeg libsm6 libxext6
- apt install g++
- create venvs, setup repos
- for cascade repo, change numpy to 1.24.4
- for img2dataset, change albumentations to 1.2
- pip install ipykernel
- python -m ipykernel install --user
- jupyter notebook
