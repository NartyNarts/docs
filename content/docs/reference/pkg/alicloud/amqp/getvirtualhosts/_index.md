
---
title: "getVirtualHosts"
title_tag: "alicloud.amqp.getVirtualHosts"
meta_desc: "Documentation for the alicloud.amqp.getVirtualHosts function with examples, input properties, output properties, and supporting types."
---



<!-- WARNING: this file was generated by Pulumi Docs Generator. -->
<!-- Do not edit by hand unless you're certain you know what you are doing! -->

This data source provides the Amqp Virtual Hosts of the current Alibaba Cloud user.

> **NOTE:** Available in v1.126.0+.


{{% examples %}}

## Example Usage

{{< chooser language "typescript,python,go,csharp" / >}}





{{< example csharp >}}

```csharp
using Pulumi;
using AliCloud = Pulumi.AliCloud;

class MyStack : Stack
{
    public MyStack()
    {
        var ids = Output.Create(AliCloud.Amqp.GetVirtualHosts.InvokeAsync(new AliCloud.Amqp.GetVirtualHostsArgs
        {
            InstanceId = "amqp-abc12345",
            Ids = 
            {
                "my-VirtualHost-1",
                "my-VirtualHost-2",
            },
        }));
        this.AmqpVirtualHostId1 = ids.Apply(ids => ids.Hosts[0].Id);
        var nameRegex = Output.Create(AliCloud.Amqp.GetVirtualHosts.InvokeAsync(new AliCloud.Amqp.GetVirtualHostsArgs
        {
            InstanceId = "amqp-abc12345",
            NameRegex = "^my-VirtualHost",
        }));
        this.AmqpVirtualHostId2 = nameRegex.Apply(nameRegex => nameRegex.Hosts[0].Id);
    }

    [Output("amqpVirtualHostId1")]
    public Output<string> AmqpVirtualHostId1 { get; set; }
    [Output("amqpVirtualHostId2")]
    public Output<string> AmqpVirtualHostId2 { get; set; }
}
```


{{< /example >}}


{{< example go >}}

```go
package main

import (
	"github.com/pulumi/pulumi-alicloud/sdk/v3/go/alicloud/amqp"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		ids, err := amqp.GetVirtualHosts(ctx, &amqp.GetVirtualHostsArgs{
			InstanceId: "amqp-abc12345",
			Ids: []string{
				"my-VirtualHost-1",
				"my-VirtualHost-2",
			},
		}, nil)
		if err != nil {
			return err
		}
		ctx.Export("amqpVirtualHostId1", ids.Hosts[0].Id)
		opt0 := "^my-VirtualHost"
		nameRegex, err := amqp.GetVirtualHosts(ctx, &amqp.GetVirtualHostsArgs{
			InstanceId: "amqp-abc12345",
			NameRegex:  &opt0,
		}, nil)
		if err != nil {
			return err
		}
		ctx.Export("amqpVirtualHostId2", nameRegex.Hosts[0].Id)
		return nil
	})
}
```


{{< /example >}}


{{< example python >}}

```python
import pulumi
import pulumi_alicloud as alicloud

ids = alicloud.amqp.get_virtual_hosts(instance_id="amqp-abc12345",
    ids=[
        "my-VirtualHost-1",
        "my-VirtualHost-2",
    ])
pulumi.export("amqpVirtualHostId1", ids.hosts[0].id)
name_regex = alicloud.amqp.get_virtual_hosts(instance_id="amqp-abc12345",
    name_regex="^my-VirtualHost")
pulumi.export("amqpVirtualHostId2", name_regex.hosts[0].id)
```


{{< /example >}}


{{< example typescript >}}


```typescript
import * as pulumi from "@pulumi/pulumi";
import * as alicloud from "@pulumi/alicloud";

const ids = alicloud.amqp.getVirtualHosts({
    instanceId: "amqp-abc12345",
    ids: [
        "my-VirtualHost-1",
        "my-VirtualHost-2",
    ],
});
export const amqpVirtualHostId1 = ids.then(ids => ids.hosts[0].id);
const nameRegex = alicloud.amqp.getVirtualHosts({
    instanceId: "amqp-abc12345",
    nameRegex: "^my-VirtualHost",
});
export const amqpVirtualHostId2 = nameRegex.then(nameRegex => nameRegex.hosts[0].id);
```


{{< /example >}}





{{% /examples %}}




## Using getVirtualHosts {#using}

{{< chooser language "typescript,python,go,csharp" / >}}


{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">function </span>getVirtualHosts<span class="p">(</span><span class="nx">args</span><span class="p">:</span> <span class="nx">GetVirtualHostsArgs</span><span class="p">,</span> <span class="nx">opts</span><span class="p">?:</span> <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#InvokeOptions">InvokeOptions</a></span><span class="p">): Promise&lt;<span class="nx"><a href="#result">GetVirtualHostsResult</a></span>></span></code></pre></div>
{{% /choosable %}}


{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span>get_virtual_hosts(</span><span class="nx">ids</span><span class="p">:</span> <span class="nx">Optional[Sequence[str]]</span> = None<span class="p">,</span>
                      <span class="nx">instance_id</span><span class="p">:</span> <span class="nx">Optional[str]</span> = None<span class="p">,</span>
                      <span class="nx">name_regex</span><span class="p">:</span> <span class="nx">Optional[str]</span> = None<span class="p">,</span>
                      <span class="nx">output_file</span><span class="p">:</span> <span class="nx">Optional[str]</span> = None<span class="p">,</span>
                      <span class="nx">opts</span><span class="p">:</span> <span class="nx"><a href="/docs/reference/pkg/python/pulumi/#pulumi.InvokeOptions">Optional[InvokeOptions]</a></span> = None<span class="p">) -&gt;</span> GetVirtualHostsResult</code></pre></div>
{{% /choosable %}}


{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetVirtualHosts<span class="p">(</span><span class="nx">ctx</span><span class="p"> *</span><span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v3/go/pulumi?tab=doc#Context">Context</a></span><span class="p">,</span> <span class="nx">args</span><span class="p"> *</span><span class="nx">GetVirtualHostsArgs</span><span class="p">,</span> <span class="nx">opts</span><span class="p"> ...</span><span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v3/go/pulumi?tab=doc#InvokeOption">InvokeOption</a></span><span class="p">) (*<span class="nx"><a href="#result">GetVirtualHostsResult</a></span>, error)</span></code></pre></div>

> Note: This function is named `GetVirtualHosts` in the Go SDK.

{{% /choosable %}}


{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static class </span><span class="nx">GetVirtualHosts </span><span class="p">{</span><span class="k">
    public static </span>Task&lt;<span class="nx"><a href="#result">GetVirtualHostsResult</a></span>> <span class="p">InvokeAsync(</span><span class="nx">GetVirtualHostsArgs</span><span class="p"> </span><span class="nx">args<span class="p">,</span> <span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.InvokeOptions.html">InvokeOptions</a></span><span class="p">? </span><span class="nx">opts = null<span class="p">)</span><span class="p">
}</span></code></pre></div>
{{% /choosable %}}



The following arguments are supported:


{{% choosable language csharp %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="instanceid_csharp">
<a href="#instanceid_csharp" style="color: inherit; text-decoration: inherit;">Instance<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}InstanceId.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="ids_csharp">
<a href="#ids_csharp" style="color: inherit; text-decoration: inherit;">Ids</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">List&lt;string&gt;</span>
    </dt>
    <dd>{{% md %}}A list of Virtual Host IDs. Its element value is same as Virtual Host Name.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="nameregex_csharp">
<a href="#nameregex_csharp" style="color: inherit; text-decoration: inherit;">Name<wbr>Regex</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}A regex string to filter results by Virtual Host name.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="outputfile_csharp">
<a href="#outputfile_csharp" style="color: inherit; text-decoration: inherit;">Output<wbr>File</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language go %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="instanceid_go">
<a href="#instanceid_go" style="color: inherit; text-decoration: inherit;">Instance<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}InstanceId.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="ids_go">
<a href="#ids_go" style="color: inherit; text-decoration: inherit;">Ids</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of Virtual Host IDs. Its element value is same as Virtual Host Name.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="nameregex_go">
<a href="#nameregex_go" style="color: inherit; text-decoration: inherit;">Name<wbr>Regex</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}A regex string to filter results by Virtual Host name.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="outputfile_go">
<a href="#outputfile_go" style="color: inherit; text-decoration: inherit;">Output<wbr>File</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language nodejs %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="instanceid_nodejs">
<a href="#instanceid_nodejs" style="color: inherit; text-decoration: inherit;">instance<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}InstanceId.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="ids_nodejs">
<a href="#ids_nodejs" style="color: inherit; text-decoration: inherit;">ids</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}A list of Virtual Host IDs. Its element value is same as Virtual Host Name.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="nameregex_nodejs">
<a href="#nameregex_nodejs" style="color: inherit; text-decoration: inherit;">name<wbr>Regex</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}A regex string to filter results by Virtual Host name.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="outputfile_nodejs">
<a href="#outputfile_nodejs" style="color: inherit; text-decoration: inherit;">output<wbr>File</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language python %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="instance_id_python">
<a href="#instance_id_python" style="color: inherit; text-decoration: inherit;">instance_<wbr>id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}InstanceId.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="ids_python">
<a href="#ids_python" style="color: inherit; text-decoration: inherit;">ids</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">Sequence[str]</span>
    </dt>
    <dd>{{% md %}}A list of Virtual Host IDs. Its element value is same as Virtual Host Name.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="name_regex_python">
<a href="#name_regex_python" style="color: inherit; text-decoration: inherit;">name_<wbr>regex</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A regex string to filter results by Virtual Host name.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="output_file_python">
<a href="#output_file_python" style="color: inherit; text-decoration: inherit;">output_<wbr>file</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd></dl>
{{% /choosable %}}




## getVirtualHosts Result {#result}

The following output properties are available:



{{% choosable language csharp %}}
<dl class="resources-properties"><dt class="property-"
            title="">
        <span id="hosts_csharp">
<a href="#hosts_csharp" style="color: inherit; text-decoration: inherit;">Hosts</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getvirtualhostshost">List&lt;Pulumi.<wbr>Ali<wbr>Cloud.<wbr>Amqp.<wbr>Outputs.<wbr>Get<wbr>Virtual<wbr>Hosts<wbr>Host&gt;</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="id_csharp">
<a href="#id_csharp" style="color: inherit; text-decoration: inherit;">Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The provider-assigned unique ID for this managed resource.
{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="ids_csharp">
<a href="#ids_csharp" style="color: inherit; text-decoration: inherit;">Ids</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">List&lt;string&gt;</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="instanceid_csharp">
<a href="#instanceid_csharp" style="color: inherit; text-decoration: inherit;">Instance<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="names_csharp">
<a href="#names_csharp" style="color: inherit; text-decoration: inherit;">Names</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">List&lt;string&gt;</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="nameregex_csharp">
<a href="#nameregex_csharp" style="color: inherit; text-decoration: inherit;">Name<wbr>Regex</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="outputfile_csharp">
<a href="#outputfile_csharp" style="color: inherit; text-decoration: inherit;">Output<wbr>File</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language go %}}
<dl class="resources-properties"><dt class="property-"
            title="">
        <span id="hosts_go">
<a href="#hosts_go" style="color: inherit; text-decoration: inherit;">Hosts</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getvirtualhostshost">[]Get<wbr>Virtual<wbr>Hosts<wbr>Host</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="id_go">
<a href="#id_go" style="color: inherit; text-decoration: inherit;">Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The provider-assigned unique ID for this managed resource.
{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="ids_go">
<a href="#ids_go" style="color: inherit; text-decoration: inherit;">Ids</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="instanceid_go">
<a href="#instanceid_go" style="color: inherit; text-decoration: inherit;">Instance<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="names_go">
<a href="#names_go" style="color: inherit; text-decoration: inherit;">Names</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="nameregex_go">
<a href="#nameregex_go" style="color: inherit; text-decoration: inherit;">Name<wbr>Regex</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="outputfile_go">
<a href="#outputfile_go" style="color: inherit; text-decoration: inherit;">Output<wbr>File</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language nodejs %}}
<dl class="resources-properties"><dt class="property-"
            title="">
        <span id="hosts_nodejs">
<a href="#hosts_nodejs" style="color: inherit; text-decoration: inherit;">hosts</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getvirtualhostshost">Get<wbr>Virtual<wbr>Hosts<wbr>Host[]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="id_nodejs">
<a href="#id_nodejs" style="color: inherit; text-decoration: inherit;">id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The provider-assigned unique ID for this managed resource.
{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="ids_nodejs">
<a href="#ids_nodejs" style="color: inherit; text-decoration: inherit;">ids</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="instanceid_nodejs">
<a href="#instanceid_nodejs" style="color: inherit; text-decoration: inherit;">instance<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="names_nodejs">
<a href="#names_nodejs" style="color: inherit; text-decoration: inherit;">names</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="nameregex_nodejs">
<a href="#nameregex_nodejs" style="color: inherit; text-decoration: inherit;">name<wbr>Regex</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="outputfile_nodejs">
<a href="#outputfile_nodejs" style="color: inherit; text-decoration: inherit;">output<wbr>File</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language python %}}
<dl class="resources-properties"><dt class="property-"
            title="">
        <span id="hosts_python">
<a href="#hosts_python" style="color: inherit; text-decoration: inherit;">hosts</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getvirtualhostshost">Sequence[Get<wbr>Virtual<wbr>Hosts<wbr>Host]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="id_python">
<a href="#id_python" style="color: inherit; text-decoration: inherit;">id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The provider-assigned unique ID for this managed resource.
{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="ids_python">
<a href="#ids_python" style="color: inherit; text-decoration: inherit;">ids</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">Sequence[str]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="instance_id_python">
<a href="#instance_id_python" style="color: inherit; text-decoration: inherit;">instance_<wbr>id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="names_python">
<a href="#names_python" style="color: inherit; text-decoration: inherit;">names</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">Sequence[str]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="name_regex_python">
<a href="#name_regex_python" style="color: inherit; text-decoration: inherit;">name_<wbr>regex</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd><dt class="property-"
            title="">
        <span id="output_file_python">
<a href="#output_file_python" style="color: inherit; text-decoration: inherit;">output_<wbr>file</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd></dl>
{{% /choosable %}}




## Supporting Types


<h4 id="getvirtualhostshost">Get<wbr>Virtual<wbr>Hosts<wbr>Host</h4>



{{% choosable language csharp %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="id_csharp">
<a href="#id_csharp" style="color: inherit; text-decoration: inherit;">Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Host.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="instanceid_csharp">
<a href="#instanceid_csharp" style="color: inherit; text-decoration: inherit;">Instance<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}InstanceId.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="virtualhostname_csharp">
<a href="#virtualhostname_csharp" style="color: inherit; text-decoration: inherit;">Virtual<wbr>Host<wbr>Name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}VirtualHostName.
{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language go %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="id_go">
<a href="#id_go" style="color: inherit; text-decoration: inherit;">Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Host.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="instanceid_go">
<a href="#instanceid_go" style="color: inherit; text-decoration: inherit;">Instance<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}InstanceId.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="virtualhostname_go">
<a href="#virtualhostname_go" style="color: inherit; text-decoration: inherit;">Virtual<wbr>Host<wbr>Name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}VirtualHostName.
{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language nodejs %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="id_nodejs">
<a href="#id_nodejs" style="color: inherit; text-decoration: inherit;">id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Host.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="instanceid_nodejs">
<a href="#instanceid_nodejs" style="color: inherit; text-decoration: inherit;">instance<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}InstanceId.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="virtualhostname_nodejs">
<a href="#virtualhostname_nodejs" style="color: inherit; text-decoration: inherit;">virtual<wbr>Host<wbr>Name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}VirtualHostName.
{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language python %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="id_python">
<a href="#id_python" style="color: inherit; text-decoration: inherit;">id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Host.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="instance_id_python">
<a href="#instance_id_python" style="color: inherit; text-decoration: inherit;">instance_<wbr>id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}InstanceId.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="virtual_host_name_python">
<a href="#virtual_host_name_python" style="color: inherit; text-decoration: inherit;">virtual_<wbr>host_<wbr>name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}VirtualHostName.
{{% /md %}}</dd></dl>
{{% /choosable %}}





<h2 id="package-details">Package Details</h2>
<dl class="package-details">
	<dt>Repository</dt>
	<dd><a href="https://github.com/pulumi/pulumi-alicloud">https://github.com/pulumi/pulumi-alicloud</a></dd>
	<dt>License</dt>
	<dd>Apache-2.0</dd>
	<dt>Notes</dt>
	<dd>{{% md %}}This Pulumi package is based on the [`alicloud` Terraform Provider](https://github.com/aliyun/terraform-provider-alicloud).{{% /md %}}</dd>
</dl>

