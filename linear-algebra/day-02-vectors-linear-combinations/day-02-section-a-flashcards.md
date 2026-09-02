# Day 2 — Section A: 2-Minute Flashcards

**Course:** MIT 18.06SC Linear Algebra, Lecture 1  
**Use:** Read the prompt, answer aloud, then check the back. Target: ~2 minutes.  
**Deep reload:** [Section B — Detailed Notes](day-02-section-b-detailed-notes.md)

---

## Core cards

1. **What is a vector?**  
   A displacement: direction and magnitude. In coordinates, `[3, 2]` means “3 right, 2 up” from its tail.

2. **Point vs. vector?**  
   A point says *where*; a vector says *how far and in which direction*. A vector can be translated without changing it.

3. **What does scalar multiplication do?**  
   `cv` scales length by `|c|`; a negative scalar also reverses direction; `0v = 0`.

4. **What is vector addition?**  
   Add components (equivalently, head-to-tail displacements): `[a,b] + [c,d] = [a+c,b+d]`.

5. **What is a linear combination?**  
   `x₁v₁ + ··· + xₙvₙ`: scale each vector by its scalar coefficient, then add the component contributions.

6. **Column view of `Ax`?**  
   If columns of `A` are `a₁,…,aₙ`, then `Ax = x₁a₁ + ··· + xₙaₙ`: construct the target from columns.

7. **Row view of `Ax`?**  
   Each output entry is the corresponding row of `A` dotted with `x`: each row measures one weighted combination of `x`.

8. **Row picture vs. column picture for `Ax=b`?**  
   Row: where do the equation constraints intersect? Column: can the columns combine to make `b`? Same system, two views—not trial and error.

9. **What is the dot product?**  
   `u·v = Σuᵢvᵢ = ‖u‖‖v‖cosθ`: a scalar measuring magnitude-weighted alignment.

10. **Raw dot product vs. cosine similarity?**  
    Dot product includes both magnitudes and direction. `u·v/(‖u‖‖v‖) = cosθ` is pure directional alignment (for nonzero vectors).

11. **Why can `[3,0]·[5,0]` differ from `[3,0]·[6,0]` if both align perfectly?**  
    Alignment is 1 in both cases; the second vector has different magnitude. Dot product intentionally retains that magnitude.

12. **What does orthogonal mean?**  
    Perpendicular: `u·v = 0` (for nonzero vectors). Their magnitudes do not change the zero result.

13. **What is magnitude?**  
    `‖v‖ = √(v·v) = √(Σvᵢ²)`. It is the arrow’s length—not a “distance between vectors.”

14. **Why is `v·v = ‖v‖²`?**  
    A vector has angle `0°` with itself, so `v·v = ‖v‖‖v‖cos0 = ‖v‖²`.

15. **What is the span of vectors?**  
    All vectors reachable by their linear combinations. Two non-parallel vectors in 2D span the plane; parallel nonzero vectors span a line.

16. **Independent vs. dependent?**  
    Independent: only the all-zero coefficients give `0`. Dependent: some nonzero coefficient combination gives `0`; one vector is redundant/a combination of others.

17. **Dimension rule for multiplication?**  
    `(m×n)(n×p) = (m×p)`. A row vector times a column vector can be `1×1`, i.e. a scalar.

---

## Error-trigger cards

- **Trigger:** “The origin determines the vector.”  
  **Redirect:** The *tail’s position* is irrelevant; the tail-to-head displacement defines the vector. Drawing at the origin is a convention.

- **Trigger:** “`a` and `b` are vectors / the question forgot the vectors.”  
  **Redirect:** State the whole expression: given `u,v`, `au+bv` where `a,b ∈ ℝ` are scalar coefficients.

- **Trigger:** “Column picture means guess coefficients.”  
  **Redirect:** Coefficients are unknowns to solve for systematically; the picture asks whether `b` is in the columns’ span.

- **Trigger:** “Dot product is correlation.”  
  **Redirect:** Raw dot product = magnitude-weighted alignment. Use cosine similarity for magnitude-independent directional alignment.

- **Trigger:** “A matrix product never gives a scalar.”  
  **Redirect:** Use outer dimensions; `(1×n)(n×1) = 1×1`.

---

Next: use [Section B — Detailed Notes](day-02-section-b-detailed-notes.md) when a card feels fuzzy.
