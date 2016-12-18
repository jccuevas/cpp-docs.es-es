---
title: "Error del compilador C2668 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2668"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2668"
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2668
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : llamada ambigua a una función sobrecargada  
  
 La llamada de función sobrecargada especificada no se pudo resolver.  Puede resultar conveniente convertir explícitamente uno o varios de los parámetros reales.  
  
 También se obtiene este error mediante el uso de plantillas.  Si en alguna clase hay una función miembro normal y una función miembro basada en plantilla con la misma firma, tiene prioridad esta última.  La implementación actual de Visual C\+\+ tiene esta limitación.  
  
 Vea el artículo de Knowledge Base Q240869 para obtener más información sobre la ordenación parcial de plantillas de función.  
  
 En caso de que esté compilando un proyecto ATL que contenga un objeto COM compatible con `ISupportErrorInfo`, vea el artículo de Knowledge Base Q243298.  
  
## Ejemplo  
 El código siguiente genera el error C2668:  
  
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
  
## Ejemplo  
 Otra forma de corregir este error es mediante una [declaración using](../../cpp/using-declaration.md):  
  
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
  
## Ejemplo  
 Este error también puede producirse como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003: la conversión de constante 0 es ambigua.  
  
 La conversión mediante la constante 0 es ambigua, ya que int requiere conversiones a long y void\*.  Para corregir este error, convierta 0 al tipo exacto del parámetro de la función para la que se está utilizando, de forma que no sea necesario realizar ninguna conversión \(este código será válido en la versiones Visual Studio .NET 2003 y Visual Studio .NET de Visual C\+\+\).  
  
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
  
## Ejemplo  
 Este error puede producirse porque, ahora, CRT incorpora formas de tipo float y double de todas las funciones matemáticas.  
  
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
  
## Ejemplo  
 Este error puede producirse porque la función pow\(int, int\) se haya quitado de math.h en CRT.  
  
```  
// C2668e.cpp  
#include <math.h>  
int main() {  
   pow(9,9);   // C2668  
   pow((double)9,9);   // OK  
}  
```