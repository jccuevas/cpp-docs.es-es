---
title: "InterfaceTraits::CastToBase (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CastToBase (método)"
ms.assetid: 0591a017-0adf-4358-b946-eb0a307ce7f2
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# InterfaceTraits::CastToBase (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
template<  
   typename T  
>  
static __forceinline Base* CastToBase(  
   _In_ T* ptr  
);  
```  
  
#### Parámetros  
 `T`  
 El tipo de parámetro `ptr`.  
  
 `ptr`  
 Puntero a un tipo `T`.  
  
## Valor devuelto  
 Un puntero a `Base`.  
  
## Comentarios  
 Convierte el puntero especificado a un puntero a `Base`.  
  
 Para obtener más información sobre `Base`, vea la sección Public Typedefs en [InterfaceTraits \(Estructura\)](../windows/interfacetraits-structure.md).  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [InterfaceTraits \(Estructura\)](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)