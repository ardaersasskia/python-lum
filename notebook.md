应当测量T，计算如下图

$$
T(f) = \frac{ \frac{1}{2}  \int_{\text{monitor}} \mathbf{Re} (\mathbf{P}(f)) \cdot d\mathbf{S} }{\text{ sourcepower(f)} }
$$

![1706788806287](image/notebook/1706788806287.png)

```c
# simplify variable names by removing spaces
theta_start = %theta start%;
theta_stop = %theta stop%;
r_cross_section = %r cross section%;

# set parameters for cylinders to construct toroid
height = 4*pi*radius/slices*1.1;

slices=round(slices*abs(theta_start-theta_stop)/360);
theta = linspace(theta_start*pi/180,theta_stop*pi/180,slices);

for(i=1:slices) {
  addcircle;
  set("first axis","x");
  set("rotation 1",90);
  set("second axis","z");
  set("rotation 2",theta(i)*180/pi);
  set("radius",r_cross_section);
  set("x",radius*cos(theta(i)));
  set("y",radius*sin(theta(i)));

  set("z min",-height/2);
  set("z max",height/2);
  set("material",material); 
  if(get("material")=="<Object defined dielectric>") 
    { set("index",index); }
}

```
