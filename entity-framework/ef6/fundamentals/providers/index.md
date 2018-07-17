---
title: Fournisseurs Entity Framework - EF6
author: divega
ms.date: 2018-06-27
ms.prod: entity-framework
ms.author: divega
ms.manager: avickers
ms.technology: entity-framework-6
ms.topic: article
ms.assetid: 7BFB7763-CD6C-4520-93A2-7B265F5FA586
caps.latest.revision: 3
ms.openlocfilehash: 8bd5a5a420d741accd1167845575e23c09579ae1
ms.sourcegitcommit: 390f3a37bc55105ed7cc5b0e0925b7f9c9e80ba6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2018
ms.locfileid: "37914295"
---
# <a name="entity-framework-6-providers"></a><span data-ttu-id="57b4d-102">Fournisseurs Entity Framework 6</span><span class="sxs-lookup"><span data-stu-id="57b4d-102">Entity Framework 6 Providers</span></span>
> [!NOTE]
> <span data-ttu-id="57b4d-103">**EF6 et versions ultérieures uniquement** : Les fonctionnalités, les API, etc. décrites dans cette page ont été introduites dans Entity Framework 6.</span><span class="sxs-lookup"><span data-stu-id="57b4d-103">**EF6 Onwards Only** - The features, APIs, etc. discussed in this page were introduced in Entity Framework 6.</span></span> <span data-ttu-id="57b4d-104">Si vous utilisez une version antérieure, certaines ou toutes les informations ne s’appliquent pas.</span><span class="sxs-lookup"><span data-stu-id="57b4d-104">If you are using an earlier version, some or all of the information does not apply.</span></span>

<span data-ttu-id="57b4d-105">Entity Framework est maintenant développé sous une licence open source, et EF6 et les versions ultérieures ne font pas partie du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="57b4d-105">The Entity Framework is now being developed under an open-source license and EF6 and above will not be shipped as part of the .NET Framework.</span></span> <span data-ttu-id="57b4d-106">Cela présente de nombreux avantages, mais nécessite aussi que les fournisseurs EF soient régénérés sur les assemblys EF6.</span><span class="sxs-lookup"><span data-stu-id="57b4d-106">This has many advantages but also requires that EF providers be rebuilt against the EF6 assemblies.</span></span> <span data-ttu-id="57b4d-107">Cela signifie que les fournisseurs EF pour EF5 et les versions antérieures ne fonctionnent pas avec EF6 s’ils ne sont pas regénérés.</span><span class="sxs-lookup"><span data-stu-id="57b4d-107">This means that EF providers for EF5 and below will not work with EF6 until they have been rebuilt.</span></span>

## <a name="which-providers-are-available-for-ef6"></a><span data-ttu-id="57b4d-108">Quels sont les fournisseurs disponibles pour EF6 ?</span><span class="sxs-lookup"><span data-stu-id="57b4d-108">Which providers are available for EF6?</span></span>

<span data-ttu-id="57b4d-109">Les fournisseurs regénérés pour EF6 dont nous avons connaissance sont notamment :</span><span class="sxs-lookup"><span data-stu-id="57b4d-109">Providers we are aware of that have been rebuilt for EF6 include:</span></span>

*   <span data-ttu-id="57b4d-110">**Fournisseur Microsoft SQL Server**</span><span class="sxs-lookup"><span data-stu-id="57b4d-110">**Microsoft SQL Server provider**</span></span>
    *   <span data-ttu-id="57b4d-111">Généré à partir de la [base de code open source Entity Framework](http://github.com/aspnet/EntityFramework6)</span><span class="sxs-lookup"><span data-stu-id="57b4d-111">Built from the [Entity Framework open source code base](http://github.com/aspnet/EntityFramework6)</span></span>
    *   <span data-ttu-id="57b4d-112">Partie intégrante du [package NuGet EntityFramework](http://nuget.org/packages/EntityFramework)</span><span class="sxs-lookup"><span data-stu-id="57b4d-112">Shipped as part of the [EntityFramework NuGet package](http://nuget.org/packages/EntityFramework)</span></span>
*   <span data-ttu-id="57b4d-113">**Fournisseur de l’édition Microsoft SQL Server Compact**</span><span class="sxs-lookup"><span data-stu-id="57b4d-113">**Microsoft SQL Server Compact Edition provider**</span></span>
    *   <span data-ttu-id="57b4d-114">Généré à partir de la [base de code open source Entity Framework](http://github.com/aspnet/EntityFramework6)</span><span class="sxs-lookup"><span data-stu-id="57b4d-114">Built from the [Entity Framework open source code base](http://github.com/aspnet/EntityFramework6)</span></span>
    *   <span data-ttu-id="57b4d-115">Partie intégrante du [package NuGet EntityFramework.SqlServerCompact](http://nuget.org/packages/EntityFramework.SqlServerCompact)</span><span class="sxs-lookup"><span data-stu-id="57b4d-115">Shipped in the [EntityFramework.SqlServerCompact NuGet package](http://nuget.org/packages/EntityFramework.SqlServerCompact)</span></span>
*   [<span data-ttu-id="57b4d-116">**Fournisseurs de données Devart dotConnect** </span><span class="sxs-lookup"><span data-stu-id="57b4d-116">**Devart dotConnect Data Providers**</span></span>](http://www.devart.com/dotconnect/)
    *   <span data-ttu-id="57b4d-117">Il existe des fournisseurs tiers de [Devart](http://www.devart.com/) pour diverses bases de données, notamment Oracle, MySQL, PostgreSQL, SQLite, Salesforce, DB2 et SQL Server</span><span class="sxs-lookup"><span data-stu-id="57b4d-117">There are third-party providers from [Devart](http://www.devart.com/) for a variety of databases including Oracle, MySQL, PostgreSQL, SQLite, Salesforce, DB2, and SQL Server</span></span>
*   [<span data-ttu-id="57b4d-118">**Fournisseurs de logiciels CData**</span><span class="sxs-lookup"><span data-stu-id="57b4d-118">**CData Software providers**</span></span>](http://www.cdata.com/ado/)
    *   <span data-ttu-id="57b4d-119">Il existe des fournisseurs tiers de [logiciels CData](http://www.cdata.com/ado/) pour divers magasin de données, notamment Salesforce, Stockage Table Azure, MySql et bien plus encore</span><span class="sxs-lookup"><span data-stu-id="57b4d-119">There are third-party providers from [CData Software](http://www.cdata.com/ado/) for a variety of data stores including Salesforce, Azure Table Storage, MySql, and many more</span></span>
*   <span data-ttu-id="57b4d-120">**Fournisseur Firebird**</span><span class="sxs-lookup"><span data-stu-id="57b4d-120">**Firebird provider**</span></span>
    *   <span data-ttu-id="57b4d-121">Disponible sous forme de [package NuGet](http://www.nuget.org/packages/FirebirdSql.Data.FirebirdClient/)</span><span class="sxs-lookup"><span data-stu-id="57b4d-121">Available as a [NuGet Package](http://www.nuget.org/packages/FirebirdSql.Data.FirebirdClient/)</span></span>
*   <span data-ttu-id="57b4d-122">**Fournisseur Visual Fox Pro**</span><span class="sxs-lookup"><span data-stu-id="57b4d-122">**Visual Fox Pro provider**</span></span>
    *   <span data-ttu-id="57b4d-123">Disponible sous forme de [package NuGet](https://www.nuget.org/packages/VFPEntityFrameworkProvider2/)</span><span class="sxs-lookup"><span data-stu-id="57b4d-123">Available as a [NuGet package](https://www.nuget.org/packages/VFPEntityFrameworkProvider2/)</span></span>
*   <span data-ttu-id="57b4d-124">**MySQL**</span><span class="sxs-lookup"><span data-stu-id="57b4d-124">**MySQL**</span></span>
    *   [<span data-ttu-id="57b4d-125">Connecteur MySQL/Net</span><span class="sxs-lookup"><span data-stu-id="57b4d-125">MySQL Connector/Net</span></span>](http://dev.mysql.com/downloads/connector/net/)
*   <span data-ttu-id="57b4d-126">**PostgreSQL**</span><span class="sxs-lookup"><span data-stu-id="57b4d-126">**PostgreSQL**</span></span>
    *   <span data-ttu-id="57b4d-127">Npgsql est disponible sous forme de [package NuGet](http://www.nuget.org/packages/Npgsql.EF6/)</span><span class="sxs-lookup"><span data-stu-id="57b4d-127">Npgsql is available as a [NuGet package](http://www.nuget.org/packages/Npgsql.EF6/)</span></span>
*   <span data-ttu-id="57b4d-128">**Oracle**</span><span class="sxs-lookup"><span data-stu-id="57b4d-128">**Oracle**</span></span>
    *   <span data-ttu-id="57b4d-129">ODP.NET est disponible sous forme de [package NuGet](https://www.nuget.org/packages/Oracle.ManagedDataAccess.EntityFramework/)</span><span class="sxs-lookup"><span data-stu-id="57b4d-129">ODP.NET is available as a [NuGet package](https://www.nuget.org/packages/Oracle.ManagedDataAccess.EntityFramework/)</span></span>

<span data-ttu-id="57b4d-130">Notez que le niveau de fonctionnalité ou de prise en charge n’est pas indiqué pour un fournisseur donné, la liste indique uniquement qu’une build pour EF6 a été rendue disponible.</span><span class="sxs-lookup"><span data-stu-id="57b4d-130">Note that inclusion in this list does not indicate the level of functionality or support for a given provider, only that a build for EF6 has been made available.</span></span>

## <a name="registering-ef-providers"></a><span data-ttu-id="57b4d-131">Inscription de fournisseurs EF</span><span class="sxs-lookup"><span data-stu-id="57b4d-131">Registering EF providers</span></span>

<span data-ttu-id="57b4d-132">À partir d’Entity Framework 6, les fournisseurs EF peuvent être inscrits à l’aide d’une configuration basée sur le code ou dans le fichier config de l’application.</span><span class="sxs-lookup"><span data-stu-id="57b4d-132">Starting with Entity Framework 6 EF providers can be registered using either code-based configuration or in the application’s config file.</span></span>

### <a name="config-file-registration"></a><span data-ttu-id="57b4d-133">Inscription dans le fichier config</span><span class="sxs-lookup"><span data-stu-id="57b4d-133">Config file registration</span></span>

<span data-ttu-id="57b4d-134">L’inscription du fournisseur EF dans le fichier app.config ou web.config a le format suivant :</span><span class="sxs-lookup"><span data-stu-id="57b4d-134">Registration of the EF provider in app.config or web.config has the following format:</span></span>


``` xml
    <entityFramework>
       <providers>
         <provider invariantName="My.Invariant.Name" type="MyProvider.MyProviderServices, MyAssembly" />
       </providers>
    </entityFramework>
```

<span data-ttu-id="57b4d-135">Notez que, souvent, si le fournisseur EF est installé à partir de NuGet, le package NuGet ajoute automatiquement cette inscription au fichier config.</span><span class="sxs-lookup"><span data-stu-id="57b4d-135">Note that often if the EF provider is installed from NuGet, then the NuGet package will automatically add this registration to the config file.</span></span> <span data-ttu-id="57b4d-136">Si vous installez le package NuGet dans un projet qui n’est pas le projet de démarrage de votre application, vous devez peut-être copier l’inscription dans le fichier config de votre projet de démarrage.</span><span class="sxs-lookup"><span data-stu-id="57b4d-136">If you install the NuGet package into a project that is not the startup project for your app, then you may need to copy the registration into the config file for your startup project.</span></span>

<span data-ttu-id="57b4d-137">Le paramètre « InvariantName » dans cette inscription est le même nom invariant que celui utilisé pour identifier un fournisseur ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="57b4d-137">The “invariantName” in this registration is the same invariant name used to identify an ADO.NET provider.</span></span> <span data-ttu-id="57b4d-138">Il s’agit de l’attribut « invariant » dans une inscription DbProviderFactories et de l’attribut « providerName » dans une inscription de chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="57b4d-138">This can be found as the “invariant” attribute in a DbProviderFactories registration and as the “providerName” attribute in a connection string registration.</span></span> <span data-ttu-id="57b4d-139">Le nom invariant à utiliser doit également se trouver dans la documentation du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="57b4d-139">The invariant name to use should also be included in documentation for the provider.</span></span> <span data-ttu-id="57b4d-140">« System.Data.SqlClient » pour SQL Server et « System.Data.SqlServerCe.4.0 » pour SQL Server Compact sont des exemples de noms invariants.</span><span class="sxs-lookup"><span data-stu-id="57b4d-140">Examples of invariant names are “System.Data.SqlClient” for SQL Server and “System.Data.SqlServerCe.4.0” for SQL Server Compact.</span></span>

<span data-ttu-id="57b4d-141">Le « type » dans cette inscription est le nom qualifié d’assembly du type de fournisseur qui dérive de « System.Data.Entity.Core.Common.DbProviderServices ».</span><span class="sxs-lookup"><span data-stu-id="57b4d-141">The “type” in this registration is the assembly-qualified name of the provider type that derives from “System.Data.Entity.Core.Common.DbProviderServices”.</span></span> <span data-ttu-id="57b4d-142">Par exemple, la chaîne à utiliser pour SQL Compact est « System.Data.Entity.SqlServerCompact.SqlCeProviderServices EntityFramework.SqlServerCompact ».</span><span class="sxs-lookup"><span data-stu-id="57b4d-142">For example, the string to use for SQL Compact is “System.Data.Entity.SqlServerCompact.SqlCeProviderServices, EntityFramework.SqlServerCompact”.</span></span> <span data-ttu-id="57b4d-143">Le type à utiliser ici doit se trouver dans la documentation du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="57b4d-143">The type to use here should be included in documentation for the provider.</span></span>

### <a name="code-based-registration"></a><span data-ttu-id="57b4d-144">Inscription basée sur le code</span><span class="sxs-lookup"><span data-stu-id="57b4d-144">Code-based registration</span></span>

<span data-ttu-id="57b4d-145">À partir d’Entity Framework 6, la configuration d’EF au niveau de l’application peut être spécifiée dans le code.</span><span class="sxs-lookup"><span data-stu-id="57b4d-145">Starting with Entity Framework 6 application-wide configuration for EF can be specified in code.</span></span> <span data-ttu-id="57b4d-146">Pour des détails complets, consultez _[Configuration d’Entity Framework basée sur le code](https://msdn.microsoft.com/en-us/data/jj680699)_.</span><span class="sxs-lookup"><span data-stu-id="57b4d-146">For full details see _[Entity Framework Code-Based Configuration](https://msdn.microsoft.com/en-us/data/jj680699)_.</span></span> <span data-ttu-id="57b4d-147">La méthode normale pour inscrire un fournisseur EF à l’aide d’une configuration basée sur le code est de créer une classe dérivant de System.Data.Entity.DbConfiguration et de la placer dans le même assembly que votre classe DbContext.</span><span class="sxs-lookup"><span data-stu-id="57b4d-147">The normal way to register an EF provider using code-based configuration is to create a new class that derives from System.Data.Entity.DbConfiguration and place it in the same assembly as your DbContext class.</span></span> <span data-ttu-id="57b4d-148">Votre classe DbConfiguration doit ensuite inscrire le fournisseur dans son constructeur.</span><span class="sxs-lookup"><span data-stu-id="57b4d-148">Your DbConfiguration class should then register the provider in its constructor.</span></span> <span data-ttu-id="57b4d-149">Par exemple, pour inscrire le fournisseur SQL Compact, la classe DbConfiguration ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="57b4d-149">For example, to register the SQL Compact provider the DbConfiguration class looks like this:</span></span>

``` csharp
    public class MyConfiguration : DbConfiguration
    {
        public MyConfiguration()
        {
            SetProviderServices(
                SqlCeProviderServices.ProviderInvariantName,
                SqlCeProviderServices.Instance);
        }
    }
```

<span data-ttu-id="57b4d-150">Dans ce code « SqlCeProviderServices.ProviderInvariantName » représente la chaîne du nom invariant du fournisseur SQL Server Compact (« System.Data.SqlServerCe.4.0 ») et SqlCeProviderServices.Instance retourne l’instance singleton du fournisseur EF SQL Compact.</span><span class="sxs-lookup"><span data-stu-id="57b4d-150">In this code “SqlCeProviderServices.ProviderInvariantName” is a convenience for the SQL Server Compact provider invariant name string (“System.Data.SqlServerCe.4.0”) and SqlCeProviderServices.Instance returns the singleton instance of the SQL Compact EF provider.</span></span>

## <a name="what-if-the-provider-i-need-isnt-available"></a><span data-ttu-id="57b4d-151">Que faire si le fournisseur dont j’ai besoin n’est pas disponible ?</span><span class="sxs-lookup"><span data-stu-id="57b4d-151">What if the provider I need isn’t available?</span></span>

<span data-ttu-id="57b4d-152">Si le fournisseur est disponible pour les versions précédentes d’EF, nous vous encourageons à contacter le propriétaire du fournisseur et lui demander de créer une version EF6.</span><span class="sxs-lookup"><span data-stu-id="57b4d-152">If the provider is available for previous versions of EF, then we encourage you to contact the owner of the provider and ask them to create an EF6 version.</span></span> <span data-ttu-id="57b4d-153">Vous devez indiquer une référence à la [documentation du modèle de fournisseur EF6](~/ef6/fundamentals/providers/provider-model.md).</span><span class="sxs-lookup"><span data-stu-id="57b4d-153">You should include a reference to the [documentation for the EF6 provider model](~/ef6/fundamentals/providers/provider-model.md).</span></span>

## <a name="can-i-write-a-provider-myself"></a><span data-ttu-id="57b4d-154">Puis-je écrire un fournisseur moi-même ?</span><span class="sxs-lookup"><span data-stu-id="57b4d-154">Can I write a provider myself?</span></span>

<span data-ttu-id="57b4d-155">Il est tout à fait possible de créer un fournisseur EF vous-même, bien que ce ne soit pas une opération quelconque.</span><span class="sxs-lookup"><span data-stu-id="57b4d-155">It is certainly possible to create an EF provider yourself although it should not be considered a trivial undertaking.</span></span> <span data-ttu-id="57b4d-156">Le lien ci-dessus concernant le modèle de fournisseur EF6 est un bon point de départ.</span><span class="sxs-lookup"><span data-stu-id="57b4d-156">The the link above about the EF6 provider model is a good place to start.</span></span> <span data-ttu-id="57b4d-157">Vous pouvez aussi utiliser le code du fournisseur SQL Server et SQL CE inclus dans la [base de code open source EF](https://github.com/aspnet/EntityFramework6) comme point de départ ou de référence.</span><span class="sxs-lookup"><span data-stu-id="57b4d-157">You may also find it useful to use the code for the SQL Server and SQL CE provider included in the [EF open source codebase](https://github.com/aspnet/EntityFramework6) as a starting point or for reference.</span></span>

<span data-ttu-id="57b4d-158">Notez qu’à partir d’EF6, le fournisseur EF dépend moins du fournisseur ADO.NET sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="57b4d-158">Note that starting with EF6 the EF provider is less tightly coupled to the underlying ADO.NET provider.</span></span> <span data-ttu-id="57b4d-159">Vous pouvez donc plus facilement écrire un fournisseur EF sans écrire ou wrapper les classes ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="57b4d-159">This makes it easier to write an EF provider without needing to write or wrap the ADO.NET classes.</span></span>