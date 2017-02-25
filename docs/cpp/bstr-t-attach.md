---
title: "_bstr_t::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_bstr_t::Attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Attach (método)"
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _bstr_t::Attach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Vincula un contenedor `_bstr_t` a un `BSTR`.  
  
## Sintaxis  
  
```  
  
      void Attach(  
   BSTR s  
);  
```  
  
#### Parámetros  
 *s*  
 `BSTR` que se va a asociar con, o asignar a, la variable `_bstr_t`.  
  
## Comentarios  
 Si `_bstr_t` se ha asociado previamente a otro `BSTR`, `_bstr_t` limpiará el recurso de `BSTR`, si ninguna otra variable `_bstr_t` está utilizando `BSTR`.  
  
## Ejemplo  
 Vea [\_bstr\_t::Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo del uso de **Attach**.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_bstr\_t \(Clase\)](../cpp/bstr-t-class.md)