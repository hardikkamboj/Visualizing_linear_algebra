# Column Space & Left Null Space Visualizer

An interactive 3D tool to visualize the column space and left null space of 3x3 matrices.

## Mathematical Background

### The Four Fundamental Subspaces

Every m×n matrix A has four fundamental subspaces. This visualization focuses on two of them for a 3×3 matrix:

**Column Space C(A)**
- The span of the column vectors of A
- Contains all possible outputs Ax for any input x
- For a 3×3 matrix, this is a subspace of R³
- Dimension equals the rank of A

**Left Null Space N(Aᵀ)**
- The set of all vectors y such that Aᵀy = 0 (equivalently, yᵀA = 0)
- Contains vectors orthogonal to every column of A
- For a 3×3 matrix, this is also a subspace of R³
- Dimension equals 3 - rank(A)

### Key Relationship

The column space and left null space are **orthogonal complements** in R³:

```
C(A) ⊥ N(Aᵀ)
dim(C(A)) + dim(N(Aᵀ)) = 3
```

This means:
- **Rank 1 matrix**: Column space is a line, left null space is a plane
- **Rank 2 matrix**: Column space is a plane, left null space is a line
- **Rank 3 matrix**: Column space is all of R³, left null space is just {0}

The visualization demonstrates this orthogonality - you can see how the red (left null space) and green (column space) subspaces are perpendicular to each other.

## Features

- **Interactive 3D visualization** - Rotate, zoom, and pan to explore the spaces
- **Custom matrix input** - Enter any 3x3 matrix values
- **Random matrix generation** - Generate random rank-1 or rank-2 matrices
- **Real-time computation** - Basis vectors and rank update instantly
- **Visual representation**:
  - Column space in green (vectors + plane/line)
  - Left null space in red (vectors + plane/line)

## Usage

1. Open `index.html` in a modern web browser
2. Enter values in the 3×3 matrix input fields, or use the random matrix buttons
3. Click "Visualize Spaces" to update
4. Mouse controls:
   - **Left-drag**: Rotate
   - **Scroll**: Zoom
   - **Right-drag**: Pan

## Examples to Try

**Rank 1 Matrix** (column space = line, left null space = plane):
```
1  2  3
2  4  6
1  2  3
```

**Rank 2 Matrix** (column space = plane, left null space = line):
```
1  0  1
0  1  1
0  0  0
```

## Implementation Notes

- Matrix rank computed via row echelon form with partial pivoting
- Left null space computed as the null space of Aᵀ
- Uses Three.js ArrowHelper for vectors and custom geometry for planes
