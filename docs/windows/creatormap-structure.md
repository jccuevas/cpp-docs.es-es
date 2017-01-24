---
title: "CreatorMap (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::CreatorMap"
  - "implements/Microsoft::WRL::Details::CreatorMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreatorMap (estructura)"
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CreatorMap (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Es compatible con la infraestructura de [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] y no está diseñado para que se utilice directamente desde el código.  
  
## Sintaxis  
  
```  
struct CreatorMap;  
```  
  
## Comentarios  
 Contiene información sobre cómo inicializar, registrar, y los objetos del registro.  
  
 CreatorMap contiene la siguiente información:  
  
-   Cómo inicializar, registrar, y los objetos del registro.  
  
-   Cómo comparar datos de activación dependiendo de COM o de un generador clásico de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] .  
  
-   Información sobre el nombre de caché y de servidor de generador de una interfaz.  
  
## Miembros  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CreatorMap::activationId \(Miembro de datos\)](../windows/creatormap-activationid-data-member.md)|Representa un identificador de objeto que se identifica mediante un identificador clásico de la clase COM o un nombre de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] .|  
|[CreatorMap::factoryCache \(Miembro de datos\)](../windows/creatormap-factorycache-data-member.md)|Almacena el puntero a la memoria caché del generador del CreatorMap.|  
|[CreatorMap::factoryCreator \(Miembro de datos\)](../Topic/CreatorMap::factoryCreator%20Data%20Member.md)|Crea un generador para el CreatorMap especificado.|  
|[CreatorMap::serverName \(Miembro de datos\)](../windows/creatormap-servername-data-member.md)|Almacena el nombre del CreatorMap.|  
  
## Jerarquía de herencia  
 `CreatorMap`  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)