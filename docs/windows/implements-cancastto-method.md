---
title: "Implements::CanCastTo (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Implements::CanCastTo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanCastTo (método)"
ms.assetid: a8e85c7d-4dcd-446d-bebc-a97da46ce44a
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Implements::CanCastTo (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene un puntero a la interfaz especificada.  
  
## Sintaxis  
  
```  
__forceinline HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### Parámetros  
 `riid`  
 Una referencia a un identificador de interfaz  
  
 `ppv`  
 Si es correcto, un puntero a la interfaz especificada por `riid`.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que indica el error, como E\_NOINTERFACE.  
  
## Comentarios  
 Ésta es una función interna auxiliar que realiza una operación de QueryInterface.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Implements \(Estructura\)](../Topic/Implements%20Structure.md)