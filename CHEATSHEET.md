| Symbol          | Name                        | Formula                                                                                                | Description / Example                                 |
|-----------------|-----------------------------|--------------------------------------------------------------------------------------------------------|-------------------------------------------------------|
| Homography      |
| $\tilde{X_i^c}$ | Image coordinates           | $\tilde{X_i^c} \backsim\ \tilde{H_b^c} \cdotp \tilde{p}_i^b$                                           |                                                       |
| $K_c$           | Calibration matrix, Camera matrix          | $K_c = \begin{bmatrix} f_x & 0 & c_x \\ 0 & f_y & c_y \\ 0 & 0 & 1 \end{bmatrix}$       |                                                  
 $\tilde{x}$| homogenous transformation | $\tilde{x}= K*\begin{bmatrix} x\\y\\z \end{bmatrix}$| for direction of light rays f.e.                        |                                                        |
| $\tilde{H_b^c}$ |                             |                                                                                                        |                                                       |
| $\tilde{p}_i^b$ | Object markers              |                                                                                                        | Coordinates on the planar object                      |
| $E_b^c$         | Camera extrinsic matrix     | $E_b^c = \begin{bmatrix} R_b^c & t_{cb}^c \\ \begin{bmatrix} 0 & 0 & 0 \end{bmatrix}& 1 \end{bmatrix}$ | Relative pose between object and camera               |
|$E_c^g$ | Inverse rigid motion matrix | $E_c^g=(E_g^c)^{-1}=\begin{bmatrix} R_g^c&t_{cg}^c\\\vec{0}&1 \end{bmatrix}=$ $\begin{bmatrix} R_c^g&-R_c^gt_{cg}^c\\\vec{0}&1 \end{bmatrix}$
| $R_b^c$         | Rotation matrix             |   $R_b^c=\begin{bmatrix}0_x & 0_y & 0_z\end{bmatrix}$                                                                                                     |                                                       |
| $t_{cb}^c$      | Translation vector          | $t_c^b=p^c-R_b^c*p^b$                                                                                                   |                                                       |
| $H_b^c$         | Homography matrix           | $H_b^c \backsim\ K_c \cdotp \begin{bmatrix} r^c_{b,x} & r_{b,y}^c & t_{cb}^c \end{bmatrix}$            |                                                       |
| $r_{b,x}^c$     | Rotation vector x           | $r_{b,x}^c = \begin{bmatrix} 0 & -t_{cb,z}^c & t_{cb,y}^c \end{bmatrix}$                               |                                                       |
| $f_x, f_y$      | Focal length                | $f_x = f_y = f$                                                                                        | assume: focal length is the same in both directions   |
| $c_x, c_y$      | Principal point             |                                                                                                        |                                                       |
|                 | Object point to image point | $\begin{bmatrix} x_{s,i} \\ y_{s,i} \\ 1 \end{bmatrix} = H_b^c \cdotp \tilde{p}_i^b$                   |                                                       |
| Hough&nbsp;transform |
| $x_i, y_i$           | Image space coordinates     | $y_i = m \cdotp x_i + c \Leftrightarrow c = - m \cdotp x_i + y_i$                                    | Converted to parameter space, lines                 |
| $\theta$             | Angle of point              | $\theta$                                                                                             | angle between $x$ and line in parameter space       |
| $\rho$               | Proper Line Parametrization | $\rho = x \cos(\theta) + y \sin(\theta)$                                                             | length of line                                      |
| $\rho$               |                             | $\rho =[x,y]*n$                                                                                      |                                                     |
| $n$                  | normal vector               | $n = [\cos(\theta), \sin(\theta)]^T$                                                                 |                                                     | 
| RANSAC&nbsp;probabilities |
| $\epsilon$ | Probability of picking an outlier | $\epsilon = \dfrac{N_{outliers}}{N_{inliers} + N_{outliers}}$| with $N$ = no of, $s$ = points, $n$ = no. of trials |
|                 | probability of picking individual inlier | $p=1-\epsilon$ |
|                 | probability of picking $s$ inliers in sequence | $p=(1-\epsilon)^s$ |
|                 | probability of not picking $s$ inliers in sequence | $p=1-(1-\epsilon)^s$ |
|                 | probability of not picking $s$ inliers in sequence of $n$ trials | $p=(1-(1-\epsilon)^s)^n$ |
|                 | probability of picking at least in one of $n$ trials $s$ inliers in sequence | $p_{success}=1-(1-(1-\epsilon)^s)^n$ | for lines 2 , for circles 3 points are needed  |
|                 | expected number of trials needed | $n=\dfrac{log(1-p_{success})}{log(1-(1-\epsilon)^s)}$ | 
| Geometric transformation |
| $\tilde{x}$|Intersection of two lines| $\tilde{x}=\tilde{I_1}\times \tilde{I_2}$|cross product of two lines defines their intersection |
| $\tilde{I}$|two points lie on the line| $\tilde{I}=\tilde{x_1}\times \tilde{x_2}$|cross product of two points define their collective line |
| Matrix basics |
| $E$                       | unit matrix  | $\begin{bmatrix} 1&0&0\\0&1&0\\0&0&1  \end{bmatrix}$ |                                             
| $R^{-1}$ | Inverse rotational matrix | $R^{-1} = R^T$ |
| $R_x$ | Rotational matrix around x | $R_x=\begin{bmatrix} 1&0&0\\0&\cos&-\sin\\0&\sin&\cos  \end{bmatrix}$ |
| $R_y$ | Rotational matrix around x | $R_y=\begin{bmatrix} \cos&0&\sin\\0&1&0\\-\sin&0&\cos  \end{bmatrix}$ |
| $R_z$ | Rotational matrix around x | $R_z=\begin{bmatrix} \cos&-\sin&0\\\sin&\cos&0\\0&0&1 \end{bmatrix}$|


| $\alpha$ in degrees | 0°                       | 30°                                 | 45°                             | 60°                             | 90°                      |
|---------------------|--------------------------|-------------------------------------|---------------------------------|---------------------------------|--------------------------|
| $\alpha$ in radians | 0                        | $\frac{\pi}{6}$                     | $\frac{\pi}{4}$                 | $\frac{\pi}{3}$                 | $\frac{\pi}{2}$          |
| sin $\alpha$        | $\frac{\sqrt{0}}{2} = 0$ | $\frac{\sqrt{1}}{2} = \frac{1}{2} $ | $\frac{\sqrt{2}}{2} = 0.707.. $ | $\frac{\sqrt{3}}{2} = 0.866.. $ | $\frac{\sqrt{4}}{2} = 1$ |
| cos $\alpha$        | 1                        | $\frac{1}{2} \sqrt{3}$              | $\frac{1}{2} \sqrt{2}$          | $\frac{1}{2}$                   | 0                        |
| tan $\alpha$        | 0                        | $\frac{1}{3} \sqrt{3}$              | 1                               | $\sqrt{3}$                      | not defined              |
