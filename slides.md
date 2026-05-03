---
# Tufte-inspired theme — extracted to ./slidev-theme-tufte
theme: ./slidev-theme-tufte
title: Introducing Pixi
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
highlighter: shiki
---

<div class="relative mx-auto w-64 mb-4">
  <img src="/paxton.png" class="w-full" alt="Paxton" />
</div>


# Introducing Pixi

## A Journey of Making a Package Manager in Rust

<div class="mt-28">
Tim de Jager at <img src="/prefix-logo.svg" class="inline align-middle h-5 mx-1" alt="prefix.dev" />
</div>


---

# Who am I?


<img src="/tim.jpeg" class="absolute right-24 top-24 w-44 rounded-full" alt="Tim" />
<div class="absolute right-12 bottom-24 w-72 h-44">
  <img v-click="[4, 5]" src="/reus.jpg" class="absolute inset-0 w-full h-full object-contain rounded shadow" alt="Reus" />
  <img v-click="[5, 6]" src="/smart-robotics.jpg" class="absolute inset-0 w-full h-full object-contain rounded shadow" alt="Smart Robotics" />
  <img v-click="[6, 7]" src="/prefix-logo.svg" class="absolute inset-0 w-full h-full object-contain" alt="prefix.dev" />
  <RiveAnimation v-click="7" src="/paxton_animation.riv" class="absolute inset-0 w-full h-full" />
</div>

<v-clicks depth="2">

- Tim de Jager, see: [github](https://github.com/tdejager)
- Developer at <img src="/prefix-logo.svg" class="inline align-middle h-5 mx-1" alt="prefix.dev" />
- Used to work at:
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

<v-clicks>

- Working on package managers is a great enabler
- Both algorithmic and more engineering problems
- People are generally quite grateful
- Active discord around ~250 members

</v-clicks>

<div class="testimonials absolute right-12 top-28 w-[28rem] flex flex-col gap-3">

  <a v-click="5" href="https://github.com/prefix-dev/pixi/issues/1128" class="testimonial">
    <img src="https://avatars.githubusercontent.com/u/22605641?v=4" alt="Ben-Epstein" />
    <div class="body">
      <p>"Thanks for the awesome package and work! I'd love for pixi to become my go-to package manager, the python ecosystem really needs it."</p>
      <footer>— <strong>Ben-Epstein</strong> · <span>#1128</span></footer>
    </div>
  </a>

  <a v-click="6" href="https://github.com/prefix-dev/pixi/issues/3457" class="testimonial">
    <img src="https://avatars.githubusercontent.com/u/381141?v=4" alt="tringenbach" />
    <div class="body">
      <p>"I really like how pixi follows what I think of as the nodejs / <code>node_modules</code> pattern. I run <code>pixi install</code> and, thanks to the lock file, I get exactly what every other developer using pixi gets."</p>
      <footer>— <strong>tringenbach</strong> · <span>#3457</span></footer>
    </div>
  </a>

  <a v-click="7" href="https://github.com/prefix-dev/pixi/issues/5230" class="testimonial">
    <img src="https://avatars.githubusercontent.com/u/67614381?v=4" alt="garylvov" />
    <div class="body">
      <p>"I'm looking forward to using Pixi this New Year! As always, I've been enjoying using Pixi on my project."</p>
      <footer>— <strong>garylvov</strong> · <span>#5230</span></footer>
    </div>
  </a>

</div>

<style scoped>
.testimonials .testimonial {
  display: flex;
  gap: 0.7rem;
  align-items: flex-start;
  padding: 0.7rem 0.8rem;
  background: var(--tufte-bg);
  border: 1px solid var(--tufte-rule);
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08), 0 1px 2px rgba(0, 0, 0, 0.06);
  text-decoration: none !important;
  color: inherit;
  border-bottom: 1px solid var(--tufte-rule) !important;
  transition: transform 200ms ease, box-shadow 200ms ease;
}
.testimonials .testimonial:hover {
  transform: translateY(-1px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.08);
  border-bottom-color: var(--tufte-accent) !important;
}
.testimonials .testimonial img {
  width: 2.6rem;
  height: 2.6rem;
  border-radius: 50%;
  flex-shrink: 0;
  object-fit: cover;
  border: 1px solid rgba(0, 0, 0, 0.08);
}
.testimonials .testimonial .body { flex: 1; }
.testimonials .testimonial p {
  font-style: italic;
  font-size: 0.78rem;
  line-height: 1.35;
  color: var(--tufte-text);
  margin: 0;
}
.testimonials .testimonial p code {
  font-style: normal;
  font-family: var(--tufte-mono) !important;
  font-size: 0.85em !important;
}
.testimonials .testimonial footer {
  font-size: 0.7rem;
  color: var(--tufte-muted);
  margin-top: 0.25rem;
  font-style: normal;
}
.testimonials .testimonial footer strong {
  font-weight: 400;
  font-style: italic;
  color: var(--tufte-text);
}
.testimonials .testimonial footer span {
  font-family: var(--tufte-mono);
  font-size: 0.9em;
}
</style>

---

# So what is Pixi?!

<img src="/paxton.png" class="absolute right-12 w-64" alt="Paxton" />

### Open Source on Github: https://github.com/prefix-dev/pixi (7k)
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

</v-clicks>

<div v-click="6">

## I'll explain more of this in depth

</div>

---

# Philosophy of Pixi

<v-clicks>

- Pixi values:
  - Fast.
  - User Friendly.
  - Isolated Environments.
  - Single tool.
  - Fun.
- First class windows support
- `pixi run start` should be all you need

</v-clicks>


<!--
Pain-point opener. Concrete: we built robots, the deploy story was a mess.
-->

---
layout: two-cols
---

# Who's using `pixi`?

### Some repositories on GitHub with a `pixi.toml`

<div class="users-grid" :class="`clicks-${Math.min($clicks, 6)}`">

| stars | repository | how they use it |
|------:|:-----------|:-----------|
| **73k** | [python/cpython](https://github.com/python/cpython/tree/main/Tools/pixi-packages) | Build Environment for compiling CPython |
| **32k** | [numpy/numpy](https://github.com/numpy/numpy) | Dev environment for Contributors |
| **31k** | [FreeCAD/FreeCAD](https://github.com/FreeCAD/FreeCAD) | 5-platform C++/Python build & task runner |
| **26k** | [modular/modular](https://github.com/modular/modular) | recommended way to install MAX & Mojo |
| **5.4k** | [ros2/ros2](https://github.com/ros2/ros2) | windows installation, partial linux |
| **3.2k** | [NVIDIA/cuda-python](https://github.com/NVIDIA/cuda-python) | monorepo runner with CUDA 12 / 13 envs |

</div>

<style scoped>
.users-grid table {
  margin-top: 0.6rem;
  font-size: 0.95rem;
}
.users-grid th { font-weight: 400; font-style: italic; }
/* Each tbody row stays in the layout but starts muted, then brightens
 * cumulatively as its matching logo appears (clicks 1–5). */
.users-grid tbody tr {
  color: var(--tufte-muted);
  opacity: 0.4;
  transition: opacity 250ms ease, color 250ms ease;
}
.users-grid tbody tr a { color: inherit; }
.users-grid.clicks-1 tbody tr:nth-child(-n+1),
.users-grid.clicks-2 tbody tr:nth-child(-n+2),
.users-grid.clicks-3 tbody tr:nth-child(-n+3),
.users-grid.clicks-4 tbody tr:nth-child(-n+4),
.users-grid.clicks-5 tbody tr:nth-child(-n+5),
.users-grid.clicks-6 tbody tr:nth-child(-n+6) {
  color: var(--tufte-text);
  opacity: 1;
}
.logo-cloud {
  position: relative;
  width: 100%;
  height: 100%;
}
.logo-cloud img {
  position: absolute;
  object-fit: contain;
  filter: drop-shadow(0 2px 6px rgba(0, 0, 0, 0.12));
}
.logo-cloud .l-python  { top: 4%;  left: 18%; width: 28%; transform: rotate(-6deg); }
.logo-cloud .l-numpy   { top: 10%; right: 4%; width: 34%; transform: rotate(4deg); }
.logo-cloud .l-freecad { top: 36%; left: 4%;  width: 26%; transform: rotate(8deg); }
.logo-cloud .l-modular { top: 40%; right: 18%; width: 20%; transform: rotate(-3deg); }
.logo-cloud .l-nvidia  { bottom: 18%; left: 26%; width: 32%; transform: rotate(2deg); }
.logo-cloud .l-ros2    { bottom: 4%;  right: 6%; width: 32%; transform: rotate(-4deg); }
</style>

::right::

<div class="logo-cloud">
  <img v-click="1" src="/logos/python.svg"  class="l-python"  alt="Python" />
  <img v-click="2" src="/logos/numpy.svg"   class="l-numpy"   alt="NumPy" />
  <img v-click="3" src="/logos/freecad.svg" class="l-freecad" alt="FreeCAD" />
  <img v-click="4" src="/logos/modular.svg" class="l-modular" alt="Modular" />
  <img v-click="5" src="/logos/ros2.svg"    class="l-ros2"    alt="ROS 2" />
  <img v-click="6" src="/logos/nvidia.svg"  class="l-nvidia"  alt="NVIDIA" />
</div>

<!--
Counts pulled from a github code-search for `filename:pixi.toml`,
deduped to ~500 repos, then queried via GraphQL for stargazerCount and
sorted. Skipped prefix-dev/pixi itself and pixi-adjacent tooling.
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

<RecipeCard v-click="1" side="left" side-offset="30%" top="4%" width="60%" font-size="0.7rem">

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

</RecipeCard>

</div>

<style>
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

# A `pixi.toml`: basics

<br/>

<v-clicks at="1">

1. *`pixi`*` add python`
2. *`pixi`*` add --feature test pytest`
3. *`pixi`*` project environment add test --feature test`
4. *`pixi`*` task add greet '...'`
5. *`pixi`*` run greet` 
6. *`pixi`*` run -e test pytest`

</v-clicks>

<!--
One slide, six clicks. Each click runs a real pixi command and the
manifest on the right morphs to match. The seventh click swaps the
manifest for the file tree showing the two isolated environments pixi
materialised on disk.
-->

::right::

<div v-click.hide="7">

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

</div>

<div class="env-stack">

<div v-click="[7, 8]" class="env-layer">

<FileTree
  rootLabel=".pixi/envs/"
  :tree="[
    { name: 'default', type: 'dir', comment: '`pixi run`', children: [
      { name: 'bin', type: 'dir', children: [
        { name: 'python', type: 'file' },
        { name: 'pip', type: 'file' },
      ]},
      { name: 'conda-meta', type: 'dir', children: [
        { name: 'python-3.14.4-h0_0.json', type: 'file' },
      ]},
      { name: 'lib/python3.14/site-packages/', type: 'dir' },
      { name: 'include/', type: 'dir' },
      { name: 'share/', type: 'dir' },
    ]},
    { name: 'test', type: 'dir', comment: '`pixi run -e test`', children: [
      { name: 'bin', type: 'dir', children: [
        { name: 'python', type: 'file' },
        { name: 'pytest', type: 'file' },
        { name: 'pip', type: 'file' },
      ]},
      { name: 'conda-meta', type: 'dir', children: [
        { name: 'python-3.14.4-h0_0.json', type: 'file' },
        { name: 'pytest-9.0.3-py_0.json', type: 'file' },
      ]},
      { name: 'lib/python3.14/site-packages/', type: 'dir', comment: 'pytest, _pytest, …' },
      { name: 'include/', type: 'dir' },
      { name: 'share/', type: 'dir' },
    ]},
  ]"
/>

</div>

<div v-click="8" class="env-layer">

<img src="./assets/pixi-env-reflinks.svg" class="w-full" alt="pixi envs reflinking from the global package cache" />

</div>

</div>

<style scoped>
.env-stack {
  position: relative;
}
.env-layer {
  position: absolute;
  inset: 0;
}
</style>


<style>
/* Disable the theme's slide-scoped overflow scroll for this one slide so
 * the rotated recipe card can extend past the SVG without being clipped. */
.slidev-layout {
  overflow: visible !important;
}
</style>


---
layout: center
<!--class: text-center-->
---

# Some more demo's

---

# Demo: "Works on my Machine"

<div class="womm-cap mt-2">one HTTPS request:</div>

```rust {lines:true}
fn main() -> Result<(), Box<dyn std::error::Error>> {
    let zen = reqwest::blocking::get("https://api.github.com/zen")?
        .error_for_status()?
        .text()?;
    println!("GitHub zen: {}", zen.trim());
    Ok(())
}
```

<div v-click="1" class="womm-cap mt-3">build it the obvious way:</div>

<div v-click="1">

```sh
$ cargo build
```

</div>

<div v-click="2" class="womm-punchline mt-3">
…this should just work, right?
</div>

<style scoped>
.womm-cap {
  font-family: var(--tufte-serif);
  font-style: italic;
  font-size: 0.85rem;
  color: var(--tufte-muted, #888);
}
.womm-punchline {
  font-family: var(--tufte-serif);
  font-style: italic;
  font-size: 1.1rem;
  color: var(--tufte-accent, #c14a26);
}
</style>

<!--
Don't read the slide. Run cargo build in a fresh rust:1.93-slim, watch
openssl-sys explode, then `pixi run build` and watch it pass. The
punchline is delivered by the terminal, not the markdown.
-->

---
layout: two-cols
---

# Demo: Global installations (`btop`)

<v-clicks at="1">

- One manifest, one isolated env per tool
- `pixi global install btop`, get its own env
- Trampoline in `~/.pixi/bin` (on `$PATH`)

</v-clicks>

<br/>

<div v-click="1">

```toml {lines: true}
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

# Demo: `Pixi` as a Polyglot

<v-clicks>

- conda-forge has: C++, Rust, R, Fortran etc. compilers
- Normally conda packages are binary.
- We have `pixi build`: *source directory* into a conda package
- **backend** per language

</v-clicks>


<div v-click class="mt-4">
<img src="./assets/pixi-multilang-flow.svg" class="w-full" alt="pixi multi-language build flow" />
</div>

<!--
Source → conda package, language-specific backend, one lock.
Don't read the bullets; let them land. Pivot straight to the demo.
-->


---

# Demo: `Pixi` with Inko 


<v-clicks>

- Try pixi and <img src="/inko-logo.png" class="inline align-middle h-5 mx-1" alt="Inko" />
- Put inko to conda-forge: https://github.com/conda-forge/inko-feedstock
- Allows you to manage Inko compiler with Pixi

</v-clicks>

<img v-click="[2, 4]" src="/inko.png" class="absolute right-12 bottom-16 w-128 rounded shadow" alt="Inko screenshot" />

<RecipeCard v-click="4" side="right" class="inko-recipe">

```yaml
# inko-feedstock recipe.yaml
context:
  version: "0.20.0"

package:
  name: inko
  version: ${{ version }}

source:
  url: https://github.com/inko-lang/inko/archive/refs/tags/v${{ version }}.tar.gz
  sha256: 19cef883…

build:
  number: 0
  skip: win
  script:
    interpreter: nu
    content: |
      cargo auditable build --release --locked
      cp $"target/release/inko" $"($env.PREFIX)/bin/inko"

requirements:
  build:
    - ${{ compiler('c') }}
    - ${{ compiler('rust') }}
    - cargo-auditable
    - nushell
  host:
    - llvmdev 18.1.*
    - zlib
    - libxml2-devel
    - libffi
```

</RecipeCard>

<style>
.slidev-layout:has(.inko-recipe) {
  overflow: visible !important;
}
</style>


---

# How did we get here?

<div v-click="[1, 5]" class="absolute right-12 top-24 w-100 grid grid-cols-2 gap-3">
  <img src="/smart-robotics.jpg" class="w-full h-44 object-cover rounded shadow" alt="Smart Robotics palletising robot" />
  <img src="/smart-robotics-pick-place.jpg" class="w-full h-44 object-cover rounded shadow" alt="Smart Robotics pick-and-place robot" />
</div>

<v-clicks at="1">

- Working at Smart Robotics
- ROS1 Installations
- Coupled to Ubuntu versions
- This poses problems:

</v-clicks>

<PainPoint v-click="6" class="pain-1">
  We could not debug older machines when switching to a new Ubuntu.
</PainPoint>
<PainPoint v-click="7" class="pain-2">
  I could not work together with other developers using a different Ubuntu.
</PainPoint>

<img v-click="5" src="/logos/paxton-frying-pan.svg" class="absolute paxton-frying-pan" alt="Paxton with a frying pan" />

<style scoped>
/* Playful arrangement: each pain note pinned at a slight tilt, like
 * post-its dropped onto the slide; Paxton angled in the bottom-right
 * holding the pan up toward them. */
.pain-1 {
  position: absolute;
  right: 4rem;
  top: 5.5rem;
  transform: rotate(-3deg);
  z-index: 2;
}
.pain-2 {
  position: absolute;
  right: 0.5rem;
  top: 17rem;
  transform: rotate(2.5deg);
  z-index: 2;
}
.paxton-frying-pan {
  width: 16rem;
  bottom: 1rem;
  right: 15rem;
  transform: scale(120%) scaleX(-1) rotate(-7deg);
  filter: drop-shadow(0 4px 8px rgba(0, 0, 0, 0.15));
  z-index: 1;
}
</style>

---

# Found Conda & Mamba

<div class="grid grid-cols-12 gap-6 mt-2">

<div class="col-span-7">

<v-clicks>

- Conda packages are nice,
- Superior to Docker for local development,
- Robostack is distroless ROS (finally!),
- Micromamba, is a Conda rewrite. Written by [Wolf](https://github.com/wolfv)

</v-clicks>

</div>

<div class="col-span-5 logo-col relative">

<div v-click="1" class="logo-pair conda-pair">
  <img src="/logos/conda-mark.png" alt="conda" class="logo-main conda-mark" />
  <img src="/logos/python.svg" alt="python" class="sticker python-sticker" />
</div>

<div v-click="3" class="logo-pair robostack-row">
  <img src="/logos/robostack.png" alt="robostack" class="logo-main robostack-mark" />
</div>

<div v-click="4" class="race">
  <div class="racer racer-conda">
    <img src="/logos/conda-mark.png" alt="conda" class="logo-mini" />
    <span class="speed-label slow">slow…</span>
  </div>
  <div class="racer racer-mamba">
    <img src="/logos/mamba.png" alt="micromamba" class="logo-mamba" />
    <img src="/logos/cpp.svg" alt="C++" class="sticker cpp-sticker" />
    <span class="speed-label fast">fast!</span>
  </div>
</div>

</div>

</div>

<style scoped>
.logo-col { min-height: 22rem; }
.logo-pair { position: absolute; display: inline-flex; align-items: center; }
.logo-main { width: 7rem; height: auto; filter: drop-shadow(0 3px 6px rgba(0,0,0,0.18)); }
.sticker {
  position: absolute;
  width: 2.4rem;
  height: 2.4rem;
  background: #fffff8;
  border-radius: 50%;
  padding: 0.25rem;
  box-shadow: 0 2px 4px rgba(0,0,0,0.18);
}

.conda-pair { top: 0.2rem; right: 6.5rem; transform: rotate(-4deg); }
.conda-pair .python-sticker { right: -1rem; bottom: -0.6rem; transform: rotate(8deg); }

.robostack-row { top: 7.5rem; right: 1.5rem; transform: rotate(5deg); }
.robostack-row .robostack-mark { width: 6rem; border-radius: 12px; }

.race {
  position: absolute;
  bottom: 0.5rem;
  left: 0;
  right: 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  padding: 0 0.5rem;
}
.racer { position: relative; display: flex; flex-direction: column; align-items: center; }
.logo-mini { width: 4.5rem; height: auto; filter: drop-shadow(0 2px 4px rgba(0,0,0,0.18)); }
.logo-mamba { width: 9rem; height: auto; filter: drop-shadow(0 3px 6px rgba(0,0,0,0.2)); }

.racer-mamba .cpp-sticker { position: absolute; right: -0.2rem; top: -0.6rem; transform: rotate(10deg); }

.speed-label {
  font-family: var(--tufte-serif);
  font-style: italic;
  font-size: 0.85rem;
  margin-top: 0.25rem;
}
.speed-label.slow { color: var(--tufte-muted, #888); }
.speed-label.fast { color: var(--tufte-accent, #c14a26); font-weight: 700; }

.racer-conda .logo-mini {
  animation: conda-crawl 3.2s ease-in-out infinite;
  filter: drop-shadow(0 2px 4px rgba(0,0,0,0.18)) grayscale(0.2);
  opacity: 0.85;
}
@keyframes conda-crawl {
  0%, 100% { transform: translateX(0) rotate(-2deg); }
  50%      { transform: translateX(0.6rem) rotate(2deg); }
}

.racer-mamba { animation: mamba-zoom 0.55s cubic-bezier(0.2, 0.9, 0.3, 1.4) both; }
@keyframes mamba-zoom {
  0%   { transform: translateX(-3rem) scale(0.6); opacity: 0; }
  60%  { transform: translateX(0.4rem) scale(1.08); opacity: 1; }
  100% { transform: translateX(0) scale(1); opacity: 1; }
}
.racer-mamba::before {
  content: '';
  position: absolute;
  left: -2.4rem;
  top: 45%;
  width: 2.2rem;
  height: 2px;
  background: linear-gradient(to right, transparent, var(--tufte-accent, #c14a26));
  border-radius: 2px;
  opacity: 0.7;
  box-shadow:
    0 -0.45rem 0 -0.5px var(--tufte-accent, #c14a26),
    0  0.45rem 0 -0.5px var(--tufte-accent, #c14a26);
}
</style>

---

# Conda Workflow is Strange
**at least for `cargo`, `npm`, etc. users**

<div class="grid grid-cols-2 gap-8 mt-4">

<div>

<v-clicks at="1">

- Has the concept of `base` and `global` environments
- "base" is always activated :(

</v-clicks>
<br />
<v-clicks at="3">

- `conda activate my-env`
- `conda install foo` &#8594; into an env
- No lock file &ne; No Reproducibility per Project

</v-clicks>

</div>

<div v-click="1">

<FileTree
  rootLabel="~/miniconda3/"
  :tree="[
    { name: 'envs', type: 'dir', comment: 'all your envs live here, globally', children: [
      { name: 'base', type: 'dir', comment: 'always active' },
      { name: 'ml-project', type: 'dir', comment: 'must remember `conda activate`' },
      { name: 'tutorial', type: 'dir' },
      { name: 'data-cleanup', type: 'dir' },
    ]},
    { name: 'pkgs', type: 'dir', comment: 'global package cache' },
  ]"
/>

<div v-click="6" class="conda-shell mt-6">
<pre><span class="prompt">(base) $</span> cd ml-project
<span class="prompt">(base) $</span> <span class="cmd">conda activate ml-project</span>
<span class="prompt">(ml-project) $</span> <span class="cmd">conda install r</span>
<span class="prompt">(ml-project) $</span> r calc.r
<span class="prompt">(ml-project) $</span> <span class="cmd">deactivate </span>
<span class="prompt">(base) $</span> r hi.r    <span class="oops"># oops no R installed!</span></pre>
</div>

</div>

</div>

<style scoped>
.conda-shell pre {
  font-family: var(--tufte-mono);
  font-size: 0.7rem;
  line-height: 1.5;
  background: transparent;
  padding: 0;
  margin: 0;
  white-space: pre;
}
.conda-shell .prompt { color: var(--tufte-muted); }
.conda-shell .cmd    { color: var(--tufte-text); font-weight: 500; }
.conda-shell .oops   { color: var(--tufte-accent); font-style: italic; }
</style>

---

# Wished for Something Better

<div class="grid grid-cols-[1fr_auto] gap-8 items-center">
<div>

<v-clicks>

- We ❤️ `cargo` and Rust,
- Wolf asked us to join prefix (was being funded),
- Wolf wanted to use C++ for the next thing, 
- but we were 3 people, 
- and two of us voted for Rust!
- **So let's rewrite it in Rust**

</v-clicks>

</div>
<div v-click="5" class="text-center relative w-64 mx-auto">
  <img src="https://rustacean.net/assets/rustacean-flat-happy.svg" class="w-64" alt="Ferris" />
  <div class="absolute text-6xl" style="top: 30%; left: 8%; transform: rotate(-20deg);">🏆</div>
</div>
</div>

---

# What did we Need, 
### &nbsp;&nbsp;&nbsp;&nbsp; and what did we end up with

<div class="grid grid-cols-2 gap-8 mt-4">

<div>

<v-clicks>

- Isolated Environments.
- Ease of Use.
- Fast.
- Tries to Always keep Environment up-to-date.

</v-clicks>

</div>

<div class="needs-panels relative">

<div v-click="[1, 2]" class="panel">
<div class="caption">an isolated env, scoped to the project</div>
<FileTree
  rootLabel="my-project/"
  :tree="[
    { name: 'pixi.toml', type: 'file' },
    { name: 'pixi.lock', type: 'file' },
    { name: 'src', type: 'dir' },
    { name: '.pixi', type: 'dir', comment: 'lives next to your code', children: [
      { name: 'envs', type: 'dir', children: [
        { name: 'default', type: 'dir', children: [
          { name: 'bin', type: 'dir' },
          { name: 'lib', type: 'dir' },
          { name: 'conda-meta', type: 'dir' },
        ]},
        { name: 'test', type: 'dir', comment: 'feature-based, on demand' },
      ]},
    ]},
  ]"
/>
</div>

<div v-click="[2, 3]" class="panel">
<div class="caption">just a few commands cover the common cases</div>

```bash
$ pixi init my-project        # new workspace
$ pixi add python pytest      # add deps
$ pixi add --pypi httpx       # pypi works too
$ pixi run test               # run a task
$ pixi shell                  # activate env
$ pixi update                 # bump the lock
```

</div>

<div v-click="[3, 4]" class="panel">
<div class="caption later">i'll show this later…</div>
</div>

<div v-click="4" class="panel">

```toml {all|1-3|5-8|7|all}
[dependencies]
pnpm    = "*"
nodejs  = "*"

[tasks]
install = { cmd = "pnpm install --frozen-lockfile" }
dev     = { cmd = "pnpm exec slidev --open",
            # This forces an install first
            depends-on = ["install"] }
```

</div>

</div>

</div>

<style scoped>
.needs-panels { min-height: 22rem; }
.panel { position: absolute; inset: 0; }
.panel .caption {
  font-family: var(--tufte-serif);
  font-style: italic;
  font-size: 0.85rem;
  color: var(--tufte-muted, #888);
  margin-bottom: 0.6rem;
}
.panel .caption code {
  font-family: var(--tufte-mono);
  font-style: normal;
  font-size: 0.85em;
  background: rgba(193, 74, 38, 0.06);
  padding: 0 0.2em;
  border-radius: 2px;
}
.panel .caption.later {
  font-size: 1rem;
  color: var(--tufte-accent, #c14a26);
}
</style>

---

# Aside: Universal Package Manager Concepts


<div class="universals" :class="`step-${$clicks}`">

<v-clicks>

- **Versions**
  - npm, cargo: `1.2.3` (SemVer)
  - pip: PEP 440, e.g. `1.2.3rc1`
  - conda: own ordering, e.g. `1.2.3=py312_0`
- **Requirements**
  - npm: `^1.2.0`
  - pip: PEP 508, e.g. `requests>=2,<3`
  - cargo: `serde = "^1.0"`
  - conda: MatchSpec, e.g. `lua >=5.4`
- **Artifacts**
  - npm: `.tgz`
  - pip: `.whl` (or sdist)
  - cargo: `.crate`
  - conda: `.conda`, `.tar.bz2`
- **An index**
  - npm: `registry.npmjs.org`
  - pip: `pypi.org/simple/`
  - cargo: `index.crates.io`
  - conda: a channel, `repodata.json`

</v-clicks>

</div>

<div class="pkg-flow mt-3">

<svg viewBox="0 0 720 200" class="w-full" preserveAspectRatio="xMidYMid meet">

  <defs>
    <marker id="pkg-arrow" viewBox="0 0 10 10" refX="9" refY="5"
      markerWidth="9" markerHeight="9" orient="auto-start-reverse">
      <path d="M 0 0 L 10 5 L 0 10 z" fill="#c14a26" />
    </marker>
  </defs>

  <g v-click="6">
    <rect x="20"  y="36" width="200" height="80" rx="4" class="step-box" />
    <text x="120" y="82"  class="step-name">Discovery</text>
    <text x="120" y="102" class="step-role">"what exists?"</text>
  </g>

  <g v-click="7">
    <line x1="222" y1="76" x2="258" y2="76" class="flow-arrow" marker-end="url(#pkg-arrow)" />
    <rect x="260" y="36" width="200" height="80" rx="4" class="step-box" />
    <text x="360" y="82"  class="step-name">Solving</text>
    <text x="360" y="102" class="step-role">"which versions fit together?"</text>
  </g>

  <g v-click="8">
    <line x1="462" y1="76" x2="498" y2="76" class="flow-arrow" marker-end="url(#pkg-arrow)" />
    <rect x="500" y="36" width="200" height="80" rx="4" class="step-box" />
    <text x="600" y="82"  class="step-name">Installation</text>
    <text x="600" y="102" class="step-role">"get them onto disk"</text>
  </g>

</svg>

</div>

<style scoped>
.universals-caption {
  font-family: var(--tufte-serif);
  font-style: italic;
  font-size: 0.85rem;
  color: var(--tufte-muted, #888);
  margin-bottom: 0.4rem;
}
.universals :deep(> ul) {
  column-count: 2;
  column-gap: 2.5rem;
  font-size: 0.78rem;
  line-height: 1.3;
  margin-top: 0.2rem;
}
.universals :deep(> ul > li) {
  break-inside: avoid;
  margin-bottom: 0.35rem;
}
.universals :deep(ul ul) {
  font-size: 0.95em;
  line-height: 1.25;
  margin-top: 0.05rem;
  margin-bottom: 0.1rem;
}
.universals :deep(ul li) { margin-bottom: 0.05rem; }
.universals :deep(ul li > strong) { font-weight: 700; }
.universals :deep(code) {
  font-family: var(--tufte-mono, "IBM Plex Mono", Consolas, monospace);
  font-size: 0.92em;
  background: rgba(193, 74, 38, 0.06);
  padding: 0 0.18em;
  border-radius: 2px;
}

.universals :deep(> ul > li) {
  transition: opacity 250ms ease, color 250ms ease;
}
.universals.step-2 :deep(> ul > li:nth-child(1)),
.universals.step-3 :deep(> ul > li:nth-child(-n+2)),
.universals.step-4 :deep(> ul > li:nth-child(-n+3)),
.universals.step-5 :deep(> ul > li:nth-child(-n+4)),
.universals.step-6 :deep(> ul > li:nth-child(-n+4)),
.universals.step-7 :deep(> ul > li:nth-child(-n+4)),
.universals.step-8 :deep(> ul > li:nth-child(-n+4)) {
  opacity: 0.35;
}
.universals.step-2 :deep(> ul > li:nth-child(1)) :deep(code),
.universals.step-3 :deep(> ul > li:nth-child(-n+2)) :deep(code),
.universals.step-4 :deep(> ul > li:nth-child(-n+3)) :deep(code),
.universals.step-5 :deep(> ul > li:nth-child(-n+4)) :deep(code),
.universals.step-6 :deep(> ul > li:nth-child(-n+4)) :deep(code),
.universals.step-7 :deep(> ul > li:nth-child(-n+4)) :deep(code),
.universals.step-8 :deep(> ul > li:nth-child(-n+4)) :deep(code) {
  background: transparent;
}
.universals-foot {
  font-family: var(--tufte-serif);
  font-style: italic;
  font-size: 0.85rem;
  color: var(--tufte-accent, #c14a26);
  margin-top: 0.8rem;
}
.pkg-flow { display: flex; justify-content: center; }
.pkg-flow svg { font-family: var(--tufte-serif); max-width: 100%; max-height: 8.5rem; }
.pkg-flow .step-box {
  fill: #fffff8;
  stroke: #333;
  stroke-width: 1.4;
  filter: drop-shadow(0 2px 3px rgba(0,0,0,0.14));
}
.pkg-flow .step-num   { font: italic 14px "et-book", serif; fill: var(--tufte-accent, #c14a26); text-anchor: middle; }
.pkg-flow .step-name  { font: 22px "et-book", serif; fill: #111; font-weight: bold; text-anchor: middle; }
.pkg-flow .step-role  { font: italic 13px "et-book", serif; fill: #555; text-anchor: middle; }
.pkg-flow .crate      { font: 13px "IBM Plex Mono", Consolas, monospace; fill: var(--tufte-accent, #c14a26); text-anchor: middle; }
.pkg-flow .crate-sub  { font: italic 11.5px "et-book", serif; fill: #777; text-anchor: middle; }
.pkg-flow .flow-arrow { stroke: #c14a26; stroke-width: 1.6; fill: none; }
.pkg-flow .flow-title { font: italic 13px "et-book", serif; fill: #555; text-anchor: middle; }
.pkg-flow .flow-foot  { font: italic 13px "et-book", serif; fill: var(--tufte-accent, #c14a26); text-anchor: middle; }
.pkg-flow g.slidev-vclick-target { transition: opacity 350ms ease-out; }
.pkg-flow g.slidev-vclick-hidden { opacity: 0; }
</style>

---
# This is converting the ecosystem to rust
src: ./pages/converting-to-rust.md
---

---

# Resolvo, our SAT Solver

<div class="grid grid-cols-12 gap-6 mt-2 items-start">

<div class="col-span-7">

<v-clicks>

- A CDCL SAT solver, started as a port of `libsolv`.
- Made *generic*, so it knows nothing about conda, PyPI, RPM, etc.
- Already powering: `pixi` & `rattler` (conda), `resolvo-rpm` *experimental* (Fedora).
- Async, multithreaded, lazy: only fetches metadata it actually needs.
- Outputs *human-readable* error messages, not just "unsatisfiable".

</v-clicks>

</div>

<div class="col-span-5 flex justify-center">
  <img src="/logos/paxton-juggler.png" alt="resolvo" class="w-28 drop-shadow-md" />
</div>

</div>

<div class="grid grid-cols-12 gap-6 mt-2">

<div v-click="6" class="col-span-7 trait-snippet">

<div class="snippet-cap">the whole interface, in one trait</div>

```rust {all|2-5|7-9|11-13|all}
trait DependencyProvider: Interner {
  async fn get_candidates(&self, name: NameId)
    -> Option<Candidates>;

  async fn get_dependencies(&self, s: SolvableId)
    -> Dependencies;

  async fn filter_candidates(&self,
    cs: &[SolvableId], vs: VersionSetId,
    inverse: bool) -> Vec<SolvableId>;

  async fn sort_candidates(&self, ...);
}
```

</div>

<div v-click="7" class="col-span-5 conda-glue self-end">

<div class="snippet-cap">conda support is just an <code>impl</code> of that trait, in <code>rattler_solve</code>:</div>

```rust
impl DependencyProvider
  for CondaDependencyProvider<'_>
{ ... }

impl Interner
  for CondaDependencyProvider<'_>
{ ... }
```

</div>

</div>

<style scoped>
.trait-snippet :deep(pre), .conda-glue :deep(pre) {
  font-size: 0.72rem !important;
  line-height: 1.4 !important;
  margin: 0 !important;
}
.snippet-cap {
  font-family: var(--tufte-serif);
  font-style: italic;
  font-size: 0.78rem;
  color: var(--tufte-muted, #888);
  margin-bottom: 0.25rem;
}
.snippet-cap code {
  font-family: var(--tufte-mono);
  font-style: normal;
  font-size: 0.9em;
  background: rgba(193, 74, 38, 0.06);
  padding: 0 0.18em;
  border-radius: 2px;
}
</style>

---

# Rattler, Conda Primitives

<div class="grid grid-cols-12 gap-6 mt-2">

<div class="col-span-9">

<v-clicks>

- A *library*-first reimplementation of conda's primitives in Rust.
- Used by `pixi`, `prefix.dev`, `py-rattler` (Python bindings), `mise`, parts of `mamba`, and now `conda` itself (`conda --solver rattler`).
- Async I/O, Multithreaded

</v-clicks>

</div>

<div class="col-span-3 flex justify-center">
  <img src="/logos/paxton-rattler.png" alt="rattler" class="w-32 drop-shadow-md" />
</div>

</div>

<div v-click="4" class="rattler-map mt-2">

<svg viewBox="0 0 760 230" class="w-full" preserveAspectRatio="xMidYMid meet">
  <defs>
    <marker id="rt-arrow" viewBox="0 0 10 10" refX="9" refY="5"
      markerWidth="9" markerHeight="9" orient="auto-start-reverse">
      <path d="M 0 0 L 10 5 L 0 10 z" fill="#c14a26" />
    </marker>
  </defs>

  <!-- Foundation: conda_types, full width across the top -->
  <rect x="200" y="10" width="360" height="46" rx="4" class="rt-box rt-box--base" />
  <text x="380" y="32" class="rt-name">rattler_conda_types</text>
  <text x="380" y="48" class="rt-role">Version, MatchSpec, RepoData, NoArchType, …</text>

  <!-- Three middle crates -->
  <rect x="20"  y="100" width="220" height="54" rx="4" class="rt-box" />
  <text x="130" y="124" class="rt-name">rattler_repodata_gateway</text>
  <text x="130" y="142" class="rt-role">fetch &amp; parse the index</text>

  <rect x="270" y="100" width="220" height="54" rx="4" class="rt-box" />
  <text x="380" y="124" class="rt-name">rattler_solve</text>
  <text x="380" y="142" class="rt-role">resolvo glue for conda</text>

  <rect x="520" y="100" width="220" height="54" rx="4" class="rt-box" />
  <text x="630" y="124" class="rt-name">rattler_package_streaming</text>
  <text x="630" y="142" class="rt-role">read / write .conda archives</text>

  <!-- Top-level: rattler -->
  <rect x="270" y="184" width="220" height="40" rx="4" class="rt-box rt-box--top" />
  <text x="380" y="210" class="rt-name">rattler</text>

  <!-- Dotted lines from base down to the three middle crates -->
  <line x1="380" y1="56" x2="130" y2="100" class="rt-link rt-link--dotted" />
  <line x1="380" y1="56" x2="380" y2="100" class="rt-link rt-link--dotted" />
  <line x1="380" y1="56" x2="630" y2="100" class="rt-link rt-link--dotted" />

  <!-- Solid arrows from middle crates into rattler -->
  <line x1="130" y1="154" x2="320" y2="184" class="rt-link" marker-end="url(#rt-arrow)" />
  <line x1="380" y1="154" x2="380" y2="184" class="rt-link" marker-end="url(#rt-arrow)" />
  <line x1="630" y1="154" x2="440" y2="184" class="rt-link" marker-end="url(#rt-arrow)" />

  <text x="380" y="76" class="rt-caption">shared types</text>
</svg>

</div>

<div v-click="5" class="rattler-foot mt-2">
…and a dozen more (cache, networking, shell, lock, index, menuinst, …): pick what you need.
</div>

<style scoped>
.rattler-map svg { font-family: var(--tufte-serif); max-width: 100%; max-height: 11rem; }
.rattler-map .rt-box {
  fill: #fffff8;
  stroke: #333;
  stroke-width: 1.4;
  filter: drop-shadow(0 2px 3px rgba(0,0,0,0.14));
}
.rattler-map .rt-box--base { stroke: #888; }
.rattler-map .rt-box--top  { stroke: #c14a26; }
.rattler-map .rt-name {
  font: 13px "IBM Plex Mono", Consolas, monospace;
  fill: var(--tufte-accent, #c14a26);
  text-anchor: middle;
}
.rattler-map .rt-role {
  font: italic 11px "et-book", serif;
  fill: #555;
  text-anchor: middle;
}
.rattler-map .rt-caption {
  font: italic 10.5px "et-book", serif;
  fill: #888;
  text-anchor: middle;
}
.rattler-map .rt-link {
  stroke: #c14a26;
  stroke-width: 1.4;
  fill: none;
}
.rattler-map .rt-link--dotted {
  stroke: #888;
  stroke-width: 1;
  stroke-dasharray: 3 2;
}
.rattler-foot {
  font-family: var(--tufte-serif);
  font-style: italic;
  font-size: 0.85rem;
  color: var(--tufte-accent, #c14a26);
  text-align: center;
}
.snippet-cap {
  font-family: var(--tufte-serif);
  font-style: italic;
  font-size: 0.78rem;
  color: var(--tufte-muted, #888);
  margin-bottom: 0.25rem;
}
</style>

---

# Rattler-Build, the Package Builder

<div class="grid grid-cols-12 gap-6 mt-2">

<div class="col-span-9">

<v-clicks>

- A from-scratch replacement for `conda-build`, written in Rust.
- Standalone binary, *no Python in the build pipeline*.
- New, stricter `recipe.yaml` schema (CEP-13/14), Jinja-templated.
- Cross-platform: Linux, macOS, Windows; reproducible-ish.
- Already used to build many `conda-forge` packages.

</v-clicks>

</div>

<div class="col-span-3 flex justify-center">
  <img src="/logos/paxton-builder.png" alt="rattler-build" class="w-32 drop-shadow-md" />
</div>

</div>

<div v-click="6" class="rb-flow mt-2">

<svg viewBox="0 0 760 110" class="w-full" preserveAspectRatio="xMidYMid meet">
  <defs>
    <marker id="rb-arrow" viewBox="0 0 10 10" refX="9" refY="5"
      markerWidth="9" markerHeight="9" orient="auto-start-reverse">
      <path d="M 0 0 L 10 5 L 0 10 z" fill="#c14a26" />
    </marker>
  </defs>

  <rect x="10"  y="20" width="150" height="60" rx="4" class="rb-box" />
  <text x="85"  y="48" class="rb-name">recipe.yaml</text>
  <text x="85"  y="66" class="rb-role">+ Jinja vars</text>
  <line x1="162" y1="50" x2="198" y2="50" class="rb-arrow" marker-end="url(#rb-arrow)" />

  <rect x="200" y="20" width="170" height="60" rx="4" class="rb-box" />
  <text x="285" y="44" class="rb-name">build env</text>
  <text x="285" y="62" class="rb-role">solve, fetch, link</text>
  <text x="285" y="76" class="rb-role">(uses rattler)</text>
  <line x1="372" y1="50" x2="408" y2="50" class="rb-arrow" marker-end="url(#rb-arrow)" />

  <rect x="410" y="20" width="170" height="60" rx="4" class="rb-box" />
  <text x="495" y="44" class="rb-name">run script</text>
  <text x="495" y="62" class="rb-role">capture file list</text>
  <text x="495" y="76" class="rb-role">+ patch prefixes</text>
  <line x1="582" y1="50" x2="618" y2="50" class="rb-arrow" marker-end="url(#rb-arrow)" />

  <rect x="620" y="20" width="130" height="60" rx="4" class="rb-box rb-box--out" />
  <text x="685" y="48" class="rb-name">.conda</text>
  <text x="685" y="66" class="rb-role">archive</text>
</svg>

</div>

<style scoped>
.rb-flow svg { font-family: var(--tufte-serif); max-width: 100%; max-height: 7rem; }
.rb-box      { fill: #fffff8; stroke: #333; stroke-width: 1.4; filter: drop-shadow(0 2px 3px rgba(0,0,0,0.14)); }
.rb-box--out { stroke: #c14a26; }
.rb-name     { font: 16px "et-book", serif; font-weight: bold; fill: #111; text-anchor: middle; }
.rb-role     { font: italic 11px "et-book", serif; fill: #555; text-anchor: middle; }
.rb-arrow    { stroke: #c14a26; stroke-width: 1.6; fill: none; }
</style>

---
layout: center
class: text-center
---

# What were Things we did Right

<div class="text-left">
<v-clicks>

- Directly made `Rattler` into a library,
- Started dogfooding `Rattler` with `Prefix.dev`,
- We invested into making our own solver,
- We had a project `rip` which we ditched for `uv`

</v-clicks>
</div>

<div v-click="5" class="absolute right-24 bottom-24 w-48 h-48 rounded-full overflow-hidden border-2 border-[var(--tufte-rule)] shadow-lg flex items-center justify-center bg-white">
  <img src="/tombstone.png" class="w-full h-full object-cover" alt="rip tombstone" />
</div>

---

# What were Things we could've done Better,

<div class="grid grid-cols-12 gap-6 mt-2">

<div class="col-span-6">

<v-clicks>

- We did not split pixi into crates directly,
- We did not invest *enough* into faster CI,
  - Offline tests
  - Mock Registries (conda and PyPI)
- We started on the *build feature* late in the process,
- We still find it really hard to juggle features v.s. issues

</v-clicks>

</div>

<div class="col-span-6 mock-panels relative">

<div v-click="4" class="mock-panel">

```rust
use pixi_test_utils::{MockRepoData, Package};

let mut db = MockRepoData::default();
// Add test packages
db.add_package(Package::build("b", "1").finish());
db.add_package(
    Package::build("a", "1")
        .with_dependency("b >=1")
        .finish(),
);

// Write to a file
let channel = db.into_channel().await?;
```

</div>

<div v-click="4" class="mock-panel mock-panel--pypi">
<hr />

```rust
use crate::common::pypi_index::{Database, PyPIPackage};

let index = Database::new()
    .with(PyPIPackage::new("httpx", "0.27.0"))
    // Ooh, that's rich!
    .with(
        PyPIPackage::new("rich", "13.0.0")
            .with_requires_dist(["pygments >=2.13"]),
    )
    // This writes index into a file
    .into_simple_index()?;
```

</div>

</div>

</div>

<style scoped>
.mock-panels { min-height: 22rem; }
.mock-panel {
  margin-bottom: 0.6rem;
  transition: opacity 250ms ease;
}
.mock-caption {
  font-family: var(--tufte-serif);
  font-style: italic;
  font-size: 0.78rem;
  color: var(--tufte-muted, #888);
  margin-bottom: 0.25rem;
}
.mock-panel :deep(pre) {
  font-size: 0.7rem !important;
  line-height: 1.35 !important;
  margin: 0 !important;
}
</style>


---
layout: center
class: text-center
---

# Thanks For Listening
### Feel Free to ask me Anything

<div class="grid mt-10 grid-cols-2 gap-x-8 gap-y-6 my-6 justify-items-center">
  <a href="https://github.com/prefix-dev/pixi"><img src="/logos/pixi-banner.png" alt="pixi" class="max-h-30 object-contain drop-shadow-md" /></a>
  <a href="https://github.com/conda/rattler"><img src="/logos/rattler-banner.webp" alt="rattler" class="max-h-30 object-contain drop-shadow-md" /></a>
  <a href="https://github.com/prefix-dev/rattler-build"><img src="/logos/rattler-build-banner.webp" alt="rattler-build" class="max-h-30 object-contain drop-shadow-md" /></a>
  <a href="https://github.com/prefix-dev/resolvo"><img src="/logos/resolvo-banner.webp" alt="resolvo" class="max-h-30 object-contain drop-shadow-md" /></a>
</div>
