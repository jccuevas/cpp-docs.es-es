---
title: "HString::CopyTo (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: a1fd2ef0-e175-4c18-927b-550e02a89e43
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString::CopyTo (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copia el objeto HString actual a un objeto HSTRING.  
  
## Sintaxis  
  
```  
  
HRESULT CopyTo(  
   _Out_ HSTRING *str  
   ) const throw();  
```  
  
#### Parámetros  
 `str`  
 La HSTRING que recibe la copia.  
  
## Comentarios  
 Este método llama a la función [WindowsDuplicateString](http://msdn.microsoft.com/library/br224634.aspx).  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [HString \(Clase\)](../windows/hstring-class.md)