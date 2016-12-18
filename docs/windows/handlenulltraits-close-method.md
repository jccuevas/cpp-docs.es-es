---
title: "HANDLENullTraits::Close (M&#233;todo) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Close (método)"
ms.assetid: 6fb2fa0d-df20-45dc-856f-f78497f8bdf9
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HANDLENullTraits::Close (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cierre el identificador especificado.  
  
## Sintaxis  
  
```  
inline static bool Close(  
   _In_ Type h  
);  
```  
  
#### Parámetros  
 `h`  
 El identificador cerrar.  
  
## Valor devuelto  
 **true** si se cierra el identificador `h` correctamente; si no, **false**.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers::HandleTraits  
  
## Vea también  
 [HANDLENullTraits \(Estructura\)](../windows/handlenulltraits-structure.md)