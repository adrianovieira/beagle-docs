---
title: Visão Geral
weight: 1
type: overview
description: 'Aqui você encontrará bibliotecas que te auxiliarão iniciar um projeto usando o beagle para Android. Essas bibliotecas irão facilitar a configuração inicial do Beagle em um projeto, evitando algumas etapas e iniciando os estudos mais rapidamente.'
---

---

### Utilizando as Libs de apoio

Para começar a utilizar o Beagle, você pode usar como auxílio as bibliotecas abaixo:

{{% alert color="warning" %}}
![Maven Central](https://img.shields.io/maven-central/v/br.com.zup.beagle/beagle-scaffold?color=green&label=Beagle-Scaffold)

Esta biblioteca irá definir quase todas as configurações necessárias para começar a usar o Beagle em seu projeto. Aconselhamos o uso dessas bibliotecas para pessoas que nunca usaram o Beagle antes. Vá para a seção [Beagle-Scaffold]({{< ref path="/android/libs/beagle-scaffold.md" lang="pt" >}}) para configurar o Beagle em uma aplicação Android
{{% /alert %}}

{{% alert color="warning" %}}
![Maven Central](https://img.shields.io/maven-central/v/br.com.zup.beagle/beagle-defaults?color=green&label=Beagle-Defaults)

Esta biblioteca irá definir somente as classes que definem a camada de cliente HTTP HttpClient, Logger e Cache padrão que demonstram o contrato com o Beagle. 

Todas as outras configurações necessárias para o funcionamento do Beagle serão feitas manualmente<br> Todas essas classes também estão disponíveis na biblioteca Scaffold. Vá para a seção [Beagle-Defaults]({{< ref path="/android/libs/beagle-defaults.md" lang="pt" >}}) para configurar o Beagle em uma aplicação Android
{{% /alert %}}