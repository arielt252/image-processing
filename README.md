# image-processing

import cv2
import numpy as np

img=cv2.imread('noisy.jpg',0)

m,n=img.shape

mask=np.ones([3,3])
mask=mask/9


img_new=np.zeros([m,n])


for i in range(1, m-1):
    for j in range(1, n-1):
        temp = img[i-1, j-1]*mask[0, 0]+img[i-1, j]*mask[0, 1]+img[i-1, j + 1]*mask[0, 2]+img[i, j-1]*mask[1, 0]+ img[i, j]*mask[1, 1]+img[i, j + 1]*mask[1, 2]+img[i + 1, j-1]*mask[2, 0]+img[i + 1, j]*mask[2, 1]+img[i + 1, j + 1]*mask[2, 2]
        
        img_new[i, j]= temp
         
img_new = img_new.astype(np.uint8)

cv2.imshow('orginal picture',img)
cv2.imshow('Hachlaka',img_new)

#%%

img=cv2.imread('noisy.jpg',0)
m,n=img.shape

img_new1=np.zeros([m,n])

for i in range(1, m-1):
    for j in range(1, n-1):
        temp=[img [i-1, j-1],
              img[i-1, j],
              img[i-1, j+1],
              img[i, j-1],
              img[i, j],
              img[i, j + 1],
              img[i + 1, j-1],
              img[i + 1, j],
              img[i + 1, j + 1]]
              
        temp=sorted(temp)
        img_new[i,j]=temp[4]
        
        img_new1=img_new1.astype(np.uint8)
        
        cv2.imshow('orginal picture',img)
        cv2.imshow('median',img_new)
              
        
