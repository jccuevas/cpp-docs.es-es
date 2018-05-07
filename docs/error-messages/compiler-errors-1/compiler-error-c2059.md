---
title: Error del compilador C2059 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2059
dev_langs:
- C++
helpviewer_keywords:
- C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69182e4b27b474cafe60b71b02594a244f65a09b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2059"></a>Error del compilador C2059
error de sintaxis: 'token'  
  
 El token provocó un error de sintaxis.  
  
 En el ejemplo siguiente se genera un mensaje de error de la línea que declara `j`.  
  
```  
// C2059e.cpp  
// compile with: /c  
// C2143 expected  
// Error caused by the incorrect use of '*'.  
   int j*; // C2059   
```  
  
 Para determinar la causa del error, examine no sólo la línea que aparece en el mensaje de error, sino también las líneas por encima de él. Si examina las líneas no da ninguna pista sobre el problema, pruebe como comentario la línea que aparece en el mensaje de error y quizás varias líneas por encima de él.  
  
 Si el mensaje de error se produce en un símbolo que sigue inmediatamente a un `typedef` variable, asegúrese de que la variable se define en el código fuente.  
  
 Puede obtener C2059 si un símbolo se evalúa como nada, ya que puede ocurrir cuando **/D** `symbol` **=** se utiliza para compilar.  
  
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
  
 Otro caso en que puede producirse el error C2059 es cuando se compila una aplicación que especifica una estructura en los argumentos predeterminados para una función. El valor predeterminado de un argumento debe ser una expresión. Una lista de inicializadores, por ejemplo, uno que utiliza para inicializar una estructura, no es una expresión.  Para resolver este problema, defina un constructor para llevar a cabo la inicialización necesaria.  
  
 El ejemplo siguiente genera el error C2059:  
  
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
  
 El error C2059 también se puede producir si se define una clase de plantilla miembro o una función fuera de la clase. Para obtener información, consulte [el artículo de Knowledge Base 241949](http://support.microsoft.com/kb/241949).  
  
 C2059 puede producirse por una conversión de un formato incorrecto.  
  
 El ejemplo siguiente genera el error C2059:  
  
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
  
 También puede producirse el error C2059 si se intenta crear un nombre de espacio de nombres que contiene un punto.  
  
 El ejemplo siguiente genera el error C2059:  
  
```  
// C2059d.cpp  
// compile with: /c  
namespace A.B {}   // C2059  
  
// OK  
namespace A  {  
   namespace B {}  
}  
```  
  
 C2059 puede producirse cuando un operador que puede calificar un nombre (`::`, `->`, y `.`) debe ir seguida de la palabra clave `template`, tal y como se muestra en este ejemplo:  
  
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
  
 De forma predeterminada, C++ supone que `AY::Rebind` no es una plantilla; por lo tanto, los siguientes `<` se interpreta como una menor-que el inicio de sesión.  Debe indicar al compilador explícitamente que `Rebind` es una plantilla para que pueda analizar correctamente el corchete angular de cierre. Para corregir este error, utilice el `template` palabra clave en nombre del tipo dependientes, como se muestra aquí:  
  
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