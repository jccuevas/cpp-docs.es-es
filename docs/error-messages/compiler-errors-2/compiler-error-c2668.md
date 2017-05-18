---
title: Compilador Error C2668 | Documentos de Microsoft
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2668
dev_langs:
- C++
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: b790beb88de009e1c7161f3c9af6b3e21c22fd8e
ms.openlocfilehash: 6bb1dc7c1dbf26a4ff8ec25a46fe7128e0fb6aa8
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="compiler-error-c2668"></a>C2668 de Error del compilador
'función': llamada ambigua a una función sobrecargada  
  
 No se pudo resolver la llamada de función sobrecargada especificada. Puede convertir explícitamente uno o varios de los parámetros reales.  
  
 También puede obtener este error mediante el uso de la plantilla. Si, en la misma clase, tiene una función miembro normal y una función de miembro con plantilla con la misma firma, uno con plantilla debe aparecer en primer lugar. Se trata de una limitación de la implementación actual de Visual C++.  
  
 Vea el artículo de Knowledge Base Q240869 para obtener más información sobre la ordenación parcial de plantillas de función.  
  
 Si está creando un proyecto ATL que contiene un objeto COM compatible con `ISupportErrorInfo`, vea el artículo de Knowledge Base Q243298.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2668:  
  
```  
// C2668.cpp  
struct A {};  
struct B : A {};  
struct X {};  
struct D : B, X {};  
  
void func( X, X ){}  
void func( A, B ){}  
D d;  
int main() {  
   func( d, d );   // C2668 D has an A, B, and X   
   func( (X)d, (X)d );   // OK, uses func( X, X )  
}  
```  
  
## <a name="example"></a>Ejemplo  
 Otra manera de resolver este error es con un [mediante declaración](../../cpp/using-declaration.md):  
  
```  
// C2668b.cpp  
// compile with: /EHsc /c  
// C2668 expected  
#include <iostream>  
class TypeA {  
public:  
   TypeA(int value) {}  
};  
  
class TypeB {  
   TypeB(int intValue);  
   TypeB(double dbValue);  
};  
  
class TestCase {  
public:  
   void AssertEqual(long expected, long actual, std::string  
                    conditionExpression = "");  
};  
  
class AppTestCase : public TestCase {  
public:  
   // Uncomment the following line to resolve.  
   // using TestCase::AssertEqual;  
   void AssertEqual(const TypeA expected, const TypeA actual,  
                    std::string conditionExpression = "");  
   void AssertEqual(const TypeB expected, const TypeB actual,  
                    std::string conditionExpression = "");  
};  
  
class MyTestCase : public AppTestCase {  
   void TestSomething() {  
      int actual = 0;  
      AssertEqual(0, actual, "Value");  
   }  
};  
```  
  
## <a name="example"></a>Ejemplo  
 Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio .NET 2003: conversión ambigua en la conversión de constante 0.  
  
 La conversión mediante la constante 0 es ambigua debido a que int requiere conversiones a long y void *. Para resolver este error, convierta 0 al tipo exacto del parámetro de función para que se va a usarlo para que sea necesario ninguna conversión que se realicen (este código será válido en las versiones de Visual Studio .NET 2003 y Visual Studio .NET de Visual C++).  
  
```  
// C2668c.cpp  
#include "stdio.h"  
void f(long) {  
   printf_s("in f(long)\n");  
}  
void f(void*) {  
   printf_s("in f(void*)\n");  
}  
int main() {  
   f((int)0);   // C2668  
  
   // OK  
   f((long)0);  
   f((void*)0);  
}  
```  
  
## <a name="example"></a>Ejemplo  
 Este error puede producirse porque CRT tiene ahora formas float y double de todas las funciones matemáticas.  
  
```  
// C2668d.cpp  
#include <math.h>  
int main() {  
   int i = 0;  
   float f;  
   f = cos(i);   // C2668  
   f = cos((float)i);   // OK  
}  
```  
  
## <a name="example"></a>Ejemplo  
 Este error puede producirse porque la función pow (int, int) se ha quitado de math.h en CRT.  
  
```  
// C2668e.cpp  
#include <math.h>  
int main() {  
   pow(9,9);   // C2668  
   pow((double)9,9);   // OK  
}  
```

## <a name="example"></a>Ejemplo  
Este código se ejecuta correctamente en Visual Studio 2015, pero se produce un error en Visual Studio de 2017 y versiones posteriores con C2668. En Visual Studio 2015, el compilador trataba erróneamente la inicialización de lista de copia como si fuera inicialización de copia regular; solo consideraba la conversión de constructores para la resolución de sobrecarga. 

```
C++
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```
