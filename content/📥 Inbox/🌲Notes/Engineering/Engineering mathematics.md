Engineering mathematics 

### linear algebra/matrix theory

#### Matrix $[{a_i}_j]_{m\times{n}}$   
* *$a_{ij}=i^{th} row, j^{th}coloumn$  
* $m\times{n}$ is the order
* matrix multiplication
	* let $A=[{a_i}_j]_{m\times{n}}$ and $B=[{b_i}_j]_{n\times{r}}$
	* $C=A\times B = [C_{ij}]_{m\times r}$ 
		* where $C_{ij}=\begin{bmatrix}a_{i1}&a_{i2}&a_{i3}&...&a_{in}\end{bmatrix}\times\begin{bmatrix}b_{1j}\\ b_{2j} \\.\\.\\.\\ b_{nj}\end{bmatrix}$  
		* $C_{ij}=a_{i1}\times b_{1j}+a_{i2}\times b_{2j}+...+a_{in}\times b_{nj}$
	* Number of multiplications to find $AB$ : $mrn$
	* number of additions to find $AB:mr(n-1)$
	* example questions: 
		* eg1. how many multiplicaitons required for $A_{4\times 5}\times B_{5\times 2}\times C_{2\times 1}$ 
			* Soln: 4x5x2 + 4x2 = 48. (but not minimum) This is for (AxB)xC
			* For Ax(BxC), we get 30 multiplications. 
		* eg2. Number of square matrices of order 2 whose elements can be either 0 or 1 
			* Soln: $2^4=16$
		* eg3. Numner of square matrices of order n 
			* Soln: $2^{n^2}$
		* eg4. 
		* eg5. $U=[a_{ij}]_{m\times n}$ is upper triangular matrix if $a_{ij}= 0 \ \ \forall \ \ i>j$    
* Vectors
	* Let $X=\begin{bmatrix}x_1\\ x_2\\ .\\.\\ x_n\end{bmatrix}$ and $Y=\begin{bmatrix}y_1\\ y_2\\ .\\.\\ y_n\end{bmatrix}$ be 2 coloumn vectors
	* Properties:
		* Length or norm
			* $\|X\|=\sqrt{x_1^2+x_2^2+...+x_n^2}$ 
			* not 'mod'
		* Normalizing a vector X
			* i.e. getting a unit vector in the direction of vector X
			* normalized $\hat X = \frac{\vec X}{\|X\|}$   
		* Dot product 
			* $X\cdot Y=x_1y_1+x_2y_2+...+x_ny_n$ 
			* If $X\cdot Y=0$ then $X,Y$ are orthogonal vectors
			*  If $X\cdot Y=0$, and $\|X\|=1=\|Y\|$ then $X\ \& \  Y$ are  orthonormal vectors
* Symmetry definitions: A **square** matrix $A=(a_{ij})_{m\times n}$ is 
	* symmetric $\implies$ $A=A^T$ , i.e $a_{ij}=a_{ji}$ 
	* skew symmetric $\implies$ $A= -A^T$ , i.e. $a_{ij}=-a_{ji} \ \ \&\ \  a_{ii}=0$ 
	* Orthogonal $\implies$ $A^T=A^{-1} \ \ or\ \  A\cdot A^T=I$ 
	* result: the rows(columns) of an orthogonal matrix form an orthonormal setasdf: 
	* Examples:
		* eg. $A=\begin{bmatrix}\frac{1}{\sqrt{2}}&\frac{-1}{\sqrt{2}}\\ \frac{1}{\sqrt{2}}&\frac{1}{\sqrt{2}}\end{bmatrix}$ is orthogonal
			* $\|X\|=1 \& \ \ \|Y\|=1$ , and $X\cdot Y=0$  ,which means X and Y are northonormal 
		* eg2. $\begin{bmatrix}  1/9 & -4/9 & 8/9\\  8/9 & 4/9 & 1/9   \\ \frac{\alpha}{9}  & -7/9 & \frac{\beta}{9}   \end{bmatrix}$ is orthogonal. Find $\alpha , \beta$ 
			* note: check using one and verify using other.X,Y
		* eg3. $\begin{bmatrix}  4 & 3 & 2\\  a & 5 & 6  \\ b& c&1\end{bmatrix}$ is symmetric. Find $a,b,c$
		* eg4.  $\begin{bmatrix}  a & 2 & -1\\  b & 0 & 3  \\ c& d&e\end{bmatrix}$ is skew symmetric. Find the variables. 
* Complex matrix: $A=\begin{bmatrix}2+3i&1-i\\3+2i&5\end{bmatrix}$
	* Conjugate matrix: $A=\begin{bmatrix}2-3i&1+i\\3-2i&5\end{bmatrix}$
	* Conjugate transpose: $A=\begin{bmatrix}2+3i&3-2i\\1+i&5\end{bmatrix}$
	* A complex square matrix $A=[a_{ij}]$ is 
		* Hermitian: $\overline{A}^{\ T}=A$ 
			* main diagonals are real
			* $a_{ij}=\overline{a_{ji}}$ 
			* eg. $\begin{bmatrix}2&1+i&2+3i\\1-i&-3&1-3i\\2-3i&1+3i&5\end{bmatrix}$
		* Skew hermitian:  $\overline{A}^{\ T}=-A$ 
			* main diagonals are pure imaginary or 0
			* $a_{ij}=-\overline{a_{ji}}$
			* eg. $\begin{bmatrix}i&1+i&2+3i\\-1+i&0&1-3i\\-2+3i&-1-3i&2i\end{bmatrix}$
		* Unitary: $\overline{A}^{\ T}=A^{-1}$ $\implies$ $A\cdot \overline{A}^{\ T}=I$ 
			* Determinant =1
			* note: there is no shortcut to verify
		* 
* Invertible or non-singular matrix
	* $A_{n\times n}$ is invertible if $AB=BA=I$ for some $B_{n\times n}$ 
	* We write $B=A^{-1}$.
	* Otherwise, A is non-invertible(or singular)
	* Results: 
		* $(A^{-1})^{-1}=A$ 
		* $(kA)^{-1}=\frac{1}{k}\cdot A^{-1}$   
		* $(I^{-1})=I$
		* $(AB)^{-1}=B^{-1}A^{-1}$
		* $(ABC)^{-1}=C^{-1}B^{-1}A^{-1}$
		* Note: $(A+B)^{-1}\neq A^{-1}+B^{-1}$ 
	* Examples: 
		* eg1. X and Y are singular matrices such that $XY=Y$ and $YX=X$. Then $X^2+Y^2=\_\_\_$ 
		* eg2. A,B,C,D are non-singular such that $DABEC=I$, $B^{-1}=\_\_\_$ 
		* #gatepyq eg3. $M^4=I(M\neq I,M^2\neq I,M^3\neq I$ $M^{-1}=?$
* Elementary row operations
	* $R_i\leftrightarrow R_j$
	* $R_i\leftrightarrow kR_i$
	* $R_i\leftrightarrow R_i+kR_j$ 
* Row-echlon form : A matrix is said to be in echlon form if: 
	* The zero rows(if any) occur at the bottom of the matrix
	* The leading non-zero entry in any row is to the right side of leading non-zero entry in the preceding row
	* Examples:
		* $\begin{bmatrix}1&2&-1&4\\0&1&0&3\\0&0&1&-2\end{bmatrix}$
		* $\begin{bmatrix}1&-5&2&-1&3\\0&0&1&3&-2\\0&0&0&1&4\\0&0&0&0&1\end{bmatrix}$
		* $\begin{bmatrix}0&0&0\\0&0&0\\0&0&0\end{bmatrix}$
* Reduced row echlon form: A matrix is said to be in reduced row echlon form if the above 2 from "row echlon form " are applicable, and: 
	* The leading non-zero entries(if any) must be 1
	* The leading 1 is the only non-zero entry in its coloumn
	* Examples: 
		* $\begin{bmatrix}0&1&0&5\\0&0&1&3\\0&0&0&0\end{bmatrix}$
		* $\begin{bmatrix}1&0&0&-1\\0&1&0&2\\0&0&1&3\\0&0&0&0\end{bmatrix}$
	* Note: Every matrix can be reduced to echlon form and reduced echlon form using finite number of elementary row operations. 
* Rank of matrix:: The number of non-zero rows in the echlon form of a matrix A is called rank of A. notation$\rightarrow \rho{(A)}$   
* Elimination method
	* Though the strict way of doing is gaussian elimination, this sort of step wise method is easier for pure logic implementation. 
	* steps: 
		* Apply forward elimination (echlon form)
		* Apply back elimination(which gives you reduced echlon form)
			* 1+2=gauss jordan elimination(if done strictly)
		* at each step:
			* transfer 0 rows to the bottom of matrix
			* Arrange remaining rows in such a way that. row having zeros before leading non-zero element is below a row having less zeros before leading non-zero element
	* Example: $\begin{bmatrix}1&1&1&4\\1&2&3&6\\2&3&8&14\end{bmatrix}\equiv\begin{bmatrix}1&1&1&4\\0&1&2&2\\0&0&4&4\end{bmatrix}\equiv\begin{bmatrix}1&0&0&3\\0&1&0&0\\0&0&1&1\end{bmatrix}$ where the 2nd matrix is in echlon form, and the 3rd and final matrix is in reduced echlon form
	* Questions: Find the rank of the following matrices: 
		* $\begin{bmatrix}1&1&1\\1&1&1\\1&1&1\end{bmatrix}\equiv\begin{bmatrix}1&1&1\\0&0&0\\0&0&0\end{bmatrix}$ Therefore, rank=1
		* $A=[a_{ij}]_{m\times n}$ where $a_{ij}=3$. $\rho{(A)}=1$.(same logic as previous example)
		* $\begin{bmatrix}a&a&a^2&\dots &a^n\\a &a&a^2&\dots&a^n\\\vdots&\ddots &\\a&a&a^2&\dots&a^n \end{bmatrix}$ 
			* Since all rows are identical, here also, rank is 1.
		* $\begin{bmatrix}1&2&3\\2&4&6\\3&6&9\end{bmatrix}$
			* Since all rows are proportional/dependent rows, rank is 1
		* $A=[a_{ij}]_{m\times n}\space where\space a_{ij}=i*j$ . 
			* $A=\begin{bmatrix}1&2&3&\dots&n\\2&2*2&2*3&\cdots&2*n\\\vdots&\\m&m*2&m*3&\dots&m*n\end{bmatrix}$. Here also, the rows are dependent, so rank is 1
		* 
			
				
 asdf

#### Determinants
- 2 X 2 matrix
	- If $A=\begin{bmatrix}a&b\\c&d\end{bmatrix}$
	- $A=\begin{vmatrix}a&b\\c&d\end{vmatrix}=ad-bc$
	- note: $\left|A\right|$ can be negetive 
- Some definitions for $A=[a_ij]_{m\times n}$
	- Minor of $a_{ij}=M_{ij}=$ Determinant of square submatrix obtained by deleting $i^{th}$ row and $j^{th}$ coloumn
	- Cofactor of $a_{ij}=C_{ij}=(-1)^{i+j}M_{ij}$
	- Cofactor matrix of $A=(C_{ij})_{n\times n}$
	- Adjoint of $A=Adj(A)=[Cofactor\space matrix]^T$ 
	- Inverse of a matrix = $\frac{Adj(A)}{\left|A\right|}$, ==when det is not zero==.
		- If determinant is zero, then inverse of matrix does not exist
	- Example: $A=\begin{bmatrix}1&2&3\\2&1&4\\1&5&1\end{bmatrix}$
		- $\left|A\right|=-19+4+27=12$
		- cofactor matrix of $A=\begin{bmatrix}-19&2&9\\-13&-2&-3\\5&2&-3\end{bmatrix}$
		- $Adj(A)=\begin{bmatrix}-19&-13&5\\2&-2&2\\9&-3&-3\end{bmatrix}$
- Laplace expansions: Given $A=[a_{ij}]_{m\times n}$
	- row expansion: $\left|A\right|=a_{i1}*C_{i1}+a_{i2}*C_{i2}+\dots+a_{in}*C_{in}$ $i=1,2,3,....,n$
	- coloumn expansion: $\left|A\right|=a_{1j}*C_{1j}+a_{2j}*C_{2j}+\dots+a_{nj}*C_{nj}$ where $j=1,2,...,n$
	- Examples: 
		- $\begin{vmatrix}2&3&1\\4&0&2\\1&0&3\end{vmatrix}=-3*(4*3-2*1)=-30$
		- $\begin{vmatrix}2&3&1&5\\0&4&0&0\\0&5&3&1\\0&6&0&5\end{vmatrix}=2(4(3*5))=120$

##### Properties of determinants
$\equiv$
1. $\left|A\right|=\left|A^T\right|$
2. Number of termsn in expansion of determinant of $A_{n\times n}=n!$ 
3. Conditions that result in determinant being 0: 
	1. let A be a square matrix. $\left|A\right|=0$ when A has
		1. zero row(or zero column)
		2. identical rows/coloumns
		3.  proportional rows/coloumns
	2. If sum of all elemenrs in rows(or coloumns) of A=0, then $\left|A\right|=0$
	3. A=skew-symmetric matrix of odd order then $A=-A^T\implies\left|A\right|=0$
4. A is an upper triangulr, lower triangular or diagonal matrix, then $\left|A\right|=a_{11}a_{22}\dots a_{nn}$ 
5. Suppose B is obtained from A by an elementary row(or coloumn) operation
	a. If 2 rows(or coloumns) of A were interchanged, then $\left|B\right|=-\left|A\right|$ 
	b. If a row(or coloumn)of A were multiplied by a scalar k, then $\left|B\right|=k\left|A\right|$
	c. If a multiple of row(or coloumn) of A were added to another row(or coloumn) of A, then $\left|B\right|=\left|A\right|$
6. $\left|kA\right|=k^n\left|A\right|$
7. $\left|I_n\right|=1$
8. $\begin{vmatrix}a_{11}&a_{12}&a_{13}\\ a_{21}&a_{22}&a_{23}\\a_{31}+k_{31}&a_{32}+k_{32}&a_{33}+k_{33}\end{vmatrix}=\begin{vmatrix}a_{11}&a_{12}&a_{13}\\ a_{21}&a_{22}&a_{23}\\a_{31}&a_{32}&a_{33}\end{vmatrix}+\begin{vmatrix}a_{11}&a_{12}&a_{13}\\ a_{21}&a_{22}&a_{23}\\k_{31}&k_{32}&k_{33}\end{vmatrix}$
9. $\left|AB\right|=\left|A\right|\left|B\right|$
10. if A is invertible, then $|A|^{-1}=\frac{1}{|A|}$
11. $\left|A+B\right|\neq|A|+|B|$ 

examples: 
	- eg. $\begin{vmatrix}10&-6&-4\\3&2&-5\\4&-8&4\end{vmatrix}$. Here, the sum of the first row adds up to 0. Therefore, Det=0
	- eg. $A=\begin{bmatrix}0&3&-5\\-3&0&2\\5&-2&0\end{bmatrix}$ is a skew hermitian matrix, therefore, $|A|=0$
	- eg. $A=\begin{bmatrix}0&-1\\1&0\end{bmatrix}$. $|A|=1$
	- eg. $A = [a_{ij}]_{3\times 3}$  where $a_{ij}=i^2-j^2\forall i,j$
		- is a skew symmetric matrix of odd order, therefore, |A|=0
	- eg. $\begin{bmatrix}4&3&2\\0&5&6\\0&0&3\end{bmatrix}$
		- this is an upper triangular matrix. therefore, |A|=4.5.3=60

###### Notes: 
1. $\begin{matrix}R_i&\leftrightarrow&R_j\\A&\sim&B\end{matrix}$         results in $|B|=-|A|$
2. $\begin{matrix}R_i&\leftrightarrow&kR_i\\A&\sim&B\end{matrix}$       results in $|B|=k|A|$
3. consider $A_{n\times n}$$\longrightarrow$$|kA|=k^2|A|$
4. $\begin{matrix}R_i&\leftrightarrow&R_i+k.R_j\\A&\sim&B\end{matrix}$     $|B|=|A|$ #important/fml


