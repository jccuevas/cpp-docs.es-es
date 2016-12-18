---
title: "invalid_argument (Clase) | Microsoft Docs"
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
  - "std.invalid_argument"
  - "stdexcept/std::invalid_argument"
  - "invalid_argument"
  - "std::invalid_argument"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_argument (clase)"
ms.assetid: af6c227d-ad7c-4e63-9dee-67af81d83506
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# invalid_argument (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un argumento inválido.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class invalid_argument : public logic_error {  
public:  
    explicit invalid_argument(const string& message);

    explicit invalid_argument(const char *message);

};  
```  
  
## <a name="remarks"></a>Comentarios  
 El valor devuelto por [qué](../standard-library/exception-class1.md) es una copia de **mensaje**`.`[datos](../standard-library/basic-string-class.md#basic_string__data).  
  
## <a name="example"></a>Ejemplo  
  
```  
// invalid_arg.cpp  
// compile with: /EHsc /GR  
#include <bitset>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   try   
   {  
      bitset< 32 > bitset( string( "11001010101100001b100101010110000") );  
   }  
   catch ( exception &e )   
   {  
      cerr << "Caught " << e.what( ) << endl;  
      cerr << "Type " << typeid( e ).name( ) << endl;  
   };  
}  
\* Output:   
Caught invalid bitset<N> char  
Type class std::invalid_argument  
*\  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< stdexcept>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [logic_error (clase)](../standard-library/logic-error-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

