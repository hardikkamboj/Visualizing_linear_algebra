# Vector Projection onto 2D Plane

An interactive 3D tool to visualize the projection of a vector onto a 2D plane in R³.

## Mathematical Background

### Projection onto a Subspace

Given a 2D plane (subspace) spanned by two linearly independent vectors **a₁** and **a₂**, we can project any vector **b** onto this plane.

**The Setup:**
- Let **A** = [a₁ | a₂] be the 3×2 matrix with columns a₁ and a₂
- The column space of **A** is our 2D plane
- We want to find **p**, the projection of **b** onto this plane

### The Projection Matrix

The projection matrix **P** projects any vector onto the column space of **A**:

```
P = A(AᵀA)⁻¹Aᵀ
```

The projection of **b** is:
```
p = Pb = A(AᵀA)⁻¹Aᵀb
```

### The Error Vector

The error (or residual) vector **e** is the component of **b** perpendicular to the plane:

```
e = b - p
```

**Key property:** The error vector **e** is orthogonal to the plane, meaning:
- e ⊥ a₁
- e ⊥ a₂
- e ⊥ p

This is the fundamental property that makes **p** the closest point to **b** on the plane.

### Properties of the Projection Matrix

The projection matrix **P** has special properties:

1. **Symmetric:** P = Pᵀ
2. **Idempotent:** P² = P (projecting twice gives the same result)
3. **Rank:** rank(P) = 2 (dimension of the plane)

### Geometric Interpretation

- **Yellow arrow (b):** The original vector we want to project
- **Green arrow (p):** The projection, which lies on the blue plane
- **Red arrow (e):** The error vector, perpendicular to the plane
- **Blue plane:** The 2D subspace spanned by a₁ and a₂

The projection **p** is the point on the plane closest to the tip of **b**.

## Features

- **Interactive 3D visualization** - Rotate, zoom, and pan to see the geometry
- **Custom input** - Enter any plane basis vectors and vector to project
- **Random generation** - Generate random planes and vectors
- **Projection matrix display** - See the actual 3×3 projection matrix
- **Error magnitude** - Shows how far **b** is from the plane

## Usage

1. Open `index.html` in a modern web browser
2. Enter the two basis vectors (a₁, a₂) that define your 2D plane
3. Enter the vector **b** you want to project
4. Click "Project Vector" to see the visualization
5. Use the random buttons to explore different configurations
6. Mouse controls:
   - **Left-drag**: Rotate
   - **Scroll**: Zoom
   - **Right-drag**: Pan

## Examples to Try

**XY Plane:**
```
a₁ = [1, 0, 0]
a₂ = [0, 1, 0]
b = [1, 2, 3]
→ Projection: [1, 2, 0], Error: [0, 0, 3]
```

**Tilted Plane:**
```
a₁ = [1, 0, 1]
a₂ = [0, 1, 0]
b = [1, 1, 1]
→ The projection will lie on the plane passing through origin with normal perpendicular to both a₁ and a₂
```

## Connection to Least Squares

This projection is exactly what happens in least squares regression:
- **A** contains the feature vectors
- **b** is the target vector
- **p = Ax̂** is the best approximation in the column space
- **e** is the residual error we minimize

The least squares solution x̂ = (AᵀA)⁻¹Aᵀb gives coefficients such that Ax̂ = p.
