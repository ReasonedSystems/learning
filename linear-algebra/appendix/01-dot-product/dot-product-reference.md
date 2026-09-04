# Appendix — The Dot Product Operation Reference

> A durable reference for the ideas developed in the Day 2 discussion. The goal is not to remember a recipe; it is to be able to reconstruct the meaning, the formula, and the appropriate operation from first principles.

---

# Section 1 — Vectors

## 1.1 Vector Core Mental Model

A vector represents a **displacement**:

> **HOW FAR + WHICH DIRECTION**

For example:

$$v=[3,2]$$

means:

> move 3 units in the x-direction and 2 units in the y-direction.

If the vector starts at the origin, its head lands at the point $(3,2)$.

But the vector itself does **not** have to start at the origin.

The same displacement could start at $(5,4)$ and end at $(8,6)$, or start at $(-2,7)$ and end at $(1,9)$.

The tail can be translated freely without changing the vector.

So:

> **A vector is not a location. It is a displacement.**

### Point vs Vector

| Object | Mental question | Example | Meaning |
|---|---|---|---|
| Point | **WHERE?** | $(3,2)$ | A location |
| Vector | **HOW FAR + WHICH DIRECTION?** | $[3,2]$ | A displacement |

A point and a vector may contain the same numbers, but they represent different ideas.

---

## 1.2 Vector Coordinates / Components

A vector is represented by components relative to the chosen coordinate axes.

For:

$$v=[3,2]$$

the components are:

$$v_x=3$$

and:

$$v_y=2$$

So the numbers inside a vector representation tell us how much displacement occurs along each coordinate direction.

When we later write something like:

$$[2,1]\cdot[5,2]$$

the two objects are **vectors represented by components**, not points.

The arithmetic:

$$2(5)+1(2)$$

uses those coordinate components.

### Important terminology distinction

We will use the word **component** in two different ways:

1. **Vector coordinate components** such as $a_1,a_2,\ldots$
2. **Scalar component along a direction**, such as $\mathrm{comp}_a(b)$

These are related ideas, but they are not the same object.

---

## 1.3 Row and Column Representation

The same abstract vector may be written as a row:

$$\begin{bmatrix} 3 & 2 \end{bmatrix}$$

or as a column:

$$\begin{bmatrix} 3\\ 2 \end{bmatrix}$$

In many linear-algebra calculations, column notation is conventional because it fits naturally into expressions such as:

$$Ax$$

The row/column orientation is usually a matter of representation required by the algebra.

It does not create a different geometric vector.

---

## 1.4 Magnitude / Norm / Length

The magnitude of a vector is its geometric length.

For:

$$v=[v_1,v_2]$$

the magnitude is:

| $$\|v\| = \sqrt{v_1^2+v_2^2}$$ |
| :--- |

For:

$$v=[3,2]$$

we have:

$$\|v\| = \sqrt{3^2+2^2} = \sqrt{13}$$

In $n$ dimensions:

$$\boxed{ \|v\| = \sqrt{ v_1^2+v_2^2+\cdots+v_n^2 } }$$

This is the generalized Pythagorean length.

---

## 1.5 Vector Addition

Let:

$$a=[3,3]$$

and:

$$b=[5,1]$$

Then:

$$a+b = [3+5,\;3+1]$$

so:

$$\boxed{ a+b=[8,4] }$$

Vector addition produces another **vector**.

Geometrically, it combines displacements.

The usual geometric interpretations are:

- tip-to-tail addition
- parallelogram addition

The important contrast for later is:

> **Vector addition produces a vector.**

The dot product will produce a scalar.

---

## 1.6 Vector Decomposition

A vector can be decomposed relative to another direction.

Suppose we use vector $a$ as the reference direction.

Then vector $b$ can be split into:

$$\boxed{ b=b_{\parallel}+b_{\perp} }$$

where:

- $b_{\parallel}$ is parallel to $a$
- $b_{\perp}$ is perpendicular to $a$

The parallel part is the vector projection of $b$ onto the direction of $a$:

$$b_{\parallel} = \mathrm{proj}_a(b)$$

and:

$$b_{\perp} = b-\mathrm{proj}_a(b)$$

This decomposition becomes extremely useful for understanding the dot product:

> **Only the part of $b$ lying along the direction of $a$ contributes to $a\cdot b$.**

The perpendicular part contributes zero.

We will derive the exact component and projection formulas later.

---

## Section 1 Mental-Model Card

> **Point → WHERE**

> **Vector → HOW FAR + WHICH DIRECTION**

> **Magnitude → HOW LONG**

> **Addition → COMBINE vectors**

> **Decomposition → SPLIT a vector into parallel + perpendicular parts**

---

# Section 2 — Dot Product

## 2.1 What Is a Dot Product?

The dot product takes two vectors of the same dimension and produces one scalar.

For example:

$$a=[3,3]$$

$$b=[5,1]$$

Then:

$$a\cdot b = 3(5)+3(1) = 18$$

So:

$$\boxed{ a\cdot b=18 }$$

The output is not:

- a vector
- a point
- a displacement
- a resultant arrow

It is a **scalar**.

Conceptually, the scalar captures a signed relationship between the two vectors.

---

## 2.2 Core Mental Model

The geometric formula is:

$$\boxed{ a\cdot b = \|a\|\|b\|\cos\theta }$$

where $\theta$ is the angle between the vectors.

The most useful mental model is:

$$\boxed{ \text{Dot Product} = \text{MAGNITUDE} \times \text{MAGNITUDE} \times \text{ALIGNMENT} }$$

The two magnitude terms tell us how long the vectors are.

The $\cos\theta$ term tells us how aligned their directions are.

So the raw dot product is **not alignment alone**.

It contains both:

- magnitude information
- directional alignment information

---

## 2.3 Alignment Scale

Because the directional part is $\cos\theta$, the sign and size of the dot product depend on the angle.

| Angle $\theta$ | $\cos\theta$ | Directional interpretation |
|---:|---:|---|
| $0^\circ$ | $1$ | perfectly aligned |
| $30^\circ$ | $\approx0.866$ | strongly aligned |
| $60^\circ$ | $0.5$ | partly aligned |
| $90^\circ$ | $0$ | perpendicular |
| $120^\circ$ | $-0.5$ | partly opposing |
| $180^\circ$ | $-1$ | exactly opposite |

Therefore, for nonzero vectors:

$$a\cdot b>0$$

means the angle is acute.

$$a\cdot b=0$$

means the vectors are perpendicular.

$$a\cdot b<0$$

means the angle is obtuse.

---

## 2.4 Scalar-Component View

There is another extremely useful interpretation.

Choose $a$ as the reference direction.

Let:

$$\mathrm{comp}_a(b)$$

mean:

> the signed scalar amount of $b$ that lies along the direction of $a$.

Then:

$$\boxed{ a\cdot b = \|a\| \mathrm{comp}_a(b) }$$

This gives another mental model:

> **Dot product = magnitude of the reference vector × HOW MUCH of the other vector lies along it.**

If $b$ is decomposed as:

$$b=b_{\parallel}+b_{\perp}$$

then the perpendicular component contributes nothing:

$$a\cdot b_{\perp}=0$$

Therefore:

$$\boxed{ a\cdot b = a\cdot b_{\parallel} }$$

Only the parallel amount contributes.

---

## 2.5 Symmetry

The dot product is symmetric:

$$\boxed{ a\cdot b=b\cdot a }$$

So both of these interpretations are valid:

$$a\cdot b = \|a\| \mathrm{comp}_a(b)$$

and:

$$a\cdot b = \|b\| \mathrm{comp}_b(a)$$

The two scalar components are generally different.

But after multiplying by the corresponding reference-vector magnitude, the same dot product is obtained.

---

## 2.6 What a Dot Product Does NOT Do

A dot product does **not**:

- add the vectors
- produce a resultant vector
- produce the projection vector itself
- represent pure directional similarity independent of magnitude

That last point matters.

If we want to remove vector magnitudes and preserve only directional alignment, we will later use **cosine similarity**.

---

## 2.7 Essential Algebraic Properties

### Symmetry

$$\boxed{ a\cdot b=b\cdot a }$$

### Distributivity

$$\boxed{ a\cdot(b+c) = a\cdot b+a\cdot c }$$

### Scalar multiplication

$$\boxed{ (\lambda a)\cdot b = \lambda(a\cdot b) }$$

### Self-dot

$$\boxed{ a\cdot a = \|a\|^2 }$$

Therefore:

$$\boxed{ \|a\| = \sqrt{a\cdot a} }$$

---

## Section 2 Mental-Model Card

$$\boxed{ \text{Dot product} = \text{magnitude} \times \text{magnitude} \times \text{alignment} }$$

and equivalently:

$$\boxed{ a\cdot b = \|a\| \times \text{HOW MUCH of }b\text{ lies along }a }$$

> **Dot product → scalar**

> **Projection helps us understand the geometry, but projection is not required to calculate the dot product.**

---

# Section 3 — Dot Product Calculation: Three Equivalent Views

The dot product has three especially useful views:

1. Vector-components view
2. Geometric / alignment view
3. Scalar-component view

These are not competing definitions.

They are three ways of seeing the same scalar quantity.

---

## 3.1 Vector-Components View

Let:

$$a=[a_1,a_2,\ldots,a_n]$$

and:

$$b=[b_1,b_2,\ldots,b_n]$$

Then:

$$a\cdot b = \sum_{i=1}^{n}a_ib_i $$

In two dimensions:

$$a\cdot b = a_1b_1+a_2b_2$$

For example:

$$[2,1]\cdot[5,2] = 2(5)+1(2) = 12$$

The computational rule is simply:

> **Multiply matching components → add.**

This is the easiest and most direct way to **compute** a dot product, especially in high-dimensional spaces.

Remember that these are the vector's coordinate components.

They are different from the scalar directional component $\mathrm{comp}_a(b)$ introduced later.

---

## 3.2 Geometric / Alignment View

The geometric formula is:

$$\boxed{ a\cdot b = \|a\|\|b\|\cos\theta }$$

This tells us **why** the coordinate formula has geometric meaning.

---

### 3.2.1 Deriving the Geometric Formula

Consider vectors $a$ and $b$ drawn from the same tail.

The third side of the triangle joining their heads is:

$$a-b$$

From coordinate algebra:

$$\|a-b\|^2 = (a-b)\cdot(a-b)$$

Expanding:

$$\|a-b\|^2 = a\cdot a -2a\cdot b +b\cdot b$$

Since:

$$a\cdot a=\|a\|^2$$

and:

$$b\cdot b=\|b\|^2$$

we get:

$$\|a-b\|^2 = \|a\|^2+\|b\|^2-2a\cdot b$$

Now use the law of cosines on the same triangle:

$$\|a-b\|^2 = \|a\|^2+\|b\|^2 - 2\|a\|\|b\|\cos\theta$$

Comparing the two expressions:

$$-2a\cdot b = -2\|a\|\|b\|\cos\theta$$

Therefore:

$$\boxed{ a\cdot b = \|a\|\|b\|\cos\theta }$$

So the coordinate rule and geometric rule are exactly equivalent.

---

### 3.2.2 Magnitude × Magnitude × Alignment

This formula produces the central mental model:

$$\boxed{ \text{Dot Product} = \text{MAGNITUDE} \times \text{MAGNITUDE} \times \text{ALIGNMENT} }$$

The $\cos\theta$ factor behaves like this:

| $\theta$ | $\cos\theta$ | Interpretation |
|---:|---:|---|
| $0^\circ$ | $1$ | fully aligned |
| $30^\circ$ | $\approx0.866$ | strongly aligned |
| $60^\circ$ | $0.5$ | partially aligned |
| $90^\circ$ | $0$ | perpendicular |
| $120^\circ$ | $-0.5$ | partly opposing |
| $180^\circ$ | $-1$ | opposite |

The raw dot product is therefore not a pure measure of direction.

Magnitude still matters.

---

## 3.3 Scalar-Component View

Now choose $a$ as the reference direction.

This view begins from geometry rather than from the dot-product formula.

---

### 3.3.1 HOW MUCH of $b$ Lies Along $a$?

The signed scalar amount of $b$ lying along the direction of $a$ is:

$$\boxed{ \mathrm{comp}_a(b) = \|b\|\cos\theta }$$

This is a **scalar**.

Its mental question is:

> **HOW MUCH of $b$ lies along the direction of $a$?**

The sign carries directional information:

- acute angle → positive component
- $90^\circ$ → zero component
- obtuse angle → negative component

Now return to the geometric dot-product formula:

$$a\cdot b = \|a\|\|b\|\cos\theta$$

Since:

$$\mathrm{comp}_a(b) = \|b\|\cos\theta$$

we obtain:

$$\boxed{ a\cdot b = \|a\| \mathrm{comp}_a(b) }$$

Therefore:

$$\boxed{ \mathrm{comp}_a(b) = \frac{a\cdot b}{\|a\|} }$$

This is the scalar-component interpretation of the dot product.

---

### 3.3.2 Projection — Adding WHICH DIRECTION

The scalar component tells us:

> **HOW MUCH**

But sometimes we need the actual vector lying along the reference direction.

For that we need:

> **HOW MUCH × WHICH DIRECTION**

The unit vector in the direction of $a$ is:

$$\boxed{ \hat a = \frac{a}{\|a\|} }$$

It tells us:

> **WHICH DIRECTION**

Now multiply the scalar component by this unit direction:

$$\boxed{ \mathrm{proj}_a(b) = \mathrm{comp}_a(b)\hat a }$$

So:

> **Projection = HOW MUCH × WHICH DIRECTION**

Substitute the component formula:

$$\mathrm{proj}_a(b) = \frac{a\cdot b}{\|a\|} \frac{a}{\|a\|}$$

Therefore:

$$\boxed{ \mathrm{proj}_a(b) = \frac{a\cdot b}{\|a\|^2}a }$$

Since:

$$\|a\|^2=a\cdot a$$

we can also write:

$$\boxed{ \mathrm{proj}_a(b) = \frac{a\cdot b}{a\cdot a}a }$$

Projection is not required to calculate the dot product.

Its purpose is different:

> It gives the **actual parallel vector**.

Then:

$$\boxed{ b = \mathrm{proj}_a(b) + b_{\perp} }$$

---

### 3.3.3 Component ↔ Dot Product ↔ Projection

The scalar component sits at the center of the geometry.

From:

$$\mathrm{comp}_a(b)$$

we can branch in two different directions.

Multiply by the magnitude of $a$:

$$\boxed{ \mathrm{comp}_a(b)\|a\| = a\cdot b }$$

to obtain the dot product.

Or multiply by the unit direction of $a$:

$$\boxed{ \mathrm{comp}_a(b)\hat a = \mathrm{proj}_a(b) }$$

to obtain the projection vector.

So the conceptual structure is:

> **Geometry gives Component. Component then branches into Dot Product or Projection.**

| Object | Type | Formula | Mental model |
|---|---|---|---|
| Scalar component | Scalar | $\mathrm{comp}_a(b)=\|b\|\cos\theta$ | **HOW MUCH** |
| Unit vector | Vector | $\hat a=a/\|a\|$ | **WHICH DIRECTION** |
| Projection | Vector | $\mathrm{proj}_a(b)=\mathrm{comp}_a(b)\hat a$ | **HOW MUCH × WHICH DIRECTION** |
| Dot product | Scalar | $a\cdot b=\|a\|\mathrm{comp}_a(b)$ | reference magnitude × **HOW MUCH** |

---

## 3.4 Connecting the Three Dot-Product Views

The three actual dot-product views are:

$$\boxed{ \sum_i a_ib_i = \|a\|\|b\|\cos\theta = \|a\|\mathrm{comp}_a(b) }$$

| View | Formula | Best mental use |
|---|---|---|
| Vector components | $\sum_i a_ib_i$ | easiest way to **COMPUTE** |
| Geometry / alignment | $\|a\|\|b\|\cos\theta$ | explains magnitude + alignment |
| Scalar component | $\|a\|\mathrm{comp}_a(b)$ | shows **WHAT CONTRIBUTES** |

The most durable switching rule is:

> **Use vector components to CALCULATE the dot product.**

> **Use geometry and scalar components to UNDERSTAND the dot product.**

Projection is related to the component view, but it is not a fourth independent way of calculating the dot product.

---

# Section 4 — Worked Example: One Dot Product, Three Views

Let:

$$a=[3,3]$$

and:

$$b=[5,1]$$

We will calculate the same dot product using:

1. vector components
2. geometry / alignment
3. scalar component

Then we will use projection and decomposition to verify what the component view means geometrically.

The point is not to perform all of these calculations every time.

The point is to see that all views describe the same scalar.

---

## 4.1 View 1 — Vector Components

Using:

$$a\cdot b = a_1b_1+a_2b_2$$

we get:

$$a\cdot b = 3(5)+3(1)$$

$$= 15+3$$

Therefore:

$$\boxed{ a\cdot b=18 }$$

This is the easiest computational route:

> **Multiply matching components → add.**

---

## 4.2 View 2 — Geometry / Alignment

First calculate the magnitudes.

For $a$:

$$\|a\| = \sqrt{3^2+3^2} = \sqrt{18}$$

so:

$$\|a\| \approx4.243$$

For $b$:

$$\|b\| = \sqrt{5^2+1^2} = \sqrt{26}$$

so:

$$\|b\| \approx5.099$$

The direction of $a$ relative to the x-axis is:

$$45^\circ$$

The direction of $b$ relative to the x-axis is:

$$\tan^{-1}\left(\frac{1}{5}\right) \approx11.31^\circ$$

Therefore the angle between them is:

$$\theta \approx45^\circ-11.31^\circ$$

$$\boxed{ \theta\approx33.69^\circ }$$

Now use:

$$a\cdot b = \|a\|\|b\|\cos\theta$$

Substituting:

$$a\cdot b = \sqrt{18}\sqrt{26}\cos33.69^\circ$$

which gives:

$$\boxed{ a\cdot b\approx18 }$$

So the same result can be interpreted as:

$$\boxed{ 18 = \text{magnitude of }a \times \text{magnitude of }b \times \text{alignment} }$$

---

## 4.3 View 3 — Scalar Component

The signed scalar amount of $b$ along the direction of $a$ is:

$$\mathrm{comp}_a(b) = \|b\|\cos\theta$$

Therefore:

$$\mathrm{comp}_a(b) = \sqrt{26}\cos33.69^\circ$$

which evaluates to:

$$\boxed{ \mathrm{comp}_a(b) = \sqrt{18} }$$

Now use:

$$a\cdot b = \|a\|\mathrm{comp}_a(b)$$

Therefore:

$$a\cdot b = \sqrt{18}\times\sqrt{18}$$

so:

$$\boxed{ a\cdot b=18 }$$

Interpretation:

> The dot product is the magnitude of $a$ multiplied by **HOW MUCH of $b$ lies along $a$**.

---

### 4.3.1 Projection of $b$ onto $a$

The unit vector in the direction of $a$ is:

$$\hat a = \frac{a}{\|a\|} = \frac{[3,3]}{\sqrt{18}}$$

Projection is:

$$\mathrm{proj}_a(b) = \mathrm{comp}_a(b)\hat a$$

Substituting:

$$\mathrm{proj}_a(b) = \sqrt{18} \frac{[3,3]}{\sqrt{18}}$$

Therefore:

$$\boxed{ \mathrm{proj}_a(b) = [3,3] = a }$$

This is a convenient geometric coincidence in this example:

> the part of $b$ lying along $a$ is exactly the vector $a$ itself.

We can also see this using the projection coefficient:

$$\frac{a\cdot b}{a\cdot a} = \frac{18}{18} = 1$$

So:

$$\mathrm{proj}_a(b) = 1a = a$$

The coefficient $1$ means:

> one signed copy of $a$ forms the parallel component of $b$.

---

### 4.3.2 Decomposing $b$

We now have:

$$b_{\parallel} = \mathrm{proj}_a(b) = [3,3]$$

Therefore:

$$b_{\perp} = b-b_{\parallel}$$

$$= [5,1]-[3,3]$$

so:

$$\boxed{ b_{\perp} = [2,-2] }$$

Thus:

$$\boxed{ b = [3,3]+[2,-2] }$$

or:

$$\boxed{ b = b_{\parallel}+b_{\perp} }$$

---

### 4.3.3 Verify the Perpendicular Part Contributes Zero

Check:

$$a\cdot b_{\perp} = [3,3]\cdot[2,-2]$$

$$= 3(2)+3(-2)$$

$$= 6-6$$

Therefore:

$$\boxed{ a\cdot b_{\perp}=0 }$$

By distributivity:

$$a\cdot b = a\cdot(b_{\parallel}+b_{\perp})$$

$$= a\cdot b_{\parallel} + a\cdot b_{\perp}$$

Since the perpendicular term is zero:

$$\boxed{ a\cdot b = a\cdot b_{\parallel} }$$

This verifies the key geometric idea:

> **Only the parallel part contributes to the dot product.**

---

## 4.4 All Three Views Side by Side

| View | Calculation | Result |
|---|---|---:|
| Vector components | $3(5)+3(1)$ | $18$ |
| Geometry / alignment | $\sqrt{18}\sqrt{26}\cos33.69^\circ$ | $18$ |
| Scalar component | $\sqrt{18}\times\sqrt{18}$ | $18$ |

So:

$$\boxed{ 3(5)+3(1) = \sqrt{18}\sqrt{26}\cos33.69^\circ = \sqrt{18}\mathrm{comp}_a(b) = 18 }$$

and:

$$\mathrm{comp}_a(b) = \sqrt{18}$$

$$\mathrm{proj}_a(b) = [3,3]$$

$$b_{\perp} = [2,-2]$$

### Worked-example mental model

> **Vector components → How do I compute it?**

> **Geometry → What do magnitude and alignment mean?**

> **Scalar component → What part actually contributes?**

> **Projection → What is the actual vector part along the reference direction?**

Projection is subordinate to the scalar-component view, not a fourth independent dot-product calculation.

---

# Section 5 — Cosine Similarity: Removing Magnitude

We established:

$$\boxed{ a\cdot b = \|a\|\|b\|\cos\theta }$$

Therefore a raw dot product contains two kinds of information:

$$\boxed{ \text{Dot Product} = \text{MAGNITUDE} \times \text{MAGNITUDE} \times \text{ALIGNMENT} }$$

Sometimes this is exactly what we want.

But sometimes our question is different:

> **How similar are the directions of these vectors, irrespective of their magnitudes?**

If magnitude should **not** influence the comparison, we need to remove it.

---

## 5.1 Removing the Magnitudes

Start with:

$$a\cdot b = \|a\|\|b\|\cos\theta$$

Divide both sides by the two vector magnitudes:

$$\frac{a\cdot b} {\|a\|\|b\|} = \cos\theta$$

Therefore:

$$\boxed{ \mathrm{cosine\ similarity}(a,b) = \frac{a\cdot b} {\|a\|\|b\|} }$$

### Zero-Vector Caveat

Cosine similarity requires **both vectors to have nonzero magnitude**.

If either vector is the zero vector, then:

$$\|a\|\|b\|=0$$

and the cosine-similarity formula would require division by zero. Therefore:

> **Cosine similarity is mathematically undefined if either vector is the zero vector.**

Conceptually:

$$\boxed{ \text{Cosine Similarity} = \frac{ \text{MAGNITUDE}\times\text{MAGNITUDE}\times\text{ALIGNMENT} }{ \text{MAGNITUDE}\times\text{MAGNITUDE} } }$$

leaving:

$$\boxed{ \text{Cosine Similarity} = \text{ALIGNMENT} }$$

So the simplest distinction is:

> **Dot product = magnitude-weighted alignment.**

> **Cosine similarity = alignment with the original magnitudes removed.**

---

## 5.2 Unit-Normalizing the Vectors

There is another way to arrive at exactly the same result.

Normalize each vector to length $1$:

$$\hat a = \frac{a}{\|a\|}$$

$$\hat b = \frac{b}{\|b\|}$$

These unit vectors preserve the original directions, but remove the original magnitudes:

$$\|\hat a\| = \|\hat b\| = 1$$

Now take their dot product:

$$\hat a\cdot\hat b = \|\hat a\|\|\hat b\|\cos\theta$$

Since both magnitudes are $1$:

$$\hat a\cdot\hat b = (1)(1)\cos\theta$$

Therefore:

$$\boxed{ \hat a\cdot\hat b = \cos\theta }$$

Hence:

$$\boxed{ \text{Dot product of unit-normalized vectors} = \text{Cosine similarity} }$$

This gives two equivalent procedures.

### Method 1 — Dot first, remove magnitudes afterward

$$\boxed{ \cos\theta = \frac{a\cdot b}{\|a\|\|b\|} }$$

### Method 2 — Remove magnitudes first, then dot

$$\boxed{ \cos\theta = \left(\frac{a}{\|a\|}\right) \cdot \left(\frac{b}{\|b\|}\right) }$$

Same mathematics. Same result.

> **Cosine similarity = normalize first → dot product**

or:

> **Cosine similarity = dot product first → divide out both magnitudes**

---

## 5.3 What Unit Normalization Changes

Suppose:

$$a=[3,3]$$

Its magnitude is:

$$\|a\| = \sqrt{18}$$

Normalize it:

$$\hat a = \frac{[3,3]}{\sqrt{18}}$$

The resulting vector has:

$$\|\hat a\| = 1$$

What changed?

- **Magnitude:** changed to $1$
- **Direction:** unchanged

So normalization should be visualized as:

> **Shrink or stretch the vector along the same direction until its length becomes 1.**

It does **not** rotate the vector.

### Terminology

Here we are performing **unit-vector normalization** or **L2 normalization**.

This should not be confused with statistical **standardization**, such as transforming data using a mean and standard deviation.

---

## 5.4 Interpreting Cosine Similarity

For nonzero real vectors:

$$-1 \le \cos\theta \le 1$$

| Cosine similarity | Angle | Interpretation |
|---:|---:|---|
| $1$ | $0^\circ$ | same direction |
| $0.866$ | $30^\circ$ | strongly aligned |
| $0.5$ | $60^\circ$ | partly aligned |
| $0$ | $90^\circ$ | perpendicular |
| $-0.5$ | $120^\circ$ | partly opposing |
| $-1$ | $180^\circ$ | opposite direction |

Notice what has disappeared:

> **vector magnitude**

A vector of length $2$ and another of length $200$ can have cosine similarity $1$ if they point in exactly the same direction.

---

## 5.5 Example — Same Direction, Different Magnitudes

Consider:

$$a=[3,0]$$

$$b=[5,0]$$

$$c=[10,0]$$

All three point in exactly the same direction.

But their raw dot products are:

$$a\cdot b = 3(5) = 15$$

while:

$$a\cdot c = 3(10) = 30$$

Therefore:

$$\boxed{ a\cdot b \ne a\cdot c }$$

even though both pairs are perfectly aligned.

Why?

Because raw dot product retains magnitude.

Now calculate cosine similarity:

$$\cos(a,b) = \frac{15}{(3)(5)} = 1$$

and:

$$\cos(a,c) = \frac{30}{(3)(10)} = 1$$

Therefore:

$$\boxed{ \cos(a,b) = \cos(a,c) = 1 }$$

Cosine similarity answers the narrower question:

> **How aligned are these vectors, ignoring their original lengths?**

---

## 5.6 Dot Product vs Cosine Similarity

| | Dot Product | Cosine Similarity |
|---|---|---|
| Formula | $a\cdot b$ | $\frac{a\cdot b}{\|a\|\|b\|}$ |
| Magnitude retained? | **Yes** | **No** |
| Alignment retained? | **Yes** | **Yes** |
| Range | Unbounded | $[-1,1]$ for nonzero real vectors |
| Core meaning | Magnitude-weighted alignment | Directional alignment |

Neither operation is inherently better.

They answer different questions.

The decision trigger is:

$$\boxed{ \textbf{Do we want magnitude to matter here, or do we want to remove it?} }$$

If magnitude carries useful information:

> **Dot product may be appropriate.**

If we want directional similarity independent of magnitude:

> **Cosine similarity may be appropriate.**

---

## 5.7 Important ML / Embedding Distinction

Later, when we work with embeddings, it may be tempting to say:

> “Cosine similarity understands whether two sentences mean the same thing.”

More precisely:

> **The embedding model creates the semantic representation. Cosine similarity only compares the resulting vectors geometrically.**

Cosine similarity itself does not understand language or semantics.

If semantically related inputs end up pointing in similar directions, that useful structure came from how the **embedding model learned to represent them**.

Cosine similarity simply measures the directional relationship between those representations.

---

## Section 5 Mental-Model Card

$$\boxed{ \text{Dot Product} = \text{MAGNITUDE} \times \text{MAGNITUDE} \times \text{ALIGNMENT} }$$

Remove the magnitudes:

$$\boxed{ \text{Cosine Similarity} = \text{ALIGNMENT} }$$

Equivalently:

$$\boxed{ \text{Cosine Similarity} = \text{Dot Product of Unit-Normalized Vectors} }$$

Decision question:

> **Do we want magnitude to matter here, or do we want to remove it?**

---

# Section 6 — Why Equal Dot Products Need Not Mean Equal Alignment

A subtle but important consequence of:

$$a\cdot b = \|a\|\|b\|\cos\theta$$

is that **different combinations of magnitude and alignment can produce exactly the same dot product**.

---

## 6.1 Construct Two Different Cases

Let vector $a$ have magnitude:

$$\|a\| = L$$

Now consider two different vectors.

### Case 1 — Perfect Alignment

Let $b_1$ also have magnitude $L$ and point in exactly the same direction as $a$:

$$\|b_1\| = L$$

$$\theta_1 = 0^\circ$$

Then:

$$a\cdot b_1 = L\cdot L\cdot\cos0^\circ$$

Since:

$$\cos0^\circ = 1$$

we get:

$$\boxed{ a\cdot b_1 = L^2 }$$

### Case 2 — Larger Magnitude, Weaker Alignment

Now let $b_2$ have twice the magnitude:

$$\|b_2\| = 2L$$

but make an angle of:

$$\theta_2 = 60^\circ$$

with $a$.

Then:

$$a\cdot b_2 = L\cdot2L\cdot\cos60^\circ$$

Since:

$$\cos60^\circ = \frac12$$

we get:

$$a\cdot b_2 = L\cdot2L\cdot\frac12$$

Therefore:

$$\boxed{ a\cdot b_2 = L^2 }$$

So:

$$\boxed{ a\cdot b_1 = a\cdot b_2 = L^2 }$$

Yet:

$$\theta_1 = 0^\circ$$

while:

$$\theta_2 = 60^\circ$$

Therefore:

$$\boxed{ \text{Equal dot products do NOT imply equal alignment} }$$

---

## 6.2 What Compensated for the Weaker Alignment?

For $b_1$:

$$L\times L\times1 = L^2$$

For $b_2$:

$$L\times2L\times\frac12 = L^2$$

The second vector is:

- twice as large
- but only half as aligned

The two effects exactly compensate.

Conceptually:

$$\boxed{ 2\times\frac12 = 1 }$$

---

## 6.3 Scalar-Component Interpretation

Recall:

$$a\cdot b = \|a\| \mathrm{comp}_a(b)$$

For $b_1$:

$$\mathrm{comp}_a(b_1) = L\cos0^\circ = L$$

For $b_2$:

$$\mathrm{comp}_a(b_2) = 2L\cos60^\circ$$

$$= 2L\left(\frac12\right)$$

so:

$$\boxed{ \mathrm{comp}_a(b_2) = L }$$

Therefore:

$$\boxed{ \mathrm{comp}_a(b_1) = \mathrm{comp}_a(b_2) = L }$$

This reveals the deeper reason the dot products are equal:

> **Both vectors have exactly the same signed amount lying along the direction of $a$.**

Their perpendicular parts differ, but those parts do not contribute to the dot product.

---

## 6.4 Cosine Similarity Separates the Two Cases

If the real question is:

> **Which vector is more directionally aligned with $a$?**

then raw dot product cannot distinguish these two cases.

For $b_1$:

$$\cos\theta_1 = \cos0^\circ = \boxed{1}$$

For $b_2$:

$$\cos\theta_2 = \cos60^\circ = \boxed{0.5}$$

Therefore:

$$\boxed{ \cos(a,b_1) = 1 }$$

while:

$$\boxed{ \cos(a,b_2) = 0.5 }$$

Now the directional difference is visible immediately.

---

## 6.5 The Incorrect Shortcut

This statement is false:

> **“A larger dot product always means better alignment.”**

A larger dot product could result from:

- better alignment
- larger vector magnitudes
- both

Likewise, equal dot products can hide very different directional relationships.

The safer mental model is:

$$\boxed{ \text{Dot Product} = \text{MAGNITUDE-WEIGHTED ALIGNMENT} }$$

not merely:

$$\text{Dot Product} = \text{alignment}$$

---

## 6.6 Equal Dot Products Do Not Mean Equal Resultant Vectors

Suppose these vectors were interpreted as forces.

It would still be wrong to conclude:

> “If the dot products are equal, the resultant force must be equal.”

Resultant force comes from **vector addition**:

$$a+b$$

not from the dot product.

So:

$$\boxed{ a\cdot b_1 = a\cdot b_2 }$$

does **not** imply:

$$\boxed{ a+b_1 = a+b_2 }$$

---

## Section 6 Mental-Model Card

Two different vector pairs can satisfy:

$$\boxed{ a\cdot b_1 = a\cdot b_2 }$$

even when:

$$\theta_1 \ne \theta_2$$

because:

$$\boxed{ \text{magnitude and alignment can compensate for each other} }$$

In the example:

$$\boxed{ L\times L\times1 = L\times2L\times\frac12 = L^2 }$$

Durable distinction:

> **Equal dot product = equal magnitude-weighted relationship.**

> **It does not necessarily mean equal alignment.**

> **If alignment alone matters, examine cosine similarity.**

---

# Section 7 — Dot Product vs Vector Addition, Linear Combinations, and Matrix Multiplication

We now place the dot product beside several operations that can look superficially similar because they all involve multiplying and/or adding numbers.

The key distinction is:

> **What operation are we performing, what question does it answer, and what type of object does it produce?**

---

## 7.1 Vector Addition

Let:

$$u=[u_1,u_2]$$

and:

$$v=[v_1,v_2]$$

Vector addition is:

$$\boxed{ u+v = [u_1+v_1,\;u_2+v_2] }$$

The output is another vector.

Geometrically, vector addition combines two displacements.

If:

$$u=[1,2]$$

and:

$$v=[3,-1]$$

then:

$$u+v = [4,1]$$

The question being answered is:

> **What resultant displacement do these two vectors produce when combined?**

So:

$$\boxed{ \text{Vector + Vector} \rightarrow \text{Vector} }$$

---

## 7.2 Linear Combinations

A linear combination scales vectors and then adds them.

For example:

$$2u-v$$

means:

$$2u+(-1)v$$

If:

$$u=[1,2]$$

and:

$$v=[3,-1]$$

then:

$$2u-v = [2,4]-[3,-1]$$

$$= [2,4]+[-3,1]$$

so:

$$\boxed{ 2u-v = [-1,5] }$$

The output is a vector.

More generally:

$$\boxed{ x_1v_1+x_2v_2+\cdots+x_nv_n }$$

is a linear combination.

Its conceptual question is:

> **What vector can I construct by scaling and combining these vectors?**

---

## 7.3 Dot Product

Now compare that with:

$$u\cdot v$$

Using vector components:

$$u\cdot v = u_1v_1+u_2v_2$$

The corresponding components are multiplied and those numbers are added.

The result is one scalar:

$$\boxed{ u\cdot v \rightarrow \text{scalar} }$$

Conceptually, we are not constructing a new displacement.

We are measuring a scalar relationship between the vectors:

$$\boxed{ u\cdot v = \|u\|\|v\|\cos\theta }$$

So:

> **Linear combination → constructs a vector.**

> **Dot product → measures a scalar relationship between vectors.**

---

### 7.3.1 Side-by-Side Comparison

| Operation | Example | Output | Mental question |
|---|---|---|---|
| Vector addition | $u+v$ | Vector | What is their combined displacement? |
| Linear combination | $2u-v$ | Vector | What vector can these weighted vectors construct? |
| Dot product | $u\cdot v$ | Scalar | What is their magnitude-weighted directional relationship? |
| Cosine similarity | $\frac{u\cdot v}{\|u\|\|v\|}$ | Scalar | How aligned are their directions after removing magnitude? |

---

## 7.4 Matrix-Vector Multiplication

Consider:

$$A = \begin{bmatrix} 2&1\\ 3&4 \end{bmatrix}$$

and:

$$x = \begin{bmatrix} 5\\ 2 \end{bmatrix}$$

We want:

$$Ax$$

The answer is:

$$\boxed{ Ax = \begin{bmatrix} 12\\ 23 \end{bmatrix} }$$

There are two equally valid ways to understand what happened.

---

### 7.4.1 Row View — Dot Products

Look at the rows of $A$:

$$r_1=[2,1]$$

$$r_2=[3,4]$$

Each output number is the dot product of one row with $x$.

First output:

$$r_1\cdot x = [2,1]\cdot[5,2]$$

$$= 2(5)+1(2)$$

$$= 12$$

Second output:

$$r_2\cdot x = [3,4]\cdot[5,2]$$

$$= 3(5)+4(2)$$

$$= 23$$

Therefore:

$$Ax = \begin{bmatrix} r_1\cdot x\\ r_2\cdot x \end{bmatrix}$$

So the row view says:

> **Each row of the matrix takes a dot product with $x$ to produce one output number.**

For an $m\times n$ matrix:

$$A = \begin{bmatrix} r_1\\ r_2\\ \vdots\\ r_m \end{bmatrix}$$

we can think of:

$$\boxed{ Ax = \begin{bmatrix} r_1\cdot x\\ r_2\cdot x\\ \vdots\\ r_m\cdot x \end{bmatrix} }$$

---

### 7.4.2 Geometric Meaning of the Row View

Because each output is a dot product:

$$r_i\cdot x = \|r_i\|\|x\|\cos\theta_i$$

each row can be thought of as asking:

> **How much magnitude-weighted alignment does $x$ have with my direction?**

So matrix-vector multiplication can be viewed as several rows independently evaluating the same input vector.

---

## 7.5 Column View — Linear Combination

Now look at the columns of $A$.

Let:

$$c_1 = \begin{bmatrix} 2\\ 3 \end{bmatrix}$$

and:

$$c_2 = \begin{bmatrix} 1\\ 4 \end{bmatrix}$$

The entries of $x$ act as coefficients for the columns:

$$Ax = 5c_1+2c_2$$

Therefore:

$$Ax = 5 \begin{bmatrix} 2\\ 3 \end{bmatrix} + 2 \begin{bmatrix} 1\\ 4 \end{bmatrix}$$

$$= \begin{bmatrix} 10\\ 15 \end{bmatrix} + \begin{bmatrix} 2\\ 8 \end{bmatrix}$$

so:

$$\boxed{ Ax = \begin{bmatrix} 12\\ 23 \end{bmatrix} }$$

So the column view says:

> **Matrix-vector multiplication forms a linear combination of the columns of $A$, using the entries of $x$ as coefficients.**

In general:

$$\boxed{ Ax = x_1c_1+x_2c_2+\cdots+x_nc_n }$$

---

## 7.6 Same Operation — Two Mental Models

For:

$$Ax$$

we have two complementary interpretations.

| View | Look at | Interpretation |
|---|---|---|
| **Row view** | Rows of $A$ | Each output coordinate is a **dot product** |
| **Column view** | Columns of $A$ | Output vector is a **linear combination** of columns |

These are not competing explanations.

They are two views of the **same operation**.

---

## 7.7 A Useful Switching Trigger: $Ax=b$

Suppose:

$$Ax=b$$

### $A$ and $x$ known → understand $b$

The **row view** is often natural:

> **What output does each row produce when dotted with $x$?**

$$b_i = r_i\cdot x$$

### $A$ and $b$ known → understand unknown $x$

The **column view** is often more intuitive:

> **What coefficients $x_1,x_2,\ldots,x_n$ combine the columns of $A$ to construct $b$?**

$$\boxed{ x_1c_1+x_2c_2+\cdots+x_nc_n = b }$$

### Important caveat

This is a **mental-model switch**, not an algorithmic rule.

When solving:

$$Ax=b$$

we do not generally guess different column combinations manually.

Actual computational methods include elimination, factorization, least squares, and others.

The column view tells us **what problem we are solving geometrically**.

---

## 7.8 Matrix Multiplication — Extending the Same Idea

Suppose:

$$C=AB$$

Every entry of $C$ is obtained by taking:

> **one row of $A$ · one column of $B$**

So:

$$\boxed{ C_{ij} = \mathrm{row}_i(A) \cdot \mathrm{column}_j(B) }$$

If $A$ is $m\times n$ and $B$ is $n\times p$, then:

$$AB$$

has dimensions:

$$\boxed{ m\times p }$$

because each of the $m$ rows of $A$ is paired with each of the $p$ columns of $B$.

---

### 7.8.1 Dot Product as a $1\times1$ Matrix Product

Take:

$$a^T = \begin{bmatrix} a_1&a_2&\cdots&a_n \end{bmatrix}$$

which is $1\times n$, and:

$$b = \begin{bmatrix} b_1\\ b_2\\ \vdots\\ b_n \end{bmatrix}$$

which is $n\times1$.

Then:

$$a^Tb$$

has dimensions:

$$(1\times n)(n\times1) \rightarrow 1\times1$$

and:

$$a^Tb = a_1b_1+a_2b_2+\cdots+a_nb_n$$

Therefore:

$$\boxed{ a^Tb = a\cdot b }$$

The resulting $1\times1$ object is conventionally treated as a scalar.

---

## 7.9 Putting Everything Together

| Operation | Basic structure | Output | Mental model |
|---|---|---|---|
| **Vector addition** | $u+v$ | Vector | Combine displacements |
| **Linear combination** | $x_1v_1+\cdots+x_nv_n$ | Vector | Construct a vector from weighted vectors |
| **Dot product** | $u\cdot v$ | Scalar | Magnitude-weighted alignment |
| **Matrix-vector: row view** | $r_i\cdot x$ | Scalars assembled into vector | Each row computes one output |
| **Matrix-vector: column view** | $x_1c_1+\cdots+x_nc_n$ | Vector | Weighted columns construct output |
| **Matrix multiplication** | row · column | Matrix | Dot products produce individual matrix entries |

The important connection is:

$$\boxed{ \text{Matrix-vector multiplication} }$$

can simultaneously be understood as:

$$\boxed{ \text{DOT PRODUCTS of rows} }$$

and:

$$\boxed{ \text{LINEAR COMBINATION of columns} }$$

---

## Section 7 Mental-Model Card

Ask:

> **Am I CONSTRUCTING a vector or MEASURING a relationship?**

If we are scaling/combining vectors:

$$\boxed{ \text{Linear combination} \rightarrow \text{VECTOR} }$$

If we are comparing vectors through the dot operation:

$$\boxed{ \text{Dot product} \rightarrow \text{SCALAR} }$$

For:

$$Ax=b$$

remember:

> **ROWS → dot products → how each output number is computed**

> **COLUMNS → linear combination → how the output vector is constructed**

And for general matrix multiplication:

> **Each output entry = ROW · COLUMN**

---

# Section 8 — Very Short Physical Analogy

The cleanest physical use of the dot product is **mechanical work**:

$$\boxed{ W=F\cdot d }$$

Only the component of force along the displacement contributes to work.

A perpendicular force contributes zero because:

$$\cos90^\circ=0$$

This is not merely an analogy; it is an actual physical application of the dot product.

One warning is sufficient:

> **Resultant force uses vector addition, not dot product.**

Equal dot products therefore do **not** imply equal resultant forces.

---

# Section 9 — Common Thinking Traps: What to Catch Yourself Thinking

Use this section as a future **debugging checklist for your own thinking**.

| If I catch myself thinking... | Replace it with... |
|---|---|
| **“Dot product measures alignment.”** | Not quite. **Dot product measures magnitude-weighted alignment.** |
| **“These vectors are perfectly aligned, so their dot products should be the same.”** | Perfect alignment only fixes $\cos\theta=1$. Their magnitudes can still make the dots different. |
| **“Larger dot product means better directional similarity.”** | Not necessarily. Larger magnitudes can also produce a larger dot. Use cosine similarity if magnitude should be removed. |
| **“Cosine similarity is another independent signal I should calculate after dot product.”** | Usually it is the **same directional relationship with magnitude removed**, not an independent piece of evidence. |
| **“Cosine similarity means dot product × cosine.”** | No. $\displaystyle \cos\theta=\frac{a\cdot b}{\|a\|\|b\|}$. |
| **“Normalize the magnitudes.”** | Normalize the **vectors** to unit length. |
| **“Projection onto $a$ means horizontal projection.”** | Projection lies along the **line in $a$'s direction**, whatever that direction is. |
| **“Component and projection are the same thing.”** | Component = signed scalar **HOW MUCH**. Projection = vector **HOW MUCH × WHICH DIRECTION**. |
| **“The dot product is the projected vector.”** | Dot product is a **scalar**. Projection is a **vector**. |
| **“$\|b\|\cos\theta$ is the projection.”** | It is the **scalar component**. Multiply it by $\hat a$ to obtain the projection vector. |
| **“A dot product produces some resultant vector.”** | Dot product produces one scalar. Vector addition produces a resultant vector. |
| **“$v\cdot v$ is the length of $v$.”** | $v\cdot v=\|v\|^2$. Take the square root to get length. |
| **“A vector has to start at the origin.”** | A vector is a displacement. Drawing it from the origin is only a convenient representation. |
| **“$[3,2]$ in a dot product is a point.”** | It is a vector represented by its components. A point answers **WHERE**; a vector answers **HOW FAR + WHICH DIRECTION**. |
| **“Equal dot products mean the vectors have the same geometry.”** | Different magnitude-angle combinations can produce exactly the same dot product. |
| **“Cosine similarity and correlation are basically the same.”** | No. Correlation involves statistical centering and its own definition; cosine similarity is normalized directional comparison. |

---

# Section 10 — Useful Consequences and Choosing the Right Operation

Most of the underlying ideas have already been derived, so only the genuinely useful consequences remain here.

---

## 10.1 Self-Dot Gives Squared Magnitude

$$\boxed{ v\cdot v = \|v\|^2 }$$

Therefore:

$$\boxed{ \|v\| = \sqrt{v\cdot v} }$$

This follows because the angle between a vector and itself is $0^\circ$.

---

## 10.2 Distance Uses the Norm of a Displacement

For points $P$ and $Q$, form the displacement:

$$d=Q-P$$

Then:

$$\boxed{ \mathrm{distance}(P,Q) = \|d\| = \sqrt{d\cdot d} }$$

So dot product participates in distance **through the self-dot of the displacement vector**.

A generic:

$$a\cdot b$$

is not a distance.

---

## 10.3 Dot Product Gives a Quick Angle Test

For nonzero vectors:

$$a\cdot b>0 \quad\Rightarrow\quad \text{acute / net aligned}$$

$$a\cdot b=0 \quad\Rightarrow\quad \text{perpendicular}$$

$$a\cdot b<0 \quad\Rightarrow\quad \text{obtuse / net opposing}$$

No angle calculation is required.

---

## 10.4 Maximum Possible Dot Product

Because:

$$-1 \le \cos\theta \le 1$$

we have:

$$\boxed{ |a\cdot b| \le \|a\|\|b\| }$$

Equality occurs when the nonzero vectors are parallel or anti-parallel.

This is the **Cauchy–Schwarz inequality**.

At this stage, the useful intuition is simply:

> **Alignment cannot amplify the product of the two magnitudes beyond a factor of 1.**

The formal inequality can be revisited when Cauchy–Schwarz becomes important later.

---

## 10.5 Dot Product or Cosine Similarity?

The entire choice can be compressed into one question:

$$\boxed{ \textbf{Do we want magnitude to matter?} }$$

| If... | Use |
|---|---|
| Magnitude **should matter** | Dot product |
| Magnitude **should be removed** and only directional alignment matters | Cosine similarity |
| Vectors are already unit-normalized | Dot product = cosine similarity |

Remember:

$$\boxed{ \text{Dot} = \text{magnitude} \times \text{magnitude} \times \text{alignment} }$$

while:

$$\boxed{ \text{Cosine similarity} = \text{alignment} }$$

Neither is universally better.

They answer different questions.

---

# Section 11 — Practice / Midnight-Recall Questions

Try to answer these **without looking at the formulas first**.

1. What is a vector fundamentally: a location or a displacement?
2. What is the difference between point $(3,2)$ and vector $[3,2]$?
3. What does $\|v\|$ represent?
4. What type of object does vector addition produce?
5. What type of object does a dot product produce?
6. Give the three equivalent views of the dot product.
7. What is the quickest computational formula for $a\cdot b$?
8. What is the core geometric mental model of the dot product?
9. What does $\cos\theta$ represent inside the geometric formula?
10. Why does the perpendicular part of $b$ contribute zero to $a\cdot b$?
11. What exactly is $\mathrm{comp}_a(b)$?
12. Is $\mathrm{comp}_a(b)$ a scalar or vector?
13. What is the difference between scalar component and vector projection?
14. What does the unit vector $\hat a$ contribute to the projection formula?
15. Reconstruct projection from **HOW MUCH × WHICH DIRECTION**.
16. Why is projection not required to calculate a dot product?
17. Why is $a\cdot b=b\cdot a$, even though the component interpretation chooses one vector as reference?
18. What does $v\cdot v$ equal?
19. How do you obtain $\|v\|$ from $v\cdot v$?
20. What does a positive, zero, or negative dot product tell you about the angle?
21. Why can two pairs of vectors have the same dot product but different alignment?
22. Why can perfectly aligned vectors have different raw dot products?
23. What does cosine similarity remove from the raw dot product?
24. What happens geometrically when a vector is unit-normalized?
25. What is the relationship between cosine similarity and the dot product of normalized vectors?
26. What question should you ask before choosing dot product versus cosine similarity?
27. If two sentence embeddings have high cosine similarity, where did the semantic meaning actually come from?
28. What is the difference between vector addition and dot product?
29. What is a linear combination conceptually doing?
30. In $Ax$, what does the **row view** say?
31. In $Ax$, what does the **column view** say?
32. If $A$ and $b$ are known in $Ax=b$, what does the column view ask you to find?
33. In general matrix multiplication, how is each output entry calculated?
34. Why can a dot product be viewed as a $1\times n$ row multiplied by an $n\times1$ column?
35. In the work formula $W=F\cdot d$, which part of the force contributes?
36. Why does a force perpendicular to displacement do zero work in this model?
37. Does equal dot product imply equal resultant vectors?
38. How can distance between two points be expressed using a dot product?
39. What is the Cauchy–Schwarz bound telling us geometrically?
40. Without memorizing formulas, reconstruct the chain:

$$\text{Geometry} \rightarrow \text{Component} \rightarrow \begin{cases} \text{Dot Product}\\ \text{Projection} \end{cases}$$

---

## 11.1 Answer Key

1. A **displacement**: magnitude plus direction.
2. Point = **WHERE**. Vector = **HOW FAR + WHICH DIRECTION**.
3. Vector length/magnitude.
4. A vector.
5. A scalar.
6. Vector-components, geometry/alignment, scalar-component.
7. $\displaystyle a\cdot b=\sum_i a_ib_i$.
8. **Magnitude × magnitude × alignment.**
9. Signed directional alignment.
10. It is at $90^\circ$, so $\cos90^\circ=0$.
11. The signed amount of $b$ lying along the direction of $a$.
12. Scalar.
13. Component = **HOW MUCH**; projection = **HOW MUCH × WHICH DIRECTION**.
14. The direction of $a$, with magnitude 1.
15. $\displaystyle \mathrm{proj}_a(b)=\mathrm{comp}_a(b)\hat a$.
16. The scalar component already contains the amount needed for $a\cdot b=\|a\|\mathrm{comp}_a(b)$.
17. Either reference-direction interpretation produces the same scalar; the algebra is symmetric.
18. $\|v\|^2$.
19. $\sqrt{v\cdot v}$.
20. Positive = acute; zero = perpendicular; negative = obtuse.
21. Magnitude and alignment can compensate for each other.
22. Raw dot retains magnitude.
23. The two original vector magnitudes.
24. Its direction remains unchanged; its length becomes 1.
25. They are equal.
26. **Do we want magnitude to matter?**
27. From the embedding model; cosine only compares the resulting vectors.
28. Addition constructs a vector; dot product produces a scalar relationship.
29. Scaling vectors and adding them to construct another vector.
30. Each output entry is a row of $A$ dotted with $x$.
31. $x$'s entries weight the columns of $A$ to construct the output vector.
32. The coefficients that combine the columns of $A$ to produce $b$.
33. Row of the first matrix · column of the second.
34. The multiplication produces one $1\times1$ result, conventionally treated as a scalar.
35. The component of force along displacement.
36. Its component along displacement is zero.
37. No. Resultants come from vector addition.
38. Let $d=Q-P$; distance $=\sqrt{d\cdot d}$.
39. The absolute dot product cannot exceed the product of the vector magnitudes.
40. Geometry gives:

$$\mathrm{comp}_a(b) = \|b\|\cos\theta$$

then:

$$\mathrm{comp}_a(b)\times\|a\| \rightarrow a\cdot b$$

while:

$$\mathrm{comp}_a(b)\times\hat a \rightarrow \mathrm{proj}_a(b)$$

---

# Section 12 — Final Mental-Model Cards

These are the **smallest durable reload layer**—not a summary of every detail.

---

## Card 1 — Vector

$$\boxed{ \text{Vector} = \text{HOW FAR} + \text{WHICH DIRECTION} }$$

Point = **WHERE**

Vector = **DISPLACEMENT**

---

## Card 2 — Dot Product

$$\boxed{ a\cdot b = \|a\|\|b\|\cos\theta }$$

> **Dot product = MAGNITUDE × MAGNITUDE × ALIGNMENT**

Output:

$$\boxed{ \text{SCALAR} }$$

---

## Card 3 — Three Views of the Same Dot Product

$$\boxed{ \sum_i a_ib_i = \|a\|\|b\|\cos\theta = \|a\|\mathrm{comp}_a(b) }$$

> **Components COMPUTE it.**

> **Geometry EXPLAINS alignment.**

> **Scalar component shows WHAT CONTRIBUTES.**

---

## Card 4 — Component and Projection

$$\boxed{ \mathrm{comp}_a(b) = \|b\|\cos\theta }$$

> **Component = HOW MUCH**

$$\boxed{ \hat a = \frac{a}{\|a\|} }$$

> **Unit vector = WHICH DIRECTION**

$$\boxed{ \mathrm{proj}_a(b) = \mathrm{comp}_a(b)\hat a }$$

> **Projection = HOW MUCH × WHICH DIRECTION**

And:

$$\boxed{ \mathrm{comp}_a(b) \begin{cases} \times\|a\| \rightarrow a\cdot b\\ \times\hat a \rightarrow \mathrm{proj}_a(b) \end{cases} }$$

---

## Card 5 — What Contributes to a Dot Product?

Decompose:

$$b = b_{\parallel}+b_{\perp}$$

Then:

$$\boxed{ a\cdot b_{\perp} = 0 }$$

Therefore:

$$\boxed{ a\cdot b = a\cdot b_{\parallel} }$$

> **Only the part along the reference direction contributes.**

---

## Card 6 — Cosine Similarity

$$\boxed{ \cos\theta = \frac{a\cdot b}{\|a\|\|b\|} }$$

> **Cosine similarity = dot product with magnitude removed.**

And:

$$\boxed{ \hat a\cdot\hat b = \cos\theta }$$

Decision trigger:

> **Do we want magnitude to matter?**

---

## Card 7 — Linear Combination vs Dot Product

> **Linear combination → CONSTRUCT a VECTOR**

$$x_1v_1+\cdots+x_nv_n$$

> **Dot product → MEASURE a SCALAR relationship**

$$u\cdot v$$

---

## Card 8 — Matrix-Vector Multiplication

For:

$$Ax=b$$

> **ROWS → DOT PRODUCTS → how each output number is computed**

> **COLUMNS → LINEAR COMBINATION → how the output vector is constructed**

And in matrix multiplication:

$$\boxed{ C_{ij} = \mathrm{row}_i(A) \cdot \mathrm{column}_j(B) }$$

---

## Card 9 — Self-Dot

$$\boxed{ v\cdot v = \|v\|^2 }$$

Therefore:

$$\boxed{ \|v\| = \sqrt{v\cdot v} }$$

---

## Card 10 — Final One-Line Reload

If only **one chain** survives months from now, keep this:

$$\boxed{ \text{Vector} \rightarrow \text{Magnitude + Direction} \rightarrow \text{Dot = Magnitude-Weighted Alignment} \rightarrow \text{Component = HOW MUCH Along} \rightarrow \text{Projection = HOW MUCH × WHICH DIRECTION} }$$

And for choosing similarity:

$$\boxed{ \textbf{Magnitude matters? Dot.} \qquad \textbf{Magnitude removed? Cosine.} }$$
