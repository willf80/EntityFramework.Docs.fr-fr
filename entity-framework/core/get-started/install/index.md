---
title: "Installation d’EF Core"
author: divega
ms.author: divega
ms.date: 08/06/2017
ms.assetid: 608cc774-c570-4809-8a3e-cd2c8446b8b2
ms.technology: entity-framework-core
uid: core/get-started/install/index
ms.openlocfilehash: 31b96ebd0ae282b88be98988eff6263084dc5dd5
ms.sourcegitcommit: 5e2d97e731f975cf3405ff3deab2a3c75ad1b969
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="installing-ef-core"></a>Installation d’EF Core

## <a name="prerequisites"></a>Conditions préalables

Pour développer des applications .NET Core 2.0 (y compris des applications ASP.NET Core 2.0 qui ciblent .NET Core), vous devez télécharger et installer une version du [SDK .NET Core 2.0](https://www.microsoft.com/net/download/core) qui convient à votre plateforme. **Cela est vrai même si vous avez installé Visual Studio 2017 version 15.3.**

Pour utiliser EF Core 2.0 ou toute autre bibliothèque .NET Standard 2.0 avec une plateforme .NET en plus de .NET Core 2.0 (par exemple, avec .NET Framework 4.6.1 ou version supérieure), vous avez besoin d’une version de NuGet qui prend en charge .NET Standard 2.0 et ses frameworks compatibles. Voici quelques façons de procéder :

* Installez Visual Studio 2017 version 15.3.
* Si vous utilisez Visual Studio 2015, [téléchargez et mettez à niveau le client NuGet vers la version 3.6.0](https://www.nuget.org/downloads).

Les projets créés avec des versions précédentes de Visual Studio et ciblant .NET Framework peuvent nécessiter des modifications supplémentaires pour être compatibles avec les bibliothèques .NET Standard 2.0 :

* Modifiez le fichier projet et vérifiez que l’entrée suivante apparaît dans le groupe de propriétés initiales :
  ``` xml
  <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
  ```

* Pour les projets de test, vérifiez également que l’entrée suivante est présente :
  ``` xml
  <GenerateBindingRedirectsOutputType>true</GenerateBindingRedirectsOutputType>
  ```

## <a name="getting-the-bits"></a>Obtention des bits
La méthode recommandée pour ajouter des bibliothèques runtime EF Core à une application consiste à installer un fournisseur de base de données EF Core à partir de NuGet.

Outre les bibliothèques runtime, vous pouvez installer des outils qui facilitent la réalisation de plusieurs tâches EF Core dans votre projet au moment de la conception, telles que la création et l’application de migrations et la création d’un modèle basé sur une base de données existante.

> [!TIP]  
> Si vous devez mettre à jour une application qui utilise un fournisseur de base de données tiers, recherchez toujours une mise à jour du fournisseur qui est compatible avec la version d’EF Core à utiliser. Par ex. les fournisseurs de base de données pour les versions antérieures ne sont pas compatibles avec la version 2.0 du runtime EF Core.  

> [!TIP]  
> Les applications ciblant ASP.NET Core 2.0 peuvent utiliser EF Core 2.0 sans dépendances supplémentaires en plus des fournisseurs de base de données tiers. Les applications ciblant des versions antérieures d’ASP.NET Core doivent être mises à niveau vers ASP.NET Core 2.0 pour utiliser EF Core 2.0.

<a name="cli"></a>
### <a name="cross-platform-development-using-the-net-core-command-line-interface-cli"></a>Développement multiplateforme à l’aide de l’interface de ligne de commande de base (CLI) .NET Core

Pour développer des applications qui ciblent [.NET Core](https://www.microsoft.com/net/download/core), vous pouvez choisir d’utiliser les [commandes CLI `dotnet`](https://docs.microsoft.com/dotnet/core/tools/) en combinaison avec votre éditeur de texte, ou bien un environnement de développement intégré (IDE) tel que Visual Studio, Visual Studio pour Mac ou Visual Studio Code.

> [!IMPORTANT]  
> Les applications qui ciblent .NET Core requièrent des versions spécifiques de Visual Studio, par exemple, le développement .NET Core 1.x nécessite Visual Studio 2017, tandis que le développement .NET Core 2.0 requiert Visual Studio 2017 version 15.3.

Pour installer ou mettre à niveau le fournisseur SQL Server dans une application .NET Core multiplateforme, basculez vers le répertoire de l’application et exécutez la commande suivante dans une ligne de commande :

``` Console
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

Vous pouvez indiquer une installation de version spécifique dans la commande `dotnet add package`, à l’aide du modificateur `-v`. Par ex. pour installer les packages EF Core 2.0, ajoutez `-v 2.0.0` à la commande.

EF Core comprend un ensemble de [commandes supplémentaires pour l’interface CLI `dotnet`](../../miscellaneous/cli/dotnet.md), commençant par `dotnet ef`. Pour que vous puissiez utiliser les commandes CLI `dotnet ef`, le fichier `.csproj` de votre application doit contenir l’entrée suivante :

``` xml
<ItemGroup>
  <DotNetCliToolReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="2.0.0" />
</ItemGroup>
```

Les outils CLI .NET Core pour EF Core nécessitent également un package distinct appelé Microsoft.EntityFrameworkCore.Design. Vous pouvez simplement l’ajouter au projet à l’aide de la commande suivante :

``` Console
dotnet add package Microsoft.EntityFrameworkCore.Design
```

> [!IMPORTANT]  
> Utilisez toujours des versions des packages d’outils qui correspondent à la version principale des packages du runtime.

<a name="visual-studio"></a>
### <a name="visual-studio-development"></a>Développement Visual Studio

Vous pouvez développer de nombreux types d’applications différents qui ciblent .NET Core, .NET Framework ou d’autres plateformes prises en charge par EF Core à l’aide de Visual Studio.

Vous pouvez installer un fournisseur de base de données EF Core dans votre application à partir de Visual Studio de deux façons :

#### <a name="using-nugets-package-manager-user-interfacehttpsdocsmicrosoftcomnugettoolspackage-manager-ui"></a>Utilisation de [l’interface utilisateur du Gestionnaire de package](https://docs.microsoft.com/nuget/tools/package-manager-ui) de NuGet

* Sélectionnez le menu **Projet > Gérer les packages NuGet**.

* Cliquez sur l’onglet **Parcourir** ou **Mises à jour**.

* Sélectionnez le package `Microsoft.EntityFrameworkCore.SqlServer` et la version souhaitée, puis confirmez.

#### <a name="using-nugets-package-manager-console-pmchttpsdocsmicrosoftcomnugettoolspackage-manager-console"></a>Utilisation de la [console du Gestionnaire de package](https://docs.microsoft.com/nuget/tools/package-manager-console) de NuGet.

* Sélectionnez le menu **Outils -> Gestionnaire de package NuGet -> Console du Gestionnaire de package**.

* Tapez et exécutez la commande suivante dans la console du Gestionnaire de package :

  ``` PowerShell  
  Install-Package Microsoft.EntityFrameworkCore.SqlServer
  ```
* Vous pouvez utiliser la commande `Update-Package` à la place pour mettre à jour un package qui est déjà installé dans une version plus récente.

* Pour spécifier une version spécifique, vous pouvez utiliser le modificateur `-Version` ; par exemple, pour installer des packages EF Core 2.0, ajoutez `-Version 2.0.0` aux commandes.

#### <a name="tools"></a>Outils

Il existe également dans Visual Studio une version de PowerShell des [commandes EF Core qui s’exécutent dans la console du Gestionnaire de package](../../miscellaneous/cli/powershell.md), avec des fonctionnalités similaires aux commandes `dotnet ef`. Pour utiliser ces commandes, installez le package `Microsoft.EntityFrameworkCore.Tools` à l’aide de l’interface utilisateur du Gestionnaire de package ou de la console du Gestionnaire de package.

> [!IMPORTANT]  
> Utilisez toujours des versions des packages d’outils qui correspondent à la version principale des packages du runtime.

> [!TIP]  
> Bien que vous puissiez utiliser les commandes `dotnet ef` à partir de la console du Gestionnaire de package dans Visual Studio, il est beaucoup plus pratique d’utiliser la version PowerShell :
> * Elles fonctionnent automatiquement avec le projet sélectionné dans la console du Gestionnaire de package sans que vous ayez besoin de basculer manuellement entre les répertoires.  
> * Elles ouvrent automatiquement les fichiers générés par les commandes de Visual Studio après avoir été exécutées.

> [!IMPORTANT]  
> **Packages dépréciés dans EF Core 2.0 :** si vous mettez à niveau une application existante vers EF Core 2.0, vous pouvez être amené à supprimer manuellement des références à des packages EF Core plus anciens. En particulier, les packages design-time des fournisseurs de base de données tels que `Microsoft.EntityFrameworkCore.SqlServer.Design` ne sont plus requis ou pris en charge dans EF Core 2.0, mais ils ne sont pas automatiquement supprimés durant la mise à niveau des autres packages.