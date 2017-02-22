---
title: "length_error (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdexcept/std::length_error"
  - "length_error"
  - "std::length_error"
  - "std.length_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "length_error (clase)"
ms.assetid: d53c46c5-4626-400d-bd76-bf3e1e0f64ae
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# length_error (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase que actúa como la clase base para todas las excepciones iniciadas para informar de un intento de generar un objeto demasiado largo como para poder especificarlo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class length_error : public logic_error {  
public:  
    explicit length_error(const string& message);

    explicit length_error(const char *message);

};  
```  
  
## <a name="remarks"></a>Comentarios  
 El valor devuelto por [qué](../standard-library/exception-class1.md) es una copia de **mensaje**`.`[datos](../standard-library/basic-string-class.md#basic_string__data).  
  
## <a name="example"></a>Ejemplo  
  
```  
// length_error.cpp  
// compile with: /EHsc /GR /MDd  
#include <vector>  
#include <iostream>  
  
using namespace std;  
  
template<class  T>  
class stingyallocator : public allocator< T>  
{  
public:  
   template <class U>  
      struct rebind { typedef stingyallocator<U> other; };  
   _SIZT max_size( ) const  
   {  
         return 10;  
   };  
  
};  
  
int main( )  
{  
   try  
   {  
      vector<int, stingyallocator< int > > myv;  
      for ( int i = 0; i < 11; i++ ) myv.push_back( i );  
   }  
   catch ( exception &e )  
   {  
      cerr << "Caught " << e.what( ) << endl;  
      cerr << "Type " << typeid( e ).name( ) << endl;  
   };  
}  
\* Output:   
Caught vector<T> too long  
Type class std::length_error  
*\  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< stdexcept>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [logic_error (clase)](../standard-library/logic-error-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

