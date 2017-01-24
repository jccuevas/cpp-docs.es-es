---
title: "CloakedIid (Estructura) | Microsoft Docs"
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
  - "implements/Microsoft::WRL::CloakedIid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CloakedIid (estructura)"
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CloakedIid (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica al RuntimeClass, plantillas implementa y de ChainInterfaces que la interfaz especificada no está disponible en la lista de IID.  
  
## Sintaxis  
  
```  
template<  
   typename T  
>  
struct CloakedIid : T;  
```  
  
#### Parámetros  
 `T`  
 La interfaz se oculta que \(escondido\).  
  
## Comentarios  
 A continuación se muestra un ejemplo de cómo se utiliza CloakedIid: `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`.  
  
## Jerarquía de herencia  
 `T`  
  
 `CloakedIid`  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)