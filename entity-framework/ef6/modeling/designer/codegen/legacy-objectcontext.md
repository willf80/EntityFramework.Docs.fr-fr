---
title: Retour à ObjectContext dans Entity Framework Designer - EF6
author: divega
ms.date: 2016-10-23
ms.prod: entity-framework
ms.author: divega
ms.manager: avickers
ms.technology: entity-framework-6
ms.topic: article
ms.assetid: 36550569-a1de-47cb-ba6d-544794ffd500
caps.latest.revision: 3
ms.openlocfilehash: 17fa6538cf5e92f59ab72376af96ad65c640a085
ms.sourcegitcommit: f05e7b62584cf228f17390bb086a61d505712e1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2018
ms.locfileid: "39121164"
---
# <a name="reverting-to-objectcontext-in-entity-framework-designer"></a><span data-ttu-id="6e6a0-102">Retour à ObjectContext dans Entity Framework Designer</span><span class="sxs-lookup"><span data-stu-id="6e6a0-102">Reverting to ObjectContext in Entity Framework Designer</span></span>
<span data-ttu-id="6e6a0-103">Avec une version précédente d’un modèle créé avec le Concepteur EF de Entity Framework génère un contexte dérivé ObjectContext et les classes d’entité dérivé à partir d’EntityObject.</span><span class="sxs-lookup"><span data-stu-id="6e6a0-103">With previous version of Entity Framework a model created with the EF Designer would generate a context that derived from ObjectContext and entity classes that derived from EntityObject.</span></span>

<span data-ttu-id="6e6a0-104">En commençant par EF4.1 recommandé de passer en un modèle de génération de code qui génère un contexte dérivant des classes d’entité DbContext et POCO.</span><span class="sxs-lookup"><span data-stu-id="6e6a0-104">Starting with EF4.1 we recommended swapping to a code generation template that generates a context deriving from DbContext and POCO entity classes.</span></span>

<span data-ttu-id="6e6a0-105">Dans Visual Studio 2012, vous obtenez code DbContext généré par défaut pour tous les nouveaux modèles créés avec le Concepteur EF.</span><span class="sxs-lookup"><span data-stu-id="6e6a0-105">In Visual Studio 2012 you get DbContext code generated by default for all new models created with the EF Designer.</span></span> <span data-ttu-id="6e6a0-106">Les modèles existants continueront à générer du code d’ObjectContext en fonction, sauf si vous décidez d’échange pour le Générateur de code en fonction de DbContext.</span><span class="sxs-lookup"><span data-stu-id="6e6a0-106">Existing models will continue to generate ObjectContext based code unless you decide to swap to the DbContext based code generator.</span></span>

## <a name="reverting-back-to-objectcontext-code-generation"></a><span data-ttu-id="6e6a0-107">Retour à la génération de Code d’ObjectContext</span><span class="sxs-lookup"><span data-stu-id="6e6a0-107">Reverting Back to ObjectContext Code Generation</span></span>

### <a name="1-disable-dbcontext-code-generation"></a><span data-ttu-id="6e6a0-108">1. Désactiver la génération de Code de DbContext</span><span class="sxs-lookup"><span data-stu-id="6e6a0-108">1. Disable DbContext Code Generation</span></span>

<span data-ttu-id="6e6a0-109">Génération des classes DbContext et POCO dérivées est gérée par deux fichiers .tt dans votre projet, si vous développez le fichier .edmx dans l’Explorateur de solutions, vous verrez ces fichiers.</span><span class="sxs-lookup"><span data-stu-id="6e6a0-109">Generation of the derived DbContext and POCO classes is handled by two .tt files in you project, if you expand the .edmx file in solution explorer you will see these files.</span></span> <span data-ttu-id="6e6a0-110">Supprimez ces deux fichiers de votre projet.</span><span class="sxs-lookup"><span data-stu-id="6e6a0-110">Delete both of these files from your project.</span></span>

![CodeGenFiles](~/ef6/media/codegenfiles.png)

<span data-ttu-id="6e6a0-112">Si vous utilisez VB.NET, vous devrez sélectionner le **afficher tous les fichiers** bouton pour afficher les fichiers imbriqués.</span><span class="sxs-lookup"><span data-stu-id="6e6a0-112">If you are using VB.NET you will need to select the **Show All Files** button to see the nested files.</span></span>

![ShowAllFiles](~/ef6/media/showallfiles.png)

### <a name="2-re-enable-objectcontext-code-generation"></a><span data-ttu-id="6e6a0-114">2. Réactiver la génération de Code de ObjectContext</span><span class="sxs-lookup"><span data-stu-id="6e6a0-114">2. Re-Enable ObjectContext Code Generation</span></span>

<span data-ttu-id="6e6a0-115">Ouvrir dans le Concepteur EF, de modèle avec le bouton droit sur une section vide de l’aire de conception et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6e6a0-115">Open you model in the EF Designer, right-click on a blank section of the design surface and select **Properties**.</span></span>

<span data-ttu-id="6e6a0-116">Dans la modification de la fenêtre Propriétés la **stratégie de génération de Code** de **aucun** à **par défaut**.</span><span class="sxs-lookup"><span data-stu-id="6e6a0-116">In the Properties window change the **Code Generation Strategy** from **None** to **Default**.</span></span>

![CodeGenStrategy](~/ef6/media/codegenstrategy.png)