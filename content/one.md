---
title: "One"
---

{{< notebook-helper/notebook >}}

{{ print "foo" }}
{{ print "bar" }}

{{ range $k, $v := .Params.arrays }}
<h3>{{ $k }}</h3>
{{ $v }}
{{ end }}

{{< /notebook-helper/notebook >}}

{{< notebook-helper/notebook >}}
{{ $f := site.GetPage "one" }}
{{ $f }}
<br>
{{ $f.Title }}
{{< /notebook-helper/notebook >}}


{{< notebook-helper/notebook >}}
<ul>
{{ range $i, $e := first 5 site.Pages }}
<li>{{.Title}}</li>
{{ end }}
</ul>
{{< /notebook-helper/notebook >}}