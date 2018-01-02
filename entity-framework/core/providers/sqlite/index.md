---
title: "Fournisseur de base de données SQLite - EF Core"
author: rowanmiller
ms.author: divega
ms.date: 10/27/2016
ms.assetid: 3e2f7698-fec2-4cec-9e2d-2e3e0074120c
ms.technology: entity-framework-core
uid: core/providers/sqlite/index
ms.openlocfilehash: 0f3905a491fb5f7a657ce9037d166771e1f326d8
ms.sourcegitcommit: 5e2d97e731f975cf3405ff3deab2a3c75ad1b969
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="sqlite-ef-core-database-provider"></a>Fournisseur de base de données EF Core SQLite

Ce fournisseur de base de données permet d’utiliser Entity Framework Core avec SQLite. Il est géré dans le cadre du [projet GitHub EntityFramework](https://github.com/aspnet/EntityFramework).

## <a name="install"></a>Installer

Installez le [package NuGet Microsoft.EntityFrameworkCore.Sqlite](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.Sqlite/).

``` powershell
Install-Package Microsoft.EntityFrameworkCore.Sqlite
```

## <a name="get-started"></a>Bien démarrer

Les ressources suivantes vous permettent de commencer à utiliser ce fournisseur.
* [Base de données SQLite locale sur UWP](../../get-started/uwp/getting-started.md)

* [Application .NET Core avec une nouvelle base de données SQLite](../../get-started/netcore/new-db-sqlite.md)

* [Exemple d’application Unicorn Clicker](https://github.com/rowanmiller/UnicornStore/tree/master/UnicornClicker/UWP)

* [Exemple d’application Unicorn Packer](https://github.com/rowanmiller/UnicornStore/tree/master/UnicornPacker)

## <a name="supported-database-engines"></a>Moteurs de base de données pris en charge

* SQLite (versions 3.7 et suivantes)

## <a name="supported-platforms"></a>Plateformes prises en charge

* .NET Framework (versions 4.5.1 et suivantes)

* .NET Core

* Mono (versions 4.2.0 et suivantes)

* Plateforme Windows universelle

## <a name="limitations"></a>Limitations

Consultez [Limitations de SQLite](limitations.md) pour connaître certaines limitations importantes du fournisseur SQLite.