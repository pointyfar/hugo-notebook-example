---
title: "Two"
foo:
    - bar
    - baz
lorem: ipsum
---

{{< notebook-helper/notebook >}}

{{ range $i, $e := .Params.foo }}
{{ $i }}: {{ $e }}
<br>
{{ end }}

<!-- This here is a HTML comment. -->
<!-- This won't be visible on the rendered tab. -->

{{ if isset .Params "lorem" }}
Lorem is set to {{.Params.lorem}}.
{{ end }}

{{< /notebook-helper/notebook >}}
