---
title: "Ejemplo de llamada: prototipo y llamada de funci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "convenciones de llamada, ejemplos [C++]"
  - "ejemplos [C++], convenciones de llamada"
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Ejemplo de llamada: prototipo y llamada de funci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 En el ejemplo siguiente se muestran los resultados de realizar una llamada de función mediante diversas convenciones de llamada.  
  
 Este ejemplo está basado en el esqueleto de función siguiente.  Reemplace `calltype` por la convención de llamada adecuada.  
  
```  
void    calltype MyFunc( char c, short s, int i, double f );  
.  
.  
.  
void    MyFunc( char c, short s, int i, double f )  
    {  
    .  
    .  
    .  
    }  
.  
.  
.  
MyFunc ('x', 12, 8192, 2.7183);  
```  
  
 Para obtener más información, vea [Resultados de ejemplo de llamada](../cpp/results-of-calling-example.md).  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Convenciones de llamada](../cpp/calling-conventions.md)