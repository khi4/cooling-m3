# cooling-m3

Interactive 3D concept and thermal simulator for a slim corrugated-aluminium
cooling wedge for the fanless MacBook Air 13.6" M3, with an optional magnetic
battery-powered fan module.

**Live:** https://khi4.github.io/cooling-m3/

## The product

A metal wedge that sits under only the rear ~55% of the laptop, so the front
edge stays on the desk and the typing angle barely changes. Its body is a
corrugated (zigzag) sheet brazed between two skins — the folds are both the fin
area and the walls of the air channels, the way a radiator core is built.
A rectangular fan module clips magnetically to the tall rear face to convert it
from passive to active cooling.

## The simulator

Runs two transient cases side by side — on the stand and flat on the desk — and
plots the gap between them.

- Solids are lumped RC nodes: SoC junction, chassis, and 20 slices of the stand
  along the flow path
- Air is marched slice by slice with an effectiveness-NTU step
- Channel flow comes from a pressure balance: buoyancy head against viscous loss
  when passive, fan curve against system curve when active
- Radiation uses parallel-plate view factors
- The desk is a semi-infinite solid under transient flux, which is why a steel
  desk behaves nothing like oak
- The SoC throttles when the junction reaches its limit, so the benefit shows up
  as sustained watts as well as degrees

## Accuracy

**This is not a measurement and not CFD.** It resolves temperature along the
channel, not across the machine, so it cannot show hot spots or recirculation.
One constant is fitted so that a bare machine on a wooden desk reaches 46 °C
case and 95 °C junction after 45 minutes at 16 W and 22 °C ambient — what these
machines actually measure at. Everything else is standard heat-transfer
correlations, good to roughly ±30–40% on individual conductances.

Use it to compare configurations against each other. Do not quote absolute
numbers from it. A prototype and a thermocouple settle it in an afternoon.

## Running locally

No build step — the page is self-contained and loads three.js from a CDN.
Just open `index.html` in a browser.
