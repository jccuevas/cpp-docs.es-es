---
title: Error de compilador Error C2659 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2659
dev_langs:
- C++
helpviewer_keywords:
- C2659
ms.assetid: b0883600-4d27-4ca7-a931-8ca6bd48654d
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: ad412a583a0835fab0f295acf928bba0bac1839d
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2659"></a>Error C2659 de Error del compilador
'operador' : función sobrecargada como operando izquierdo  
  
 Había una función en el operando izquierdo del operador especificado. La causa más común de este error es que el compilador ha analizado el identificador situado a la izquierda del operador como una función, cuando el desarrollador pretendía que fuera una variable. Para obtener más información, vea Wikipedia artículo [análisis molestos en el aspecto más](http://en.wikipedia.org/wiki/Most_vexing_parse). En este ejemplo se muestra una declaración de función y una definición de variable que pueden confundirse fácilmente:  
  
```  
// C2659a.cpp  
// Compile using: cl /W4 /EHsc C2659a.cpp  
#include <string>  
using namespace std;  
  
int main()   
{  
   string string1(); // string1 is a function returning string  
   string string2{}; // string2 is a string initialized to empty   
  
   string1 = "String 1"; // C2659  
   string2 = "String 2";  
}  
```  
  
 Para resolver este problema, cambie la declaración del identificador para que no pueda analizarse como una declaración de función.  
  
 El error C2659 también puede producirse cuando la función tiene un tipo que no se puede usar en el operando izquierdo del operador especificado en la expresión. En este ejemplo se genera el error C2659 cuando el código asigna un puntero de función a una función:  
  
```  
// C2659b.cpp  
// Compile using: cl /W4 /EHsc C2659b.cpp  
int func0(void) { return 42; }  
int (*func1)(void);  
  
int main()  
{  
   func1 = func0;  
   func0 = func1; // C2659  
}  
```
