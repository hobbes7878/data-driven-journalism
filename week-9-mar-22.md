# SQL refresh and analysis

## In class

Let's make an analysis!

Checkout [this data](https://www.theguardian.com/world/2017/mar/20/mapping-gun-murders-micro-level-new-data-2015) on gun-related homicides released by _The Guardian_ recently.

What's in it? What questions do you have about it? What other data can we use to supplement in our understanding of it?

Let's do analysis in class!

---

#### top states by killed

```sql
SELECT
state,
sum(num_killed) as total_killed
FROM gva_release_2015_raw_incidents
GROUP BY state
ORDER BY 2 desc;
```

#### top states by injured

```sql
SELECT
state,
sum(num_injured) as total_injured
FROM gva_release_2015_raw_incidents
GROUP BY state
ORDER BY 2 desc;
```

