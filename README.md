# Hugo Documentation Helper

## What

A notebook-inspired component

![Screenshot](https://raw.githubusercontent.com/pointyfar/hugo-notebook/master/images/code.png)

![Screenshot](https://raw.githubusercontent.com/pointyfar/hugo-notebook/master/images/result.png)

![Screenshot](https://raw.githubusercontent.com/pointyfar/hugo-notebook/master/images/rendered.png)

## Why

I needed one, and I thought it might be useful to others as well.

## How

Use as a typical Hugo Theme Component.

The example site imports it as a Hugo Module:

```toml
# config.toml

[module]
[[module.imports]]
    path = "github.com/pointyfar/hugo-notebook"
    [[module.imports.mounts]]
        source = "assets"
        target = "assets"
    [[module.imports.mounts]]
        source = "layouts"
        target = "layouts"
```

Embed the script somewhere near the bottom of your layouts: 

by calling the partial:

```
{{ if .HasShortcode "notebook-helper/notebook" }}
    {{ partial "notebook-helper/notebook-script" . }}
{{ end }}
```

or as a js resource:
```
{{ $nhjs := resources.Get "notebook-helper/script.js" }}
<script src="{{$nhjs.Permalink}}"></script>
```


Import the stylesheet:

as `scss`:
```
@import './../notebook-helper/styles';
```

or as a partial:
```
{{ partial "notebook-helper/notebook-style" . }}
```

or as a resource:
```
{{ $nhcss := resources.Get "notebook-helper/style.scss" | resources.ToCSS }}
<link rel="stylesheet" href="{{$nhcss.Permalink}}" >
```

Use the shortcode:

```
{{< notebook-helper/notebook >}}

{{ print "foo" }}
{{ print "bar" }}
{{ $arr := slice "foo" "bar" }}
{{ range $i, $e := $arr }}
{{ . }}
{{ end }}

{{< /notebook-helper/notebook >}}
```

