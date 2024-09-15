---
title: "What is Spinor?"
date: 2024-09-15
lastmod: 2024-09-15
tags: ["Spinor", "Mathematical-Physics"]
author: ["Emon Hossain"]
description: "nobody understands quantum mechanics - feynman"
summary: "nobody understands quantum mechanics - feynman"
editPost:
  URL: "https://emonhossainraihan.github.io/"
  Text: "GitHub repository"
showToc: true
disableAnchoredHeadings: false
---

We can convert $3D$-vector into $2\times 2$ Pauli vector using Pauli matrices as a basis. That means for traditional basis $\vec e_1, \vec e_2$ and $\vec e_3$ we choose $\sigma_x, \sigma_y$ and $\sigma_z$. Hence, $V=V^ie_i$ become $V=V^i\sigma_i$ where,

\\begin{align*}
\\sigma_x &= \\begin{bmatrix}
0&1\\\1&0
\\end{bmatrix}\\\
\\sigma_y &= \\begin{bmatrix}
0&-i\\\
i&0
\\end{bmatrix}\\\
\sigma_z &= \\begin{bmatrix}
1&0\\\
0&-1
\\end{bmatrix}
\\end{align*}

Each of these Pauli matrices is trace-less with determinant of $-1$. Some properties of these Pauli matrices are:

- Traceless $\operatorname{tr}(\sigma_i)=0$
- Hermitian $(\sigma_i)^\dagger=\sigma_i$
- Square to identity $(\sigma_i)^2=I_2$
- Anti-commute $\sigma_i\sigma_j=-\sigma_j\sigma_i,\quad i\neq j$

$(3)+(4)$ can summarize by anti-commutation: $\sigma_i\sigma_j+\sigma_j\sigma_i=\{\sigma_i,\sigma_j\}=2\delta_{ij}$.

Considering them as a basis can make life easier.

$$
\\begin{bmatrix}
    x\\\y\\\z
\\end{bmatrix}\\rightarrow \\begin{bmatrix}
    z&x-yi\\\x+yi&-z
\\end{bmatrix}\rightarrow \\underbrace{\\begin{bmatrix}
    \\xi_1\\\\xi_2
\\end{bmatrix}\\begin{bmatrix}
    -\\xi_2&\\xi_1
\\end{bmatrix}}_{\\text{Spinors}}
$$

$$
\\begin{bmatrix}
    ct\\\x\\\y\\\z
\\end{bmatrix}\\rightarrow \\begin{bmatrix}
    ct+z&x-yi\\\x+yi&ct-z
\\end{bmatrix}\\rightarrow \\underbrace{\\begin{bmatrix}
    \\psi_1\\\\psi_2
\\end{bmatrix}\\begin{bmatrix}
    -\\psi_2^\*&\\psi_1^\*
\\end{bmatrix}}_{\\text{Weyl Spinors}}
$$

Let the Pauli vector is defined as: $V=x\sigma_x+y\sigma_y+z\sigma_z$. Because we can represent reflection and rotation easily on this basis. Let's give a try for conjugating the Pauli vector by $\sigma_z$,

\\begin{align*}
V&\\rightarrow \\sigma_z^{-1} V\\sigma_z\\\
&=\\sigma_z (x\\sigma_x+y\\sigma_y+z\\sigma_z)\\sigma_z\\\
&=(x\\sigma_z\\sigma_x\\sigma_z+y\\sigma_z\\sigma_y\\sigma_z+z\\sigma_z\\sigma_z\\sigma_z)\\\
&=-x\\sigma_x-y\\sigma_y+z\\sigma_z\\\
\\end{align*}

It seems like we can represent reflection if we use negative conjugation.

\\begin{align*}
V&\\rightarrow -\\sigma_z^{-1} V\\sigma_z\\\
&=-\\sigma_z (x\\sigma_x+y\\sigma_y+z\\sigma_z)\\sigma_z\\\
&= -(x\\sigma_z\\sigma_x\\sigma_z+y\\sigma_z\\sigma_y\\sigma_z+z\\sigma_z\\sigma_z\\sigma_z)\\\
&=x\\sigma_x+y\\sigma_y-z\\sigma_z\\\
&=\\text{Reflection along z-axis}
\end{align*}

Let's further generalize it to make reflection along unit vector $U$:

\\begin{align*}
V&\\rightarrow \\sigma_z^{-1} V\\sigma_z\\\
 &=\\sigma_z (x\\sigma_x+y\\sigma_y+z\\sigma_z)\\sigma_z\\\
 &=(x\\sigma_z\\sigma_x\\sigma_z+y\\sigma_z\\sigma_y\\sigma_z+z\\sigma_z\\sigma_z\\sigma_z)\\\
 &=-x\\sigma_x-y\\sigma_y+z\\sigma_z\\\
\\end{align*}

Great! So far so good. But now instead of reflection, we want to represent rotation. And we already knew that, "A rotation is nothing but two reflections". For that, we need two mirrors which will be used in reflections. The angle between them is the half of the rotation. Again, start with some trial. Let's try to rotate the Pauli vector by angle $\theta$ in $xy$-plane. For this, we first reflect along the $x$-axis. And rotate further by another mirror which creates $\theta/2$ angle from the $x$-axis which we denoted by $\tau=\cos\frac{\theta}{2}\sigma_x+\sin\frac{\theta}{2}\sigma_y$.

$$
\\begin{align}
\\begin{split}
 V&\\rightarrow -\\tau(-\\sigma_x V\\sigma_x)\\tau\\\
 &= \\left(\\cos\\frac{\\theta}{2}\\sigma_x\\sigma_x+\\sin\\frac{\\theta}{2}\\sigma_y\\sigma_x\\right) V \\left(\\cos\\frac{\\theta}{2}\\sigma_x\\sigma_x+\\sin\\frac{\\theta}{2}\\sigma_x\\sigma_y\\right)\\\
 &= \\underbrace{\\left(\\cos\\frac{\\theta}{2}\\mathds{1}-\\sin\\frac{\\theta}{2}\\sigma_x\\sigma_y\\right)}\_{I} V \\underbrace{\\left(\\cos\\frac{\\theta}{2}\\mathds{1}-\\sin\\frac{\\theta}{2}\\sigma_x\\sigma_y\\right)^\\dagger}\_{II}
\\end{split}
\\end{align}
$$

Writing the first term in matrix notation we get,

\\begin{align*}
&\\cos\\frac{\\theta}{2}\\mathds{1}-\\sin\\frac{\\theta}{2}\\sigma_x\\sigma_y\\\
 &= \\cos\\frac{\\theta}{2}\\begin{bmatrix}
1&0\\\0&1
\\end{bmatrix}-\\sin\\frac{\\theta}{2}\\begin{bmatrix}
0&1\\\1&0
\\end{bmatrix}\\begin{bmatrix}
0&-i\\\\+i&0
\\end{bmatrix}\\\
 &= \\begin{bmatrix}
\\cos\\frac{\\theta}{2}-\\sin\\frac{\\theta}{2}&0\\\
 0&\\cos\\frac{\\theta}{2}+\\sin\\frac{\\theta}{2}
\\end{bmatrix}\\\
 &= \\begin{bmatrix}
e^{-i\\frac{\\theta}{2}}&0\\\0&e^{i\\frac{\\theta}{2}}
\\end{bmatrix}
\\end{align*}

Do the same thing for the right term and by combining all expression \ref{rotation_sigma} become:

\\begin{align*}
&\\left(\\cos\\frac{\\theta}{2}\\mathds{1}-\\sin\\frac{\\theta}{2}\\sigma_x\\sigma_y\\right)V\\left(\\cos\\frac{\\theta}{2}\\mathds{1}-\\sin\\frac{\\theta}{2}\\sigma_x\\sigma_y\\right)^\\dagger\\\
 &=\\begin{bmatrix}
e^{-i\\frac{\\theta}{2}}&0\\\0&e^{i\\frac{\\theta}{2}}
\\end{bmatrix} \\begin{bmatrix}
z&(x-iy)\\\ (x+iy)&-z
\\end{bmatrix} \\begin{bmatrix}
e^{-i\\frac{\\theta}{2}}&0\\\0&e^{i\\frac{\\theta}{2}}
\\end{bmatrix}^\\dagger\\\
 &= \\begin{bmatrix}
z&e^{-i\\theta}(x-iy)\\\e^{i\\theta}(x+iy)&-z
\\end{bmatrix}
\\end{align*}

Here,

\\begin{align*}
e^{i\\theta}(x+iy)&=(\\cos\\theta+i\\sin\\theta)(x+iy)\\\
 &= (x\\cos\\theta-y\\sin\\theta)+i(x\\sin\\theta+y\\cos\\theta)
\\end{align*}
Which exactly matches our rotation transformation in $3$-dimension by angle $\\theta$:
\\begin{align*}
\\begin{bmatrix}
x\\\y\\\z
\\end{bmatrix}\\rightarrow\\begin{pmatrix}
\\cos\\theta&-\\sin\\theta&0\\\
 \\sin\\theta&\\cos\\theta&0\\\
 0&0&1
\\end{pmatrix}\\begin{bmatrix}
x\\\y\\\z
\\end{bmatrix}
\\end{align*}

Similiarly, Rotate the Pauli vector by angle $\theta$ in $yz$-plane and $zx$-plane we get:

\\begin{align*}
V&\\rightarrow\\left(\\cos\\frac{\\theta}{2}\\mathds{1}-\\sin\\frac{\\theta}{2}\\sigma_y\\sigma_z\\right)V\\left(\\cos\\frac{\\theta}{2}\\mathds{1}-\\sin\\frac{\\theta}{2}\\sigma_y\\sigma_z\\right)^\\dagger\\\
 V&\\rightarrow\\left(\\cos\\frac{\\theta}{2}\\mathds{1}-\\sin\\frac{\\theta}{2}\\sigma_z\\sigma_x\\right)V\\left(\\cos\\frac{\\theta}{2}\\mathds{1}-\\sin\\frac{\\theta}{2}\\sigma_z\\sigma_x\\right)^\\dagger
\\end{align*}

And their corresponding matrix expression becomes,

\\begin{align*}
\\left(\\cos\\frac{\\theta}{2}\\mathds{1}-\\sin\\frac{\\theta}{2}\\sigma_x\\sigma_y\\right)&\\rightarrow
\\begin{bmatrix}
e^{-i\\frac{\\theta}{2}}&0\\\0&e^{i\\frac{\\theta}{2}}
\\end{bmatrix} \\\
 \\left(\\cos\\frac{\\theta}{2}\\mathds{1}-\\sin\\frac{\\theta}{2}\\sigma_z\\sigma_x\\right)&\\rightarrow\\begin{bmatrix}
\\cos\\frac{\\theta}{2}&-\\sin\\frac{\\theta}{2}\\\ \\sin\\frac{\\theta}{2}&\\cos\\frac{\\theta}{2}
\\end{bmatrix}\\\
 \\left(\\cos\\frac{\\theta}{2}\\mathds{1}-\\sin\\frac{\\theta}{2}\\sigma_y\\sigma_z\\right)&\\rightarrow\\begin{bmatrix}
\\cos\\frac{\\theta}{2}&-i\\sin\\frac{\\theta}{2}\\\ i\\sin\\frac{\\theta}{2}&\\cos\\frac{\\theta}{2}
\\end{bmatrix}
\\end{align*}

Hence, the two-sided rotation of our Pauli vector worked. It turns out that this two-sided rotation matrices are special unitary $2\times2$ matrices. For example,

\\begin{align*}
\\begin{pmatrix}
e^{-i\\frac{\\theta}{2}}&0\\\
 0&e^{i\\frac{\\theta}{2}}
\\end{pmatrix}\\begin{pmatrix}
e^{-i\\frac{\\theta}{2}}&0\\\
 0&e^{i\\frac{\\theta}{2}}
\\end{pmatrix}^\\dagger&=\\begin{pmatrix}
e^{-i\\frac{\\theta}{2}}&0\\\
 0&e^{i\\frac{\\theta}{2}}
\\end{pmatrix}\\begin{pmatrix}
e^{i\\frac{\\theta}{2}}&0\\\
 0&e^{-i\\frac{\\theta}{2}}
\\end{pmatrix}\\\
 &=\\begin{pmatrix}
1&0\\\
 0&1
\\end{pmatrix}
\\end{align*}

And $\det \\begin{pmatrix}
    e^{-i\\frac{\\theta}{2}}&0\\\
        0&e^{i\\frac{\\theta}{2}}
\\end{pmatrix}=+1$.

We start assuming that rotating a Pauli-vector can be done with a double-sided transformation with matrices $A, B$: $V\rightarrow AVB$. Then we can figure out what $A, B$ look like from the properties of the Pauli vector. Since the Pauli vector is hermitian, the resulting Pauli vector after the transformation should also be hermitian $AVB=(AVB)^\dagger$. This gives us:

\\begin{align*}
AVB&=(AVB)^\\dagger\\\
 &= B^\\dagger V^\\dagger A^\\dagger\\\
 &= B^\\dagger V A^\\dagger\\\
\\end{align*}

This hints to us, $A=B^\dagger$ and $B=A^\dagger$. This implies, $B=A^\dagger$. Hence, $V\rightarrow AVA^\dagger$. Again, determinant or squared length $\det V=-\|\vec v\|^2$ unchanged after rotation.

\\begin{align*}
\\det V &= \\det (AVA^\\dagger)\\\
 1&= \\det A \\det A^*\\\
 1 &= |\\det A|^2
\\end{align\*}

This means that the determinant of $A$ can be any complex number with magnitude $1$ which implies $\det A=e^{i\theta}$. Let's replace our $A$ with $Ae^{i\phi}$:

\\begin{align*}
V&\\rightarrow AVA^\\dagger\\\
 &= (Ae^{i\\phi})V(Ae^{i\\phi})^\\dagger\\\
 &= A e^{i\\phi} V e^{-i\\phi} A^\\dagger\\\
 &= AVA^\\dagger
\\end{align*}

So, there is a redundancy in the $A$ matrices for doing rotations. But we can always force a matrix to have a determinant $1$ without changing the phase because of the double-sided transformation.

$$
\text{If }\det \\begin{bmatrix}
    a&b\\\c&d
\\end{bmatrix}=ad-bc=e^{i\theta}\text{ then }\det \left(e^{-i\frac{\theta}{2}} \\begin{bmatrix}
    a&b\\\c&d
\\end{bmatrix}\right)=+1
$$

With, $$(Ae^{-i\frac{\theta}{2}})V(Ae^{-i\frac{\theta}{2}})^\dagger=AVA^\dagger$$
Finally, the Pauli vector has no trace.

\\begin{align}
\\begin{split}
\\operatorname{tr}(AVA^\\dagger)&=0\\\
\\operatorname{tr}(A^\\dagger AV)&=0
\\end{split}
\\end{align}

But $A^\dagger A = k\mathds 1$. We can show that by assuming $A^\dagger A=\\begin{bmatrix}
    a&b\\\c&d
\\end{bmatrix}$ and solving the system of equations $0=\operatorname{tr}(Q\sigma_x)=\operatorname{tr}(Q\sigma_y)=\operatorname{tr}(Q\sigma_z)$ using ?.

\\begin{align*}
\\det(A^\\dagger A)&= k\\mathds{1}\\\
 \\det A^\\dagger \\det A &= k^2\\\
 \\implies k&= \\pm 1
\\end{align*}

But, $$A^\\dagger A=\\begin{bmatrix}
    \\alpha^\*&\\beta^\*\\\
    \\gamma^\*&\\delta^\*
\\end{bmatrix}\\begin{bmatrix}
    \\alpha&\\gamma\\\
    \\beta&\\delta
\\end{bmatrix}=\\begin{bmatrix}
    \\underbrace{\\alpha^\*\\alpha+\\beta^\*\\beta}_{\\geq 0}&\-\\\\-&\-
    \\end{bmatrix}\\implies A^\\dagger A=\\mathds{1}$$

This implies $A^\dagger=A^{-1}$. Altogether we can say, $A\in SU(2)$, that means rotating a Pauli vector we need:

$$
[SU(2)]\\begin{bmatrix}
    z&x-yi\\\
    x+yi&-z
\\end{bmatrix}[SU(2)]^\dagger
$$

And we know that all $SU(2)$ matrices look like, $$A=\\begin{bmatrix}
    \\alpha&-\\beta^\*\\\ \\beta&\\alpha^\*
\\end{bmatrix},\\quad \\det(A)=+1\\implies |\\alpha^2|+|\\beta|^2=1$$

That means we have $4$-real constraints. But we can deduce one more from the determinant condition of $U(2)$ matrix: $e^{i\theta}=1\implies \theta=0$. This reflects there are $3$ independent planes of rotation, $xy,yz$ and $zx$-plane. Now, again replace $A\rightarrow-A$ we get,

\\begin{align*}
V&\\rightarrow(-A)V(-A)^\\dagger\\\
 &=AVA^\\dagger
\\end{align*}

This means that for every $3\times3$ rotation matrix in the group $SO(3)$, there are $2$ corresponding rotation matrices $\pm A$ in $SU(2)$ that do the same rotation.

Instead of rotating a $3$D vector with a $3\times3$ rotation matrix, we can rotate it using a double-sided transformation.

\\begin{align*}
\\begin{bmatrix}
\\cos\\theta&-\\sin\\theta&0\\\
 \\sin\\theta&\\cos\\theta&0\\\
 0&0&1
\\end{bmatrix}\\begin{bmatrix}
x\\\y\\\z
\\end{bmatrix}&\\longleftrightarrow \\begin{bmatrix}
e^{-i\\frac{\\theta}{2}}&0\\\
 0&e^{i\\frac{\\theta}{2}}
\\end{bmatrix}\\begin{bmatrix}
z&x-yi\\\
 x+yi&-z
\\end{bmatrix}\\begin{bmatrix}
e^{-i\\frac{\\theta}{2}}&0\\\
 0&e^{i\\frac{\\theta}{2}}
\\end{bmatrix}^\\dagger\\\
\\end{align*}

Wait a minute, doesn't it look like a quaternion transformation? We can find the equivalence by considering the unit quaternions to $SU(2)$ matrices. In fact, our Pauli matrices look like the quaternion imaginary units.

$$
i\leftrightarrow-\sigma_y\sigma_z,\quad j\leftrightarrow-\sigma_z\sigma_x,\quad k\leftrightarrow-\sigma_x\sigma_y
$$

Then considering $ v=0+xi+yj+zk$ we get,

$$
\left(\cos\frac{\theta}{2}+\sin\frac{\theta}{2}[a^xi+a^yj+a^zk]\right) v\left(\cos\frac{\theta}{2}+\sin\frac{\theta}{2}[a^xi+a^yj+a^zk]\right)^*
$$

where $a^xi+a^yj+a^zk$ represent the axis of rotation.

**definition**: A spin group $\operatorname{Spin}(n)$ is defined as a double cover of the special orthogonal group $SO(n)$ satisfying some more condition.
$$1\rightarrow\mathbb Z_2\rightarrow\operatorname{Spin}(n)\rightarrow SO(n)\rightarrow 1$$

"A 3D vector can be factored into column and row spinors".

We know that most of the time we can factor our matrix into two small matrices. If we factor our Pauli vector into a pair of Pauli Spinors then each Spinor only transforms with a single $SU(2)$ matrix.

\\begin{align}
\\begin{bmatrix}
z&x-iy\\\x+iy&-z
\\end{bmatrix}=\\underbrace{\\begin{bmatrix}
\\epsilon^1\\\ \\epsilon^2
\\end{bmatrix} \\begin{bmatrix}
-\\epsilon^2&\\epsilon^1
\\end{bmatrix}}\_{\\text{Pauli Spinors}}
\\end{align}

Where

\\begin{align}
[SU(2)]\\begin{bmatrix}
z&x-iy\\\x+iy&-z
\\end{bmatrix}[SU(2)]^\\dagger=\\underbrace{[SU(2)]\\begin{bmatrix}
\\epsilon^1\\\ \\epsilon^2
\\end{bmatrix}}\_{\\text{Half Rotation}} \\underbrace{\\begin{bmatrix}
-\\epsilon^2&\\epsilon^1
\\end{bmatrix}[SU(2)]^\\dagger}\_{\\text{Half Rotation}}
\\end{align}

This explains why Spinor rotates half as much as vectors do. So, we want,

$$
\\begin{bmatrix}
    a\\\b
\\end{bmatrix}\\begin{bmatrix}
    c&d
\\end{bmatrix}=\\begin{bmatrix}
    z&x-iy\\\x+iy&-z
\\end{bmatrix}\\implies \\begin{cases}
    ac=z\\\
    bc=x+iy\\\
    ad=x-iy\\\
    bd=-z
\\end{cases}
$$

Which have a solution only when $\det M=0\implies -(x^2+y^2+z^2)=0$. So, we have:

$$
\\begin{align*}
z&=i\\sqrt{x^2+y^2}\\\
 &=\\left(\\sqrt{x-iy}\\right)\\left(\\sqrt{x+iy}\\right)i\\\
 &=\\underbrace{\\left(\\sqrt{x-iy}\\right)}\_{a}\\underbrace{\\left(\\sqrt{x+iy}\\right)i}\_{c}\\\
 \\\
 bc&=x+iy\\\
 \\implies b&=-c\\quad\\text{using }c\\\
 \\\
 ad&= x-iy\\\
 \\implies d&=a\\quad\\text{using }a
\\end{align*}
$$

Relabelling $a,b$ into $\epsilon^1,\epsilon^2$ we get,

$$
\\begin{bmatrix}
    \\epsilon^1\\\ \\epsilon^2
\\end{bmatrix}\\begin{bmatrix}
    -\\epsilon^2&\\epsilon^1
\\end{bmatrix}=\\begin{bmatrix}
    z&x-yi\\\
    x+yi&-z
\\end{bmatrix}
$$

Hence,

$$
\\begin{bmatrix}
    \\epsilon^1\\\ \\epsilon^2
\\end{bmatrix}=\\begin{bmatrix}
    \\sqrt{x-iy}\\\ -i\sqrt{x+iy}
\\end{bmatrix}
$$

We can always multiply our Spinors by a complex number with magnitude $A$ and phase $\theta$,

$$
\\begin{bmatrix}
    \\epsilon^1\\\ \\epsilon^2
\\end{bmatrix}Ae^{i\\theta}\\frac{1}{Ae^{i\\theta}}\\begin{bmatrix}
    -\\epsilon^2&\\epsilon^1
\\end{bmatrix}
$$

When we choose $Ae^{i\theta}=\epsilon^1$ then we get,

$$
\\begin{bmatrix}
    \\epsilon^1\\\ \\epsilon^2
\\end{bmatrix}\\frac{1}{\\epsilon^1}\\epsilon^1\\begin{bmatrix}
    -\\epsilon^2&\\epsilon^1
\\end{bmatrix}=\\begin{bmatrix}
    1\\\ \\frac{\\epsilon^2}{\\epsilon^1}
\\end{bmatrix}\\epsilon^1\\begin{bmatrix}
    -\\epsilon^2&\\epsilon^1
\\end{bmatrix}
$$

Then we can relate our ratio $\frac{\epsilon^2}{\epsilon^1}$ with the concept of Projective geometry. When several Spinors have the same component ratio, we do consider them to be different Spinors but they are all associated with the same Pauli vector. So, they can be grouped together in a kind of family. Now, back to our equation \ref{half_rotation}. For $\epsilon=\\begin{bmatrix}
    \\epsilon^1\\\ \\epsilon^2
\\end{bmatrix}$ we know that $\|\epsilon\|^2=\epsilon^\dagger\epsilon$. When we apply $SU(2)$ multiplication,

$$
\\begin{align*}
    \\epsilon^\\dagger\\epsilon&\\rightarrow (U\\epsilon)^\\dagger(U\\epsilon)\\\
    &=\\epsilon^\\dagger U^\\dagger U \\epsilon\\\
    &= \\epsilon^\\dagger \\epsilon
\\end{align*}
$$

But what if our Pauli vector has $\det V\neq 0$. Then we can't factor it like \ref{factor_sp}.

$$
\\begin{align*}
    \\begin{bmatrix}
        z&x-yi\\\x+yi&-z
    \\end{bmatrix}&=z\\begin{bmatrix}
        1&0\\\0&0
    \\end{bmatrix}+(x+yi)\\begin{bmatrix}
        0&0\\\1&0
    \\end{bmatrix}+(x-yi)\\begin{bmatrix}
        0&1\\\0&0
    \\end{bmatrix}+(-z)\\begin{bmatrix}
        0&0\\\0&1
    \\end{bmatrix}\\\
    &=z\\underbrace{\\begin{bmatrix}
        1\\\0
    \\end{bmatrix}\\begin{bmatrix}
        1&0
    \\end{bmatrix}}\_{\\text{Spinor pair}}+(x+yi)\\underbrace{\\begin{bmatrix}
        0\\\1
    \\end{bmatrix}\\begin{bmatrix}
        1&0
    \\end{bmatrix}}\_{\\text{Spinor pair}}+(x-yi)\\underbrace{\\begin{bmatrix}
        1\\\0
    \\end{bmatrix}\\begin{bmatrix}
        0&1
    \\end{bmatrix}}\_{\\text{Spinor pair}}+(-z)\\underbrace{\\begin{bmatrix}
        0\\\1
    \\end{bmatrix}\\begin{bmatrix}
        0&1
    \\end{bmatrix}}\_{\\text{Spinor pair}}
\\end{align*}
$$

Some useful links:

- https://math.stackexchange.com/a/37583
- https://math.stackexchange.com/a/1725873
- https://www.wikiwand.com/en/articles/Covering_space#Universal_covering
