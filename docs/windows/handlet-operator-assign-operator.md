---
title: "HandleT::operator= (Operador) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleT::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= (operador)"
ms.assetid: 9e42dcca-30fa-4e8b-8954-802fd64a5595
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HandleT::operator= (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Mueve el valor del objeto especificado de HandleT al objeto actual de HandleT.  
  
## Sintaxis  
  
```  
HandleT& operator=(  
   _Inout_ HandleT&& h  
);  
```  
  
#### Parámetros  
 `h`  
 Una rvalue\-referencia a un identificador.  
  
## Valor devuelto  
 Una referencia al objeto actual de HandleT.  
  
## Comentarios  
 Esta operación invalida el objeto de HandleT especificado por el parámetro `h`.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [HandleT \(Clase\)](../Topic/HandleT%20Class.md)