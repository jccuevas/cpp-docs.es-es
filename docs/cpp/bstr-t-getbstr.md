---
title: "_bstr_t::GetBSTR | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "GetBSTR"
  - "_bstr_t::GetBSTR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetBSTR (método)"
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::GetBSTR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Señala al principio del objeto `BSTR` incluido en `_bstr_t`.  
  
## Sintaxis  
  
```  
  
BSTR& GetBSTR( );  
  
```  
  
## Valor devuelto  
 Principio del objeto `BSTR` incluido en `_bstr_t`.  
  
## Comentarios  
 `GetBSTR` afecta a todos los objetos de `_bstr_t` que comparten `BSTR`.  Varios `_bstr_t` pueden compartir `BSTR` mediante el uso del constructor copy y `operator=`.  
  
## Ejemplo  
 Vea [\_bstr\_t::Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo del uso de `GetBSTR`.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_bstr\_t \(Clase\)](../cpp/bstr-t-class.md)