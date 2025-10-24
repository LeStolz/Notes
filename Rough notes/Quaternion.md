2025-10-14 16:49

#Algebra

> Multiply 2 quaternion results in a rotation in 3D space.

$$
q = a + bi + cj + dk
$$
Where:
- $i^2=j^2=k^2=-1$
- $ij=k=-ji$
- $jk=i=-kj$
- $ik=-j=-ki$
And can also be represented as:
- Linear combination of $(1,i,j,k)$.
- 4D vector $q=(a,b,c,d)$.
- Scalar + vector3 $q=(a,\textbf v)$ where $\textbf{v}=(b,c,d)$
# Properties
$$\overline{q}=a-bi-cj-dk$$
$$||q||=\sqrt{ a^2+b^2+c^2+d^2 }$$
$$(q_{1}q_{2})q_{3}=q_{1}(q_{2}q_{3})$$
$$q_{1}q_{2}\neq q_{2}q_{1}$$
The product can be written as:
$$qq'=(a,\textbf{v})(a',\textbf{v'})=(aa'-vv',av'+a'v+v\times v')$$
Not to be confused with the dot product:
$$q.q'=aa'+bb'+cc'+dd'=q'.q$$
Inverse:
$$q^{-1}q=qq^{-1}=1$$
$$(q'q)^{-1}=q^{-1}q'^{-1}$$
# Rotation
A rotation around a unit vector $\textbf{v}$ with angle $2\theta$ is represented by a unit quaternion:
$$
q=\cos \theta+\textbf{v}\sin \theta=e^{\textbf{v}\theta}
$$
Thus, 
$$
q^t=e^{\textbf{v}t\theta}
$$
It is also possible that:
$$\ln(q^t=e^{\textbf{v}t\theta})=vt\theta$$
To rotate a vector $\textbf{u}$ (a quaternion with no real part), we use:
$$\textbf{u}'=q\textbf{u}q^{-1}$$
Rotation composition:
$$\textbf{u}'=q_{2}q_{1}\textbf{u}q_{1}^{-1}q_{2}^{-1}=(q_{2}q_{1})\textbf{u}(q_{2}q_{1})^{-1}$$
$$
\implies \text{The rotation } q_{1} \text{ followed by } q_{2} \text{ is just } q_{2}q_{1}
$$
Normal rotation by vector3:
$$
u'=u_{1}+\cos \theta u_{2}+\sin \theta u_{0}
$$
Where:  $u_{1}=proj(u,v)$; $u_{2}=proj(u,v_{\perp})$; $u_{0}=u\times v$
