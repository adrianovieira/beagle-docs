---
title: Canalização de componentes
weight: 95
description: >-
  Nesta seção, você encontra mais sobre como filtrar os elementos que são
  enviados e para qual plataforma.
---

---

Alguns componentes fornecidos pelo Beagle podem ser direcionados à uma plataforma espefica, pois, podem não fazer tanto sentido para outra. Por exemplo, o uso do [**ScrollView**]({{< ref path="/api/components/layout/scrollview" lang="pt" >}}) na plataforma Mobile é necessário para rolar conteúdos, mas não é necessário na Web.

Isso é possível pois o Beagle possui a funcionalidade de **Especificação de Plataforma** ou **Canalização**, que te permite ter controle sobre quais elementos são enviados pelo BFF e quais plataformas serão vão utiliza-los.
### Como funciona?

O Beagle faz uso de um cabeçalho personalizado chamado `beagle-platform` que pode conter os valores:

- `ALL`;
- `MOBILE`;
- `ANDROID`;
- `IOS`;
- `WEB`;

Dessa forma, a resposta do BFF é interceptada e os elementos são filtrados de acordo com a plataforma para qual ela está sendo enviada.

### Como acessar?

Você pode acessar esse controle de duas maneiras:

1. Por meio de **estruturas de controle de fluxo** em seu código, que verifica qual plataforma seu cliente usou para realizar uma requisição.

Veja no exemplo a seguir:

```kotlin
fun createComponentPlatformDependent(beaglePlatform: BeaglePlatform) = when {
    this.beaglePlatform.isMobilePlatform() -> {
        ScrollView(
            children = listOf(
                Text("Mobile platform")
            )
        )
    }
    this.beaglePlatform == BeaglePlatform.WEB -> {
        Text("Web platform")
    }
    else -> {
        ScrollView(
            children = listOf(
                Text("Mobile platform"),
                Text("Web platform")
            )
        )
    }
}
```

2.  **Especificando a plataforma** para qual o elemento é destinado e, com isso, o Beagle faz a filtragem dos elementos corretos.

Veja no exemplo a seguir:

```kotlin
Button(text = "mobile only text").forPlatform(BeaglePlatform.MOBILE),
Button(text = "web only text").forPlatform(BeaglePlatform.WEB),
Button(text = "ios only text").forPlatform(BeaglePlatform.IOS),
Button(text = "android only text").forPlatform(BeaglePlatform.ANDROID),
Button(text = "text free for all")
```

Se quiser saber como configurar esta funcionalidade, veja na seção de [**customização do Beagle**]({{< ref path="/backend/customization" lang="pt" >}}).

{{% alert color="info" %}}
Caso utilize um dos Beagle starters, não é necessário realizar a configuração da funcionalidade manualmente, pois ela já vem pré-configurada.
{{% /alert %}}
