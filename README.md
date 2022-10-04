# Dreambooth Usage
how to make a dreambooth project

- [ ] Collect some photos, making sure that:
  - [ ] You have at least 6
  - [ ] All of them are 512x512, I recommend [BIRME](https://www.birme.net/?target_width=512&target_height=512)
  - [ ] All of them contain only your subject
  - [ ] They include all the poses and angles that you are wanting to make images of (e.g. if you want an image of your character lying down, make sure you have at least one actual image of your character lying down)

- [ ] Go to [this notebook](https://colab.research.google.com/github/ShivamShrirao/diffusers/blob/main/examples/dreambooth/DreamBooth_Stable_Diffusion.ipynb#scrollTo=jjcSXTp-u-E) and run setup
  - [ ] run the first cell, read the output, make sure you have a GPU
  - [ ] run the second cell, make sure there are no errors, it just downloads stuff
  - [ ] give the notebook huggingface access
    - [ ] log in to [huggingface](https://huggingface.co/), click on your user icon --> settings --> access tokens --> copy one of your "User Access Tokens"
    - [ ] run the third (huggingface) cell, paste the token into the login input   
  - [ ] run the 4th cell, again it just downloads some stuff

- [ ] choose your character name, it cannot contain spaces
  - [ ] edit the "settings and run" cell, altering the "INSTANCE_DIR" and "OUTPUT_DIR" variables so they match your character name
  - [ ] edit the "start training" cell, altering the "--instance_prompt" to match your character name
  
- [ ] choose your class name, which is the class of thing your character is e.g. "man", "woman", "queen", etc.
  - [ ] edit the "settings and run" cell, altering the "CLASS_NAME" variables so they match your class name
  - [ ] optionally edit the "start training" cell, altering the "--class_promptt" so that is is more appropriate, e.g. "photo of a {CLASS_NAME} wearing glasses"
 
 - [ ] run the "settings and run" cell

- [ ] upload your images
  - [ ] use the sidebar to navigate to the "INSTANCE_DIR" directory (you may need to refresh it)
  - [ ] drag your images in

- [ ] set the correct training parameters
  - [ ] in the "start training" cell, set "--max_train_steps" to 4000
  - [ ] do not touch anything else, in general I have found it is too easy to get weird errors when you do

- [ ] begin training by running the "start training" cell, this will take around 1 hour

- [ ] convert your model to a smaller model to make it easier to download (this does not effect quality)
  - [ ] run the "Download script" cell
  - [ ] run the "Run conversion" cell, note that if your google drive is full, this cell may not work, and you may need to empty your drive and try again
  - [ ] confirm that this has worked by checking the location mentioned in your google drive (e.g. `/content/drive/MyDrive/stable_diffusion_weights/h-piker/model.ckpt` and ensuring that the model is there 

- [ ] test your model
  - [ ] run the "inference" cell to set up for inference
  - [ ] run the seed setting cell
  - [ ] in the "Run for generating images" cell, set the prompt and parameters you want, and then run, images will appear below that cell
  
 ### If you are not happy with your model, train again, otherwise continue to download the model for local use. 
 
 - [ ] download your model for local use
   - [ ] locate your model inside google drive
   - [ ] download it 
   - [ ] download the [webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui) repo, or if you already have it, make sure you have the latest version
   - [ ] move the model into the `models/Stable-diffusion` directory e.g. `stable-diffusion-webui/models/Stable-diffusion/model.ckpt`
   - [ ] rename the file to something more memorable than `model.ckpt` (keeping the ".ckpt" though)

- [ ] get the webui to use that model 
  - [ ] navigate to the "settings" tab 
  - [ ] find the "Stable Diffusion" section
  - [ ] Set the "Stable Diffusion checkpoint" option to the file you just downlaoded
  - [ ] Scroll back up to the top and "apply settings"
  - [ ] Confirm that the change has taken place by refreshing the page and checking that the model name has changed
  
### Go Buck Wild
 
## Final Tips

- Take some time experimenting with different poses and angles in the prompts. I thought my hasan model was bad because hasan's face kept looking weird, but actually it was just bad at generating images that weren't close ups.
- Keep in mind that Stable Diffusion will be affected by the actual character name you choose. I used "hasan" as my character name initially and all my images had a middle-eastern skew. I re-treained with "h-piker" as the character name and the character looked a lot more white.
- If your character is a human, then additional face-correction models will improve the quality of your outputs considerably
- I tried a few experiments, an training for 4000 steps seems good. Results here are much better than 900, 2000, and 6000, and it's also the number of steps that were used to get [these results](https://www.reddit.com/r/StableDiffusion/comments/xs2b2k/dreambooth_is_the_best_thing_ever_period_see/)



