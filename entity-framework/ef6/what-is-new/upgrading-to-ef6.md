---
title: Mise à niveau vers Entity Framework 6
author: divega
ms.date: 2016-10-23
ms.prod: entity-framework
ms.author: divega
ms.manager: avickers
ms.technology: entity-framework-6
ms.topic: article
ms.assetid: 29958ae5-85d3-4585-9ba6-550b8ec9393a
caps.latest.revision: 3
ms.openlocfilehash: d22f0d686e6b8e3922d37245386af7723bf08ba1
ms.sourcegitcommit: bdd06c9a591ba5e6d6a3ec046c80de98f598f3f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "39121479"
---
# <a name="upgrading-to-entity-framework-6"></a><span data-ttu-id="2dcf3-102">Mise à niveau vers Entity Framework 6</span><span class="sxs-lookup"><span data-stu-id="2dcf3-102">Upgrading to Entity Framework 6</span></span>

<span data-ttu-id="2dcf3-103">Dans les versions précédentes d’EF, le code a été fractionné entre core bibliothèques (principalement System.Data.Entity.dll) dans le cadre du .NET Framework et hors-bande (OOB) (principalement EntityFramework.dll) inclus dans un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-103">In previous versions of EF the code was split between core libraries (primarily System.Data.Entity.dll) shipped as part of the .NET Framework and out-of-band (OOB) libraries (primarily EntityFramework.dll) shipped in a NuGet package.</span></span> <span data-ttu-id="2dcf3-104">EF6 prend le code des bibliothèques core et l’incorpore dans les bibliothèques OOB.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-104">EF6 takes the code from the core libraries and incorporates it into the OOB libraries.</span></span> <span data-ttu-id="2dcf3-105">Cette action était nécessaire pour permettre à EF qu’il veut ouvrir la source et pour qu’elle soit en mesure de faire évoluer à un rythme différent à partir de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-105">This was necessary in order to allow EF to be made open source and for it to be able to evolve at a different pace from .NET Framework.</span></span> <span data-ttu-id="2dcf3-106">La conséquence de cela est que les applications devront être régénérés sur les types déplacés.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-106">The consequence of this is that applications will need to be rebuilt against the moved types.</span></span>

<span data-ttu-id="2dcf3-107">Il doit s’agir simple pour les applications qui utilisent de DbContext comme expédié dans Entity Framework 4.1 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-107">This should be straightforward for applications that make use of DbContext as shipped in EF 4.1 and later.</span></span> <span data-ttu-id="2dcf3-108">Un peu plus de travail est obligatoire pour les applications qui utilisent ObjectContext, mais il n’est pas toujours difficile à gérer.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-108">A little more work is required for applications that make use of ObjectContext but it still isn’t hard to do.</span></span>

<span data-ttu-id="2dcf3-109">Voici une liste de vérification des choses que vous devez faire pour mettre à niveau une application existante à EF6.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-109">Here is a checklist of the things you need to do to upgrade an existing application to EF6.</span></span>

## <a name="1-install-the-ef6-nuget-package"></a><span data-ttu-id="2dcf3-110">1. Installez le package NuGet d’EF6</span><span class="sxs-lookup"><span data-stu-id="2dcf3-110">1. Install the EF6 NuGet package</span></span>

<span data-ttu-id="2dcf3-111">Vous devez mettre à niveau vers le nouveau runtime Entity Framework 6.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-111">You need to upgrade to the new Entity Framework 6 runtime.</span></span>

1. <span data-ttu-id="2dcf3-112">Avec le bouton droit sur votre projet, puis sélectionnez **gérer les Packages NuGet...**</span><span class="sxs-lookup"><span data-stu-id="2dcf3-112">Right-click on your project and select **Manage NuGet Packages...**</span></span>  
2. <span data-ttu-id="2dcf3-113">Sous le **Online** onglet sélectionnez **EntityFramework** et cliquez sur **installer**</span><span class="sxs-lookup"><span data-stu-id="2dcf3-113">Under the **Online** tab select **EntityFramework** and click **Install**</span></span>  
   > [!NOTE]
   > <span data-ttu-id="2dcf3-114">Si une version précédente de l’installation package EntityFramework NuGet cela met à niveau à EF6.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-114">If a previous version of the EntityFramework NuGet package was installed this will upgrade it to EF6.</span></span>

<span data-ttu-id="2dcf3-115">Vous pouvez également exécuter la commande suivante à partir de la Console du Gestionnaire de Package :</span><span class="sxs-lookup"><span data-stu-id="2dcf3-115">Alternatively, you can run the following command from Package Manager Console:</span></span>

``` powershell
Install-Package EntityFramework
```

## <a name="2-ensure-that-assembly-references-to-systemdataentitydll-are-removed"></a><span data-ttu-id="2dcf3-116">2. Vérifiez que les références d’assembly à System.Data.Entity.dll sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-116">2. Ensure that assembly references to System.Data.Entity.dll are removed</span></span>

<span data-ttu-id="2dcf3-117">Installation du package NuGet d’EF6 doit supprimer automatiquement toutes les références à System.Data.Entity à partir de votre projet pour vous.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-117">Installing the EF6 NuGet package should automatically remove any references to System.Data.Entity from your project for you.</span></span>

## <a name="3-swap-any-ef-designer-edmx-models-to-use-ef-6x-code-generation"></a><span data-ttu-id="2dcf3-118">3. Remplacez tous les modèles EF Designer (EDMX) pour utiliser la génération de code EF 6.x</span><span class="sxs-lookup"><span data-stu-id="2dcf3-118">3. Swap any EF Designer (EDMX) models to use EF 6.x code generation</span></span>

<span data-ttu-id="2dcf3-119">Si vous avez tous les modèles créés avec le Concepteur EF, vous devez mettre à jour les modèles de génération de code pour générer du code compatible EF6.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-119">If you have any models created with the EF Designer, you will need to update the code generation templates to generate EF6 compatible code.</span></span>

> [!NOTE]
> <span data-ttu-id="2dcf3-120">Seuls les modèles de générateur de DbContext EF 6.x sont actuellement disponibles pour Visual Studio 2012 et 2013.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-120">There are currently only EF 6.x DbContext Generator templates available for Visual Studio 2012 and 2013.</span></span>

1. <span data-ttu-id="2dcf3-121">Supprimer les modèles de génération de code existants.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-121">Delete existing code-generation templates.</span></span> <span data-ttu-id="2dcf3-122">Ces fichiers seront généralement nommés  **\<edmx_file_name\>.tt** et  **\<edmx_file_name\>. Context.tt** et être imbriqué sous votre fichier edmx dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-122">These files will typically be named **\<edmx_file_name\>.tt** and **\<edmx_file_name\>.Context.tt** and be nested under your edmx file in Solution Explorer.</span></span> <span data-ttu-id="2dcf3-123">Vous pouvez sélectionner les modèles dans l’Explorateur de solutions, puis appuyez sur la **Del** clé pour les supprimer.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-123">You can select the templates in Solution Explorer and press the **Del** key to delete them.</span></span>  
   > [!NOTE]
   > <span data-ttu-id="2dcf3-124">Dans les projets de Site Web les modèles ne seront pas être imbriqués sous votre fichier edmx, mais répertoriées à ses côtés dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-124">In Web Site projects the templates will not be nested under your edmx file, but listed alongside it in Solution Explorer.</span></span>  

   > [!NOTE]
   > <span data-ttu-id="2dcf3-125">Dans les projets VB.NET, vous devrez activer « Afficher tous les fichiers » être en mesure de voir les fichiers de modèle imbriqué.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-125">In VB.NET projects you will need to enable 'Show All Files' to be able to see the nested template files.</span></span>
2. <span data-ttu-id="2dcf3-126">Ajouter le modèle de génération de code EF 6.x approprié.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-126">Add the appropriate EF 6.x code generation template.</span></span> <span data-ttu-id="2dcf3-127">Ouvrez votre modèle dans le Concepteur EF, clic droit sur l’aire de conception et sélectionnez **ajouter un élément de génération de Code...**</span><span class="sxs-lookup"><span data-stu-id="2dcf3-127">Open your model in the EF Designer, right-click on the design surface and select **Add Code Generation Item...**</span></span>
    - <span data-ttu-id="2dcf3-128">Si vous utilisez l’API DbContext (recommandé) puis **EF 6.x DbContext Générateur** seront disponibles sous le **données** onglet.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-128">If you are using the DbContext API (recommended) then **EF 6.x DbContext Generator** will be available under the **Data** tab.</span></span>  
      > [!NOTE]
      > <span data-ttu-id="2dcf3-129">Si vous utilisez Visual Studio 2012, vous devrez installer les outils de 6 EF pour que ce modèle.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-129">If you are using Visual Studio 2012, you will need to install the EF 6 Tools to have this template.</span></span> <span data-ttu-id="2dcf3-130">Consultez [obtenir Entity Framework](~/ef6/fundamentals/install.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-130">See [Get Entity Framework](~/ef6/fundamentals/install.md) for details.</span></span>  

    - <span data-ttu-id="2dcf3-131">Si vous utilisez l’API ObjectContext, vous devez sélectionner le **Online** onglet et recherchez **EF 6.x EntityObject Generator**.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-131">If you are using the ObjectContext API then you will need to select the **Online** tab and search for **EF 6.x EntityObject Generator**.</span></span>  
3. <span data-ttu-id="2dcf3-132">Si vous avez appliqué toutes les personnalisations pour les modèles de génération de code, vous devrez réappliquer les modèles mis à jour.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-132">If you applied any customizations to the code generation templates you will need to re-apply them to the updated templates.</span></span>

## <a name="4-update-namespaces-for-any-core-ef-types-being-used"></a><span data-ttu-id="2dcf3-133">4. Mettre à jour les espaces de noms pour les types d’EF core utilisé</span><span class="sxs-lookup"><span data-stu-id="2dcf3-133">4. Update namespaces for any core EF types being used</span></span>

<span data-ttu-id="2dcf3-134">Les espaces de noms pour les types DbContext et Code First n’ont pas changé.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-134">The namespaces for DbContext and Code First types have not changed.</span></span> <span data-ttu-id="2dcf3-135">Cela signifie que pour de nombreuses applications qui utilisent EF 4.1 ou plus tard vous ne devez pas apporter de modifications.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-135">This means for many applications that use EF 4.1 or later you will not need to change anything.</span></span>

<span data-ttu-id="2dcf3-136">Type ObjectContext qui étaient présentes dans System.Data.Entity.dll ont été déplacés vers les nouveaux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-136">Types like ObjectContext that were previously in System.Data.Entity.dll have been moved to new namespaces.</span></span> <span data-ttu-id="2dcf3-137">Cela signifie que vous devrez peut-être mettre à jour votre *à l’aide de* ou *importation* directives pour la build EF6.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-137">This means you may need to update your *using* or *Import* directives to build against EF6.</span></span>

<span data-ttu-id="2dcf3-138">La règle générale pour les modifications de l’espace de noms est que n’importe quel type dans System.Data.* est déplacé vers System.Data.Entity.Core.*.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-138">The general rule for namespace changes is that any type in System.Data.* is moved to System.Data.Entity.Core.*.</span></span> <span data-ttu-id="2dcf3-139">En d’autres termes, insérez simplement **Entity.Core.**</span><span class="sxs-lookup"><span data-stu-id="2dcf3-139">In other words, just insert **Entity.Core.**</span></span> <span data-ttu-id="2dcf3-140">Après avoir System.Data.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-140">after System.Data.</span></span> <span data-ttu-id="2dcf3-141">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2dcf3-141">For example:</span></span>

- <span data-ttu-id="2dcf3-142">System.Data.EntityException = > System.Data. **Entity.Core.** EntityException</span><span class="sxs-lookup"><span data-stu-id="2dcf3-142">System.Data.EntityException => System.Data.**Entity.Core.** EntityException</span></span>  
- <span data-ttu-id="2dcf3-143">System.Data.Objects.ObjectContext = > System.Data. **Entity.Core.** Objects.ObjectContext</span><span class="sxs-lookup"><span data-stu-id="2dcf3-143">System.Data.Objects.ObjectContext => System.Data.**Entity.Core.** Objects.ObjectContext</span></span>  
- <span data-ttu-id="2dcf3-144">System.Data.Objects.DataClasses.RelationshipManager = > System.Data. **Entity.Core.** Objects.DataClasses.RelationshipManager</span><span class="sxs-lookup"><span data-stu-id="2dcf3-144">System.Data.Objects.DataClasses.RelationshipManager => System.Data.**Entity.Core.** Objects.DataClasses.RelationshipManager</span></span>  

<span data-ttu-id="2dcf3-145">Ces types sont dans le *Core* espaces de noms car elles ne sont pas utilisées directement pour la plupart des applications DbContext.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-145">These types are in the *Core* namespaces because they are not used directly for most DbContext-based applications.</span></span> <span data-ttu-id="2dcf3-146">Certains types qui faisaient partie de System.Data.Entity.dll sont toujours utilisés couramment et directement des applications basées sur le DbContext et par conséquent, n'ont pas été transférés dans le *Core* espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-146">Some types that were part of System.Data.Entity.dll are still used commonly and directly for DbContext-based applications and so have not been moved into the *Core* namespaces.</span></span> <span data-ttu-id="2dcf3-147">Ces équivalents sont :</span><span class="sxs-lookup"><span data-stu-id="2dcf3-147">These are:</span></span>

- <span data-ttu-id="2dcf3-148">System.Data.EntityState = > System.Data. **Entité.** EntityState</span><span class="sxs-lookup"><span data-stu-id="2dcf3-148">System.Data.EntityState => System.Data.**Entity.** EntityState</span></span>  
- <span data-ttu-id="2dcf3-149">System.Data.Objects.DataClasses.EdmFunctionAttribute = > System.Data. **Entity.DbFunctionAttribute**</span><span class="sxs-lookup"><span data-stu-id="2dcf3-149">System.Data.Objects.DataClasses.EdmFunctionAttribute => System.Data.**Entity.DbFunctionAttribute**</span></span>  
  > [!NOTE]
  > <span data-ttu-id="2dcf3-150">Cette classe a été renommée ; une classe avec l’ancien nom existe toujours et qu’il fonctionne, mais il désormais marqués comme obsolète.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-150">This class has been renamed; a class with the old name still exists and works, but it now marked as obsolete.</span></span>  
- <span data-ttu-id="2dcf3-151">System.Data.Objects.EntityFunctions = > System.Data. **Entity.DbFunctions**</span><span class="sxs-lookup"><span data-stu-id="2dcf3-151">System.Data.Objects.EntityFunctions => System.Data.**Entity.DbFunctions**</span></span>  
  > [!NOTE]
  > <span data-ttu-id="2dcf3-152">Cette classe a été renommée ; une classe avec l’ancien nom existe toujours et qu’il fonctionne, mais il désormais marqué comme obsolète.)</span><span class="sxs-lookup"><span data-stu-id="2dcf3-152">This class has been renamed; a class with the old name still exists and works, but it now marked as obsolete.)</span></span>  
- <span data-ttu-id="2dcf3-153">Classes spatiales (par exemple, DbGeography, DbGeometry) ont été déplacés de System.Data.Spatial = > System.Data. **Entité.** Spatial</span><span class="sxs-lookup"><span data-stu-id="2dcf3-153">Spatial classes (for example, DbGeography, DbGeometry) have moved from System.Data.Spatial => System.Data.**Entity.** Spatial</span></span>

> [!NOTE]
> <span data-ttu-id="2dcf3-154">Certains types dans l’espace de noms System.Data se trouvent dans System.Data.dll, qui n’est pas un assembly EF.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-154">Some types in the System.Data namespace are in System.Data.dll which is not an EF assembly.</span></span> <span data-ttu-id="2dcf3-155">Ces types n’ont pas été déplacées et par conséquent, leurs espaces de noms restent inchangées.</span><span class="sxs-lookup"><span data-stu-id="2dcf3-155">These types have not moved and so their namespaces remain unchanged.</span></span>