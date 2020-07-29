---
title: Laravel Integration
description: Integration of the Laravel Framework
weight: 100 
layout: docs

---

Some work had already been carried out in the v2 development branch
to integrated some aspects of the Laravel framework in Zen Cart.

This focused initially on the `Eloquent` database ORM to allow for 
a fluent interface for building sql queries based on models of Zen Cart's
database tables.

For v158 it was decided that there were many other aspects of Laravel
that we could leverage in Zen Cart core code.

So rather than adding these piecemeal, it seemed easier to just pull in
the whole framework, and take advantage of the bootstrapping code Laravel 
already contained.

