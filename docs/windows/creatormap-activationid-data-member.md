---
title: "CreatorMap::activationId (Miembro de datos) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::CreatorMap::activationId"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "activationId (miembro de datos)"
ms.assetid: 77518b76-6e6a-4b48-8e2e-a4c7c67769e0
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CreatorMap::activationId (Miembro de datos)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
union {   
   const IID* clsid;  
   const wchar_t* (*getRuntimeName)();  
} activationId;  
```  
  
## Parámetros  
 `clsid`  
 Un identificador de interfaz  
  
 `getRuntimeName`  
 Una función que recupera el nombre en tiempo de ejecución de Windows de un objeto.  
  
## Comentarios  
 Representa un identificador de objeto que se identifica mediante un identificador clásico de la clase COM o un nombre en tiempo de ejecución de Windows.  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [CreatorMap \(Estructura\)](../windows/creatormap-structure.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)