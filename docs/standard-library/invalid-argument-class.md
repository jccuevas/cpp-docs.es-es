---
title: Clase invalid_argument | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- stdexcept/std::invalid_argument
dev_langs:
- C++
helpviewer_keywords:
- invalid_argument class
ms.assetid: af6c227d-ad7c-4e63-9dee-67af81d83506
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cbd5762478ed5ddab2694469e93b1c3445026727
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="invalidargument-class"></a>invalid_argument (Clase)
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
 El valor devuelto por [what](../standard-library/exception-class.md) es una copia de **message**`.`[data](../standard-library/basic-string-class.md#data).  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
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
 **Encabezado:** \<stdexcept>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [logic_error (Clase)](../standard-library/logic-error-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

