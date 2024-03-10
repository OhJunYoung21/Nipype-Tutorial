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
