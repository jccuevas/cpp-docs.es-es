---
title: "Especificaciones de excepciones (throw) (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Control de excepciones de C++, producir excepciones"
  - "excepciones, especificaciones de excepción"
  - "throw (palabra clave) [C++], especificaciones de excepción"
  - "throw (palabra clave) [C++], throw() frente a throw(...)"
  - "producir excepciones, throw (palabra clave)"
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
caps.latest.revision: 20
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Especificaciones de excepciones (throw) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las especificaciones de excepción son una característica del lenguaje C\+\+ que está en desuso en C\+\+11.  Se diseñaron para proporcionar información de resumen sobre qué excepciones se pueden iniciar desde una función, pero en la práctica resultaron ser problemáticas.  La única especificación de excepciones que resultó útil de alguna manera fue throw\(\).  Por ejemplo:  
  
```  
void MyFunction(int i) throw();  
```  
  
 indica al compilador que la función no produce ninguna excepción.  Es el equivalente a usar [\_\_declspec\(nothrow\)](../cpp/nothrow-cpp.md).  Su uso se considera opcional.  
  
 **\(C\+\+11\)** En el estándar C\+\+11 de ISO, se presentó el operador [noexcept](../cpp/noexcept-cpp.md), que se admite en Visual Studio de 2015 y en versiones posteriores.  Use `noexcept` siempre que pueda para especificar si una función puede generar excepciones.  
  
 Visual C\+\+ no sigue el estándar ISO C\+\+ en su implementación de las especificaciones de excepciones.  La tabla siguiente resume la implementación de Visual C\+\+ de las especificaciones de excepciones:  
  
|Especificación de la excepción|Significado|  
|------------------------------------|-----------------|  
|throw\(\)|La función no produce ninguna excepción.  Sin embargo, si se produce una excepción de una función throw\(\) marcada, el compilador de Visual C\+\+ no la llamará inesperada \(vea [unexpected](../c-runtime-library/reference/unexpected-crt.md) y [unexpected](../Topic/unexpected%20\(%3Cexception%3E\).md) para más información\).  Si una función se marca con throw\(\), el compilador de Visual C\+\+ asumirá que esta función no produce excepciones de C\+\+ y generará el código en consecuencia.  Debido a las optimizaciones del código que puede realizar el compilador de C\+\+ \(basado en la suposición de que la función no produce ninguna excepción de C\+\+\), si una función produce una excepción, el programa puede no ejecutarse correctamente.|  
|throw\(...\)|La función puede producir una excepción.|  
|throw\(`type`\)|La función puede producir una excepción del tipo `type`.  Sin embargo, en Visual C\+\+ .NET, esto se interpreta como throw\(...\).  Vea [Especificadores de excepciones de funciones](../misc/15-4-function-exception-specifiers.md).|  
  
 Si el control de excepciones se utiliza en una aplicación, debe haber una o varias funciones que controlen las excepciones producidas.  Cualquier función llamada entre la que produce una excepción y la que controla la excepción debe ser capaz de producir la excepción.  
  
 El comportamiento de throw de una función depende de los factores siguientes:  
  
-   Si está compilando la función con C o C\+\+.  
  
-   Qué opción de compilador [\/EH](../build/reference/eh-exception-handling-model.md) está usando.  
  
-   Si ha especificado explícitamente la especificación de la excepción.  
  
 Las especificaciones de excepciones explícitas no se permiten en las funciones de C.  
  
 En la tabla siguiente se resume el comportamiento de throw de una función:  
  
|Función|\/EHsc|\/EHs|\/EHa|\/EHac|  
|-------------|------------|-----------|-----------|------------|  
|Función de C|throw\(\)|throw\(...\)|throw\(...\)|throw\(...\)|  
|Función de C\+\+ sin especificación de excepciones|throw\(...\)|throw\(...\)|throw\(...\)|throw\(...\)|  
|Función de C\+\+ con especificación de excepciones throw\(\)|throw\(\)|throw\(\)|throw\(...\)|throw\(...\)|  
|Función de C\+\+ con especificación de excepciones throw\(...\)|throw\(...\)|throw\(...\)|throw\(...\)|throw\(...\)|  
|Función de C\+\+ con especificación de excepciones \(`type`\)|throw\(...\)|throw\(...\)|throw\(...\)|throw\(...\)|  
  
## Ejemplo  
  
```cpp  
// exception_specification.cpp  
// compile with: /EHs  
#include <stdio.h>  
  
void handler() {  
   printf_s("in handler\n");  
}  
  
void f1(void) throw(int) {  
   printf_s("About to throw 1\n");  
   if (1)  
      throw 1;  
}  
  
void f5(void) throw() {  
   try {  
      f1();  
   }  
   catch(...) {  
      handler();  
    }  
}  
  
// invalid, doesn't handle the int exception thrown from f1()  
// void f3(void) throw() {  
//   f1();  
// }  
  
void __declspec(nothrow) f2(void) {  
   try {  
      f1();  
   }  
   catch(int) {  
      handler();  
    }  
}  
  
// only valid if compiled without /EHc   
// /EHc means assume extern "C" functions don't throw exceptions  
extern "C" void f4(void);  
void f4(void) {  
   f1();  
}  
  
int main() {  
   f2();  
  
   try {  
      f4();  
   }  
   catch(...) {  
      printf_s("Caught exception from f4\n");  
   }  
   f5();  
}  
```  
  
  **Acerca de throw 1**  
**en controlador**  
**Acerca de throw 1**  
**Excepción detectada de f4**  
**Acerca de throw 1**  
**en controlador**   
## Vea también  
 [Instrucciones try, throw y catch \(C\+\+\)](../cpp/try-throw-and-catch-statements-cpp.md)   
 [Control de excepciones de C\+\+](../cpp/cpp-exception-handling.md)