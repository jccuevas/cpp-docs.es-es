---
title: "logic_error (Clase) | Microsoft Docs"
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
  - "stdexcept/std::logic_error"
  - "std::logic_error"
  - "logic_error"
  - "std.logic_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "logic_error (clase)"
ms.assetid: b290d73d-94e1-4288-af86-2bb5d71f677a
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# logic_error (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase que actúa como la clase base para todas las excepciones iniciadas para informar de errores supuestamente detectables antes de que se ejecute el programa, como las infracciones de las condiciones lógicas previas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class logic_error : public exception {  
public:  
    explicit logic_error(const string& message);

    explicit logic_error(const char *message);

};  
```  
  
## <a name="remarks"></a>Comentarios  
 El valor devuelto por [qué](../standard-library/exception-class1.md) es una copia de **mensaje**`.`[datos](../standard-library/basic-string-class.md#basic_string__data).  
  
## <a name="example"></a>Ejemplo  
  
```  
// logic_error.cpp  
// compile with: /EHsc /GR  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   try   
   {  
      throw logic_error( "logic error" );  
   }  
   catch ( exception &e )   
   {  
      cerr << "Caught: " << e.what( ) << endl;  
      cerr << "Type: " << typeid( e ).name( ) << endl;  
   };  
}  
```  
  
 **Salida**  
  
```  
Caught: logic error  
Type: class std::logic_error  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< stdexcept>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
[Clase Exception](../standard-library/exception-class1.md)  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

