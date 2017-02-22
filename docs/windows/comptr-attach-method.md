---
title: "ComPtr::Attach (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::ComPtr::Attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Attach (método)"
ms.assetid: 5b911f2d-9830-4dc7-b9e3-527abd55d2c8
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ComPtr::Attach (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Asocia este ComPtr en el tipo de interfaz especificado por el parámetro de tipo actual de la plantilla.  
  
## Sintaxis  
  
```  
void Attach(  
   _In_opt_ InterfaceType* other  
);  
```  
  
#### Parámetros  
 `other`  
 Un tipo de interfaz.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ComPtr \(Clase\)](../windows/comptr-class.md)