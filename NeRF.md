# TensoRF: Tensorial Radiance Fields

Achieve good quality with speed to reconstruct 3D model from images. It decompose tensors into components through CP/VM. This work is excellent, one for decompose the tensor with components which speed up without CUDA, one for take geometric and appearance feature seperately. This work bases on CP and introduce VM(vector-matrix).

![Screenshot from 2023-09-17 21-44-45](https://github.com/Brack-Wang/review/assets/62454493/ff21e568-b645-4b98-b1b2-4e65ca20d0e9)

It combine geometric and appearance feature together at the end with this equation.
![Screenshot from 2023-09-17 21-44-34](https://github.com/Brack-Wang/review/assets/62454493/375ebc32-bc9a-4051-8558-0a836ece7eba)





# ClimateNeRF: Extreme Weather Synthesis in Neural Radiance Field
2021/09/17

Render weather effects, including smog, snow, and flood, over real-world images. Utilize Instant-NGP to reconstruct 3D model, used FastPhotoStyle to transfer style, Instant-NGP again to finetune. Seperate geometry properties and appearance properties and only change appearance. They use different method to create different affects.



# NeRF: Neural Radiance Field in 3D Vision, Introduction and Review
2023/09/14

The review of the development of NeRF since the first publication since 2020. Covering from the development on quality, speed, the application from urban city to face avatar.


## Interesting topics for me:
Few shot NeRF. Build model with fewer images.
Diffusion model-based NeRF. Combine NeRF and diffusion model enabling more powerful generation and the generation with instruction of text.
Outdoor reconstruction
Reconstruction to moving videos.
There are two significant work on improving speed: Instant-NGP, TensorRF; one important work on improving quality: mip-NeRF; one basic work for outdoor NeRF:PleNoxels.
![nerf_review](https://github.com/Brack-Wang/review/assets/62454493/68046ae4-da50-4dab-a96e-9d329970570d)

## The Application of NeRF
![NeRF_application](https://github.com/Brack-Wang/review/assets/62454493/11c1431f-14a1-4e83-bd86-3c170f8e6aa4)


## The list of paper I want to read following:
1. TensorRF
2. Plenoxels
3. Plenoctrees
4. NeRF-SLAM
5.4GIGA
6. climate-Nerf
7. Mip-Nerf
8. Ref-Nerf
9. HDF-plenoxels



