---
title: "ImplementsHelper::CanCastTo (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanCastTo (método)"
ms.assetid: 9ae6fa17-d0b1-4e31-9ae5-da6ae4026e32
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ImplementsHelper::CanCastTo (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
  
HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
  
HRESULT CanCastTo(  
   _In_ const IID &iid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### Parámetros  
 `riid`  
 Referencia a un identificador de interfaz  
  
 `ppv`  
 Si esta operación es correcta, un puntero a la interfaz especificada por `riid` o `iid`.  
  
 `iid`  
 Referencia a un identificador de interfaz  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que indica el error.  
  
## Comentarios  
 Obtiene un puntero al identificador especificado de la interfaz  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [ImplementsHelper \(Estructura\)](../windows/implementshelper-structure.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)