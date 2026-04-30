---
# Tufte-inspired theme — extracted to ./slidev-theme-tufte
theme: ./slidev-theme-tufte
title: Package Management is Fun
info: |
  ## Pixi & the Rust toolchain underneath
  Tim de Jager · prefix.dev
  Rust Meetup @ Jetbrains
class: text-center
drawings:
  persist: false
transition: slide-left
comark: true
duration: 35min
---

<div class="relative mx-auto w-48">
  <img src="/paxton.png" class="w-full" alt="Paxton" />
</div>


# Introducing Pixi

## Package Management, conda, and Rust 

Tim de Jager at <img src="/prefix-logo.svg" class="inline align-middle h-5 mx-1" alt="prefix.dev" />


---

# Who am I?


<img src="/tim.jpeg" class="absolute right-24 top-24 w-44 rounded-full" alt="Tim" />
<div class="absolute right-12 bottom-24 w-72 h-44">
  <img v-click="[1, 2]" src="/reus.jpg" class="absolute inset-0 w-full h-full object-contain rounded shadow" alt="Reus" />
  <img v-click="[2, 3]" src="/smart-robotics.jpg" class="absolute inset-0 w-full h-full object-contain rounded shadow" alt="Smart Robotics" />
  <img v-click="[3, 4]" src="/prefix-logo.svg" class="absolute inset-0 w-full h-full object-contain" alt="prefix.dev" />
</div>

- Tim de Jager [github](https://github.com/tdejager)
- Developer at <img src="/prefix-logo.svg" class="inline align-middle h-5 mx-1" alt="prefix.dev" />
- Used to work at:

<v-clicks>

- Abbey Games (making games) with C++
- Smart Robotics (making robots) with C++ and Python
- .. Prefix.dev Rust and Package Managers

</v-clicks>


---
layout: center
---

# Take Away
<v-clicks>

- There is more than cargo,
- Working on package management is fun,
- ... pixi is kinda cool (hopefully)

</v-clicks>

---

# Why do I think its fun?

- Working on package managers is a great enabler
- People are generally quite grateful
- Active discord around ~250 members

---

# So what is Pixi?!

<img src="/paxton.png" class="absolute right-12 w-64" alt="Paxton" />

### Open Source on Github: https://github.com/prefix-dev/pixi
<br />
<v-clicks>

- Built on top of conda and conda-forge
- *Global* and *Local* environments
- `pixi.toml` as its main manifest with a lock file: `pixi.lock`.
- Supports *binary* and *source* dependencies.
- Especially useful in project combining multiple programming languages
  - Robotics
  - Data Science
  - etc.

## I'll explain more of this in depth

</v-clicks>


<!--
Pain-point opener. Concrete: we built robots, the deploy story was a mess.
-->

---

# So what is the conda ecosystem?!

<img src="/conda.png" class="absolute right-12 w-64" alt="conda" />

### A cross-platform, cross-language package ecosystem

<br />

<v-clicks>

- Ships C, C++, Rust, Fortran, R, Java, ... whole native stacks
- Packages live on **channels**, basically indexes
- Isolated environments similar to `.venv`
- Origins in scientific computing now used in a bunch of places.

</v-clicks>

<!--
Frame conda as a generic native-package system. The talk's earlier
"this could be bigger" beat lands here. Drop `/conda.png` in public/.
-->

---

# So what is conda-forge?!

<img v-click="[1, 5]" src="/conda-forge.png" class="absolute right-12 w-64" alt="conda-forge" />
<div v-click="5" class="absolute right-0 top-72 w-164">
<img src="/prefix-screenshot.png" class="rounded-xl" alt="conda-forge" />
<div v-click="6" class="prefix-stamp">
  <img src="/rust-logo.svg" alt="Rust" />
</div>
</div>

<style scoped>
.prefix-stamp {
  position: absolute;
  top: 0%;
  right: 2%;
  transform: rotate(14deg);
  padding: 0.6rem;
  border: 3px solid black;
  border-radius: 22%;
  background: rgba(255, 255, 255, 1);
  pointer-events: none;
}
.prefix-stamp img {
  width: 5rem;
  height: 5rem;
  display: block;
}
</style>

### The community channel that powers most of the ecosystem

<br />

<v-clicks>

- Community-maintained channel ~32,000 packages
- One **recipe** (feedstock) per package, one CI per recipe
- Curated packages, need to get through a review first.
- Differs from `pypi`, `crates.io` etc. No developer machine publishing

</v-clicks>

---

# How conda-forge ships a package

<div class="cf-stage cf-ships-slide relative mt-6">

<img src="./assets/conda-forge-flow.svg" class="w-full" alt="conda-forge flow" />

<div v-click="1" class="recipe-overlay">

```yaml
# recipe.yaml
package:
  name: btop
  version: "1.4.5"

source:
  url: https://github.com/aristocratos/btop/archive/v${{ version }}.tar.gz
  sha256: 4a4d…

build:
  number: 0
  script: make && make install PREFIX=$PREFIX

requirements:
  build:
    - ${{ compiler('cxx') }}
    - make
  host:
    - libcxx
```

</div>
</div>

<style scoped>
.recipe-overlay {
  position: absolute;
  top: 4%;
  left: 30%;
  width: 60%;
  transform: rotate(-2deg);
  background: var(--tufte-bg);
  border: 1px solid var(--tufte-rule);
  border-radius: 3px;
  padding: 0.4rem 0.9rem;
  box-shadow: 0 6px 18px rgba(0, 0, 0, 0.18), 0 1px 3px rgba(0, 0, 0, 0.12);
  font-size: 0.7rem;
  max-height: none;
  overflow: visible;
}
.recipe-overlay pre,
.recipe-overlay code,
.recipe-overlay .shiki,
.recipe-overlay .slidev-code {
  max-height: none !important;
  overflow: visible !important;
  white-space: pre !important;
  line-height: 1.25 !important;
}
.recipe-overlay::after {
  content: "";
  position: absolute;
  top: 0;
  right: 0;
  width: 18px;
  height: 18px;
  background: linear-gradient(
    135deg,
    var(--tufte-bg) 0%,
    var(--tufte-bg) 50%,
    rgba(0, 0, 0, 0.06) 50%,
    rgba(0, 0, 0, 0.12) 100%
  );
  border-left: 1px solid var(--tufte-rule);
  border-bottom: 1px solid var(--tufte-rule);
}
.recipe-overlay pre {
  margin: 0;
  background: transparent !important;
  border: none !important;
  padding: 0 !important;
}
</style>

<style>
/* Disable the theme's slide-scoped overflow scroll for this one slide so
 * the rotated recipe card can extend past the SVG without being clipped. */
.slidev-layout:has(.cf-ships-slide) {
  overflow: visible !important;
}
</style>

<!--
sources + recipe → CI → binary packages → channel.
Say it in plain English while the diagram does the lifting.
-->

---
layout: two-cols
---

# A `pixi.toml`, the basics

<br/>

<v-clicks at="1">

1. `pixi add python`
2. `pixi add --feature test pytest`
3. `pixi project environment add test --feature test`
4. `pixi task add greet '...'`
5. `pixi run greet` 
6. `pixi run -e test pytest`

</v-clicks>

<!--
One slide, five clicks. Each click runs a real pixi command and the
manifest on the right morphs to match. The final click swaps the
manifest for the actual run output.
-->

::right::

````md magic-move {at:1, lines: true}
```toml
[workspace]
channels = ["conda-forge"]
name = "demo"
platforms = ["osx-arm64"]
version = "0.1.0"

[tasks]

[dependencies]
```
```toml
[workspace]
channels = ["conda-forge"]
name = "demo"
platforms = ["osx-arm64"]
version = "0.1.0"

[tasks]

[dependencies]
python = ">=3.14.4,<3.15"
```
```toml
[workspace]
channels = ["conda-forge"]
name = "demo"
platforms = ["osx-arm64"]
version = "0.1.0"

[tasks]

[dependencies]
python = ">=3.14.4,<3.15"

[feature.test.dependencies]
pytest = "*"
```
```toml
[workspace]
channels = ["conda-forge"]
name = "demo"
platforms = ["osx-arm64"]
version = "0.1.0"

[tasks]

[dependencies]
python = ">=3.14.4,<3.15"

[feature.test.dependencies]
pytest = "*"

[environments]
test = ["test"]
```
```toml
[workspace]
channels = ["conda-forge"]
name = "demo"
platforms = ["osx-arm64"]
version = "0.1.0"

[tasks]
greet = "python -c 'print(\"hello, meetup\")'"

[dependencies]
python = ">=3.14.4,<3.15"

[feature.test.dependencies]
pytest = "*"

[environments]
test = ["test"]
```
```bash
$ pixi run greet
hello, meetup
```
```bash
$ pixi run -e test pytest --version
pytest 9.0.3
```
````

---
layout: center
<!--class: text-center-->
---

# Ready for some more?

---
layout: two-cols
---

# Global installations (`btop`)

<v-clicks at="1">

- One manifest, one isolated env per tool
- `pixi global install btop`, get its own env
- Trampoline in `~/.pixi/bin` (on `$PATH`)
- Let me show you

</v-clicks>

<br/>

<div v-click="1">

```toml
# ~/.pixi/manifests/pixi-global.toml
# .. other things
[envs.btop]
channels = ["conda-forge"]
dependencies = { btop = "*" }
exposed = { btop = "btop" }
```

</div>

::right::

<div v-click="3">

<FileTree
  rootLabel="~/.pixi/"
  :tree="[
    { name: 'bin', type: 'dir', comment: 'everything exposed sits here', children: [
      { name: 'btop', type: 'link'},
      { name: 'eza', type: 'link' },
      { name: 'jj', type: 'link' },
      { name: '…', type: 'link' },
    ]},
    { name: 'manifests', type: 'dir', children: [
      { name: 'pixi-global.toml', type: 'file', comment: 'contains your global env' },
    ]},
    { name: 'envs', type: 'dir', children: [
      { name: 'btop', type: 'dir', comment: 'isolated conda env', children: [
        { name: 'bin/btop', type: 'file' },
        { name: 'conda-meta', type: 'dir', children: [
          { name: 'btop-1.4.5-h49c215f_0.json', type: 'file' },
          { name: 'libcxx-22.1.3-h55c6f16_0.json', type: 'file' },
        ]},
        { name: 'lib/', type: 'dir' },
        { name: 'share/btop/themes/', type: 'dir' },
      ]},
      { name: 'eza', type: 'dir' },
      { name: 'jj', type: 'dir' },
    ]},
  ]"
/>

</div>

---

# `Pixi` with multiple languages.

<v-clicks>

- conda-forge has compilers for loads of languages: C++, Rust, R, Fortran etc.
- Normally conda-forge packages are binary.
- We have `pixi build`: *source directory* into a conda package
- One **backend** per language

</v-clicks>

<div v-click class="mt-4">
<img src="./assets/pixi-multilang-flow.svg" class="w-full" alt="pixi multi-language build flow" />
</div>

<!--
Source → conda package, language-specific backend, one lock.
Don't read the bullets; let them land. Pivot straight to the demo.
-->


---

# `Pixi` with Inko

---
layout: center
class: text-center
---

# Thanks.

[pixi.sh](https://pixi.sh) · [rattler-book](https://prefix-dev.github.io/rattler-book/) · [github.com/prefix-dev](https://github.com/prefix-dev)
