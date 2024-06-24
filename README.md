# Personal photo creator - telegram bot NymphLens

Our project aims to assist individuals in creating social media photos by generating images featuring their faces.

![img_3.png](img/img_3.png)

You can watch demonstration video [here](https://drive.google.com/file/d/1Lxk5jLsxXJJOfkEsO-K_JyZHNIn1w6vW/view?usp=drive_link)
and presentation [here](/presentation.pdf) ([new presentation](https://github.com/sad-bkt/photo_generation/blob/main/Presentation.pdf)).

## Team
- Dmitry Shironosov - co-founder of the NymphLens project, prompt expert
- Ivan Begunov - co-founder/CPO of the NymphLens project
- Alexander Shironosov - head of R&D
- Artem Nazarenko - developer
- Semina Anastasiia - prompt engineer

## Use-case diagram

![img_2.png](img/img_2.png)

AI personality is a Stable Diffusion checkpoint trained on the photos of 1 person.

## Sequence diagram

![img.png](img/img.png)

## My task for 1st semester

Create a window display of styles, on the basis of which photos would be generated. The style is a reference photo, positive and negative prompts, parameters: sampling method, sampling steps, denoising strength and CFG scale.

### Experiments

#### Finding the best model for reference generation 

In most cases, epiCRealism, epiCPhotoGasm, and RealDream performed well.

Experiments were carried out for different prompts and looked like this:


> Positive prompt:
> 
> portrait of beautiful fashion model, ethereal dreamy foggy, photoshoot by Annie Leibovitz, editorial Fashion Magazine photoshoot, fashion poses, in front of gothic cathedral architecture, Kinfolk Magazine, Film Grain, a soft smile, transparent sleeves, pastel colors dress, perfect hands, perfect eyes

> Negative prompt:
> 
> naked, deformed, distorted, disfigured, poorly drawn, bad anatomy, wrong anatomy, bad hands, bad body, bad face, bad teeth, bad arms, bad legs, deformities, extra limb, missing limb, floating limbs, mutated hands and fingers, disconnected limbs, mutation, mutated, ugly, disgusting, blurry, amputation,  worst quality, low quality, normal quality, lowres, low details, oversaturated, undersaturated, overexposed, underexposed, grayscale, bw, bad photo, bad photography, bad art, watermark, signature, text font, username, error, logo, words, letters, digits, autograph, trademark, name, blur, blurry, grainy, morbid, ugly, asymmetrical, mutated malformed, mutilated, poorly lit, bad shadow, draft, cropped, out of frame, cut off, censored, jpeg artifacts, out of focus, glitch, duplicate, airbrushed, cartoon, anime, semi-realistic, cgi, render, blender, digital art, manga, amateur, 3D, 3D Game, 3D Game Scene, 3D Character

| model                         | txt2img                   |
|-------------------------------|---------------------------|
| AbsoluteReality               | ![img_8.png](img/img_8.png)   |
| ColossusProjectXL             | ![img_9.png](img/img_9.png)   |
| CyberRealistic                | ![img_10.png](img/img_10.png) |
| epiCPhotoGasm                 | ![img_11.png](img/img_11.png) |
| epiCRealism                   | ![img_12.png](img/img_12.png) |
| ICantBelieveItsNotPhotography | ![img_13.png](img/img_13.png) |
| JuggernautXL                  | ![img_14.png](img/img_14.png) |
| majicMIX                      | ![img_15.png](img/img_15.png) |
| RealDream                     | ![img_16.png](img/img_16.png) |
| RealHotSpice                  | ![img_17.png](img/img_17.png) |
| RealisticStockPhoto           | ![img_18.png](img/img_18.png) |
| RealisticVision51             | ![img_19.png](img/img_19.png) |
| RealisticVision_v6            | ![img_20.png](img/img_20.png) |
| Reliberate                    | ![img_21.png](img/img_21.png) |


#### Search for the best prompts

A lot of experiments were conducted on checkpoints trained on different people. I used prompts from https://civitai.com/ and https://lexica.art/, changed them to get a more stable and good result. 

Experiments looks like:

> Positive prompt for img2txt:
> 
> portrait of beautiful fashion model, ethereal dreamy foggy, photoshoot by Annie Leibovitz, editorial Fashion Magazine photoshoot, fashion poses, in front of gothic cathedral architecture, Kinfolk Magazine, Film Grain, a soft smile, transparent sleeves, pastel colors dress, perfect hands, perfect eyes


> Positive prompt for img2img : 
> 
> ljz woman, portrait of beautiful fashion model, ethereal dreamy foggy, photoshoot by Annie Leibovitz, editorial Fashion Magazine photoshoot, fashion poses, in front of gothic cathedral architecture, Kinfolk Magazine, Film Grain, a soft smile, transparent long sleeves, pastel colors dress, perfect hands, perfect eyes

> Negative prompt:
> 
> naked, deformed, distorted, disfigured, poorly drawn, bad anatomy, wrong anatomy, bad hands, bad body, bad face, bad teeth, bad arms, bad legs, deformities, extra limb, missing limb, floating limbs, mutated hands and fingers, disconnected limbs, mutation, mutated, ugly, disgusting, blurry, amputation,  worst quality, low quality, normal quality, lowres, low details, oversaturated, undersaturated, overexposed, underexposed, grayscale, bw, bad photo, bad photography, bad art, watermark, signature, text font, username, error, logo, words, letters, digits, autograph, trademark, name, blur, blurry, grainy, morbid, ugly, asymmetrical, mutated malformed, mutilated, poorly lit, bad shadow, draft, cropped, out of frame, cut off, censored, jpeg artifacts, out of focus, glitch, duplicate, airbrushed, cartoon, anime, semi-realistic, cgi, render, blender, digital art, manga, amateur, 3D, 3D Game, 3D Game Scene, 3D Character

"ljz" is a token associated with a person. Training was conducted using the DreamBooth technique.

| reference   ![img_17.png](img/img_17.png) | checkpoint1 ![img_4.png](img/img_4.png) | checkpoint2 ![img_5.png](img/img_5.png) | checkpoint3 ![img_22.png](img/img_22.png) | checkpoint4     ![img_32.png](img/img_32.png) | checkpoint5 ![img_33.png](img/img_33.png) |
|---------------------------------------------|-------------------------------------|-------------------------------------|---------------------------------------|-------------------------------------------|---------------------------------------|
| ![img_17.png](img/img_17.png)                   | ![img_31.png](img/img_31.png)           | ![img_27.png](img/img_27.png)           | ![img_28.png](img/img_28.png)             | ![img_29.png](img/img_29.png)                 | ![img_30.png](img/img_30.png)             | 


#### Experiments with human nationality on a reference and enumeration of parameters

Checkpoints trained on me and CPO:

| Nastya                     |     Ivan             |
|----------------------------|---------------------------|
| ![img_22.png](img/img_22.png)  |![img_25.png](img/img_25.png)|

Results can be found [here](https://drive.google.com/drive/folders/1bi_MzMdOjwfO-u7Q8jPTBUivkB5vxidk?usp=sharing)

All information in naming:

1) folders with and without faceswap - whether faceswap was used on the output or not, respectively;

2) further in the frame name: ivan / sad_bkt (Ivan or Nastya);

3) number of training iterations (800 or 1600);

4) frame name for img2img mode;

5) if gfpgan was used in preprocessing, then there is a postscript "_gfpgan".

### Results

A women's window display of 23 styles was made: you can see them in the demo [video](https://drive.google.com/file/d/1Lxk5jLsxXJJOfkEsO-K_JyZHNIn1w6vW/view?usp=drive_link).

Descriptions of generation problems and their solutions can be found in the [presentation](/presentation.pdf).

I came to the conclusion that it is not necessary to use universal template for prompt structure, most often short prompts work more stable and better.

## My task for 2d semester

:white_check_mark: Add formal business style to window display.


:white_check_mark: Conduct experiments with prompts to change age and obtain more natural skin.

:arrows_counterclockwise: Add college prom style to window display.

:arrows_counterclockwise: Conduct research: extract prompts from the collected dataset of Instagram photos and use them as new styles.
