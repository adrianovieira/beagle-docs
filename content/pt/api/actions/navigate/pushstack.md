---
title: PushStack
weight: 30
description: Descrição da ação PushStack e seus atributos
---

---

## O que é?

Apresenta uma nova tela e a coloca na pilha.

A sua estrutura é representada como mostrado abaixo:

| **Atributo** | **Tipo**                                      | Obrigatório | **Definição**      |
| :----------- | :-------------------------------------------- | :---------: | :----------------- |
| route        | [Route]({{< ref path="/api/actions/navigate/route/" lang="pt" >}}) |      ✓      | Rota de navegação. |
| controllerId | String |     | O id do controlador de navegação a ser usado durante a ação de navegação. Se ausente, o controlador de navegação padrão será usado. |
| navigationContext | ​[NavigationContext]({{< ref path="/api/actions/navigate/navigationcontext" lang="pt" >}})​ | | Contexto salvo na tela destino. |

## Como usar?

No exemplo abaixo, temos uma tela vinda do BFF com um botão, que ao ser clicado, abre uma nova activity server-driven com a tela especificada pelo BFF.

Para testar, basta que um endpoint do seu BFF retorne a tela do código abaixo e chame esse endpoint no frontend. Você poderá passar tanto uma rota local \(que passará uma [**screen**]({{< ref path="/api/components/layout/screen" lang="pt" >}}) na rota\), quanto remota \(que passará o endpoint da tela para a qual irá navegar\).

{{< tabs id="T112" >}}
{{% tab name="JSON" %}}

<!-- json-playground:pushStack.json
{
  "_beagleComponent_" : "beagle:screenComponent",
  "child" : {
    "_beagleComponent_" : "beagle:button",
    "text" : "Click me!",
    "onPress" : [ {
      "_beagleAction_" : "beagle:pushStack",
      "route" : {
        "screen" : {
          "_beagleComponent_" : "beagle:screenComponent",
          "child" : {
            "_beagleComponent_" : "beagle:text",
            "text" : "Hello second Screen"
          }
        }
      }
    } ]
  }
}
-->

{{% playground file="pushStack.json" language="pt" %}}
{{% /tab %}}

{{% tab name="Kotlin DSL" %}}

```
Screen(
    child = Button(
        text = "Click me!",
        onPress = listOf(
            Navigate.PushStack(
                Route.Local(
                    Screen(
                        child = Text("Hello second Screen")
                    )
                )
            )
        )
    )
)
```

{{% /tab %}}
{{< /tabs >}}
