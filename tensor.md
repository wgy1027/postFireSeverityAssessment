

In this paper, scalars are denoted by lowercase letter, e.g., $x$, vectors are written in boldface lowercased, e.g., $\mathbf{x}$, matrices correspond to boldface capitals, e.g., $\mathbf{X}$, and high-order tensors (order three or higher) are denoted by Euler script letters, e.g., $\mathbb{X}$. A matrix is a second-order tensor, a vector is a first-order tensor, and a scalar is a tensor of order zero. A tensor can be represented as a multidimensional array of numerical values. In this representation, the elements in a $k$-th order tensor are identified by a $k$-tuple of subscripts, e.g., $x_{i_1,i_2,...,i_k}$. The operations upon tensor is based on multilinear algebra. Some important operations and concepts of matrix and tensor that are used in this paper are listed here, and the others are introduced later when they appear.

Definition 1: Different dimensions of an array are called modes. A matrix has two modes (column mode and row mode), and a kth-order tensor $\mathbb{X}$ has $k$ modes.

Definition 2: A tensor fiber is a one-dimensional fragment of a tensor, obtained by fixing all indices except for one.
Definition 3: A tensor slab is a two dimensional section (fragment) of a tensor, obtained by fixing all indices except for two indices.
Definition 4: Unfolding a tensor is the process of reordering the elements of a kth-order tensor into a matrix. For a thirdorder tensor $\mathbb{X}\in \mathbb{R}^{I\times J\times K}$, three matrices unfolded from this tensor are defined by
$\begin{aligned}\left(\mathbf{X}_{J K \times I}\right)_{(j-1) K+k, i} &=x_{i j k} \\\left(\mathbf{X}_{K I \times J}\right)_{(k-1) I+i, j} &=x_{i j k} \\\left(\mathbf{X}_{I J \times K}\right)_{(i-1) J+j, k} &=x_{i j k} \end{aligned}$
