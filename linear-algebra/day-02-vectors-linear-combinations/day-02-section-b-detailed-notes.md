# Day 2 — Section B: Detailed Notes

**Course:** MIT 18.06SC Linear Algebra, Lecture 1  
**Reload time:** ~15 minutes  
**Quick recall:** [Section A — 2-Minute Flashcards](day-02-section-a-flashcards.md)

## 1. The map of the lesson

```text
vector → scale/add vectors → linear combination → Ax
                                             ├─ column view: build a vector
                                             └─ row view: dot-product measurements

dot product → magnitude + alignment → orthogonality
linear combinations → span → independence/dependence
```

The recurring question is: **What vectors can be constructed, and what do the coefficients mean?**

## 2. Vectors: displacement, not location

A vector is an object with **magnitude** and **direction**. In 2D,

`v = [3, 2]ᵀ`

means: from the vector’s tail, move 3 units right and 2 units up. A vector is not tied to a particular location. For example, tails at `(0,0)`, `(5,4)`, and `(-2,7)` with the same displacement `(3,2)` represent the same vector.

Drawing a vector from the coordinate origin is convenient, but it is a convention. A **point** `(3,2)` answers “where is it?” A **vector** `[3,2]ᵀ` answers “what displacement?” They can look identical when drawn from the origin but mean different things.

### Vector representation

A vector can be written as a column. A `3×1` column matrix is a standard representation of a 3D vector, but conceptually the vector is the mathematical object; the column is its notation/representation.

## 3. Scaling and addition

For scalar `c`, `cv` scales vector `v`:

- `c > 0`: same direction, `|c|` times the length.
- `c < 0`: reversed direction and `|c|` times the length.
- `c = 0`: the zero vector.

Vectors add component-by-component:

`[a,b]ᵀ + [c,d]ᵀ = [a+c, b+d]ᵀ`.

Geometrically, place the tail of the second arrow at the head of the first; the resultant goes from the first tail to the last head.

## 4. Linear combinations: adjustable directional contributions

`x₁v₁ + x₂v₂ + ··· + xₙvₙ`

is a **linear combination**. Each `xᵢ` is a real-number **scalar coefficient**, not a vector. Multiply each vector by its coefficient, then add the resulting component contributions.

Example:

`v₁=[1,2]ᵀ`, `v₂=[3,-1]ᵀ`; then

`2v₁ - v₂ = [2,4]ᵀ + [-3,1]ᵀ = [-1,5]ᵀ`.

Useful precise wording: “Given vectors `u,v`, which points/vectors can be reached by `au+bv` as scalar coefficients `a,b` range over ℝ?” This avoids ambiguity about what varies and what is multiplied.

## 5. Matrix–vector multiplication: the same operation, two pictures

Let `A` have columns `a₁,…,aₙ`, and let `x=[x₁,…,xₙ]ᵀ`. Then

`Ax = x₁a₁ + x₂a₂ + ··· + xₙaₙ`.

### Column view — construction

`Ax=b` asks: **Can the columns of `A` be combined to make target `b`? If so, what coefficients in `x` do it?** This is not a random search; solving for the coefficients is the same linear-system problem used in the row view. This picture prepares span, independence, transformations, and neural-network layers.

### Row view — measurements/constraints

If the rows of `A` are `r₁ᵀ,…,rₘᵀ`, then the entries of `Ax` are `rᵢᵀx`. Each row takes a dot product with `x`. For `Ax=b`, each row is one equation/constraint; in 2D, each equation can be visualized as a line, and the solution is their intersection.

Both statements are true at once:

`Ax =` columns of `A` combined using `x`  
`Ax =` rows of `A` each dotted with `x`

### Dimensions

Matrix multiplication is defined when inner dimensions match:

`(m×n)(n×p) = (m×p)`.

So a matrix product can be a matrix, column vector, row vector, or `1×1` scalar. A dot product is the familiar row-by-column special case and returns one scalar.

## 6. Dot product, length, and orthogonality

For equal-length vectors,

`u·v = Σᵢuᵢvᵢ = ‖u‖‖v‖cosθ`.

The dot product returns a scalar. It does not transform the input vectors; it measures their relationship. A useful mental model is:

**dot product = magnitude-weighted alignment.**

- Same direction: positive and largest for fixed lengths.
- Perpendicular: `cos 90° = 0`, hence dot product `0` regardless of length.
- Opposite direction: negative.

Magnitude is

`‖v‖ = √(v·v) = √(Σᵢvᵢ²)`.

Thus `v·v = ‖v‖²`: algebraically it is the sum of squared components; geometrically the angle of `v` with itself is zero.

### Alignment versus correlation-like intuition

For `r=[3,0]ᵀ`, `v₁=[5,0]ᵀ`, and `v₂=[6,0]ᵀ`, both pairs are perfectly directionally aligned:

`cosθ = 1` in both cases.

But `r·v₁=15` and `r·v₂=18`, because the raw dot product preserves the larger aligned magnitude. If only direction is wanted, use cosine similarity:

`(u·v)/(‖u‖‖v‖) = cosθ` for nonzero vectors.

Do not equate raw dot product with statistical correlation. Cosine similarity is closer to the “ignore overall magnitude” intuition, but it is still not the same thing as statistical correlation.

## 7. Span, dependence, and independence

The **span** of vectors is the set of every linear combination they can produce.

- A single nonzero vector in 2D spans a line through the origin.
- Two non-parallel vectors in 2D span the whole plane.
- Two parallel vectors still span only a line.

Vectors `v₁,…,vₙ` are **linearly independent** when

`x₁v₁ + ··· + xₙvₙ = 0`

has only the trivial solution `x₁=···=xₙ=0`.

They are **dependent** when some nontrivial (not all zero) coefficient combination gives zero. Cancellation is possible; this is why “zero result means every coefficient is zero” is not generally valid.

Independence means no vector is redundant: none can be built from the others.

## 8. Error log: paths to recognize and redirect

| Type | Old path / statement | Correction and future trigger |
|---|---|---|
| **Conceptual error** | “If a combination gives zero, all coefficients must be zero.” | Vectors can cancel. Ask: “Is this the *only* coefficient choice?” Only then conclude independence. |
| **Conceptual error** | “Dot product is only multiply-and-add / changes vectors.” | It is a scalar measurement of magnitude-weighted alignment; the input vectors remain as they are. |
| **Incomplete mental model** | “The column picture is trial and error.” | It asks for coefficients that construct `b`; solve them systematically. Row and column pictures are complementary, not competing methods. |
| **Incomplete mental model** | “The origin matters to the vector.” | The vector is tail-to-head displacement; moving the whole arrow does not change it. |
| **Recall / notation failure** | `v·v` is the length. | `v·v=‖v‖²`; the length is `‖v‖=√(v·v)`. |
| **Recall / notation failure** | “Matrix multiplication always yields a matrix or vector.” | Check dimensions: `(m×n)(n×p)=(m×p)`; a `1×1` result is scalar. |
| **Correct understanding** | “Scale each vector by `x₁,x₂,…`, then add/subtract directional units.” | Correct. Refine the wording: add the scaled vectors component-by-component to get the resultant. |
| **Correct understanding** | “Magnitude should not matter when vectors are perfectly correlated/aligned.” | Correct for *pure directional alignment*. Raw dot product also retains magnitude; cosine similarity normalizes it away. |
| **Correct understanding** | “Orthogonal vectors stay at dot product zero even if magnitude changes.” | Correct, because the cosine factor is zero. |

## 9. Sources and breadcrumbs

- [MIT OpenCourseWare — 18.06SC Linear Algebra, Lecture 1: The Geometry of Linear Equations](https://ocw.mit.edu/courses/18-06sc-linear-algebra-fall-2011/pages/unit-i-the-geometry-of-linear-equations/lecture-1-the-geometry-of-linear-equations/)
- Gilbert Strang, *Introduction to Linear Algebra*: Sections **1.1**, **1.2**, and **2.1** (use the edition assigned with the course; section titles vary slightly by edition).
- [3Blue1Brown — Vectors, what even are they?](https://www.youtube.com/watch?v=fNk_zzaMoSs)

Return to the [Section A flashcards](day-02-section-a-flashcards.md) after this reload.
