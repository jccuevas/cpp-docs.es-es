---
title: Punto de declaración en C++ | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e42f43e6187e19df6e9c1111c0e92aa4b9929199
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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