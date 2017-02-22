---
title: "RuntimeClassBaseT::GetImplementedIIDS (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetImplementedIIDS (método)"
ms.assetid: adae54da-521d-4add-87f5-242fbd85f33b
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# RuntimeClassBaseT::GetImplementedIIDS (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
template<  
   typename T  
>  
__forceinline static HRESULT GetImplementedIIDS(  
   _In_ T* implements,  
   _Out_ ULONG *iidCount,  
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids  
);  
```  
  
#### Parámetros  
 `T`  
 Tipo del parámetro `implements`.  
  
 `implements`  
 Puntero al tipo especificado por el parámetro `T`.  
  
 `iidCount`  
 El número máximo de id. de interfaz a recuperar.  
  
 `iids`  
 Si esta operación finaliza correctamente, una matriz de los id. de la interfaz implementada por `T`escrito.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que describe el error.  
  
## Comentarios  
 Recupera una matriz de los id. de interfaz implementados por un tipo especificado.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [RuntimeClassBaseT \(Estructura\)](../windows/runtimeclassbaset-structure.md)