# readme
A collection of readme snippets

## GIT

### Branch schema

```blank
{type}/{id}-{title}
```

Possible `types` are for example

- feature
- bugfix
- hotfix

### How do i squash several commits?

First we have to change to the desired branch where the commits are located.

```
git checkout {branch name}
git switch {branchname}
```

Then we can squash the commits by doing an interative rebase.

```
git rebase -i {target}
```

Possible `targets` could be

- master
- main
- HEAD~{the number of commits we want to go back}

## Documentation

The source code should be documented. We use standardised annotations for this purpose.

### Annotation sources

- JSDoc http://usejsdoc.org/
- TSDoc https://tsdoc.org/
- PHPDoc https://docs.phpdoc.org/

### Directory structure

```blank
{directory name}
├── {directory name}
│   ├── {file name}
│   ├── {directory name}
│   |   └── {file name}
│   └── {directory name}
│       ├── {file name}
│       └── {file name}
└── {directory name}
```

## Features

Features should be able to be deactivated.

```js
const settings = {
  active: true
};

const feature = () => {
  if (settings.active === false) {
    return false;
  }

  ...
}
```

## Components

### Atomic Design

@see <https://atomicdesign.bradfrost.com/chapter-2/#the-atomic-design-methodology>

```blank

       ◯  Atoms

      ◯
     ◯ ◯  Molecules

 ◯ ◯ ◯ ◯
 ◯ ◯ ◯ ◯  Organism
 ◯ ◯ ◯ ◯

     ╌╌
    ┆  ┆  Template
     ╌╌

     ‒‒
    | \|  Pages
     ‒‒

```

### Requirements

- Do we support touch?
- Do we support keyboard?
- Do we use events?
- Do we have a `:hover` state?
- Do we have a `:focus` state?
- Do we have an `:in-focus` state?
- Do we have an `:active` state?
- Do we have a `readonly` state?
- Do we have a `disabled` state?
- Do we have a `blurred` state?
- Do we have an `invalid` state?
- Do we have a `selected` or `checked` state?
- Do we have an `animation`?

### How do we expose errors?

Components should have a general and aligned way to report errors. When a component has an error, it is announced by an event called {event name}.

> We throw an error to allow external things to catch and handle this error.

## CSS

### ITCSS

@see https://csswizardry.com/about/

@see https://itcss.io/

```blank
    ----------------- Range ------------------
    __________________________________________
| | \                                        /  Settings
| |  \                                      /  (e.g. fonts, color, etc.)
| |   \____________________________________/
| |    \                                  /  Tools
        \                                /  (e.g. mix ins, functions etc.)
U S      \______________________________/
n p       \                            /  Generics
i e        \                          /  (e.g. Reset etc.)
q c         \________________________/
u i          \                      /  Elements / Atoms
e f           \                    /  (e.g. headlines, paragraphs, images etc.)
n i            \__________________/
e c             \                /  Objects
s i              \              /  (e.g. grids etc.)
s t               \____________/
  y                \          /  Components / Atoms, Molecules, Organism, Template, Pages
|                   \        /  (e.g. buttons, inputs, sections etc.)
| |                  \______/
| |                   \    /  Utilities
| |                    \  /  (page specific styles)
| |                     \/
```

### BEM

@see http://getbem.com/

```blank
{Block}__{Element}--{Modifier}
```

`Block`, encapsulates a standalone entity that is meaningful on its own. Most likely an component.

`Element`, is a part of block and have no standalone meaning.

`Modifier`, Flags on blocks or elements. Use them to change appearance, behavior or state.
