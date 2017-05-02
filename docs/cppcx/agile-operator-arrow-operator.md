---
title: "Agile::operator-&gt; (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::operator->"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::operator->"
ms.assetid: 570f4b0b-1735-49b3-8a30-4a302ac57074
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::operator-&gt; (Operador)
Recupera un identificador al objeto representado por el objeto Agile actual.  
  
## Sintaxis  
  
```cpp  
  
       T^ operator->()   
const throw();  
```  
  
## Valor devuelto  
 Identificador al objeto representado por el objeto Agile actual.  
  
 Este operador devuelve realmente un tipo interno no revelado. Una manera cómoda de contener el valor devuelto es asignarlo a una variable que se declara con la palabra clave de deducción de tipos [auto](../Topic/auto%20\(C++\).md).  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::Agile \(Clase\)](../cppcx/platform-agile-class.md)