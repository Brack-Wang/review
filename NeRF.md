
# **NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis**

Take a review of the most important paper: NeRF itself since it contains several classical expression of math to describe the princlple of nerual filed. 1. Sample points X along the ray of the camera; 2. Input the X and D, a 5D and predict the color and density through MLP; 3. accululate along the ray and render the image; optimize with losss of the generated and input image.

![Screenshot from 2023-09-21 14-00-43](https://github.com/Brack-Wang/review/assets/62454493/e45f0ab4-a57c-4859-915a-27c9d36438c4)

The essential principle of rendering is:
![Screenshot from 2023-09-21 14-00-57](https://github.com/Brack-Wang/review/assets/62454493/460918b5-02e3-4550-819c-5dfd47a3866f)

To implement in decrete:
![Screenshot from 2023-09-21 14-01-06](https://github.com/Brack-Wang/review/assets/62454493/6aa42589-a86b-47d7-a40d-a74b4c812f1c)



# EditableNeRF: Editing Topologically Varying Neural Radiance Fields by Key Points

This work make the constructed 3D model editable by detecting key points in canonical space, using weighted key points to model dynimics. training the model under the supervision of input image sequence with the optical and depth inform.

The topic is interesting. It could also faciliate the prediction of unseen place, motion transfer, UI interface. The obstacle is the limitaion of the moving distance.



![ediablenerf](https://github.com/Brack-Wang/review/assets/62454493/1ed8350c-0321-4adc-a4dc-6323a20960ad)



# NeRF-SLAM: Real-Time Dense Monocular SLAM with Neural Radiance Fields

This work achieves SLAM with only images as input. It utilizes Detroid-SLAM to predict pose and depth from images, then constructs 3D mesh and basic blurry 3D model by weighting the depths estimated in dense SLAM by marginal covariance, finally generate NeRF under Instant-NGP structure with the prediect pose and depth. This work only use RGB info instead of RGB-D info like Nice-SLAM. It's real-time due to the utilization of Instant-NGP, but require 11 GB GPU memories, which is a common problem in Nerf-based SLAM.

It provide an insight that to reconstruct 3D model through NeRF,  accurate pose estimation or(and) accurate depth would be good enough to generate good model. 

# HDR-Plenoxels: Self-Calibrating High Dynamic Range Radiance Fields

This work is based on Plenoxels, improving the render on HDR images by considering white balance and camera response function(CRF) with its tone mapping.

![HDRplenxoel](https://github.com/Brack-Wang/review/assets/62454493/9e621d26-dcce-41d1-a79d-f7be4533a5c2)



# Plenoxels: Radiance Fields without Neural Networks

This work introduce a method without MLP to reach the similar good quality as original Nerf and faster speed. It presents an insight that the key element of NeRF is not neural network but differential volumetric render. Besides, it emphasize the importance of 3 key elements: a differentiable forward network, a continuous representation, an appropriate regulazation. 

This work got insight from PlenOctrees and continue the way of utilizing sparse voxel grid. It might enlighten the Nice-SLAm, which has similar architecture of feature grid. Though It improve the speed, it certainly require much more memory space.


![plenoxels](https://github.com/Brack-Wang/review/assets/62454493/6ba0a58c-5b15-4b49-9103-304967e3bb26)

# Ref-NeRF: Structured View-Dependent Appearance for Neural Radiance Fields

They present two insight of the defeat of NeRF on reflection: [Original Expression since I'm not fully understand]

First, NeRF’s parameterization of the outgoing radiance at each point as a function of the viewing direction is poorly-suited for interpolation. Figure 2 illustrates that, even for a simple toy setup, the scene’s true radiance function varies quickly with view direction, especially around specular highlights.

Second, NeRF tends to “fake” specular reflections using isotropic emitters inside the object instead of view-dependent radiance emitted by points at the surface, resulting in objects with semitransparent or “foggy” shells.

Therefore, they improve the Mip-Nerf by introduction integrated Deirectional Encoding(IDE) considering the roughness and the reflection of the radiance field.

![refnerf](https://github.com/Brack-Wang/review/assets/62454493/57a445b1-e527-4447-9341-917a686d14d1)

Though Ref-Nerf got better result than Mip-Nerf. The written article is kind of blurry, it needs attention to capture the important information and kind of hard to generate a general pipeline of the work.

# PlenOctrees for Real-time Rendering of Neural Radiance Fields

Implementing NeRF through Octree in 3D, achieveing similar quality but 3000 times faster than original NeRF clamed. Researcher achieves faster NeRF by implementing it with different representation like Octree here, hash encoding like Instant NGP, decomposition of VM in TensoRF.

![plenoctree](https://github.com/Brack-Wang/review/assets/62454493/acdf5a93-95af-495e-9aa2-b297d8172dc0)




# Mip-NeRF: A Multiscale Representation for Anti-Aliasing Neural Radiance Fields

NeRF render images from the radiance field along only one ray, which lead to the alias affect. Mip-NeRF got insight from the Mip-mapping, rendering from the cone, introducing Integrated Positional Encoding to replace Positional Encoding, which improve the quality and speed up. Mip-NeRF is a classic work for the following work.

![mipnerf](https://github.com/Brack-Wang/review/assets/62454493/6cb51cda-c06e-46f2-816d-a8cd9289a166)



# GIGA: Synergies Between Affordance and Geometry: 6-DoF Grasp Detection via Implicit Representations

This work predict the grasping point and the reconstruct 3D model at the same time. It provide an insight that prediction of grasping point and the reconscturtion are inverse process, whichi is facinating. The work could predict the grapsing point of the objects for the robotic arm with only images. Two main contribution is: decompose the TSDF into 3 feature plane; decompose the feature plane with geometric feature and appearance feature with implicit representation. The main pipeline are following:

![Screenshot from 2023-09-17 21-49-14](https://github.com/Brack-Wang/review/assets/62454493/85851678-e0d2-4a47-b383-d19482b9e4c3)

![GIGA_pip](https://github.com/Brack-Wang/review/assets/62454493/349520c1-3fd8-4aba-87c6-d3fe330c54d3)



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



