## What is nifti?

Nifti : Neuroimaging Informatics Technology Initiative 

MRI 데이터는 각 스캐너에 따라 얻어지는 데이터의 형식(format)이 다르다. 내가 지금 현재 진행하는 RBD환자군과 정상인의 비교연구에서는 raw data로 par/rec 형태의 데이터를 받게 된다. 연구과정을 간소화하기 위해서는 통일된 형식의 데이터가 필요했으며 이를 위해 개발된 것이 Nifti 형태의 데이터이다. 이를 위해서는 dcm2niix 패키지를 사용하면 되며, dcm은 dicom의 약자이다. 

---

### Python으로 nifti파일 다뤄보기(.ni / .nii.gz)

~~~python3
# Let's load some other packages we need
import os
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
import nibabel as nib # common way of importing nibabel
~~~

Nibabel : Nifti 파일을 읽고, 업로드하는 데에 특화된 패키지이며, nifti파일을 numpy 배열로 바꾸는 데도 사용할 수 있다.(Nifti는 3-demensional image이다.)

~~~python3
mri_file = 'anat.nii.gz'
img = nib.load(mri_file)
print(type(img))
print(img.shape)
~~~

Nibabel package를 사용해서 anat.nii.gz(anatomical nifti)파일을 업로드 하고, 업로드 한 이미지의 자료형과 모양을 파악한다.

~~~python3
fmri_file = 'func.nii.gz'
f_img = nib.load(fmri_file)
print(f_img.shape)
print(f_img.header.get_zooms())
print(f_img.header.get_xyzt_units())
~~~

functional MRI file을 nibabel 패키지를 사용해서 업로드하고, type과 shape를 출력한다.

~~~python3
# 결과물
(80,44,44,50)
(2.7,2.7,2.7,0.7)
(mm,sec)
~~~

functional MRI 이미지는 anat 과는 다르게 4번째 차원이 존재한다. 4번째 차원은 바로 시간이다. 데이터를 획득할떄 걸리는 시간이 img.shape에 들어가는 것이며, get_zooms()를 하면 voxel 단위에 시간차원이 추가된 값이 반환된다. 이렇게 말하면 이해하기 힘들 수도 있으므로 (2.7,2.7,2.7,0.7)이 있을 때, voxel의 크기(부피)는 2.7^3이지만, fMRI이미지 자체는 0.7sec마다 얻어진 것이다. 위 부분을 좀 잘 이해하려면 fMRI데이터는 한 순가에 얻어지는 것이 아닌, 촬영하는데 시간이 걸린다는 것을 알면 쉬울 것이다. 

[참조 영상(reference video](https://www.youtube.com/watch?v=4UOeBM5BwdY)

