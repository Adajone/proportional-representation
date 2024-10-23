---
toc: false
---

<div class="hero">
  <h1>Porportional Representation</h1>
  <h2></h2>
</div>

```js
const us = d3.json("https://cdn.jsdelivr.net/npm/us-atlas@3/states-10m.json");
const votes = FileAttachment(
  "data/electoral/state-electoral-votes-by-year-with-po.csv"
).csv();
```

```js
const nation = topojson.feature(us, us.objects.nation);
const states = topojson.feature(us, us.objects.states);
display(votes);

// const thisYearData = votes.filter(d => d.year === "2020")
// display(thisYearData)

const thisYearData = d3.rollup(
  votes.filter((d) => d.year === "2020"),
  (v) => v.reduce((max, row) => (+row.votes > +max.votes ? row : max)),
  (d) => d.state
);
display(thisYearData);
```

```js
const color = {
  DEMOCRAT: "blue",
  REPUBLICAN: "red",
  LIBERTARIAN: "yellow",
  OTHER: "white",
};

const label = {
  DEMOCRAT: "D",
  REPUBLICAN: "R",
  LIBERTARIAN: "L",
  OTHER: "O",
};

const votingStates = states.features.filter((d) =>
  thisYearData.has(d.properties.name)
);

display(votingStates);
```

```js
display(
  Plot.plot({
    projection: "albers-usa",
    width,
    marks: [
      Plot.geo(nation),
      Plot.geo(votingStates, {
        strokeOpacity: 1,
        strokeWidth: 1,
        stroke: "white",
        fill: (d) => {
          const state = thisYearData.get(d.properties.name);
          return state ? color[state.party.toUpperCase()] : "thistle";
        },
      }),
      Plot.text(votingStates, {
        x: (d) => d3.geoCentroid(d)[0],
        y: (d) => d3.geoCentroid(d)[1],
        text: (d) => {
          const state = thisYearData.get(d.properties.name);
          return state ?
          state.state_po + "\n" + state.votes : "";
        },
        fill: "white",
        stroke: "black",
        fontSize: 10,
        textAnchor: "middle",
      }),
    ],
  })
);
```

<style>

.hero {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: var(--sans-serif);
  margin: 4rem 0 8rem;
  text-wrap: balance;
  text-align: center;
}

.hero h1 {
  margin: 1rem 0;
  padding: 1rem 0;
  max-width: none;
  font-size: 14vw;
  font-weight: 900;
  line-height: 1;
  background: linear-gradient(30deg, var(--theme-foreground-focus), currentColor);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero h2 {
  margin: 0;
  max-width: 34em;
  font-size: 20px;
  font-style: initial;
  font-weight: 500;
  line-height: 1.5;
  color: var(--theme-foreground-muted);
}

@media (min-width: 640px) {
  .hero h1 {
    font-size: 90px;
  }
}

</style>
