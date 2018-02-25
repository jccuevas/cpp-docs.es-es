---
title: out_of_range (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- stdexcept/std::out_of_range
dev_langs:
- C++
helpviewer_keywords:
- out_of_range class
ms.assetid: d0e14dc0-065e-4666-9ac9-51e52223c503
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 758b9be05c1ed1e7f54e7de1c57634cf105d0cb8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="outofrange-class"></a>out_of_range (Clase)
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
 El valor devuelto por [what](../standard-library/exception-class.md) es una copia de **message**`.`[data](../standard-library/basic-string-class.md#data).  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
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
 **Encabezado:** \<stdexcept>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [logic_error (Clase)](../standard-library/logic-error-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

