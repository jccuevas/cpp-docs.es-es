---
title: "Excepciones de C++ no controladas | Microsoft Docs"
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
  - "control de excepciones de C++, excepciones no controladas"
  - "catch (palabra clave) [C++], controlador no encontrado"
  - "controladores de eventos, excepciones no controladas"
  - "excepciones, no controladas"
  - "excepciones no controladas"
ms.assetid: 13f09c53-9254-4407-9db9-14e730e047cc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Excepciones de C++ no controladas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si no se puede encontrar un controlador coincidente \(o el controlador **catch** de puntos suspensivos\) para la excepción actual, se llama a la función predefinida `terminate` en tiempo de ejecución. \(También puede llamar explícitamente a `terminate` en cualquiera de sus controladores\). La acción predeterminada de `terminate` es llamar a `abort`.  Si desea que `terminate` llame a otra función del programa antes de salir de la aplicación, llame a la función `set_terminate` con el nombre de la función que se va a llamar como argumento único.  Puede llamar a `set_terminate` en cualquier punto del programa.  La rutina `terminate` siempre llama a la última función especificada como argumento para `set_terminate`.  
  
## Ejemplo  
 En el ejemplo siguiente se inicia una excepción `char *`, pero no contiene un controlador designado para detectar excepciones de tipo `char *`.  La llamada a `set_terminate` indica a `terminate` que llame a `term_func`.  
  
```  
// exceptions_Unhandled_Exceptions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
void term_func() {  
   cout << "term_func was called by terminate." << endl;  
   exit( -1 );  
}  
int main() {  
   try  
   {  
      set_terminate( term_func );  
      throw "Out of memory!"; // No catch handler for this exception  
   }  
   catch( int )  
   {  
      cout << "Integer exception raised." << endl;  
   }  
   return 0;  
}  
```  
  
## Salida  
  
```  
term_func was called by terminate.  
```  
  
 La función `term_func` debe finalizar el programa o el subproceso actual, idealmente mediante una llamada a `exit`.  Si no lo hace y, en su lugar, regresa a su llamador, se llama a `abort`.  
  
## Vea también  
 [Control de excepciones de C\+\+](../cpp/cpp-exception-handling.md)