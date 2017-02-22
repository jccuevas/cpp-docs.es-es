---
title: "ActivateInstance (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Windows::Foundation::ActivateInstance"
  - "client/ABI::Windows::Foundation::ActivateInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActivateInstance (función)"
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ActivateInstance (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Registros y recupera una instancia de un tipo especificado definido en un identificador especificado de la clase  
  
## Sintaxis  
  
```  
template<  
   typename T  
>  
inline HRESULT ActivateInstance(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance  
);  
```  
  
#### Parámetros  
 `T`  
 Un tipo a activar.  
  
 `activatableClassId`  
 El nombre del identificador de la clase que define el parámetro `T`.  
  
 `instance`  
 Cuando esta operación finaliza, una referencia a una instancia de `T`.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un error HRESULT que indica la causa del error.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Windows::Foundation  
  
## Vea también  
 [Windows::Foundation \(Espacio de nombres\)](../Topic/Windows::Foundation%20Namespace.md)