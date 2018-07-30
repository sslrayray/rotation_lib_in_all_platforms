# What is homogeneous coordinate and homogeneous matrix?

---
ylei 2018.7.30

##Cartisian coordinate
Students learn to present a point with Cartisian coodinate since their primary school. It is a very useful tool because once a base coordinate frame is setup, any point in the space can be presented with just a pair of number with respective to base coordinate frame:
 $$(x_{0}, y_{0})$$

##Rotation matrix
I have a point \\(p\\) presented with Cartisian coordinate \\((x_a, y_a)\\) with respective to frame \\(F_a\\), if I rotate this point by axis Z of \\(F_a\\)with degree \\(-\theta\\), and then we have the new point \\(p'\\), the question is what's the Cartisian coordinate value of \\(p'_a\\), calculate \\((x'_a, y'_a)\\), \\(p_a\\) means the coordinate value of point \\(p\\) with respective to frame \\(F_a\\) 

Actually, rotating the point \\(p\\) by axis Z of \\(Fa\\) with \\(-\theta\\) is equal to rotating the frame \\(Fa\\) by axis Z with \\(\theta\\), and then question can be transfered to what is the point's coordinate in the new frame \\(F_b\\), aka \\(p_b\\)?

It's easy to prove the following equation from the following figure:

 \\(p'_a = p_b = \begin{bmatrix} x_b \\\ y_b \end{bmatrix}  = \begin{bmatrix} cos\theta & sin\theta \\\ -sin\theta & cos\theta\end{bmatrix} \cdot \begin{bmatrix} x_a \\\ y_a \end{bmatrix} \\) 
 
![rotation matrix](https://images2017.cnblogs.com/blog/47448/201712/47448-20171205160012238-457627183.png)

For convenience, we present rotation matrix with 
$$R_z(-\theta) = \begin{bmatrix} cos\theta & sin\theta \\\ -sin\theta & cos\theta\end{bmatrix} $$

or another more widely used notation: 
$$R_z(\theta) = \begin{bmatrix} cos\theta & -sin\theta \\\ sin\theta & cos\theta\end{bmatrix} $$


#Homogeneous matrix
Similarly, a translation can also be written in multiplication form:
if \\(p_{ab}=p_{b} - p_{a} \\), then \\(
\begin{bmatrix}p_{b_x} \\\ p_{b_y} \\\ 1 \end{bmatrix} = 
\begin{bmatrix} 1 & 0 & p_{ab\_x} \\\  0 & 1 & p_{ab\_y} \\\ 0 & 0& 1\end{bmatrix} 
\cdot \begin{bmatrix}p_{a_x} \\\ p_{a_y} \\\ 1\end{bmatrix}
\\)

What's more interesting is we can combine the rotation and translation in one homogeneous matrix, if \\(p_c\\) is the coordinate of point \\(p_a\\) after a rotation by axis Z and a following translation \\(p_{ca}\\): 

then  $$  p_c = R_z(\theta) \cdot p_a + p_{ca} $$

$$ \begin{bmatrix} p_{c_x} \\\ p_{c_y} \\\ 1 \end{bmatrix} =
 \begin{bmatrix} 1 & 0 & p_{ca_x} \\\  0 & 1 & p_{ca_y} \\\ 0 & 0& 1\end{bmatrix} \cdot \begin{bmatrix} cos\theta & -sin\theta & 0 \\\ sin\theta & cos\theta & 0 \\\ 0 & 0 & 1  \end{bmatrix}  \cdot 
 \begin{bmatrix} p_{a_x} \\\ p_{a_y} \\\ 1 \end{bmatrix} $$

 $$ \begin{bmatrix} p_{c_x} \\\ p_{c_y} \\\ 1 \end{bmatrix} =
 \begin{bmatrix} 
 cos\theta & -sin\theta & p_{ca_x} \\\
  sin\theta & cos\theta & p_{ca_y} \\\ 
  0 & 0 & 1  
  \end{bmatrix}  
  \cdot 
 \begin{bmatrix} p_{a_x} \\\ p_{a_y} \\\ 1 \end{bmatrix} $$

We call $$ \begin{bmatrix} p_{c_x} \\\ p_{c_y} \\\ 1 \end{bmatrix} $$as homogeneous coordinate, which is different from Cartisian coordinate, and call 
$$\begin{bmatrix} 
 cos\theta & -sin\theta & p_{ca_x} \\\
  sin\theta & cos\theta & p_{ca_y} \\\ 
  0 & 0 & 1  
  \end{bmatrix}$$
as homogeneous matrix, which contains a rotation part and a translation part.
