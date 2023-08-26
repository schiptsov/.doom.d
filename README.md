With &ldquo;Doom&rdquo; one *delegates* everything to the maintainers and only extends and augments the configuration. Otherwise everything will break very quickly, because it moves fast and is a subject to lots of changes at all levels (including the individual packages).

1.  use declarative embedded DSLs
2.  use stable high-level interfaces
3.  *respect the proper ADTs*
4.  *do not /over-configure*


# The rant

&ldquo;Doom&rdquo; is already bloated (but not as bloated as *Spacemacs) by doing an /over-configuration* and, what is worse &#x2013; *over-abstraction* (introducing unnecessary and redundant new abstractions, which is the root of all evil).

The most deadly sin is *to break abstraction barriers* and use and rely on other module&rsquo;s *internals*, which are supposed to be hidden (and subject to change) and only the proper abstract exported interfaces being used.

Again, breaking abstraction barriers and not respecting ADTs is a way to a ruin.

The way better concept is &ldquo;*extension methods&ldquo; of Scala /a proper way to extend without breaking existed interfaces* Well, we do not have these, but we could use the underlying principle.

But how can we peoperly extend *other people&rsquo;s code*? Well, by taking mode burden, doing more work and prepare and submit the patches.

The *right way* (to take *more* burden) is this (remember, that a proper hierarchy should go straight down to `C` implementations, like `gnutls`, `libxml2`, `json`, or `tree-sitter`):

-   study what are the &ldquo;core abstractions&rdquo; and interfaces of a *subsystem*
-   is there this kind of abstraction already implemented in Emacs
-   how could I improve or augment them it *right in Emacs*
-   prepare and submit a *patch* (yes, do more work) for Emacs.
-   when you need a better interface from *other modules* to the same

This is how to actually improve the things not just for oneself but for everyone. Lots of *ad-hoc* code from &ldquo;Doom&rdquo; could end up in Emacs.

It is absolutely OK to &ldquo;rip off&rdquo; other people&rsquo;s code and do better rewrites. The classic case is how Emacs build its own *project layer* looking at what `projectile` did.

Well, we can think of `projectile` as a nice quick *prototype* or *bootstrapping and implementation of certain good ideas*, so everyone appreciate and are grateful. And, of course, it can be used as a *standalone* package.

Import and integration, as was the case with the wonderful `use-package` toolkit is even better, but it has to be of this kind of quality and excellence.

The contrary example is when an absolutely excellent work was not integrated in a &ldquo;stdlib&rdquo; and become obsolete

-   <https://github.com/rtoy/cl-series>
-   <https://github.com/emacsattic/nxhtml.git>
-   Icicles

The motivating example is, of course. the *MIT Scheme* - a Lisp implementation (and a sdlib) done right.