---
title: PopView
weight: 80
description: Descrição da ação PopView e seus atributos
---

---

## O que é?

Remove a tela de exibição atual.

A sua estrutura é representada como mostrado abaixo:

| **Atributo** | **Tipo**                                      | Obrigatório | **Definição**      |
| :----------- | :-------------------------------------------- | :---------: | :----------------- |
| navigationContext | ​[NavigationContext]({{< ref path="/api/actions/navigate/navigationcontext" lang="pt" >}})​ | | Contexto salvo na tela destino. |

## Como usar?

No exemplo abaixo, temos uma tela vinda do BFF com um botão, que ao clicar nele, remove a view atual.

Para testar, basta que um endpoint do seu BFF retorne a tela do código abaixo e chame esse endpoint no frontend.

{{< tabs id="T115" >}}
{{% tab name="JSON" %}}
<!-- json-playground:popView.json
{
  "_beagleComponent_" : "beagle:screenComponent",
  "child" : {
    "_beagleComponent_" : "beagle:button",
    "text" : "Click me!",
    "onPress" : [ {
      "_beagleAction_" : "beagle:popView"
    } ]
  }
}
-->
{{% playground file="popView.json" language="pt" %}}
{{% /tab %}}

{{% tab name="Kotlin DSL" %}}
```
Screen(
    child = Button(
        text = "Click me!",
        onPress = listOf(
            Navigate.PopView()
        )
    )
)
```
{{% /tab %}}
{{< /tabs >}}
