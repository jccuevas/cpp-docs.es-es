---
title: "_bstr_t::GetAddress | Microsoft Docs"
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
  - "_bstr_t::GetAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetAddress (método)"
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::GetAddress
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Libera cualquier cadena existente y devuelve la dirección de una cadena recién asignada.  
  
## Sintaxis  
  
```  
  
BSTR* GetAddress( );  
  
```  
  
## Valor devuelto  
 Puntero a `BSTR` contenido en `_bstr_t`.  
  
## Comentarios  
 `GetAddress` afecta a todos los objetos de `_bstr_t` que comparten `BSTR`.  Varios `_bstr_t` pueden compartir `BSTR` mediante el uso del constructor copy y `operator=`.  
  
## Ejemplo  
 Vea [\_bstr\_t::Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo del uso de `GetAddress`.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_bstr\_t \(Clase\)](../cpp/bstr-t-class.md)