# Personal photo creator - telegram bot NymphLens

Our project aims to assist individuals in creating social media photos by generating images featuring their faces.

You can watch demonstration video [here](https://drive.google.com/file/d/1Lxk5jLsxXJJOfkEsO-K_JyZHNIn1w6vW/view?usp=drive_link)
and presentation [here](\presentation.pdf).

### Team
- Dmitry Shironosov - co-founder of the NymphLens project, prompt expert
- Ivan Begunov - co-founder/CPO of the NymphLens project
- Alexander Shironosov - head of R&D
- Artem Nazarenko - developer
- Semina Anastasiia - prompt engineer

### Sequence Diagram

![img.png](img.png)

### My task

Create a showcase of styles, on the basis of which photos would be generated. The style is a reference photo, positive and negative prompts, parameters: number of steps, sampler, denoising strength and cfg_scale.

### Results
1) A lot of experiments were conducted on checkpoints trained on different people, the structure of the prompta and its content changed. I came to the conclusion that it is not necessary to do them according to the same template, most often short flushes work more stable and better.

2) A comparison of models was made: where more realistic and high-quality references are obtained. My favorites are epiCRealism, epiCPhotoGasm, RealDream.

3) A women's showcase of 23 styles was made, the men's is now in the process of being finalized. Next, testing will be conducted on different people, unstable styles will be corrected.


[//]: # (Hi! I am Nastya and I am in charge of the showcase of styles. My job is to find the best prompts and parameters for img2img generation using Stable Diffusion. I need to make sure that the generated photos are as similar to people as possible, so that our users can then post these photos on Instagram. This job is more mechanical and tedious than difficult. I've done a lot of experiments and prepared a women's showcase, now I'm starting to do men's. You can find more information in the presentation.)

[//]: # ()
[//]: # (Грустно, что у меня не было доступа к коду, все-таки мою работу можно было несколько автоматизировать &#40;проект коммерческий, я к нему присоединилась&#41;. Потом выяснилось, что WebUI, где я работала, и код под капотом у бота, где прогонялся весь пайплайн, выдают несколько разные результаты, сейчас это чинят. )

[//]: # (Еще кажется, что для данной задачи больше нужно работать с пайплайном и моделями, недавно вышла статья, подтверждающая это https://photo-maker.github.io/  Пока что генерируемые фото хоть и похожи, но все-таки что-то выдает их нереалистичность.)



