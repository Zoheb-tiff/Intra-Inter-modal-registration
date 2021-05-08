# Intra-Inter-modal-registration

1.  Take any MRI image and call it as reference image (R). 
Write a code to create new Image (R1 = a*R+b), a and b numbers are user (your) choice. (a>0, b>0). 
Create sequence of floating images (F) from R1 by incremental rotation from 1 degree to 10 degree. 
Compute Cross Correlation (CC) between R and Fn, n=1,2,..10 and plot graph of CC vs angle. 

Code in "Intramodal Registration"

Here, we take a = 30 and b = 500. (User Defined)
R1 = aR + b
We create a matrix which contains the images F1 – F10. 
As these images are themselves matrices, we declare the type to be cell. So F contains images which are rotated from 1 degree to 10 degrees.
We create another matrix of type cell, which we name as CC. This contains the cross correlated values of R and Fn.
We plot this CC{i} as a surface plot
The maximum point of the CC{i} gives us the Cross-Correlation value. As in, how similar the F{i} image is to R. This value is stored in CrossCorr.
Then we plot CrossCorr as a function of the Angle. As expected, the more we rotate the image, the lesser is the Cross-Correlation value.


2.  Choose R as T1-W image and R1 as T2-W image. (I have uploaded T1-W and T2-W images on Moodle). 
Create sequence of floating images (Fn) from R1 by incremental rotation from 1 degree to 10 degree. 
Compute ‘Normalized Ratio’ between R and Fn, n=1,2,..10, plot graph and make interpretations.  
Similarly compute CC between Fn and R and plot graph of CC vs angle.

Code in "Inter-modal Registration"
Here we read T1W image into R and T2W image into R1.
As R and R1 images are of two different modalities, they have different intensity levels.
Both the images are normalized.

"A cost function that does allow for global differences in image intensity without the need for formal modelling of an intensity scaling parameter is the 
ratio uniformity cost function introduced in 1992. 
If one image is divided by the other image on a voxel-by-voxel basis, the resulting ratio image should have a constant uniform value when the images are well registered. 
Any mis-registration will induce non-uniformities. The ratio image cost function quantifies this lack of uniformity by computing the standard deviation of the ratio image 
and normalizing the result by the mean ratio. [1]"

We create a matrix which contains the images F1 – F10. As these images are themselves matrices, 
we declare the type to be cell. So F contains images which are rotated from 1 degree to 10 degrees. 
While creating F, we also take care that the dimensions of F{i} matches with the dimensions of R
Then we find a matrix r(x) = R(x)/F(x). Here r(x) would be a matrix itself. So we create a cell of dimension (1,10).
We take care to remove all zero values from F{i} by adding 0.001 to all values of F{i}.
For each of the r(i) values, we calculate sigma and mean, which we store in sigmar(i) and meanr(i).
We find the normalized standard deviation by dividing the standard deviation, sigmar by the corresponding mean, meanr, 
and save it in vector normratio which is of dimensions (1,10).
We see that the Normalized Ratio is increasing, thereby we conclude that with increase in angle, the standard deviation is increasing, i.e the co-efficient of variability is increasing.
We also compute the Cross Correlation, save it under CrossCorr, and plot it vs the angle.

In case of comparison of images for the similarity when the two images are of different modalities, CC might not be a reliable measure. 
In such cases, Normalized Standard Deviation is used to measure the amount of variation.



