---
title: C4868 de advertencia del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 26031e1ac6f39d745a772e1becf3f817213a59d8
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-c4868"></a>C4868 de advertencia del compilador
compilador 'file(line_number)' no puede aplicar el orden de evaluación de izquierda a derecha en la lista de inicializadores entre llaves  
  
 Son los elementos de una lista de inicializadores entre llaves se evalúan en orden de izquierda a derecha. Hay dos casos en que el compilador no puede garantizar este orden: el primero es cuando algunos de los elementos son objetos que se pasan por valor; la segunda es cuando se compila con `/clr` y algunos de los elementos son campos de objetos o elementos de la matriz. Cuando el compilador no puede garantizar la evaluación de izquierda a derecha emite la advertencia C4868.  
  
 Esta advertencia se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual C++ 2015 Update 2. El código compilado antes de la actualización 2 de Visual C++ 2015 generará C4868.  
  
 De forma predeterminada, esta advertencia está desactivada. Use `/Wall` para activar esta advertencia.  
  
 Para resolver esta advertencia, considere primero si es necesario, como cuando la evaluación de los elementos puede producir efectos secundarios depende del orden evaluación de izquierda a derecha de los elementos de la lista de inicializadores. En muchos casos, el orden en que se evalúan los elementos no tiene un efecto notable.  
  
 Si el orden de evaluación debe ser de izquierda a derecha, considere si es posible pasar los elementos por referencia (const) en su lugar. Un cambio como este, elimina la advertencia en el siguiente ejemplo de código.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4868.  
  
```  
// C4868.cpp  
// compile with: /c /Wall  
#include <cstdio>  
  
class HasCopyConstructor  
{  
public:  
    int x;  
  
    HasCopyConstructor(int x): x(x) {}  
  
    HasCopyConstructor(const HasCopyConstructor& h): x(h.x)  
    {  
        printf("Constructing %d\n", h.x);  
    }  
};  
  
class TripWarning4868  
{  
public:  
    // note that taking "HasCopyConstructor" parameters by-value will trigger copy-construction.  
    TripWarning4868(HasCopyConstructor a, HasCopyConstructor b) {}  
  
    // This variation will not trigger the warning:  
    // TripWarning4868(const HasCopyConstructor& a, const HasCopyConstructor& b) {}  
};  
  
int main()  
{  
    HasCopyConstructor a{1};  
    HasCopyConstructor b{2};  
  
    // the warning will indicate the below line, the usage of the braced initializer list.  
    TripWarning4868 warningOnThisLine{a, b};  
};  
```
