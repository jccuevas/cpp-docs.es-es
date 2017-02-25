---
title: "out_of_range (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "out_of_range"
  - "stdexcept/std::out_of_range"
  - "std.out_of_range"
  - "std::out_of_range"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "out_of_range (clase)"
ms.assetid: d0e14dc0-065e-4666-9ac9-51e52223c503
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# out_of_range (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase que actúa como la clase base para todas las excepciones iniciadas para informar sobre un argumento que está fuera de su rango válido.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class out_of_range : public logic_error {  
public:  
    explicit out_of_range(const string& message);

    explicit out_of_range(const char *message);

};  
```  
  
## <a name="remarks"></a>Comentarios  
 El valor devuelto por [qué](../standard-library/exception-class1.md) es una copia de **mensaje**`.`[datos](../standard-library/basic-string-class.md#basic_string__data).  
  
## <a name="example"></a>Ejemplo  
  
```  
// out_of_range.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
using namespace std;  
  
int main() {  
// out_of_range  
   try {  
      string str( "Micro" );  
      string rstr( "soft" );  
      str.append( rstr, 5, 3 );  
      cout << str << endl;  
   }  
   catch ( exception &e ) {  
      cerr << "Caught: " << e.what( ) << endl;  
   };  
}  
```  
  
## <a name="output"></a>Salida  
  
```  
Caught: invalid string position  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< stdexcept>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [logic_error (clase)](../standard-library/logic-error-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

