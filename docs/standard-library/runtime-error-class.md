---
title: "runtime_error (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.runtime_error"
  - "runtime_error"
  - "stdexcept/std::runtime_error"
  - "std::runtime_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "runtime_error (clase)"
ms.assetid: 4d0227bf-847b-45a2-a320-2351ebf98368
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# runtime_error (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase que actúa como la clase base para todas las excepciones iniciadas para informar de errores supuestamente detectables únicamente cuando se ejecute el programa.  
  
## Sintaxis  
  
```  
class runtime_error : public exception {  
public:  
    explicit runtime_error(const string& message);  
    explicit runtime_error(const char *message);  
};  
```  
  
## Comentarios  
 El valor devuelto por [exception \(Clase\)](../standard-library/exception-class1.md) es una copia de **mensaje**`.`[datos](../Topic/basic_string::data.md).  
  
## Ejemplo  
  
```  
// runtime_error.cpp  
// compile with: /EHsc /GR  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
// runtime_error  
   try   
   {  
      locale loc( "test" );  
   }  
   catch ( exception &e )   
   {  
      cerr << "Caught " << e.what( ) << endl;  
      cerr << "Type " << typeid( e ).name( ) << endl;  
   };  
}  
```  
  
 **Detectar std::runtime\_error de clase de tipo de nombre de configuración regional incorrecta**   
## Requisitos  
 **Encabezado:** \< stdexcept \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [exception \(Clase\)](../standard-library/exception-class1.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)