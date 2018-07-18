---
title: Requêtes SQL brutes - EF6
author: divega
ms.date: 2016-10-23
ms.prod: entity-framework
ms.author: divega
ms.manager: avickers
ms.technology: entity-framework-6
ms.topic: article
ms.assetid: 9e1ee76e-2499-408c-81e8-9b6c5d1945a0
caps.latest.revision: 3
ms.openlocfilehash: 1d968604cfa500784c4699b0923512572a06d773
ms.sourcegitcommit: f05e7b62584cf228f17390bb086a61d505712e1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2018
ms.locfileid: "39121133"
---
# <a name="raw-sql-queries"></a><span data-ttu-id="9dd3d-102">Requêtes SQL brutes</span><span class="sxs-lookup"><span data-stu-id="9dd3d-102">Raw SQL Queries</span></span>
<span data-ttu-id="9dd3d-103">Entity Framework vous permet d’interroger à l’aide de LINQ avec vos classes d’entité.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-103">Entity Framework allows you to query using LINQ with your entity classes.</span></span> <span data-ttu-id="9dd3d-104">Toutefois, il peut arriver que vous souhaitez exécuter des requêtes à l’aide de requêtes SQL brutes directement par rapport à la base de données.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-104">However, there may be times that you want to run queries using raw SQL directly against the database.</span></span> <span data-ttu-id="9dd3d-105">Cela inclut l’appel de procédures stockées, qui peuvent être utiles pour les modèles de Code First qui ne prennent actuellement pas en charge le mappage à des procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-105">This includes calling stored procedures, which can be helpful for Code First models that currently do not support mapping to stored procedures.</span></span> <span data-ttu-id="9dd3d-106">Les techniques présentées dans cette rubrique s’appliquent également aux modèles créés avec Code First et EF Designer.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-106">The techniques shown in this topic apply equally to models created with Code First and the EF Designer.</span></span>  

## <a name="writing-sql-queries-for-entities"></a><span data-ttu-id="9dd3d-107">Écriture de requêtes SQL pour les entités</span><span class="sxs-lookup"><span data-stu-id="9dd3d-107">Writing SQL queries for entities</span></span>  

<span data-ttu-id="9dd3d-108">La méthode SqlQuery sur DbSet permet à une requête SQL brute à écrire qui retournera des instances d’entité.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-108">The SqlQuery method on DbSet allows a raw SQL query to be written that will return entity instances.</span></span> <span data-ttu-id="9dd3d-109">Les objets retournés sont suivis par le contexte comme ils le seraient si elles ont été retournées par une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-109">The returned objects will be tracked by the context just as they would be if they were returned by a LINQ query.</span></span> <span data-ttu-id="9dd3d-110">Exemple :</span><span class="sxs-lookup"><span data-stu-id="9dd3d-110">For example:</span></span>  

``` csharp  
using (var context = new BloggingContext())
{
    var blogs = context.Blogs.SqlQuery("SELECT * FROM dbo.Blogs").ToList();
}
```  

<span data-ttu-id="9dd3d-111">Notez que, comme pour les requêtes LINQ, la requête n'est pas exécutée jusqu'à ce que les résultats sont énumérés, dans l’exemple ci-dessus, cela est effectué avec l’appel à ToList.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-111">Note that, just as for LINQ queries, the query is not executed until the results are enumerated—in the example above this is done with the call to ToList.</span></span>  

<span data-ttu-id="9dd3d-112">Soyez attentif à chaque fois que les requêtes SQL brutes sont écrits pour deux raisons.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-112">Care should be taken whenever raw SQL queries are written for two reasons.</span></span> <span data-ttu-id="9dd3d-113">Tout d’abord, la requête doit être écrite pour vous assurer qu’elle renvoie uniquement les entités qui sont réellement du type demandé.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-113">First, the query should be written to ensure that it only returns entities that are really of the requested type.</span></span> <span data-ttu-id="9dd3d-114">Par exemple, lors de l’utilisation des fonctionnalités telles que l’héritage, il est facile d’écrire une requête qui crée des entités qui ont le type CLR approprié.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-114">For example, when using features such as inheritance it is easy to write a query that will create entities that are of the wrong CLR type.</span></span>  

<span data-ttu-id="9dd3d-115">En second lieu, certains types de requêtes SQL brutes exposent à des risques de sécurité potentiels, notamment concernant les attaques par injection SQL.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-115">Second, some types of raw SQL query expose potential security risks, especially around SQL injection attacks.</span></span> <span data-ttu-id="9dd3d-116">Assurez-vous que vous utilisez des paramètres dans votre requête dans la méthode correcte pour protéger contre ces attaques.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-116">Make sure that you use parameters in your query in the correct way to guard against such attacks.</span></span>  

### <a name="loading-entities-from-stored-procedures"></a><span data-ttu-id="9dd3d-117">Chargement d’entités à partir de procédures stockées</span><span class="sxs-lookup"><span data-stu-id="9dd3d-117">Loading entities from stored procedures</span></span>  

<span data-ttu-id="9dd3d-118">Vous pouvez utiliser DbSet.SqlQuery pour charger des entités à partir des résultats d’une procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-118">You can use DbSet.SqlQuery to load entities from the results of a stored procedure.</span></span> <span data-ttu-id="9dd3d-119">Par exemple, le code suivant appelle le dbo. Procédure GetBlogs dans la base de données :</span><span class="sxs-lookup"><span data-stu-id="9dd3d-119">For example, the following code calls the dbo.GetBlogs procedure in the database:</span></span>  

``` csharp
using (var context = new BloggingContext())
{
    var blogs = context.Blogs.SqlQuery("dbo.GetBlogs").ToList();
}
```  

<span data-ttu-id="9dd3d-120">Vous pouvez également transmettre des paramètres à une procédure stockée à l’aide de la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="9dd3d-120">You can also pass parameters to a stored procedure using the following syntax:</span></span>  

``` csharp
using (var context = new BloggingContext())
{
    var blogId = 1;

    var blogs = context.Blogs.SqlQuery("dbo.GetBlogById @p0", blogId).Single();
}
```  

## <a name="writing-sql-queries-for-non-entity-types"></a><span data-ttu-id="9dd3d-121">Écriture de requêtes SQL pour les types de non-entité</span><span class="sxs-lookup"><span data-stu-id="9dd3d-121">Writing SQL queries for non-entity types</span></span>  

<span data-ttu-id="9dd3d-122">Une requête SQL renvoie des instances de n’importe quel type, y compris les types primitifs, peut être créée à l’aide de la méthode SqlQuery sur la classe de base de données.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-122">A SQL query returning instances of any type, including primitive types, can be created using the SqlQuery method on the Database class.</span></span> <span data-ttu-id="9dd3d-123">Exemple :</span><span class="sxs-lookup"><span data-stu-id="9dd3d-123">For example:</span></span>  

``` csharp
using (var context = new BloggingContext())
{
    var blogNames = context.Database.SqlQuery<string>(
                       "SELECT Name FROM dbo.Blogs").ToList();
}
```  

<span data-ttu-id="9dd3d-124">Les résultats retournés par SqlQuery sur la base de données ne sont jamais suivis par le contexte même si les objets sont des instances d’un type d’entité.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-124">The results returned from SqlQuery on Database will never be tracked by the context even if the objects are instances of an entity type.</span></span>  

## <a name="sending-raw-commands-to-the-database"></a><span data-ttu-id="9dd3d-125">Envoi de commandes à la base de données brutes</span><span class="sxs-lookup"><span data-stu-id="9dd3d-125">Sending raw commands to the database</span></span>  

<span data-ttu-id="9dd3d-126">Commandes de non-requête peuvent être envoyés à la base de données à l’aide de la méthode ExecuteSqlCommand sur la base de données.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-126">Non-query commands can be sent to the database using the ExecuteSqlCommand method on Database.</span></span> <span data-ttu-id="9dd3d-127">Exemple :</span><span class="sxs-lookup"><span data-stu-id="9dd3d-127">For example:</span></span>  

``` csharp
using (var context = new BloggingContext())
{
    context.Database.ExecuteSqlCommand(
        "UPDATE dbo.Blogs SET Name = 'Another Name' WHERE BlogId = 1");
}
```  

<span data-ttu-id="9dd3d-128">Notez que toutes les modifications apportées aux données dans la base de données à l’aide de ExecuteSqlCommand sont opaques pour le contexte jusqu'à ce que les entités chargées ou rechargées à partir de la base de données.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-128">Note that any changes made to data in the database using ExecuteSqlCommand are opaque to the context until entities are loaded or reloaded from the database.</span></span>  

### <a name="output-parameters"></a><span data-ttu-id="9dd3d-129">Paramètres de sortie</span><span class="sxs-lookup"><span data-stu-id="9dd3d-129">Output Parameters</span></span>  

<span data-ttu-id="9dd3d-130">Si les paramètres de sortie sont utilisés, leurs valeurs ne sera pas disponibles jusqu'à ce que les résultats ont été lues entièrement.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-130">If output parameters are used, their values will not be available until the results have been read completely.</span></span> <span data-ttu-id="9dd3d-131">Il s’agit en raison du comportement sous-jacent de DbDataReader, consultez [extraction de données à l’aide d’un DataReader](http://go.microsoft.com/fwlink/?LinkID=398589) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-131">This is due to the underlying behavior of DbDataReader, see [Retrieving Data Using a DataReader](http://go.microsoft.com/fwlink/?LinkID=398589) for more details.</span></span>  