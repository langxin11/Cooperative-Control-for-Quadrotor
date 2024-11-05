# 领航跟随的四旋翼无人机协同控制实现

## 动力学模型
别急噪！！！
1. 坐标系
  地面坐标系
  机体坐标系

  <img src="C:/Users/86150/AppData/Roaming/Typora/typora-user-images/image-20241104231103931.png" alt="image-20241104231103931" style="zoom:80%;" />

  旋转矩阵(机体坐标系${O_1}_{z_1y_1z_1}$到地面坐标系$O_{zyz}$)
$$
R(\phi,\theta,\psi)=\begin{bmatrix}\cos\psi\cos\theta&-\sin\psi\cos\theta&\sin\theta\\\sin\psi\cos\phi+\cos\psi\sin\theta\sin\phi&\cos\psi\cos\phi-\sin\psi\sin\theta\sin\phi&-\cos\theta\sin\phi\\\sin\psi\sin\phi-\cos\psi\sin\theta\cos\phi&\sin\phi\cos\psi+\sin\psi\sin\theta\cos\phi&\cos\theta\cos\phi\end{bmatrix}
$$
${P}=(x,y,z)^T\\
\Phi=(\phi,\theta,\psi)^T$

滚转角、俯仰角、偏航角
2.电机模型
$$
F=k_{F}\omega^2\\
M=k_{M}\omega^2
$$
3.动力学模型

<img src="C:/Users/86150/AppData/Roaming/Typora/typora-user-images/image-20241104203356428.png" alt="image-20241104203356428" style="zoom:80%;" />


$$
\begin{bmatrix}u\\\tau_x\\\tau_y\\\tau_z\end{bmatrix}=\begin{bmatrix}1&1&1&1\\0&-l&0&l\\-l&0&l&0\\-c&c&-c&c\end{bmatrix}\begin{bmatrix}f_1\\f_2\\f_3\\f_4\end{bmatrix}
$$


期望轨迹
$$
\begin{aligned}
&p_{xr}(t) =\cos(t) \\
&p_{yr}(t) =\sin(t) \\
&p_{zr}(t) =\sqrt{t+0.1} \\
&\psi_{r}(t) =\frac{\sin(t+0.1)}{t+0.1} 
\end{aligned}
$$


