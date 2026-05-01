# Converting the ecosystem to Rust

<div class="absolute left-12 right-12 bottom-12 top-32">
<svg viewBox="0 0 1200 540" class="w-full h-full tree">

  <!-- 1. rattler — top centre, with snake-charmer Paxton on the left -->
  <g v-click="1">
    <image href="/logos/paxton-rattler.png" x="340" y="20" width="140" height="160" preserveAspectRatio="xMidYMid meet" />
    <rect x="490" y="40" width="220" height="120" rx="4" class="box" />
    <text x="600" y="78" class="name">rattler</text>
    <text x="600" y="102" class="role">conda primitives</text>
    <text x="600" y="120" class="role">parse, solve, install etc.</text>
    <text x="600" y="146" class="when">Nov 2021</text>
  </g>

  <!-- 2. rattler-build — Sep 2022, lower-left child, with builder Paxton -->
  <g v-click="2">
    <path d="M 540 160 C 540 280 350 280 350 360" class="link" fill="none" />
    <image href="/logos/paxton-builder.png" x="80" y="350" width="150" height="150" preserveAspectRatio="xMidYMid meet" />
    <rect x="240" y="360" width="220" height="120" rx="4" class="box" />
    <text x="350" y="398" class="name">rattler-build</text>
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
    <text x="850" y="440" class="role">"cargo" for conda</text>
    <text x="850" y="466" class="when">Apr 2023</text>
    <image href="/paxton.png" x="980" y="350" width="150" height="150" preserveAspectRatio="xMidYMid meet" />
  </g>

  <!-- 4. resolvo — Jul 2023, satellite to the right of rattler, with juggler Paxton -->
  <g v-click="4">
    <line x1="710" y1="100" x2="840" y2="100" class="link" />
    <rect x="840" y="40" width="220" height="120" rx="4" class="box box--soft" />
    <text x="950" y="78" class="name">resolvo</text>
    <text x="950" y="102" class="role">CDCL SAT solver</text>
    <text x="950" y="120" class="role">Based on libsolv</text>
    <text x="950" y="146" class="when">Jul 2023</text>
    <image href="/logos/paxton-juggler.png" x="1070" y="20" width="140" height="160" preserveAspectRatio="xMidYMid meet" />
  </g>
</svg>
</div>

<style scoped>
.tree { font-family: var(--tufte-serif); }
.tree .box       { fill: #fffff8; stroke: #333; stroke-width: 1.4; }
.tree .box--soft { stroke: #888; }
.tree .name      { font: 26px "et-book", "et-book", serif; fill: #111; font-weight: bold; text-anchor: middle; }
.tree .role      { fill: #555; text-anchor: middle; font-size: 12px; }
.tree .when      { font: italic 13px "et-book", "et-book", serif; fill: #c14a26; text-anchor: middle; }
.tree .link      { stroke: #c14a26; stroke-width: 1.4; fill: none; stroke-dasharray: 4 3; }

/* Soft reveal on each click instead of an instant pop. */
.tree g.slidev-vclick-target {
  transition: opacity 600ms ease-out;
}
.tree g.slidev-vclick-hidden {
  opacity: 0;
}
</style>
