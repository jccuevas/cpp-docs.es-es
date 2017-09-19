---
title: Funciones &lt;ostream&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
caps.latest.revision: 15
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 89eebd013c08f52175e5e4038b501d4ce572e55a
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="ltostreamgt-functions"></a>Funciones &lt;ostream&gt;
||||  
|-|-|-|  
|[swap](#swap)|[endl](#endl)|[ends](#ends)|  
|[flush](#flush)|  
  
##  <a name="endl"></a> endl  
 Termina una línea y vacía el búfer.  
  
```  
template class<Elem, Tr> basic_ostream<Elem, Tr>& endl(basic_ostream<Elem, Tr>& Ostr);
```  
  
### <a name="parameters"></a>Parámetros  
 `Elem`  
 El tipo de elemento.  
  
 `Ostr`  
 Objeto de tipo `basic_ostream`.  
  
 `Tr`  
 Rasgos de los caracteres.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto de tipo `basic_ostream`.  
  
### <a name="remarks"></a>Comentarios  
 El manipulador llama a `Ostr`**.**[put](../standard-library/basic-ostream-class.md#put)( `Ostr`**.** [widen](../standard-library/basic-ios-class.md#widen)( **'\n'**)) y, después, llama a `Ostr`**.**[flush](../standard-library/basic-ostream-class.md#flush). Devuelve `Ostr`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ostream_endl.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "testing" << endl;  
}  
```  
  
```Output  
testing  
```  
  
##  <a name="ends"></a> ends  
 Termina una cadena  
  
```  
template class<Elem, Tr> basic_ostream<Elem, Tr>& ends(basic_ostream<Elem, Tr>& Ostr);
```  
  
### <a name="parameters"></a>Parámetros  
 `Elem`  
 El tipo de elemento.  
  
 `Ostr`  
 Objeto de tipo `basic_ostream`.  
  
 `Tr`  
 Rasgos de los caracteres.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto de tipo `basic_ostream`.  
  
### <a name="remarks"></a>Comentarios  
 El manipulador llama a `Ostr`**.**[put](../standard-library/basic-ostream-class.md#put)( `Elem`( **'\0'**)). Devuelve `Ostr.`  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ostream_ends.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "a";  
   cout << "b" << ends;  
   cout << "c" << endl;  
}  
```  
  
```Output  
ab c  
```  
  
##  <a name="flush"></a> flush  
 Vacía el búfer.  
  
```  
template class<Elem, Tr> basic_ostream<Elem, Tr>& flush(basic_ostream<Elem, Tr>& Ostr);
```  
  
### <a name="parameters"></a>Parámetros  
 `Elem`  
 El tipo de elemento.  
  
 `Ostr`  
 Objeto de tipo `basic_ostream`.  
  
 `Tr`  
 Rasgos de los caracteres.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto de tipo `basic_ostream`.  
  
### <a name="remarks"></a>Comentarios  
 El manipulador llama a `Ostr`**.**[flush](../standard-library/basic-ostream-class.md#flush). Devuelve `Ostr`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ostream_flush.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "testing" << flush;  
}  
```  
  
```Output  
testing  
```  
  
##  <a name="swap"></a> swap  
 Intercambia los valores de dos objetos `basic_ostream`.  
  
```  
template <class Elem, class Tr>  
void swap(
    basic_ostream<Elem, Tr>& left,  
    basic_ostream<Elem, Tr>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Referencia lvalue a un objeto `basic_ostream`.  
  
 `right`  
 Referencia lvalue a un objeto `basic_ostream`.  
  
### <a name="remarks"></a>Comentarios  
 La función de plantilla `swap` ejecuta `left.swap(right)`.  
  
## <a name="see-also"></a>Vea también  
 [\<ostream>](../standard-library/ostream.md)


