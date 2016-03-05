Lighter Javascript Templates
============================

Derived from EJS Embedded Javascript Templates with new expressions for lighter templates

## Install
```
npm install ljs-template --save
```

## Render
```
var ljs = require('ljs-template');

var out = ljs.render("Hello {{_name_}}", {name: "Max"});

console.log(out);
```

It displays:
```
Hello Max
```

## Sample

### Template :
```
var template = `

<h1>Books:</h1>

{#each books as book, index #}
<h2>{{_book.title_}}</h2>
<ul>
  <li>Authors:
   {#if book.authors #}
    <ul>
    {#each book.authors as author #}
      <li>{{_author_}}</li>
    {/each/}
    </ul>
   {/if/}
  </li>
  <li>Price: {{_book.price_}}
</ul>
{/each/}

`;
```

### Data :
```
var data =
{
  books: [
    {
      title: "Cravings: Recipes for All the Food You Want to Eat",
      authors: ["Chrissy Teigen", "Adeena Sussman"],
      price: "$17.85"
    },
    {
      title: "Pretty Happy: Healthy Ways to Love Your Body",
      authors: ["Kate Hudson"],
      price: "$15.89"
    }
  ]
}
```

### Render :
```
var ljs = require('ljs-template');

var out = ljs.render(template, data);

console.log(out);
```

### It displays:
```
<h1>Books:</h1>
<h2>Cravings: Recipes for All the Food You Want to Eat</h2>
<ul>
  <li>Authors:
    <ul>
      <li>Chrissy Teigen</li>
      <li>Adeena Sussman</li>
    </ul>
  </li>
  <li>Price: $17.85
</ul>
<h2>Pretty Happy: Healthy Ways to Love Your Body</h2>
<ul>
  <li>Authors:
    <ul>
      <li>Kate Hudson</li>
    </ul>
  </li>
  <li>Price: $15.89
</ul>
```

## Expressions

### Javascript code :
```
{%
  Javascript code
%}
```

### Define variable :
```
{#var variable_name = [javascript code] #}
```

### Display Javascript code :
```
{{_[Javascript code]_}}
```

### If conditional :
```
{#if [Javascript condition] #}

{/else/}

{/if/}
```

### Loop over Map entries :
```
{#each [javascript code] as [value], [key] #}
{/each/}
```

### Loop over Array values :
```
{#each [javascript code] as [value], [index] #}
{/each/}
```
