---
title: "ComPtr::AsWeak (M&#233;todo) | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::AsWeak"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsWeak (método)"
ms.assetid: 23e29dcd-39cb-423f-abe6-6df4428213bf
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::AsWeak (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Recupera una referencia parcial al objeto actual.  
  
## Sintaxis  
  
```  
HRESULT AsWeak(  
   _Out_ WeakRef* pWeakRef  
);  
```  
  
#### Parámetros  
 `pWeakRef`  
 Cuando esta operación finaliza, un puntero a un objeto débil de referencia.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que indica el error.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ComPtr \(Clase\)](../windows/comptr-class.md)