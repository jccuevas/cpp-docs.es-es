---
title: "ComPtr::operator Microsoft::WRL::Details::BoolType (Operador) | Microsoft Docs"
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
ms.assetid: cfba6521-fb30-4fb8-afb2-cfab1cb5e0b8
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# ComPtr::operator Microsoft::WRL::Details::BoolType (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica si un ComPtr administra la duración de objeto de una interfaz.  
  
## Sintaxis  
  
```  
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;  
```  
  
## Valor devuelto  
 Si una interfaz está asociado a este ComPtr, la dirección del miembro de datos de [BoolStruct::Member](../Topic/BoolStruct::Member%20Data%20Member.md) ; si no, `nullptr`.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ComPtr \(Clase\)](../windows/comptr-class.md)   
 [ComPtr::Get \(Método\)](../windows/comptr-get-method.md)