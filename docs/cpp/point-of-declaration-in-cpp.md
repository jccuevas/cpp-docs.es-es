---
title: "Punto de declaraci&#243;n en C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "punto de declaración"
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Punto de declaraci&#243;n en C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se considera que un nombre se declara inmediatamente después de su declarador pero antes de su inicializador \(opcional\).  \(Para obtener más información sobre declaradores, vea [Declaradores](http://msdn.microsoft.com/es-es/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838)\).  
  
 Considere este ejemplo:  
  
```  
// point_of_declaration1.cpp  
// compile with: /W1   
double dVar = 7.0;  
int main()  
{  
   double dVar = dVar;   // C4700  
}  
```  
  
 Si el punto de declaración estuviera *después* de la inicialización, `dVar` local se inicializaría en 7.0, el valor de la variable global `dVar`.  Sin embargo, como este no es el caso, `dVar` se inicializa en un valor no definido.  
  
## Vea también  
 [Ámbito](../cpp/scope-visual-cpp.md)