# CGIntrinsics

This is the CGIntrinsics implementation described in the paper "CGIntrinsics: Better Intrinsic Image Decomposition through Physically-Based Rendering, Z. Li and N. Snavely, ECCV 2018" (Still Updating, please stay tuned).

The code skeleton is based on "https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix" and "https://github.com/lixx2938/unsupervised-learning-intrinsic-images". If you use our code for academic purposes, please consider citing:

    @inproceedings{li2018cgintrinsics,
	  	title={CGIntrinsics: Better Intrinsic Image Decomposition through Physically-Based Rendering},
	  	author={Zhengqi Li and Noah Snavely},
	  	booktitle={European Conference on Computer Vision (ECCV)},
	  	year={2018}
	}
  

#### Dependencies & Compilation:
* The code was written in Pytorch 0.2 and Python 2, but it should be easy to adapt it to Python 3 version and Pytorch 0.3/0.4 if needed. 


#### Training on the CGIntrinsics dataset:
* Download the CGIntrinsics dataset (intrinsics_final) from our website: http://www.cs.cornell.edu/projects/megadepth/dataset/cgintrinsics/intrinsics_final.zip
* Download IIW densely connected pair-wise juedgement we precomputed in our website (http://www.cs.cornell.edu/projects/megadepth/dataset/cgintrinsics/IIW.zip) and original images and data in original IIW link (http://opensurfaces.cs.cornell.edu/publications/intrinsic/#download). 
* Download SAW list in our website (http://www.cs.cornell.edu/projects/megadepth/dataset/cgintrinsics/SAW.zip) and original data in original SAW website (https://github.com/kovibalu/saw_release).
* create a directory in your machine called CGIntrinsics
* In CGIntrinsics, you should have 3 folders (1) intrinsics_final (2) IIW (3) SAW. You should put original IIW png and json you download from http://opensurfaces.cs.cornell.edu/publications/intrinsic/#download in CGIntrinsics/IIW/data/, and you should put original data you download from https://github.com/kovibalu/saw_release in folders "CGIntrinsics/SAW/saw_images_512" and "CGIntrinsics/SAW/saw_pixel_labels" from original SAW dataset/

* In train.py file, you should root and and full_root variable to your root directory for putting CGIntrinsics folder. 
* In options/base_options.py, you should change --gpu_ids to fit your machine GPUs.
* Change to "self.isTrain = True" in python file "/options/train_options.py" and run:
```bash
    python train.py
```

#### Evaluation on the IIW/SAW test splits:
* Download IIW densely connected pair-wise juedgement we precomputed in our website (http://www.cs.cornell.edu/projects/megadepth/dataset/cgintrinsics/IIW.zip) and original images and data in original IIW link (http://opensurfaces.cs.cornell.edu/publications/intrinsic/#download). 
* Download SAW list in our website (http://www.cs.cornell.edu/projects/megadepth/dataset/cgintrinsics/SAW.zip) and original data in original SAW website (https://github.com/kovibalu/saw_release).
* Download pretrained model from http://www.cs.cornell.edu/projects/cgintrinsics/cgintrinsics_iiw_saw_final_net_G.pth and put it in "checkpoints/test_local/cgintrinsics_iiw_saw_final_net_G.pth"
* Change to "self.isTrain = False" in python file "/options/train_options.py"
* In CGIntrinsics, you should have at least 2 folders (1) IIW (2) SAW. You should put original IIW png and json you download from http://opensurfaces.cs.cornell.edu/publications/intrinsic/#download in CGIntrinsics/IIW/data/, and you should put original corresponding folders you download from https://github.com/kovibalu/saw_release in folders "CGIntrinsics/SAW/saw_images_512" and "CGIntrinsics/SAW/saw_pixel_labels".
* Change to "self.isTrain = False" in python file "/options/train_options.py"
* To run evaluation on IIW test split,, change the path variable "root" and "full_root" and run:
```bash
    python test_iiw.py
```
* To run evaluation on SAW test split, change the path variable "root" and "full_root" and run:
```bash
    python test_saw.py
```
Note that we only compute AP% (challenge) mentioned in the paper. If you want to compute original AP%, please refer to https://github.com/lixx2938/unsupervised-learning-intrinsic-images
