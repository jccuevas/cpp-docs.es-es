---
title: "InterfaceTraits::FillArrayWithIid (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FillArrayWithIid (método)"
ms.assetid: 73583177-adc9-4fcb-917d-fa7e6d07c990
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# InterfaceTraits::FillArrayWithIid (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
__forceinline static void FillArrayWithIid(  
   _Inout_ unsigned long &index,  
   _In_ IID* iids  
);  
  
```  
  
#### Parámetros  
 `index`  
 Puntero a un campo que contiene un valor de índice de base cero.  
  
 `iids`  
 Una matriz de id. de la interfaz.  
  
## Comentarios  
 Asigna el identificador de interfaz de `Base` al elemento de matriz especificado por el argumento index.  
  
 El cambio en el nombre de esta API, sólo un elemento de matriz se modifica; no la matriz completa.  
  
 Para obtener más información sobre `Base`, vea la sección Public Typedefs en [InterfaceTraits \(Estructura\)](../windows/interfacetraits-structure.md).  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [InterfaceTraits \(Estructura\)](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)