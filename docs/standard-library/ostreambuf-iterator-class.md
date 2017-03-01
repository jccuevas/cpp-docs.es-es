---
title: ostreambuf_iterator (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.ostreambuf_iterator
- streambuf/std::ostreambuf_iterator
- ostreambuf_iterator
- std::ostreambuf_iterator
dev_langs:
- C++
helpviewer_keywords:
- ostreambuf_iterator class
ms.assetid: dad1e624-2f45-4e94-8887-a885e95f9071
caps.latest.revision: 16
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
translationtype: Machine Translation
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 30e8f1c86ebff67c520f4ff303ade831306cede6
ms.lasthandoff: 02/24/2017

---
# <a name="ostreambufiterator-class"></a>ostreambuf_iterator
La clase de plantilla ostreambuf_iterator describe un objeto iterador de salida que escribe elementos de caracteres sucesivos en el flujo de salida con la extracción **operator>>**. Los objetos `ostreambuf_iterator`s se diferencian de los de la [clase ostream_iterator](../standard-library/ostream-iterator-class.md) en que tienen caracteres en lugar de un tipo genérico en el tipo de objeto que se inserta en el flujo de salida.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class CharType = char class Traits = char_traits <CharType>>
```  
  
#### <a name="parameters"></a>Parámetros  
 `CharType`  
 Tipo que representa el tipo de caracteres para ostreambuf_iterator. Este argumento es opcional y el valor predeterminado es `char`*.*  
  
 `Traits`  
 Tipo que representa el tipo de caracteres para ostreambuf_iterator. Este argumento es opcional y el valor predeterminado es `char_traits`\< *CharType>.*  
  
## <a name="remarks"></a>Comentarios  
 La clase ostreambuf_iterator debe satisfacer los requisitos de un iterador de salida. Los algoritmos se pueden escribir directamente en el flujo de salida mediante `ostreambuf_iterator`. La clase proporciona un iterador de flujo de bajo nivel que permite acceso al flujo raw (sin formato) de E/S en forma de caracteres y la capacidad de omitir las traslaciones de caracteres y el almacenamiento en búfer asociados a los iteradores de flujo de alto nivel.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|Construye un objeto `ostreambuf_iterator` que se inicializa para escribir caracteres en el flujo de salida.|  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[char_type](#ostreambuf_iterator__char_type)|Tipo que proporciona el tipo de los caracteres de `ostreambuf_iterator`.|  
|[ostream_type](#ostreambuf_iterator_ostream_type)|Tipo que proporciona el tipo de flujo de `ostream_iterator`.|  
|[streambuf_type](#ostreambuf_iterator__streambuf_type)|Tipo que proporciona el tipo de flujo de `ostreambuf_iterator`.|  
|[traits_type](#ostreambuf_iterator__traits_type)|Tipo que proporciona el tipo de rasgos de los caracteres de `ostream_iterator`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[failed](#ostreambuf_iterator__failed)|Comprueba si hay errores en una inserción en el búfer del flujo de salida.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator*](#ostreambuf_iterator__operator_star)|Desreferencia el operador usado para implementar la expresión de iterador de salida * `i` = `x`.|  
|[operator++](#ostreambuf_iterator__operator_add_add)|Operador de incremento no funcional que devuelve un objeto `ostreambuf_iterator` al mismo objeto que señalaba antes de que se llamara a la operación.|  
|[operator=](#ostreambuf_iterator__operator_eq)|El operador inserta un carácter en el búfer del flujo asociado.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<iterator>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-nameostreambufiteratorchartypea--ostreambufiteratorchartype"></a><a name="ostreambuf_iterator__char_type"></a> ostreambuf_iterator::char_type  
 Tipo que proporciona el tipo de los caracteres de `ostreambuf_iterator`.  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **CharType**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ostreambuf_iterator_char_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   typedef ostreambuf_iterator<char>::char_type CHT1;  
   typedef ostreambuf_iterator<char>::traits_type CHTR1;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter:  
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output streambuf:  
   cout << "The characters written to the output stream\n"  
        << " by charOutBuf are: ";  
 *charOutBuf = 'O';  
   charOutBuf++;  
 *charOutBuf = 'U';  
   charOutBuf++;  
 *charOutBuf = 'T';  
   charOutBuf++;  
   cout << "." << endl;  
}  
\* Output:   
The characters written to the output stream  
 by charOutBuf are: OUT.  
*\  
```  
  
##  <a name="a-nameostreambufiteratorfaileda--ostreambufiteratorfailed"></a><a name="ostreambuf_iterator__failed"></a> ostreambuf_iterator::failed  
 Comprueba si hay errores en una inserción en el búfer del flujo de salida.  
  
```
bool failed() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si no se han producido errores anteriormente en ninguna inserción del búfer del flujo de salida; de otro modo **False**.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve **True** si, en algún uso anterior del miembro `operator=`, la llamada a **subf**_-> `sputc` ha devuelto **eof**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ostreambuf_iterator_failed.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   ostreambuf_iterator<char> charOut ( cout );  
  
 *charOut = 'a';  
   charOut ++;  
 *charOut  = 'b';  
   charOut ++;     
 *charOut = 'c';  
   cout << " are characters output individually." << endl;  
  
   bool b1 = charOut.failed ( );  
   if (b1)   
       cout << "At least one insertion failed." << endl;  
   else  
       cout << "No insertions failed." << endl;  
}  
\* Output:   
abc are characters output individually.  
No insertions failed.  
*\  
```  
  
##  <a name="a-nameostreambufiteratoroperatorstara--ostreambufiteratoroperator"></a><a name="ostreambuf_iterator__operator_star"></a> ostreambuf_iterator::operator*  
 Un operador de desreferencia no funcional usado para implementar la expresión de iterador de salida \* *i* = *x*.  
  
```
ostreambuf_iterator<CharType, Traits>& operator*();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto de iterador ostreambuf.  
  
### <a name="remarks"></a>Comentarios  
 Este operador solo funciona en la expresión de iterador de salida \* *i* = *x* para caracteres de salida del búfer de secuencia. Aplicado en un iterador ostreambuf, devuelve el iterador; **\*iter** devuelve **iter**,  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ostreambuf_iterator_op_deref.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter  
   ostreambuf_iterator<char> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output stream  
   cout << "Elements written to output stream:" << endl;  
 *charOutBuf = 'O';  
   charOutBuf++;   // no effect on iterator position  
 *charOutBuf = 'U';  
 *charOutBuf = 'T';  
}  
\* Output:   
Elements written to output stream:  
OUT  
*\  
```  
  
##  <a name="a-nameostreambufiteratoroperatoraddadda--ostreambufiteratoroperator"></a><a name="ostreambuf_iterator__operator_add_add"></a> ostreambuf_iterator::operator++  
 Un operador de incremento no funcional que devuelve un iterador ostream al mismo carácter que señalaba antes de que se llamara a la operación.  
  
```
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al carácter que se ha direccionado originalmente o a un objeto definido por una implementación que puede convertirse en `ostreambuf_iterator`\< **CharType**, **Traits**>.  
  
### <a name="remarks"></a>Comentarios  
 El operador se usa para implementar la expresión de iterador de salida \* *i* = *x*.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ostreambuf_iterator_op_incr.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter  
   ostreambuf_iterator<char> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output stream  
   cout << "Elements written to output stream:" << endl;  
 *charOutBuf = 'O';  
   charOutBuf++;      // No effect on iterator position  
 *charOutBuf = 'U';  
 *charOutBuf = 'T';     
}  
\* Output:   
Elements written to output stream:  
OUT  
*\  
```  
  
##  <a name="a-nameostreambufiteratoroperatoreqa--ostreambufiteratoroperator"></a><a name="ostreambuf_iterator__operator_eq"></a> ostreambuf_iterator::operator=  
 El operador inserta un carácter en el búfer del flujo asociado.  
  
```
ostreambuf_iterator<CharType, Traits>& operator=(CharType _Char);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Char`  
 El carácter que se va a insertar en el búfer de secuencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al carácter insertado en el búfer de secuencia.  
  
### <a name="remarks"></a>Comentarios  
 Operador de asignación que se usa para implementar la expresión de iterador de salida \* *i* = *x* para escribir en un flujo de salida.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ostreambuf_iterator_op_assign.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter  
   ostreambuf_iterator<char> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output stream  
   cout << "Elements written to output stream:" << endl;  
 *charOutBuf = 'O';  
   charOutBuf++;      // No effect on iterator position  
 *charOutBuf = 'U';  
 *charOutBuf = 'T';     
}  
\* Output:   
Elements written to output stream:  
OUT  
*\  
```  
  
##  <a name="a-nameostreambufiteratorostreambufiteratora--ostreambufiteratorostreambufiterator"></a><a name="ostreambuf_iterator_ostreambuf_iterator"></a> ostreambuf_iterator::ostreambuf_iterator  
 Construye un objeto `ostreambuf_iterator` que se inicializa para escribir caracteres en el flujo de salida.  
  
```
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `strbuf`  
 El objeto streambuf de salida que se ha usado para inicializar el puntero de búfer de flujo de salida.  
  
 `Ostr`  
 El objeto de flujo de salida que se ha usado para inicializar el puntero de búfer de flujo de salida.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor inicializa el puntero de búfer de flujo de salida con `strbuf`.  
  
 El segundo constructor inicializa el puntero de búfer de flujo de salida con `Ostr`. `rdbuf`Operador El puntero almacenado no debe ser un puntero nulo.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ostreambuf_iteratorOstreambuf_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   ostreambuf_iterator<char> charOut ( cout );  
  
 *charOut = 'O';  
   charOut ++;  
 *charOut  = 'U';  
   charOut ++;     
 *charOut = 'T';  
   cout << " are characters output individually." << endl;  
  
   ostreambuf_iterator<char> strOut ( cout );  
   string str = "These characters are being written to the output stream.\n ";  
   copy ( str.begin ( ), str. end ( ), strOut );  
}  
\* Output:   
OUT are characters output individually.  
These characters are being written to the output stream.  
*\  
```  
  
##  <a name="a-nameostreambufiteratorostreamtypea--ostreambufiteratorostreamtype"></a><a name="ostreambuf_iterator_ostream_type"></a> ostreambuf_iterator::ostream_type  
 Tipo que proporciona el tipo de flujo de `ostream_iterator`.  
  
```
typedef basicOstream<CharType, Traits> ostream_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo para `basicOstream`\< **CharType**, **Traits**>  
  
### <a name="example"></a>Ejemplo  
  Vea [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) para obtener un ejemplo de cómo declarar y usar `ostream_type`.  
  
##  <a name="a-nameostreambufiteratorstreambuftypea--ostreambufiteratorstreambuftype"></a><a name="ostreambuf_iterator__streambuf_type"></a> ostreambuf_iterator::streambuf_type  
 Tipo que proporciona el tipo de flujo de `ostreambuf_iterator`.  
  
```
typedef basic_streambuf<CharType, Traits> streambuf_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `basic_streambuf`\< **CharType**, **Traits**>, una clase de secuencia para búferes de E/S que se convierte en `streambuf` cuando se especializa en el tipo de carácter `char`.  
  
### <a name="example"></a>Ejemplo  
  Vea [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) para obtener un ejemplo de cómo declarar y usar `streambuf_type`.  
  
##  <a name="a-nameostreambufiteratortraitstypea--ostreambufiteratortraitstype"></a><a name="ostreambuf_iterator__traits_type"></a> ostreambuf_iterator::traits_type  
 Tipo que proporciona el tipo de rasgos de los caracteres de `ostream_iterator`.  
  
```
typedef Traits traits_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **Traits**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ostreambuf_iterator_traits_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   typedef ostreambuf_iterator<char>::char_type CHT1;  
   typedef ostreambuf_iterator<char>::traits_type CHTR1;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter:  
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output streambuf:  
   cout << "The characters written to the output stream\n"  
        << " by charOutBuf are: ";  
 *charOutBuf = 'O';  
   charOutBuf++;  
 *charOutBuf = 'U';  
   charOutBuf++;  
 *charOutBuf = 'T';  
   charOutBuf++;  
   cout << "." << endl;  
}  
\* Output:   
The characters written to the output stream  
 by charOutBuf are: OUT.  
*\  
```  
  
## <a name="see-also"></a>Vea también  
 [\<iterator>](../standard-library/iterator.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)




