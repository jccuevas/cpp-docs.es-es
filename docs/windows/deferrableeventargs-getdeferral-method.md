---
title: "M&#233;todo DeferrableEventArgs::GetDeferral | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# M&#233;todo DeferrableEventArgs::GetDeferral
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene una referencia al objeto [Aplazamiento](http://go.microsoft.com/fwlink/?LinkId=526520) que representa un evento diferido.  
  
## Sintaxis  
  
```cpp  
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```  
  
#### Parámetros  
 `result`  
 Un puntero que hará referencia al objeto [Aplazamiento](http://go.microsoft.com/fwlink/?LinkId=526520) cuando se complete la llamada.  
  
## Valor devuelto  
 S\_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.  
  
## Comentarios  
 Para ver un ejemplo de código, vea [Clase DeferrableEventArgs](../windows/deferrableeventargs-class.md).  
  
## Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Clase DeferrableEventArgs](../windows/deferrableeventargs-class.md)