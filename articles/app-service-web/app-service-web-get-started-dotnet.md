---
title: Uw eerste ASP.NET-web-app in vijf minuten maken in Azure | Microsoft Docs
description: Ontdek door implementatie van een ASP.NET-voorbeeld-app hoe eenvoudig het is om web-apps in App Service uit te voeren.
services: app-service\web
documentationcenter: 
author: cephalin
manager: wpickett
editor: 
ms.assetid: b1e6bd58-48d1-4007-9d6c-53fd6db061e3
ms.service: app-service-web
ms.workload: web
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: hero-article
ms.date: 03/17/2017
ms.author: cephalin
translationtype: Human Translation
ms.sourcegitcommit: bb1ca3189e6c39b46eaa5151bf0c74dbf4a35228
ms.openlocfilehash: a428e183e7535c7745e214332f8e449b4a8bf22c
ms.lasthandoff: 03/17/2017


---
# <a name="create-your-first-aspnet-web-app-in-azure-in-five-minutes"></a>Uw eerste ASP.NET-web-app in vijf minuten maken in Azure

[!INCLUDE [app-service-web-selector-get-started](../../includes/app-service-web-selector-get-started.md)] 

Met deze Quickstart leert u in een paar minuten hoe u uw eerste ASP.NET-web-app implementeert in [Azure App Service](../app-service/app-service-value-prop-what-is.md).

Voordat u begint, moet u controleren of de Azure-CLI is geïnstalleerd. Zie voor meer informatie de [Installatiehandleiding van de Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli).

## <a name="log-in-to-azure"></a>Meld u aan bij Azure.
Meld u aan bij Azure door `az login` uit te voeren en de aanwijzingen op het scherm te volgen.
   
```azurecli
az login
```

## <a name="create-a-resource-group"></a>Een resourcegroep maken   
Maak een [resourcegroep](../azure-resource-manager/resource-group-overview.md). Hier verzamelt u alle Azure-resources die u samen wilt beheren, zoals de web-app en de bijbehorende SQL Database-back-end.

```azurecli
az group create --location "West Europe" --name myResourceGroup
```

Gebruik de Azure CLI-opdracht `az appservice list-locations` om te zien welke waarden u kunt gebruiken voor `---location`.

## <a name="create-an-app-service-plan"></a>Een App Service-plan maken
Maak een 'GRATIS' [App Service-plan](../app-service/azure-web-sites-web-hosting-plans-in-depth-overview.md). 

```azurecli
az appservice plan create --name my-free-appservice-plan --resource-group myResourceGroup --sku FREE
```

## <a name="create-a-web-app"></a>Een webtoepassing maken
Maak een web-app met een unieke naam in `<app_name>`.

```azurecli
az appservice web create --name <app_name> --resource-group myResourceGroup --plan my-free-appservice-plan
```

## <a name="deploy-sample-application"></a>Voorbeeldtoepassing implementeren
Implementeer een voorbeeld van een ASP.NET-app vanuit GitHub.

```azurecli
az appservice web source-control config --name <app_name> --resource-group myResourceGroup \
--repo-url "https://github.com/Azure-Samples/app-service-web-dotnet-get-started.git" --branch master --manual-integration 
```

## <a name="browse-to-web-app"></a>Naar de web-app bladeren
Voer deze opdracht uit om uw app live in werking te zien in Azure.

```azurecli
az appservice web browse --name <app_name> --resource-group myResourceGroup
```

Gefeliciteerd, uw eerste ASP.NET-web-app wordt live uitgevoerd in Azure App Service.

[!INCLUDE [cli-samples-clean-up](../../includes/cli-samples-clean-up.md)]

## <a name="next-steps"></a>Volgende stappen

Bekijk vooraf gemaakte [CLI-scripts voor web-apps](app-service-cli-samples.md).

