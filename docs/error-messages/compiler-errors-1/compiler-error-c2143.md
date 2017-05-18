---
title: Compilador Error C2143 | Documentos de Microsoft
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
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: faa9361da0091ec86628af19a03eadb133ea43cc
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2143"></a>Error del compilador C2143
error de sintaxis: falta 'símbolo1' delante de 'símbolo2'  
  
 El compilador esperaba un token específico (es decir, un elemento de lenguaje que no sea un espacio en blanco) y encuentra otro token en su lugar.  
  
 Para obtener información acerca de este error cuando se produce cuando se usa un bloque try de función, consulte [el artículo de Knowledge Base 241706](http://support.microsoft.com/kb/241706).  
  
 Compruebe el [referencia del lenguaje C++](../../cpp/cpp-language-reference.md) para determinar que el código es sintácticamente incorrecto. Porque el compilador puede informar de este error después de encontrar la línea que causa el problema, compruebe varias líneas de código anteriores al error.  
  
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
  
 De forma predeterminada, C++ supone que `Ty::PutFuncType` no es una plantilla; por lo tanto, la siguiente `<` se interpreta como un menor-que el inicio de sesión.  Debe indicar al compilador explícitamente que `PutFuncType` es una plantilla para que pueda analizar correctamente el corchete angular de cierre. Para corregir este error, utilice el `template` (palabra clave) en el nombre del tipo dependientes, como se muestra aquí:  
  
```cpp  
class MyClass  
{  
    template<class Ty, typename PropTy>  
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct  
    {  
    };  
};  
  
```  
  
 Error C2143 puede producirse cuando **/CLR** se utiliza y un `using` directiva tiene un error de sintaxis:  
  
```cpp  
// C2143a.cpp  
// compile with: /clr /c  
using namespace System.Reflection;   // C2143  
using namespace System::Reflection;  
```  
  
 También puede producirse cuando intenta compilar un archivo de código fuente utilizando sintaxis CLR sin usar también **/CLR**:  
  
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
  
 El primer carácter no espacios en blanco que sigue un `if` instrucción debe ser un paréntesis izquierdo. El compilador no puede traducir nada:  
  
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
  
 C2143 puede producirse cuando está en la línea donde se detectó el error falta una llave de cierre, un paréntesis o un punto y coma o en una de las líneas justo encima de:  
  
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
  
 O bien, si una etiqueta no está conectada a una instrucción. Si debe colocar una etiqueta por sí mismo, por ejemplo, al final de una instrucción compuesta, adjuntarla a una instrucción nula:  
  
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
  
 El error puede producirse cuando se realiza una llamada incompleta a un tipo en la biblioteca estándar de C++:  
  
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
  
 O bien, si intenta definir una creación de instancias explícita:  
  
```cpp  
// C2143i.cpp  
// compile with: /EHsc /c  
// template definition  
template <class T>  
void PrintType(T i, T j) {}  
  
template void PrintType(float i, float j){}   // C2143  
template void PrintType(float i, float j);   // OK  
```  
  
 En un programa de C, las variables deben declararse al principio de la función y no se puede declarar después de las instrucciones de declaración no ejecuta la función.  
  
```C  
// C2143j.c  
int main()   
{  
    int i = 0;  
    i++;  
    int j = 0; // C2143  
}  
```  

