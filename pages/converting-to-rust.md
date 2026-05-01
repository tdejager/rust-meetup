# Converting (all the Python) to Rust

<div class="absolute left-12 right-12 bottom-12 top-32">
<svg viewBox="0 0 1200 540" class="w-full h-full tree">

  <!-- 1. rattler — top centre, with snake-charmer Paxton on the left -->
  <g v-click="1">
    <image href="/logos/paxton-rattler.png" x="340" y="20" width="140" height="160" preserveAspectRatio="xMidYMid meet" />
    <rect x="490" y="40" width="220" height="120" rx="4" class="box" />
    <text x="600" y="78" class="name">Rattler</text>
    <text x="600" y="102" class="role">conda primitives</text>
    <text x="600" y="120" class="role">parse, solve, install etc.</text>
    <text x="600" y="146" class="when">Nov 2021</text>
  </g>

  <!-- 2. rattler-build — Sep 2022, lower-left child, with builder Paxton -->
  <g v-click="2">
    <path d="M 540 160 C 540 280 350 280 350 360" class="link" fill="none" />
    <image href="/logos/paxton-builder.png" x="80" y="350" width="150" height="150" preserveAspectRatio="xMidYMid meet" />
    <rect x="240" y="360" width="220" height="120" rx="4" class="box" />
    <text x="350" y="398" class="name">Rattler-build</text>
    <text x="350" y="422" class="role">from recipe into .conda</text>
    <text x="350" y="440" class="role">conda-build replacement</text>
    <text x="350" y="466" class="when">Sep 2022</text>
  </g>

  <!-- 3. pixi — Apr 2023, lower-right child, with wand Paxton (existing) -->
  <g v-click="3">
    <path d="M 660 160 C 660 280 850 280 850 360" class="link" fill="none" />
    <rect x="740" y="360" width="220" height="120" rx="4" class="box" />
    <text x="850" y="398" class="name">pixi</text>
    <text x="850" y="422" class="role">Package Manager</text>
    <text x="850" y="440" class="role">Install, Tasks, Build</text>
    <text x="850" y="466" class="when">Apr 2023</text>
    <image href="/paxton.png" x="980" y="350" width="150" height="150" preserveAspectRatio="xMidYMid meet" />
  </g>

  <!-- 4. resolvo — Jul 2023, satellite to the right of rattler, with juggler Paxton -->
  <g v-click="4">
    <line x1="710" y1="100" x2="840" y2="100" class="link" />
    <rect x="840" y="40" width="220" height="120" rx="4" class="box" />
    <text x="950" y="78" class="name">resolvo</text>
    <text x="950" y="102" class="role">CDCL SAT solver</text>
    <text x="950" y="120" class="role">Based on libsolv</text>
    <text x="950" y="146" class="when">Jul 2023</text>
    <image href="/logos/paxton-juggler.png" x="1070" y="20" width="140" height="160" preserveAspectRatio="xMidYMid meet" />
  </g>

  <!-- 5. pixi-build-* backends — intermediate bridge between rattler-build
       and pixi.  Drawn as a stack of three offset rectangles to suggest
       a family of executables, not a single project.  pixi delegates to
       a backend over a JSON-RPC protocol; pixi-build-rattler-build is
       the one that wraps rattler-build, alongside pixi-build-cmake/
       -python/-rust/-r/-ros/-mojo. -->
  <g v-click="5">
    <line x1="460" y1="420" x2="510" y2="430" class="link" />
    <line x1="690" y1="430" x2="740" y2="420" class="link" />
    <!-- Stacked-paper effect: 2 shadow rects offset down-right, then the front sheet -->
    <rect x="514" y="388" width="180" height="100" rx="4" class="box box--stack" />
    <rect x="512" y="384" width="180" height="100" rx="4" class="box box--stack" />
    <rect x="510" y="380" width="180" height="100" rx="4" class="box box--bridge" />
    <text x="600" y="420" class="name name--small">pixi-build-*</text>
    <text x="600" y="446" class="role">backend protocol</text>
    <text x="600" y="468" class="when">Oct 2024</text>
  </g>

  <!-- 5b. Backend chips — fan out from the bridge box on click 6, each
       expanding from the box centre via a CSS scale(0)→scale(1)
       transform with a staggered delay. -->
  <g class="chips">
    <g v-click="6" class="chip chip-1">
      <rect x="345" y="494" width="70" height="24" rx="12" />
      <text x="380" y="511">cmake</text>
    </g>
    <g v-click="6" class="chip chip-2">
      <rect x="419" y="494" width="80" height="24" rx="12" />
      <text x="459" y="511">python</text>
    </g>
    <g v-click="6" class="chip chip-3">
      <rect x="503" y="494" width="60" height="24" rx="12" />
      <text x="533" y="511">rust</text>
    </g>
    <g v-click="6" class="chip chip-4">
      <rect x="567" y="494" width="110" height="24" rx="12" />
      <text x="622" y="511">rattler-build</text>
    </g>
    <g v-click="6" class="chip chip-5">
      <rect x="681" y="494" width="60" height="24" rx="12" />
      <text x="711" y="511">ros</text>
    </g>
    <g v-click="6" class="chip chip-6">
      <rect x="745" y="494" width="40" height="24" rx="12" />
      <text x="765" y="511">r</text>
    </g>
    <g v-click="6" class="chip chip-7">
      <rect x="789" y="494" width="65" height="24" rx="12" />
      <text x="821" y="511">mojo</text>
    </g>
  </g>
</svg>
</div>

<style scoped>
.tree { font-family: var(--tufte-serif); }
.tree .box       { fill: #fffff8; stroke: #333; stroke-width: 1.4; filter: drop-shadow(0 2px 3px rgba(0, 0, 0, 0.14)); }
.tree .box--soft { stroke: #888; filter: drop-shadow(0 1px 2px rgba(0, 0, 0, 0.1)); }
/* Bridge box: the front sheet of a stacked-papers motif. Dashed
 * red-brown border + faint tint to read as "protocol layer" rather
 * than another project box. */
.tree .box--bridge {
  fill: #fffff8;
  stroke: #c14a26;
  stroke-width: 1.2;
  filter: drop-shadow(0 2px 3px rgba(0, 0, 0, 0.12));
}
.tree .box--stack {
  fill: #fffff8;
  stroke: #c14a26;
  stroke-width: 1.0;
  stroke-dasharray: 5 3;
  opacity: 0.55;
  filter: none;
}
.tree .name      { font: 26px "et-book", "et-book", serif; fill: #111; font-weight: bold; text-anchor: middle; }
.tree .name--small { font-size: 18px; }
.tree .role      { fill: #555; text-anchor: middle; font-size: 12px; }
.tree .role--mono { font-family: "IBM Plex Mono", Consolas, monospace; font-size: 10.5px; }
.tree .when      { font: italic 13px "et-book", "et-book", serif; fill: #c14a26; text-anchor: middle; }
.tree .link      { stroke: #c14a26; stroke-width: 1.4; fill: none; stroke-dasharray: 3 2; filter: drop-shadow(0 1px 2px rgba(0, 0, 0, 0.1)); }

/* Soft reveal on each click instead of an instant pop. */
.tree g.slidev-vclick-target {
  transition: opacity 400ms ease-out;
}
.tree g.slidev-vclick-hidden {
  opacity: 0;
}

/* Backend chips: pill rectangles that "expand" out of the bridge box.
 * scale(0) collapses each chip to the bridge box centre (transform-origin
 * = 600 430 in viewBox space); scale(1) puts it at its real position,
 * so the transition reads as the chip flying out from the box. */
.tree .chip rect {
  fill: #fffff8;
  stroke: #c14a26;
  stroke-width: 1;
  filter: drop-shadow(0 1px 2px rgba(0, 0, 0, 0.1));
}
.tree .chip text {
  font: 11px "IBM Plex Mono", Consolas, monospace;
  fill: #c14a26;
  text-anchor: middle;
}
.tree g.chip {
  transform-box: view-box;
  transform-origin: 600px 430px;
  transition:
    opacity 300ms ease-out,
    transform 600ms cubic-bezier(0.34, 1.4, 0.64, 1);
}
/* Start at scale(0.3) so the chip is visible-but-small from the first
 * frame — the opacity transition then fades meaningfully alongside the
 * grow-and-fly-out, instead of collapsing to a single invisible point. */
.tree g.chip.slidev-vclick-hidden {
  opacity: 0;
  transform: scale(0.3);
}
/* Stagger so they fan out one after another. */
.tree g.chip-1 { transition-delay: 0ms; }
.tree g.chip-2 { transition-delay: 50ms; }
.tree g.chip-3 { transition-delay: 100ms; }
.tree g.chip-4 { transition-delay: 150ms; }
.tree g.chip-5 { transition-delay: 200ms; }
.tree g.chip-6 { transition-delay: 250ms; }
.tree g.chip-7 { transition-delay: 300ms; }
</style>
