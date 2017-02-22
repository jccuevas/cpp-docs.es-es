---
title: "range_error (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdexcept/std::range_error"
  - "std.range_error"
  - "range_error"
  - "std::range_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "range_error (clase)"
ms.assetid: 8afb3e88-fc49-4213-b096-ed63d7aea37c
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# range_error (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un error de rango.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class range_error : public runtime_error {  
public:  
    explicit range_error(const string& message);

    explicit range_error(const char *message);

};  
```  
  
## <a name="remarks"></a>Comentarios  
 El valor devuelto por [qué](../standard-library/exception-class1.md) es una copia de **mensaje**`.`[datos](../standard-library/basic-string-class.md#basic_string__data).  
  
## <a name="example"></a>Ejemplo  
  
```  
// range_error.cpp  
// compile with: /EHsc /GR  
#include <iostream>  
using namespace std;  
int main()  
{  
   try   
   {  
      throw range_error( "The range is in error!" );  
   }  
   catch (exception &e)   
   {  
      cerr << "Caught: " << e.what( ) << endl;  
      cerr << "Type: " << typeid( e ).name( ) << endl;  
   };  
}  
\* Output:   
Caught: The range is in error!  
Type: class std::range_error  
*\  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< stdexcept>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [runtime_error (clase)](../standard-library/runtime-error-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

