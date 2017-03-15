---
title: "ImplementsHelper::FillArrayWithIid (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FillArrayWithIid (método)"
ms.assetid: f60035ee-b7d6-4a08-966d-f88c646944c3
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ImplementsHelper::FillArrayWithIid (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
void FillArrayWithIid(  
   _Inout_ unsigned long *index,   
   _Inout_ IID* iids) throw();  
```  
  
#### Parámetros  
 `index`  
 Un índice cero\- basado en que indica el elemento de matriz inicial para esta operación.  Cuando esta operación finaliza, `index` se incrementa en 1.  
  
 `iids`  
 Una matriz de los identificadores IID escrito.  
  
## Comentarios  
 Inserta el identificador de interfaz especificado por el parámetro actual de la plantilla de zeroth en el elemento de matriz especificado.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [ImplementsHelper \(Estructura\)](../windows/implementshelper-structure.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)