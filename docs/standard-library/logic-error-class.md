---
title: logic_error (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdexcept/std::logic_error
- logic_error
dev_langs:
- C++
helpviewer_keywords:
- logic_error class
ms.assetid: b290d73d-94e1-4288-af86-2bb5d71f677a
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 26ca098b39cdcbad38dc3563e706fa979d44e67c
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="logicerror-class"></a>logic_error (Clase)
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
 El valor devuelto por [what](../standard-library/exception-class.md) es una copia de **message**`.`[data](../standard-library/basic-string-class.md#data).  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
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
 **Encabezado:** \<stdexcept>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
[exception (Clase)](../standard-library/exception-class.md)  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)


