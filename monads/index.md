WTF are *monads*?
===============

Excellent question!

Unfortunately... this text will probably not help much.

My confession: I love Haskell, I'm semi-competent with it, but I can't
say I "understand monads."

Not any more than I can say I "understand groups." You know, groups
from abstract algebra? My other confession is that I failed the only
abstract algebra course I took...

I remember studying it. At the time I was getting into green tea. So I
would make a lot of tea and sit down to read the textbook, do some
exercises, study some proofs... And end up frustrated.

Still, I'm going to try teaching some of it to you now, just to see if
I remember. This won't be on the exam... It's just an example for
talking about how to think about---and work with---abstract concepts,
like the concept "monad."

Hopefully the mathematical analogy will clarify something about the
relation between theory and practice, and why Haskell can seem more
intimidating than it should.

So let's leave the world of programming behind for a second, and
breathe the clean mountain air of algebra!

## Groups

The concept "group" is really simple. You start with agreeing on the
basic notions: sets, elements, operators, and equations. And then...

You need a set, call it $G$. Say $x,y,z$ are arbitrary elements
of $G$.

You need an associative operator on $G$, call it $*$, so $$x * (y * z)
= (x * y) * z,$$ which is to say you can regroup these computations.

You also need an identity element of $G$, call it $e$, so $$x*e = e*x
= x.$$ And you need inverse elements, written $-x$, so $$x*(-x)=e.$$
Why would this be interesting or useful? Well, since this basic
structure can be applied to many different sets and operators, it's
interesting to explore what you can say given only these assumptions.

For example... We can see exactly what it means to "simplify" a term
of symbolic elements---like when we reduce, say, $$x+(0 + (-x + y))$$
to just $y.$ What's the algorithm for this? If you devise a method,
and prove it correct for groups in general, then you can use it in
good faith with different groups. The exact same steps apply to
$$x*(1*(x^{-1}*y)),$$ so if you can reuse your reasoning you save on
math paper.

Concrete algebra came first. And when you learn algebra, you learn it
with numbers first, then with symbols, and then if you're interested,
you can study the abstract concepts---which are historically
rather new.

## What "Is" a Group... Like, Really?

If you do the first pages of exercises in any modern algebra book,
you'll be proficient enough in proving basic things about
groups. You'll learn about some more specific variants of groups, like
finite groups, abelian groups, and cyclic groups. And you'll learn
about other concepts built on the group concept, like subgroups.

But what *is* the thing you're studying? This question turns out to be
a deep rabbit hole that leads to philosophy, ontology, epistemology,
and who knows what.

An interesting talk by Timothy Gowers, entitled ["Does mathematics
need a
philosophy?"](https://www.dpmms.cam.ac.uk/~wtg10/philosophy.html), has
this bit, about how hard it is to find 'satisfactory' definitions of
abstract concepts:

> I would contend that it doesn't matter because it *never* matters
  what a mathematical object is, or whether it exists. What *does*
  matter is the set of rules governing how you talk about it---or
  perhaps I should say, since that sounds as though "it" refers to
  something, what matters about a piece of *mathematical terminology*
  is the set of rules governing its use.

He also says:

> What matters about them is the basic properties enjoyed by the
  objects being defined, and learning to use these fluently and easily
  means learning appropriate replacement rules rather than *grasping
  the essence of the concept.*

That's why I felt so confused when I was trying to study
abstract algebra.

From this brief detour into the pedagogy of math, let's return
to Haskell.

## Functors and Monads

If you grant that "grasping the essence of the concept" is not
applicable to abstract mathematical terminology, you might stop
worrying about whether you "understand" monads. From there you just
keep doing Haskell.

So... what are the basic properties of monads, again? Well, the
concept extends the concept of a functor.

```haskell
class Functor f where
  fmap :: (a -> b) -> (f a -> f b)

class Functor m => Monad m where
  return :: a -> m a
  join   :: m (m a) -> m a
```

Those are the type definitions, but there are also fundamental
algebraic properties ("laws") involved.

A functor behaves well with respect to the identity function and the
function composition operator, like this:

```haskell
fmap id      === id
fmap (f . g) === fmap f . fmap g
```

A monad behaves well with respect to `fmap`:

```haskell

```