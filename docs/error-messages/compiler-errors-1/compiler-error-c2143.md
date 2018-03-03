---
title: Error del compilador C2143 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2143
dev_langs:
- C++
helpviewer_keywords:
- C2143
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa7560b3b7d13beb416c2f500c0ab692e9f0d717
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2143"></a>Error del compilador C2143
error de sintaxis: falta 'token1' delante de 'token2'  
  
 El compilador esperaba un token específico (es decir, un elemento del lenguaje que no sea un espacio en blanco) y encuentra otro token en su lugar.  
  
 Para obtener información sobre este error cuando se produce cuando se usa un bloque try de función, vea [el artículo de Knowledge Base 241706](http://support.microsoft.com/kb/241706).  
  
 Compruebe el [referencia del lenguaje C++](../../cpp/cpp-language-reference.md) para determinar donde el código es sintácticamente incorrecto. Dado que el compilador puede notificar este error después de que encuentre la línea que causa el problema, compruebe varias líneas de código que preceden el error.  
  
 C2143 puede producirse en diversas situaciones.  
  
 Puede producirse cuando un operador que puede calificar un nombre (`::`, `->`, y `.`) debe ir seguida de la palabra clave `template`, como en este ejemplo:  
  
```cpp  
class MyClass  
{  
    template<class Ty, typename PropTy>  
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143  
    {  
    };  
};  
  
```  
  
 De forma predeterminada, C++ supone que `Ty::PutFuncType` no es una plantilla; por lo tanto, los siguientes `<` se interpreta como una menor-que el inicio de sesión.  Debe indicar al compilador explícitamente que `PutFuncType` es una plantilla para que pueda analizar correctamente el corchete angular de cierre. Para corregir este error, utilice el `template` palabra clave en nombre del tipo dependientes, como se muestra aquí:  
  
```cpp  
class MyClass  
{  
    template<class Ty, typename PropTy>  
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct  
    {  
    };  
};  
  
```  
  
 Error C2143 puede producirse cuando **/CLR** se utiliza y una `using` directiva tiene un error de sintaxis:  
  
```cpp  
// C2143a.cpp  
// compile with: /clr /c  
using namespace System.Reflection;   // C2143  
using namespace System::Reflection;  
```  
  
 También puede producirse cuando se intenta compilar un archivo de código fuente utilizando sintaxis CLR sin usar también **/CLR**:  
  
```cpp  
// C2143b.cpp  
ref struct A {   // C2143 error compile with /clr  
   void Test() {}  
};  
  
int main() {  
   A a;  
   a.Test();  
}  
```  
  
 El primer carácter no espacios en blanco que sigue a un `if` instrucción debe ser un paréntesis izquierdo. El compilador no puede convertir cualquier otra cosa:  
  
```cpp  
// C2143c.cpp  
int main() {  
   int j = 0;  
  
   // OK  
   if (j < 25)  
      ;  
  
   if (j < 25)   // C2143  
}  
```  
  
 C2143 puede producirse cuando una llave de cierre, un paréntesis o un punto y coma falta en la línea donde se detectó el error o en una de las líneas inmediatamente anteriores:  
  
```cpp  
// C2143d.cpp  
// compile with: /c  
class X {  
   int member1;  
   int member2   // C2143  
} x;  
```  
  
 O bien, cuando hay una etiqueta no válida en una declaración de clase:  
  
```cpp  
// C2143e.cpp  
class X {  
   int member;  
} x;  
  
class + {};   // C2143 + is an invalid tag name  
class ValidName {};   // OK  
```  
  
 O bien, si una etiqueta no está conectada a una instrucción. Si se debe colocar una etiqueta por sí solo, por ejemplo, al final de una instrucción compuesta, adjuntarla a una instrucción null:  
  
```cpp  
// C2143f.cpp  
// compile with: /c  
void func1() {  
   // OK  
   end1:  
      ;  
  
   end2:   // C2143  
}  
```  
  
 El error puede producirse cuando se realiza una llamada sin calificar a un tipo en la biblioteca estándar de C++:  
  
```cpp  
// C2143g.cpp  
// compile with: /EHsc /c  
#include <vector>  
static vector<char> bad;   // C2143  
static std::vector<char> good;   // OK  
```  
  
 O si hay una falta `typename` palabra clave:  
  
```cpp  
// C2143h.cpp  
template <typename T>  
struct X {  
   struct Y {  
      int i;  
   };  
   Y memFunc();  
};  
template <typename T>  
X<T>::Y X<T>::memFunc() {   // C2143  
// try the following line instead  
// typename X<T>::Y X<T>::memFunc() {  
   return Y();  
}  
```  
  
 O bien, si se intenta definir una creación de instancias explícita:  
  
```cpp  
// C2143i.cpp  
// compile with: /EHsc /c  
// template definition  
template <class T>  
void PrintType(T i, T j) {}  
  
template void PrintType(float i, float j){}   // C2143  
template void PrintType(float i, float j);   // OK  
```  
  
 En un programa C, las variables deben declararse al principio de la función y no pueden declararse después de la función ejecuta las instrucciones de declaración no.  
  
```C  
// C2143j.c  
int main()   
{  
    int i = 0;  
    i++;  
    int j = 0; // C2143  
}  
```  
