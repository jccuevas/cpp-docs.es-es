---
title: "Error del compilador C2059 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2059"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2059"
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# Error del compilador C2059
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error de sintaxis : 'símbolo \(token\)'  
  
 El símbolo \(token\) originó un error de sintaxis.  
  
 El siguiente ejemplo se genera un mensaje de error para la línea que declara `j`.  
  
```  
// C2059e.cpp  
// compile with: /c  
// C2143 expected  
// Error caused by the incorrect use of '*'.  
   int j*; // C2059   
```  
  
 Para determinar la causa del error, examine no solo la línea que aparece en el mensaje de error, sino también las líneas anteriores.  Si examina las líneas no produce ninguna pista sobre el problema, pruebe a marcar como comentario la línea que aparece en el mensaje de error y posiblemente varias líneas anteriores.  
  
 Si el mensaje de error en un símbolo de manera siga una variable de `typedef` , asegúrese de que la variable esté definida en el código fuente.  
  
 Se puede producir el error C2059 si un símbolo se evalúa como nothing, como puede ocurrir cuando **\/D**`symbol`**\=** se utiliza para compilar.  
  
```  
// C2059a.cpp  
// compile with: /DTEST=  
#include <stdio.h>  
  
int main() {  
   #ifdef TEST  
      printf_s("\nTEST defined %d", TEST);   // C2059  
   #else  
      printf_s("\nTEST not defined");  
   #endif  
}  
```  
  
 Otro caso en el que puede producirse el error C2059 cuando se compila una aplicación que especifica una estructura en los argumentos predeterminados para una función.  El valor predeterminado de un argumento debe ser una expresión.  Un inicializador lista\- para el ejemplo, uno que se inicializaba a estructura no es una expresión.  Para resolver este problema, defina un constructor para realizar la inicialización necesaria.  
  
 El código siguiente genera C2059:  
  
```  
// C2059b.cpp  
// compile with: /c  
struct ag_type {  
   int a;  
   float b;  
   // Uncomment the following line to resolve.  
   // ag_type(int aa, float bb) : a(aa), b(bb) {}   
};  
  
void func(ag_type arg = {5, 7.0});   // C2059  
void func(ag_type arg = ag_type(5, 7.0));   // OK  
```  
  
 El error C2059 también se puede producir si se define una función o clase de plantilla miembro fuera de la clase.  Para obtener más información, [Artículo 241949 de Knowledge Base](http://support.microsoft.com/kb/241949)vea.  
  
 Puede producirse el error C2059 a causa de una conversión incorrecta.  
  
 El código siguiente genera el error C2059:  
  
```  
// C2059c.cpp  
// compile with: /clr  
using namespace System;  
ref class From {};  
ref class To : public From {};  
  
int main() {  
   From^ refbase = gcnew To();  
   To^ refTo = safe_cast<To^>(From^);   // C2059  
   To^ refTo2 = safe_cast<To^>(refbase);   // OK  
}  
```  
  
 También puede producirse el error C2059 si se intenta crear un nombre de espacio de nombres que contenga un punto.  
  
 El código siguiente genera el error C2059:  
  
```  
// C2059d.cpp  
// compile with: /c  
namespace A.B {}   // C2059  
  
// OK  
namespace A  {  
   namespace B {}  
}  
```  
  
 C2059 puede aparecer cuando un operador que puede calificar un nombre \(`::`, `->`, y `.`\) debe ir seguido de la palabra clave `template`, como se muestra en este ejemplo:  
  
```cpp  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    typedef typename AY::Rebind<X>::Other AX; // error C2059  
};  
  
```  
  
 De forma predeterminada, C\+\+ supone que `AY::Rebind` no es una plantilla; por consiguiente, `<` siguiente se interpreta como signo menor que.  Debe indicar al compilador explícitamente que `Rebind` es una plantilla para poder correctamente analizar el corchete angular.  Para corregir este error, utilice la palabra clave de `template` en el nombre del tipo dependiente, como se muestra aquí:  
  
```cpp  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    typedef typename AY::template Rebind<X>::Other AX; // correct  
};  
  
```