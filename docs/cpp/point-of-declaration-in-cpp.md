---
title: "Punto de declaración en C++ | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 77f66182052cc2a031b7f1f8db8018f49b36801d
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

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
