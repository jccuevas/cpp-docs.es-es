---
title: "Agile::Get (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::Get"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::Get"
ms.assetid: d6295e21-ddbe-4302-9158-3498da4d9669
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::Get (M&#233;todo)
Devuelve un identificador al objeto representado por el objeto Agile actual.  
  
## Sintaxis  
  
```cpp  
  
          T^ Get() const  
;  
```  
  
## Valor devuelto  
 Un identificador al objeto representado por el objeto Agile actual.  
  
 El tipo del valor devuelto es realmente un tipo interno no revelado. Una manera cómoda de contener el valor devuelto es asignarlo a una variable que se declara con la palabra clave de deducción de tipos [auto](../Topic/auto%20\(C++\).md). Por ejemplo: `auto x = myAgileTvariable->Get();`.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::Agile \(Clase\)](../cppcx/platform-agile-class.md)