---
title: "Punto de declaración en C++ | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64c1fa1d6d8feb4b869957101bb4b37f125d0f8b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="point-of-declaration-in-c"></a>Punto de declaración en C++
Se considera que un nombre se declara inmediatamente después de su declarador pero antes de su inicializador (opcional). (Para obtener más información sobre los declaradores, vea [declaraciones y definiciones](declarations-and-definitions-cpp.md).)  
  
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
  
 Si el punto de declaración estuviera *después* la inicialización, a continuación, en el equipo local `dVar` se inicializaría en 7.0, el valor de la variable global `dVar`. Sin embargo, como este no es el caso, `dVar` se inicializa en un valor no definido.  
  
## <a name="see-also"></a>Vea también  
 [Ámbito](../cpp/scope-visual-cpp.md)