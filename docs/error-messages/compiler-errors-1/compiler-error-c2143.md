---
title: "Error del compilador C2143 | Microsoft Docs"
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
  - "C2143"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2143"
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2143
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error de sintaxis : falta 'token1' delante de 'token2'  
  
 El compilador esperaba un token específico \(es decir, un elemento de lenguaje que no fuera un espacio en blanco\) pero, en su lugar, ha encontrado otro distinto.  
  
 Para obtener información sobre este error cuando aparece cuando se usa un bloque de función\- intento, vea [Artículo 241706 de Knowledge Base](http://support.microsoft.com/kb/241706).  
  
 Compruebe la [Referencia del lenguaje C\+\+](../../cpp/cpp-language-reference.md) para determinar en qué punto es incorrecto sintácticamente el código.  Es posible que el compilador informe del error después de encontrar la línea que causa el problema, por lo que conviene comprobar varias líneas anteriores al error.  
  
 El error C2143 puede producirse en diversas situaciones.  
  
 Se puede producir cuando un operador que puede calificar un nombre \(`::`, `->`, y `.`\) debe ir seguido de la palabra clave `template`, como en este ejemplo:  
  
```cpp  
class MyClass  
{  
    template<class Ty, typename PropTy>  
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143  
    {  
    };  
};  
  
```  
  
 De forma predeterminada, C\+\+ supone que `Ty::PutFuncType` no es una plantilla; por consiguiente, `<` siguiente se interpreta como signo menor que.  Debe indicar al compilador explícitamente que `PutFuncType` es una plantilla para poder correctamente analizar el corchete angular.  Para corregir este error, utilice la palabra clave de `template` en el nombre del tipo dependiente, como se muestra aquí:  
  
```cpp  
class MyClass  
{  
    template<class Ty, typename PropTy>  
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct  
    {  
    };  
};  
  
```  
  
 C2143 puede producirse cuando se utiliza **\/clr** y una directiva de `using` tiene un error de sintaxis:  
  
```cpp  
// C2143a.cpp  
// compile with: /clr /c  
using namespace System.Reflection;   // C2143  
using namespace System::Reflection;  
```  
  
 También puede producirse cuando se intenta compilar un archivo de código fuente utilizando la sintaxis de CLR sin utilizar **\/clr**:  
  
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
  
 El primer carácter de no de espacio en blanco que sigue una instrucción de `if` debe ser un paréntesis de apertura.  De lo contrario, el compilador no podrá seguir traduciendo:  
  
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
  
 C2143 puede aparecer cuando una llave de cierre, paréntesis, o un punto y coma falta en la línea donde se ha detectado el error o en una de las líneas inmediatamente anteriores:  
  
```caml  
// C2143d.cpp  
// compile with: /c  
class X {  
   int member1;  
   int member2   // C2143  
} x;  
```  
  
 O cuando hay etiqueta no válida en una declaración de clase:  
  
```cpp  
// C2143e.cpp  
class X {  
   int member;  
} x;  
  
class + {};   // C2143 + is an invalid tag name  
class ValidName {};   // OK  
```  
  
 O cuando una etiqueta no está asociado a la instrucción.  Si, aun así, necesita colocar una etiqueta sola \(por ejemplo, al final de una instrucción compuesta\), deberá adjuntarla a una instrucción nula:  
  
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
  
 El error puede producirse cuando se efectúa una llamada incompleta a un tipo en la biblioteca estándar de C\+\+:  
  
```cpp  
// C2143g.cpp  
// compile with: /EHsc /c  
#include <vector>  
static vector<char> bad;   // C2143  
static std::vector<char> good;   // OK  
```  
  
 O hay una palabra clave que falta de `typename` :  
  
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
  
 O si intenta definir una instancia explícita:  
  
```cpp  
// C2143i.cpp  
// compile with: /EHsc /c  
// template definition  
template <class T>  
void PrintType(T i, T j) {}  
  
template void PrintType(float i, float j){}   // C2143  
template void PrintType(float i, float j);   // OK  
```  
  
 En un programa de C, las variables se deben declarar al principio de la función y no se pueden declarar después de que esta ejecute instrucciones que no son declaraciones.  
  
```c  
// C2143j.c  
int main()   
{  
    int i = 0;  
    i++;  
    int j = 0; // C2143  
}  
  
```