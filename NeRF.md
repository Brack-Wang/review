# DETR3D: 3D Object Detection from Multi-view Images via 3D-to-2D Queries

This work implement transformer to predict 3D object deirectly from multi-images instead of generating point cloud or estimating depth. Furthermore, with the pipeline of top-to-down, it discard the comsuming NMS post procssing. It first proposed M object quries and predict reference points in 3D space with MLP, then map reference points to different layers of feature images, finally map back with muiti-head attention to refine object quries.

Prof Yue Wang is AP in USC, expected to get in touch.
![Screenshot from 2023-09-23 15-53-06](https://github.com/Brack-Wang/review/assets/62454493/55f1b0ab-a596-4d7a-b176-10a99ce437e8)



# PersonNeRF : Personalized Reconstruction from Photo Collections

This work is interesting and promising: Giving a short video and construct the human in 3D. The work is based on his previous work named HumanNerf and solve the problem on non-rigid motion and human geometry. It replace non-rigid model with the skeleton model; enforce the depth smooth; train the appearance and motion in single network.

The work focus a special topic of constructing human and modify the motion with different appearances with the input of short videos. It would be promising if we could upload a video and got the 3D model of ourselves. The limitation locates on the parameters needed to finetune, traning is comsuming.

![Screenshot from 2023-09-23 14-42-03](https://github.com/Brack-Wang/review/assets/62454493/5d6af72a-2ce8-4af7-8f7a-a986b20aaad8)



# F2-NeRF: Fast Neural Radiance Field Training with Free Camera Trajectories

This work divide the works of NeRF into 2 main sections: forward-fronting and 360 centered. Situation beyond these two situations are free trajectories, which is explored little. It provide an insight that the assignment of computation resource on the neural filed is not reasonable. Space close to the camera and the far to the camera should got the similar resource instead of the farther the more. Therefore it transform the 3D space into warping space through proposed perspective warping. It utilize pCA to estimate the transformation. To calculate efficently, it imporved the hash map of instant-ngp and store the subdivided region with octree.
![Screenshot from 2023-09-23 13-57-30](https://github.com/Brack-Wang/review/assets/62454493/afc3a890-5571-466b-a5f6-4324c53ca003)
![Screenshot from 2023-09-23 14-36-45](https://github.com/Brack-Wang/review/assets/62454493/30a44ce7-2ddd-40e1-8147-f89f3ef31410)


# FreeNeRF: Improving Few-shot Neural Rendering with Free Frequency Regularization

This work add only one line of code to improve the quality of NeRF with few shots dramtically, based on the observations that 1. over-fast converge on high-frequency mapping lead to the missing of low-frequency info, therefore it introduce Frequency Regularization which use a linearly increasing frequency mask to regulate the visible frequency spectrum; 2. solid floater close the camera, therefore it introduce occlusion reularization. It's beautiful since it discover problem in details and improve it with simplicity.
![Screenshot from 2023-09-22 15-27-14](https://github.com/Brack-Wang/review/assets/62454493/01c5331d-da74-4885-9c3d-2a7637cf346b)



# NeRFactor: Neural Factorization of Shape and Reflectance Under an Unknown Illumination

This work factorize the 3D neural field into surface normals, light visibility, albedo, and Bidirectional Reflectance Distribution Functions (BRDFs) without any supervision. This work has a similar idea of Anand work.

![Screenshot from 2023-09-22 14-39-57](https://github.com/Brack-Wang/review/assets/62454493/a2d77727-4b71-4adf-b408-2951938234ee)




# ReLight My NeRF: A Dataset for Novel View Synthesis and Relighting of Real World Objects

This work is enlighting that It provide a dataset for relightable nerf, summury related works before, provides a benchmark of relightable NeRF. I will utilize its dataset and follow its work.

There is an insight that providing the relative position of the light is much better than providing a absolute position.

![Screenshot from 2023-09-22 13-45-28](https://github.com/Brack-Wang/review/assets/62454493/df7e3e1d-2be7-4dde-a2da-545a7dd9f092)

![Screenshot from 2023-09-22 13-45-37](https://github.com/Brack-Wang/review/assets/62454493/f3805c8a-c908-464a-af5f-a95de9ac0cf0)



# EfficientNeRF: Efficient Neural Radiance Fields

This work also want to delete unuseful information like NSVF but it first use valid sampling to refine the density in voxel and get the weights, then utilize pivot sampling to predict color focusing on voxels with higher weights. It aslo introduce a NeRFtree to store results more effeciently. The limitation inferred in the article is the generalization ability, trainning from scratch to new scenes.

![Screenshot from 2023-09-22 09-36-49](https://github.com/Brack-Wang/review/assets/62454493/247624cf-c25a-47cf-bf45-b4d57d46a36a)

![Screenshot from 2023-09-22 09-41-14](https://github.com/Brack-Wang/review/assets/62454493/769086ad-cdf3-4cba-862d-21dd187ea988)



# Neural Sparse Voxel Fields

This work utilize voxel grid to help the locate of the semantic position and discard non-info space by self-pruning the grids and predic the density and color in grids. It gradually delete voxels without any inform to speed up. The difference from DIVeR is that it still predict through accumulation while DIVeR utlize trilinear interpolation.

![Screenshot from 2023-09-21 15-45-57](https://github.com/Brack-Wang/review/assets/62454493/2412f40e-c694-46cd-9df2-e99aeae5fdcd)


# DIVeR: Real-time and Accurate Neural Radiance Fields with Deterministic Integration for Volume Rendering

This work utilize deterministric to replace stochastic volume rendering integral, representing the filed as voxel grid with feature vectors, predicting density, color in voxel's vertex and calculate the info of given position through trilinear interpolation. To initialize the feature vectors reasonablely, it utilize MLP to learn the correlation and initialize implicitly, then discard MLP regulation and optimize explicitly. The result is faster, better and more stable compared to original NeRF and cocunrrent works. But the limilation of original Nerf like the unbounded reconstruction, the reflection, aliasing errors remains.

![Screenshot from 2023-09-21 15-11-04](https://github.com/Brack-Wang/review/assets/62454493/e6c4b1ad-48b3-4b72-86f5-448b76350e2c)


# NeRFLight: Fast and Light Neural Radiance Fields using a Shared Feature Grid

This work clams to have the fastest FPS with relatively godd quality campared to Instant-NGP, TensoRF, DRIeR. The main concept is to divide the space into 8 grids and learn the shared feature grid in each cube, which will decrease the computation greatly. Then implementing decoder in each smaller specific region to predict the density and so-called intermedieate representation used to predict color with a single color decoder. It introduced a symmetric voxel grid method to smooth the seam since decoders predict density and color seperately. It also introduce the determetric volumn integration which integrate trilinear interpolation into the intervals.


![Screenshot from 2023-09-21 14-26-55](https://github.com/Brack-Wang/review/assets/62454493/3b8007bc-5675-4a19-b2f3-fabfc0985955)



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



