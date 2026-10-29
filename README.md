# Stappenteller

Een stappenteller met een grafiek, gemaakt met Vue 3 en vue-chartjs. Oefenproject 2 voor het keuzedeel Verdieping software.

## Wat kan het

- Je kan je stappen per dag invoeren (maandag t/m zondag).
- De grafiek past zich direct aan als je een getal verandert.
- Het berekent je totale stappen en je gemiddelde stappen per dag.
- Als je gemiddeld onder de 5000 stappen zit, wordt de kaart en de grafiek geel.

Er staan al voorbeeldwaarden in.

## Wat ik hiermee geoefend heb

| Onderdeel | Waar |
|---|---|
| `ref` | De stappen per dag |
| `v-model.number` | De invoervelden, zodat je een getal krijgt en geen tekst |
| `v-for` met `:key` | De 7 invoervelden |
| `computed` | Totaal, gemiddelde en of je onder het doel zit |
| `watch` | Een melding in de console als je onder of boven het doel komt |
| `onMounted` | De voorbeeldwaarden invullen als de pagina geladen is |
| `props` | De stappen, dagen en kleur doorgeven aan de grafiek |
| `:class` | De kaart geel maken onder het doel |

## Starten

```sh
npm install
npm run dev
```

Open daarna het adres uit de terminal (meestal http://localhost:5173).

## Bestanden

- `src/App.vue`: de invoer, de berekeningen en de opmaak.
- `src/components/BarChart.vue`: de grafiek. Krijgt de stappen, dagen en kleur binnen via props.
