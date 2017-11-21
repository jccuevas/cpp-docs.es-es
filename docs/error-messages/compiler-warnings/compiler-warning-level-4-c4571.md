---
title: Compilador advertencia (nivel 4) C4571 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4571
dev_langs: C++
helpviewer_keywords: C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 293a3ffa2ddb14292b33ed222f18ca6f8dc6faec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4571"></a>Advertencia del compilador (nivel 4) C4571
Informativo: la semántica de catch cambiada desde Visual C++ 7.1; ya no se detectan excepciones estructuradas (SEH)  
  
 C4571 se genera para cada bloque catch (...) al compilar con **/EHs**.  
  
 Cuando se compila con **/EHs**, un bloque catch (...) no detecta una excepción estructurada (división por cero, un puntero nulo, por ejemplo); una catch (...) bloque will solo catch producida explícitamente, las excepciones de C++.  Para más información, consulte [Control de excepciones](../../cpp/exception-handling-in-visual-cpp.md).  
  
 De forma predeterminada, esta advertencia está desactivada.  Active esta advertencia para asegurarse de que cuando se compila con **/EHs** los bloques catch (...) no tiene intención de detectar las excepciones estructuradas.  Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.  
  
 Resolver la advertencia C4571 en uno de los siguientes métodos,  
  
-   Compile con **/EHa** si todavía desea que los bloques catch (...) para detectar las excepciones estructuradas.  
  
-   No habilite C4571 si no desea que los bloques catch (...) para detectar las excepciones estructuradas, pero desea utilizar los bloques catch (...).  Todavía puede detectar las excepciones estructuradas mediante las palabras clave de control de excepciones estructuradas (**__try**, **__except**, y **__finally**).  Pero recuerde que, cuando se compila **/EHs** destructores solo se llamará cuando se produce una excepción de C++, no cuando se produce una excepción SEH.  
  
-   Reemplace el bloque catch (...) por bloques catch para excepciones concretas de C++ y, opcionalmente, agregue el control en el control de excepciones de C++ estructurado de excepciones (**__try**, **__except**, y **_ _finally**).  Vea [control de excepciones estructurado (C/C ++)](../../cpp/structured-exception-handling-c-cpp.md) para obtener más información.  
  
 Vea [/EH (modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4571.  
  
```  
// C4571.cpp  
// compile with: /EHs /W4 /c  
#pragma warning(default : 4571)  
int main() {  
   try {  
      int i = 0, j = 1;  
      j /= i;   // this will throw a SE (divide by zero)  
   }  
   catch(...) {}   // C4571 warning  
}  
```