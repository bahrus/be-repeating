# be-repeating (𝄆𝄇) [TODO]

Attribute based version of ib-id

## Syntax Example I -- Basic, template free.

```html
<ul>
    <li>Head Item</li>
    <li 𝄆='{
        "list": ["hello", "world"],
        "transform": {"li": "."}
    }'></li>
    <li 𝄇></li>
    <li>Footer Item</li>
</ul>
```

Generates:

```html
<ul>
    <li>Head Item</li>
    <li>hello</li>
    <li>world</li>
    <li>Footer</li>
</ul>
```

## Syntax Example II -- Updatable, template free

```html
<ul>
    <li>Head Item</li>
    <li be-repeating='{
        "list": ["hello", "world"],
        "transform": {"li": ["."]},
        "updatable": true
    }'>...</li>
    <li>Footer Item</li>
</ul>
```

Generates:

```html
<ul>
    <li>Head Item</li>
    <template is-repeating='{
        "list": ["hello", "world"],
        "transform": {"li": ["."]},
        "updatable": true
    }' data-cnt=4></template>
    <template data-ref=li-gen data-idx=0></template>
    <li>hello</li>
    <template data-ref=li-gen data-idx=1></template>
    <li>world</li>
    <li>Footer</li>
</ul>
```

## Example 3

```html
<script>
    customElements.define('my-list', class {
        ishList = ["hello", "world"]
    });
</script>
<ul itemscope=my-list>
    <li>Head Item</li>
    <li be-repeating-each="my-item in my-list"></li>
    <li>Footer</li>
</ul>
```