---
title: Entity Framework glossaire - EF6
author: divega
ms.date: 2016-10-23
ms.prod: entity-framework
ms.author: divega
ms.manager: avickers
ms.technology: entity-framework-6
ms.topic: article
ms.assetid: 3f05ffdd-49bc-499c-9732-4a368bf5d2d7
caps.latest.revision: 3
ms.openlocfilehash: cbd61838afc23dfb37cee7c624c65476c5270099
ms.sourcegitcommit: bdd06c9a591ba5e6d6a3ec046c80de98f598f3f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "39121458"
---
# <a name="entity-framework-glossary"></a><span data-ttu-id="47c41-102">Entity Framework glossaire</span><span class="sxs-lookup"><span data-stu-id="47c41-102">Entity Framework Glossary</span></span>
## <a name="code-first"></a><span data-ttu-id="47c41-103">Code First</span><span class="sxs-lookup"><span data-stu-id="47c41-103">Code First</span></span>
<span data-ttu-id="47c41-104">Création d’un modèle Entity Framework à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="47c41-104">Creating an Entity Framework model using code.</span></span> <span data-ttu-id="47c41-105">Le modèle peut cibler et base de données existante ou une base de données.</span><span class="sxs-lookup"><span data-stu-id="47c41-105">The model can target and existing database or a new database.</span></span>

## <a name="context"></a><span data-ttu-id="47c41-106">Contexte</span><span class="sxs-lookup"><span data-stu-id="47c41-106">Context</span></span>
<span data-ttu-id="47c41-107">Une classe qui représente une session avec la base de données, ce qui vous permet d’interroger et d’enregistrer des données.</span><span class="sxs-lookup"><span data-stu-id="47c41-107">A class that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="47c41-108">Un contexte dérive de la classe DbContext ou ObjectContext.</span><span class="sxs-lookup"><span data-stu-id="47c41-108">A context derives from the DbContext or ObjectContext class.</span></span>

## <a name="convention-code-first"></a><span data-ttu-id="47c41-109">Convention (Code First)</span><span class="sxs-lookup"><span data-stu-id="47c41-109">Convention (Code First)</span></span>
<span data-ttu-id="47c41-110">Une règle qui utilise de Entity Framework pour déduire la forme de modèle vous à partir de vos classes.</span><span class="sxs-lookup"><span data-stu-id="47c41-110">A rule that Entity Framework uses to infer the shape of you model from your classes.</span></span>

## <a name="database-first"></a><span data-ttu-id="47c41-111">Tout d’abord la base de données</span><span class="sxs-lookup"><span data-stu-id="47c41-111">Database First</span></span>
<span data-ttu-id="47c41-112">Création d’un modèle Entity Framework, à l’aide du Concepteur EF, qui cible une base de données existante.</span><span class="sxs-lookup"><span data-stu-id="47c41-112">Creating an Entity Framework model, using the EF Designer, that targets an existing database.</span></span>

## <a name="eager-loading"></a><span data-ttu-id="47c41-113">Chargement hâtif</span><span class="sxs-lookup"><span data-stu-id="47c41-113">Eager loading</span></span>
<span data-ttu-id="47c41-114">Modèle de chargement des données associées dans lequel une requête pour un type d’entité charge également les entités associées dans le cadre de la requête.</span><span class="sxs-lookup"><span data-stu-id="47c41-114">A pattern of loading related data where a query for one type of entity also loads related entities as part of the query.</span></span>

## <a name="ef-designer"></a><span data-ttu-id="47c41-115">Entity Framework Designer</span><span class="sxs-lookup"><span data-stu-id="47c41-115">EF Designer</span></span>
<span data-ttu-id="47c41-116">Un concepteur visuel dans Visual Studio qui vous permet de créer un modèle Entity Framework à l’aide de zones et des lignes.</span><span class="sxs-lookup"><span data-stu-id="47c41-116">A visual designer in Visual Studio that allows you to create an Entity Framework model using boxes and lines.</span></span>

## <a name="entity"></a><span data-ttu-id="47c41-117">Entité</span><span class="sxs-lookup"><span data-stu-id="47c41-117">Entity</span></span>
<span data-ttu-id="47c41-118">Classe ou objet qui représente des données d'application, telles que des clients, des produits et des commandes.</span><span class="sxs-lookup"><span data-stu-id="47c41-118">A class or object that represents application data such as customers, products, and orders.</span></span>

## <a name="entity-data-model"></a><span data-ttu-id="47c41-119">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="47c41-119">Entity Data Model</span></span>
<span data-ttu-id="47c41-120">Un modèle qui décrit les entités et les relations entre eux.</span><span class="sxs-lookup"><span data-stu-id="47c41-120">A model that describes entities and the relationships between them.</span></span> <span data-ttu-id="47c41-121">EF utilise le modèle EDM pour décrire le modèle conceptuel par rapport à laquelle les programmes de développement.</span><span class="sxs-lookup"><span data-stu-id="47c41-121">EF uses EDM to describe the conceptual model against which the developer programs.</span></span> <span data-ttu-id="47c41-122">EDM s’appuie sur le modèle entité-relation introduit par la récupération d’urgence. Peter Chen.</span><span class="sxs-lookup"><span data-stu-id="47c41-122">EDM builds on the Entity Relationship model introduced by Dr. Peter Chen.</span></span> <span data-ttu-id="47c41-123">Le modèle EDM a été développé avec pour principal objectif de devenir le common data model travers une suite de technologies de serveurs et les développeurs de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="47c41-123">The EDM was originally developed with the primary goal of becoming the common data model across a suite of developer and server technologies from Microsoft.</span></span> <span data-ttu-id="47c41-124">EDM est également utilisé dans le cadre du protocole OData.</span><span class="sxs-lookup"><span data-stu-id="47c41-124">EDM is also used as part of the OData protocol.</span></span>

## <a name="explicit-loading"></a><span data-ttu-id="47c41-125">Chargement explicite</span><span class="sxs-lookup"><span data-stu-id="47c41-125">Explicit loading</span></span>
<span data-ttu-id="47c41-126">Modèle de chargement des données associées dans lequel les objets connexes sont chargés en appelant une API.</span><span class="sxs-lookup"><span data-stu-id="47c41-126">A pattern of loading related data where related objects are loaded by calling an API.</span></span>

## <a name="fluent-api"></a><span data-ttu-id="47c41-127">API Fluent</span><span class="sxs-lookup"><span data-stu-id="47c41-127">Fluent API</span></span>
<span data-ttu-id="47c41-128">Une API qui peut être utilisée pour configurer un modèle Code First.</span><span class="sxs-lookup"><span data-stu-id="47c41-128">An API that can be used to configure a Code First model.</span></span>

## <a name="foreign-key-association"></a><span data-ttu-id="47c41-129">Association de clé étrangère</span><span class="sxs-lookup"><span data-stu-id="47c41-129">Foreign key association</span></span>
<span data-ttu-id="47c41-130">Une association entre entités où une propriété qui représente la clé étrangère est incluse dans la classe de l’entité dépendante.</span><span class="sxs-lookup"><span data-stu-id="47c41-130">An association between entities where a property that represents the foreign key is included in the class of the dependent entity.</span></span> <span data-ttu-id="47c41-131">Par exemple, le produit contient une propriété CategoryId.</span><span class="sxs-lookup"><span data-stu-id="47c41-131">For example, Product contains a CategoryId property.</span></span>

## <a name="identifying-relationship"></a><span data-ttu-id="47c41-132">Relation d’identification</span><span class="sxs-lookup"><span data-stu-id="47c41-132">Identifying relationship</span></span>
<span data-ttu-id="47c41-133">Relation où la clé primaire de l'entité principale fait également partie de la clé primaire de l'entité dépendante.</span><span class="sxs-lookup"><span data-stu-id="47c41-133">A relationship where the primary key of the principal entity is part of the primary key of the dependent entity.</span></span> <span data-ttu-id="47c41-134">Dans ce type de relation, l'entité dépendante ne peut pas exister dans l'entité principale.</span><span class="sxs-lookup"><span data-stu-id="47c41-134">In this kind of relationship, the dependent entity cannot exist without the principal entity.</span></span>

## <a name="independent-association"></a><span data-ttu-id="47c41-135">Association indépendante</span><span class="sxs-lookup"><span data-stu-id="47c41-135">Independent association</span></span>
<span data-ttu-id="47c41-136">Une association entre entités où il n’existe aucune propriété qui représente la clé étrangère dans la classe de l’entité dépendante.</span><span class="sxs-lookup"><span data-stu-id="47c41-136">An association between entities where there is no property representing the foreign key in the class of the dependent entity.</span></span> <span data-ttu-id="47c41-137">Par exemple, une classe de produit contient une relation à la catégorie, mais aucune propriété CategoryId.</span><span class="sxs-lookup"><span data-stu-id="47c41-137">For example, a Product class contains a relationship to Category but no CategoryId property.</span></span> <span data-ttu-id="47c41-138">Entity Framework effectue le suivi de l’état de l’association indépendamment de l’état des entités au niveau des terminaisons d’association de deux.</span><span class="sxs-lookup"><span data-stu-id="47c41-138">Entity Framework tracks the state of the association independently of the state of the entities at the two association ends.</span></span>

## <a name="lazy-loading"></a><span data-ttu-id="47c41-139">Chargement différé</span><span class="sxs-lookup"><span data-stu-id="47c41-139">Lazy loading</span></span>
<span data-ttu-id="47c41-140">Modèle de chargement des données associées dans lequel les objets connexes sont chargés automatiquement lors de l’accès à une propriété de navigation.</span><span class="sxs-lookup"><span data-stu-id="47c41-140">A pattern of loading related data where related objects are automatically loaded when a navigation property is accessed.</span></span>

## <a name="model-first"></a><span data-ttu-id="47c41-141">Tout d’abord de modèle</span><span class="sxs-lookup"><span data-stu-id="47c41-141">Model First</span></span>
<span data-ttu-id="47c41-142">Création d’un modèle Entity Framework, à l’aide du Concepteur EF, qui est ensuite utilisé pour créer une base de données.</span><span class="sxs-lookup"><span data-stu-id="47c41-142">Creating an Entity Framework model, using the EF Designer, that is then used to create a new database.</span></span>

## <a name="navigation-property"></a><span data-ttu-id="47c41-143">Propriété de navigation</span><span class="sxs-lookup"><span data-stu-id="47c41-143">Navigation property</span></span>
<span data-ttu-id="47c41-144">Une propriété d’une entité qui fait référence à une autre entité.</span><span class="sxs-lookup"><span data-stu-id="47c41-144">A property of an entity that references another entity.</span></span> <span data-ttu-id="47c41-145">Par exemple, produit contient une propriété de navigation de catégorie et catégorie contient une propriété de navigation de produits.</span><span class="sxs-lookup"><span data-stu-id="47c41-145">For example, Product contains a Category navigation property and Category contains a Products navigation property.</span></span>

## <a name="poco"></a><span data-ttu-id="47c41-146">POCO</span><span class="sxs-lookup"><span data-stu-id="47c41-146">POCO</span></span>
<span data-ttu-id="47c41-147">Acronyme de Plain-Old CLR Object.</span><span class="sxs-lookup"><span data-stu-id="47c41-147">Acronym for Plain-Old CLR Object.</span></span> <span data-ttu-id="47c41-148">Une classe utilisateur simple qui n’a aucune dépendance avec n’importe quelle infrastructure.</span><span class="sxs-lookup"><span data-stu-id="47c41-148">A simple user class that has no dependencies with any framework.</span></span> <span data-ttu-id="47c41-149">Dans le contexte d’EF, une classe d’entité ne dérive pas à partir d’EntityObject, implémente toutes les interfaces ou comporte des attributs définis dans EF.</span><span class="sxs-lookup"><span data-stu-id="47c41-149">In the context of EF, a an entity class that does not derive from EntityObject, implements any interfaces or carries any attributes defined in EF.</span></span> <span data-ttu-id="47c41-150">Ces classes d’entité sont dissociés de l’infrastructure de persistance sont dits également « ignorant la persistance ».</span><span class="sxs-lookup"><span data-stu-id="47c41-150">Such entity classes that are decoupled from the persistence framework are also said to be "persistence ignorant".</span></span>  

## <a name="relationship-inverse"></a><span data-ttu-id="47c41-151">Inverse de la relation</span><span class="sxs-lookup"><span data-stu-id="47c41-151">Relationship inverse</span></span>
<span data-ttu-id="47c41-152">L’autre extrémité d’une relation, par exemple, le produit. Catégorie et catégorie. Produit.</span><span class="sxs-lookup"><span data-stu-id="47c41-152">The opposite end of a relationship, for example, product.Category and category.Product.</span></span>

## <a name="self-tracking-entity"></a><span data-ttu-id="47c41-153">Entité de suivi automatique</span><span class="sxs-lookup"><span data-stu-id="47c41-153">Self-tracking entity</span></span>
<span data-ttu-id="47c41-154">Entité constituée à partir d’un modèle de génération de code qui permet au développement d’applications multicouches.</span><span class="sxs-lookup"><span data-stu-id="47c41-154">An entity built from a code generation template that helps with N-Tier development.</span></span>

## <a name="table-per-concrete-type-tpc"></a><span data-ttu-id="47c41-155">Table-par type concret (TPC)</span><span class="sxs-lookup"><span data-stu-id="47c41-155">Table-per-concrete type (TPC)</span></span>
<span data-ttu-id="47c41-156">Une méthode de mappage de l’héritage, où chaque type non abstrait dans la hiérarchie est mappé pour séparer la table dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="47c41-156">A method of mapping the inheritance where each non-abstract type in the hierarchy is mapped to separate table in the database.</span></span>

## <a name="table-per-hierarchy-tph"></a><span data-ttu-id="47c41-157">Table par hiérarchie (TPH)</span><span class="sxs-lookup"><span data-stu-id="47c41-157">Table-per-hierarchy (TPH)</span></span>
<span data-ttu-id="47c41-158">Une méthode de mappage de l’héritage où tous les types dans la hiérarchie sont mappées à la même table dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="47c41-158">A method of mapping the inheritance where all types in the hierarchy are mapped to the same table in the database.</span></span> <span data-ttu-id="47c41-159">Un ou plusieurs colonnes sont utilisé pour identifier le type de chaque ligne de discriminateur est associé.</span><span class="sxs-lookup"><span data-stu-id="47c41-159">A discriminator column(s) is used to identify what type each row is associated with.</span></span>

## <a name="table-per-type-tpt"></a><span data-ttu-id="47c41-160">Table par type (TPT)</span><span class="sxs-lookup"><span data-stu-id="47c41-160">Table-per-type (TPT)</span></span>
<span data-ttu-id="47c41-161">Une méthode de mappage de l’héritage dans lequel les propriétés communes de tous les types dans la hiérarchie sont mappées à la même table dans la base de données, mais les propriétés propres à chaque type sont mappées à une table distincte.</span><span class="sxs-lookup"><span data-stu-id="47c41-161">A method of mapping the inheritance where the common properties of all types in the hierarchy are mapped to the same table in the database, but properties unique to each type are mapped to a separate table.</span></span>

## <a name="type-discovery"></a><span data-ttu-id="47c41-162">Découverte de type</span><span class="sxs-lookup"><span data-stu-id="47c41-162">Type discovery</span></span>
<span data-ttu-id="47c41-163">Le processus d’identification des types qui doivent faire partie d’un modèle Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="47c41-163">The process of identifying the types that should be part of an Entity Framework model.</span></span>