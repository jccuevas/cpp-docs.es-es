---
title: char_traits (Struct) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iosfwd/std::char_traits
- char_traits
- string/std::char_traits::char_type
- string/std::char_traits::int_type
- string/std::char_traits::off_type
- string/std::char_traits::pos_type
- string/std::char_traits::state_type
- string/std::char_traits::assign
- string/std::char_traits::compare
- string/std::char_traits::copy
- string/std::char_traits::_Copy_s
- string/std::char_traits::eof
- string/std::char_traits::eq
- string/std::char_traits::eq_int_type
- string/std::char_traits::find
- string/std::char_traits::length
- string/std::char_traits::lt
- string/std::char_traits::move
- string/std::char_traits::_Move_s
- string/std::char_traits::not_eof
- string/std::char_traits::to_char_type
- string/std::char_traits::to_int_type
dev_langs:
- C++
helpviewer_keywords:
- char_traits struct
- char_traits class
ms.assetid: 568e59f0-4521-4207-9223-9dcf6a16d620
caps.latest.revision: 20
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
ms.openlocfilehash: 558234b6411d3f2d10e84e3befda99084c7ca6d2
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="chartraits-struct"></a>char_traits (Struct)
La estructura char_traits describe los atributos asociados a un carácter.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class CharType>  
struct char_traits;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `CharType`  
 Tipo de datos del elemento.  
  
## <a name="remarks"></a>Comentarios  
 La estructura de plantilla describe varios rasgos de caracteres del tipo **CharType**. La clase de plantilla [basic_string](../standard-library/basic-string-class.md) y varias clases de plantilla de iostream, incluida [basic_ios](../standard-library/basic-ios-class.md), usan esta información para manipular elementos de tipo **CharType**. Un tipo de elemento de este tipo no debe requerir ni una construcción ni una destrucción explícita. Debe proporcionar un constructor predeterminado, un constructor de copias y un operador de asignación, con la semántica esperada. Una copia bit a bit debe tener el mismo efecto que una asignación. Ninguna de las funciones miembro de la estructura char_traits puede iniciar excepciones.  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[char_type](#char_type)|Un tipo de carácter.|  
|[int_type](#int_type)|Tipo entero que puede representar un carácter de tipo `char_type` o un carácter de final de archivo (EOF).|  
|[off_type](#off_type)|Tipo entero que puede representar desplazamientos entre posiciones de una secuencia.|  
|[pos_type](#pos_type)|Tipo entero que puede representar posiciones de una secuencia.|  
|[state_type](#state_type)|Tipo que representa el estado de conversión de caracteres multibyte de una secuencia.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[assign](#assign)|Asigna un valor de carácter a otro.|  
|[compare](#compare)|Compara un número especificado de caracteres de dos cadenas.|  
|[copy](#copy)|Copia un número especificado de caracteres de una cadena a otra. Desusado. En su lugar, use [char_traits::_Copy_s](#copy_s).|  
|[_Copy_s](#copy_s)|Copia un número especificado de caracteres de una cadena a otra.|  
|[eof](#eof)|Devuelve el carácter de final de archivo (EOF).|  
|[eq](#eq)|Comprueba si dos caracteres `char_type` son iguales.|  
|[eq_int_type](#eq_int_type)|Comprueba si dos caracteres que se representan como `int_type` son iguales.|  
|[find](#find)|Busca la primera aparición de un carácter especificado en un intervalo de caracteres.|  
|[length](#length)|Devuelve la longitud de una cadena.|  
|[lt](#lt)|Comprueba si un carácter es menor que otro.|  
|[move](#move)|Copia un número especificado de caracteres de una secuencia en otra secuencia que puede que esté superpuesta. Desusado. En su lugar, use [char_traits::_Move_s](#move_s).|  
|[_Move_s](#move_s)|Copia un número especificado de caracteres de una secuencia en otra secuencia que puede que esté superpuesta.|  
|[not_eof](#not_eof)|Comprueba si un carácter es el carácter de final de archivo (EOF).|  
|[to_char_type](#to_char_type)|Convierte un carácter `int_type` en el carácter `char_type` correspondiente y devuelve el resultado.|  
|[to_int_type](#to_int_type)|Convierte un carácter `char_type` en el carácter `int_type` correspondiente y devuelve el resultado.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<string>  
  
 **Espacio de nombres:** std  
  
##  <a name="assign"></a>  char_traits::assign  
 Asigna un valor de carácter a otro o a un intervalo de elementos de una cadena.  
  
```  
static void assign(char_type& _CharTo,
    const char_type& _CharFrom);

static char_type *assign(char_type* strTo,
    size_t _Num,
    char_type _CharFrom);
```  
  
### <a name="parameters"></a>Parámetros  
 **_** *CharFrom*  
 El carácter cuyo valor se asignará.  
  
 *_CharTo*  
 El elemento al que se asignará el valor de carácter.  
  
 * strTo*  
 La matriz de cadenas o caracteres a cuyos elementos iniciales se les asignarán valores de caracteres.  
  
 `_Num`  
 El número de elementos a los que se van a asignar valores.  
  
### <a name="return-value"></a>Valor devuelto  
 La segunda función miembro devuelve un puntero a la cadena a cuyos primeros elementos `_Num` se les han asignado valores de *_CharFrom*.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// char_traits_assign.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // The first member function assigning   
   // one character value to another character  
   char ChTo = 't';  
   const char ChFrom = 'f';  
   cout << "The initial characters ( ChTo , ChFrom ) are: ( "  
        << ChTo << " , " << ChFrom << " )." << endl;  
   char_traits<char>::assign ( ChTo , ChFrom );  
   cout << "After assigning, the characters ( ChTo , ChFrom ) are: ( "  
        << ChTo << " , " << ChFrom << " )." << endl << endl;  
  
   // The second member function assigning   
   // character values to initial part of a string  
   char_traits<char>::char_type s1[] = "abcd-1234-abcd";  
   char_traits<char>::char_type* result1;  
   cout << "The target string s1 is: " << s1 << endl;  
   result1 = char_traits<char>::assign ( s1 , 4 , 'f' );  
   cout << "The result1 = assign ( s1 , 4 , 'f' ) is: "  
        << result1 << endl;  
}  
```  
  
```Output  
The initial characters ( ChTo , ChFrom ) are: ( t , f ).  
After assigning, the characters ( ChTo , ChFrom ) are: ( f , f ).  
  
The target string s1 is: abcd-1234-abcd  
The result1 = assign ( s1 , 4 , 'f' ) is: ffff-1234-abcd  
```  
  
##  <a name="char_type"></a>  char_traits::char_type  
 Un tipo de carácter.  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **CharType**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [copy](#copy) para obtener un ejemplo de cómo declarar y usar `char_type`.  
  
##  <a name="compare"></a>  char_traits::compare  
 Compara un número especificado de caracteres de dos cadenas.  
  
```  
static int compare(const char_type* str1,
    const char_type* str2,
    size_t _Num);
```  
  
### <a name="parameters"></a>Parámetros  
 * str1*  
 La primera de dos cadenas que se van a comparar entre sí.  
  
 * str2*  
 La segunda de dos cadenas que se van a comparar entre sí.  
  
 `_Num`  
 El número de elementos en las cadenas que se van a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor negativo si la primera cadena es menor que la segunda cadena, 0 si las dos cadenas son iguales, o un valor positivo si la primera cadena es mayor que la segunda cadena.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre las cadenas se realiza elemento por elemento, se comprueba primero la igualdad y después, si un par de elementos de la secuencia no son iguales, se comprueba cuál es menor.  
  
 Si dos cadenas son iguales en un intervalo pero una es mayor que la otra, entonces la más corta de las dos es menor que la más larga.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// char_traits_compare.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main() {  
   using namespace std;  
  
   char_traits<char>::char_type* s1 = "CAB";  
   char_traits<char>::char_type* s2 = "ABC";  
   char_traits<char>::char_type* s3 = "ABC";  
   char_traits<char>::char_type* s4 = "ABCD";  
  
   cout << "The string s1 is: " << s1 << endl;  
   cout << "The string s2 is: " << s2 << endl;  
   cout << "The string s3 is: " << s3 << endl;  
   cout << "The string s4 is: " << s4 << endl;  
  
   int comp1, comp2, comp3, comp4;  
   comp1 = char_traits<char>::compare ( s1 , s2 , 2 );  
   comp2 = char_traits<char>::compare ( s2 , s3 , 3 );  
   comp3 = char_traits<char>::compare ( s3 , s4 , 4 );  
   comp4 = char_traits<char>::compare ( s4 , s3 , 4 );  
   cout << "compare ( s1 , s2 , 2 ) = " << comp1 << endl;  
   cout << "compare ( s2 , s3 , 3 ) = " << comp2 << endl;  
   cout << "compare ( s3 , s4 , 4 ) = " << comp3 << endl;  
   cout << "compare ( s4 , s3 , 4 ) = " << comp4 << endl;  
}  
```  
  
##  <a name="copy"></a>  char_traits::copy  
 Copia un número especificado de caracteres de una cadena a otra.  
  
 Este método es potencialmente inseguro, ya que se basa en el llamador para comprobar que los valores pasados son correctos. Considere la opción de usar [use char_traits::_Copy_s](#copy_s) en su lugar.  
  
```  
static char_type *copy(char_type* _To,
    const char_type* _From,
    size_t _Num);
```  
  
### <a name="parameters"></a>Parámetros  
 `_To`  
 El elemento situado al principio de la matriz de cadenas o caracteres destinada a recibir la secuencia de caracteres copiada.  
  
 `_From`  
 El elemento situado al principio de la matriz de cadenas o caracteres de origen que se va a copiar.  
  
 `_Num`  
 Número de elementos que se van a copiar.  
  
### <a name="return-value"></a>Valor devuelto  
 El primer elemento copiado en la matriz de cadenas o caracteres destinada a recibir la secuencia de caracteres copiada.  
  
### <a name="remarks"></a>Comentarios  
 Las secuencias de caracteres de origen y destino no deben superponerse.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// char_traits_copy.cpp  
// compile with: /EHsc /W3  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   char_traits<char>::char_type s1[] = "abcd-1234-abcd";  
   char_traits<char>::char_type s2[] = "ABCD-1234";  
   char_traits<char>::char_type* result1;  
   cout << "The source string is: " << s1 << endl;  
   cout << "The destination string is: " << s2 << endl;  
   // Note: char_traits::copy is potentially unsafe, consider  
   // using char_traits::_Copy_s instead.  
   result1 = char_traits<char>::copy ( s1 , s2 , 4 );  // C4996  
   cout << "The result1 = copy ( s1 , s2 , 4 ) is: "  
        << result1 << endl;  
}  
```  
  
```Output  
The source string is: abcd-1234-abcd  
The destination string is: ABCD-1234  
The result1 = copy ( s1 , s2 , 4 ) is: ABCD-1234-abcd  
```  
  
##  <a name="copy_s"></a>  char_traits::_Copy_s  
 Copia un número especificado de caracteres de una cadena a otra.  
  
```  
static char_type *_Copy_s(
    char_type* dest,  
    size_t dest_size,  
    const char_type* _From,  
    size_t count);
```  
  
### <a name="parameters"></a>Parámetros  
 `dest`  
 La matriz de cadenas o caracteres destinada a recibir la secuencia de caracteres copiada.  
  
 `dest_size`  
 Tamaño de `dest`. Si `char_type` es `char`, se muestra el tamaño en bytes. Si `char_type` es `wchar_t`, se muestra el tamaño en palabras.  
  
 `_From`  
 Matriz de cadenas o caracteres de origen que se va a copiar.  
  
 `count`  
 Número de elementos que se van a copiar.  
  
### <a name="return-value"></a>Valor devuelto  
 La matriz de cadenas o caracteres destinada a recibir la secuencia de caracteres copiada.  
  
### <a name="remarks"></a>Comentarios  
 Las secuencias de caracteres de origen y destino no deben superponerse.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// char_traits__Copy_s.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
  
    char_traits<char>::char_type s1[] = "abcd-1234-abcd";  
    char_traits<char>::char_type s2[] = "ABCD-1234";  
    char_traits<char>::char_type* result1;  
    cout << "The source string is: " << s1 << endl;  
    cout << "The destination string is: " << s2 << endl;  
    result1 = char_traits<char>::_Copy_s(s1,  
        char_traits<char>::length(s1), s2, 4);  
    cout << "The result1 = _Copy_s(s1, "  
         << "char_traits<char>::length(s1), s2, 4) is: "  
         << result1 << endl;  
}  
```  
  
```Output  
The source string is: abcd-1234-abcd  
The destination string is: ABCD-1234  
The result1 = _Copy_s(s1, char_traits<char>::length(s1), s2, 4) is: ABCD-1234-abcd  
```  
  
##  <a name="eof"></a>  char_traits::eof  
 Devuelve el carácter de final de archivo (EOF).  
  
```  
static int_type eof();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El carácter EOF.  
  
### <a name="remarks"></a>Comentarios  
 Un valor que representa el final del archivo (como `EOF` o `WEOF`).  
  
 El estándar de C++ indica que este valor no debe corresponder a un valor `char_type` válido. El compilador de Visual C++ exige esta restricción para el tipo `char`, pero no para el tipo `wchar_t`. En el ejemplo siguiente se muestra esto.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// char_traits_eof.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    char_traits<char>::char_type ch1 = 'x';  
    char_traits<char>::int_type int1;  
    int1 = char_traits<char>::to_int_type(ch1);  
    cout << "char_type ch1 is '" << ch1 << "' and corresponds to int_type "  
         << int1 << "." << endl << endl;  
  
    char_traits<char>::int_type int2 = char_traits<char>::eof();  
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;  
  
    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();  
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;  
}  
```  
  
```Output  
char_type ch1 is 'x' and corresponds to int_type 120.  
  
The eof marker for char_traits<char> is: -1  
The eof marker for char_traits<wchar_t> is: 65535  
```  
  
##  <a name="eq"></a>  char_traits::eq  
 Comprueba si dos caracteres `char_type` son iguales.  
  
```  
static bool eq(const char_type& _Ch1, const char_type& _Ch2);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Ch1`  
 El primero de dos caracteres que se comprobará si son iguales.  
  
 `_Ch2`  
 El segundo de dos caracteres que se comprobará si son iguales.  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el primer carácter es igual al segundo carácter; en caso contrario, **False**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// char_traits_eq.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   char_traits<char>::char_type ch1 =  'x';  
   char_traits<char>::char_type ch2 =  'y';  
   char_traits<char>::char_type ch3 =  'x';  
  
   // Testing for equality  
   bool b1 = char_traits<char>::eq ( ch1 , ch2 );  
   if ( b1 )  
      cout << "The character ch1 is equal "  
           << "to the character ch2." << endl;  
   else  
      cout << "The character ch1 is not equal "  
           << "to the character ch2." << endl;  
  
   // An equivalent and alternatively test procedure  
   if ( ch1 == ch3 )  
      cout << "The character ch1 is equal "  
           << "to the character ch3." << endl;  
   else  
      cout << "The character ch1 is not equal "  
           << "to the character ch3." << endl;  
}  
```  
  
```Output  
The character ch1 is not equal to the character ch2.  
The character ch1 is equal to the character ch3.  
```  
  
##  <a name="eq_int_type"></a>  char_traits::eq_int_type  
 Comprueba si dos caracteres que se representan como `int_type`s son iguales.  
  
```  
static bool eq_int_type(const int_type& _Ch1, const int_type& _Ch2);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Ch1`  
 El primero de los dos caracteres que se comprobará si son iguales como **int_type**s.  
  
 `_Ch2`  
 El segundos de los dos caracteres que se comprobará si son iguales como `int_type`s.  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el primer carácter es igual al segundo carácter; en caso contrario, **False**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// char_traits_eq_int_type.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   char_traits<char>::char_type ch1 =  'x';  
   char_traits<char>::char_type ch2 =  'y';  
   char_traits<char>::char_type ch3 =  'x';  
  
   // Converting from char_type to int_type  
   char_traits<char>::int_type int1, int2 , int3;  
   int1 =char_traits<char>:: to_int_type ( ch1 );  
   int2 =char_traits<char>:: to_int_type ( ch2 );  
   int3 =char_traits<char>:: to_int_type ( ch3 );  
  
   cout << "The char_types and corresponding int_types are:"  
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "  
        << int1 << "."  
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "  
        << int2 << "."  
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "  
        << int3 << "." << endl << endl;  
  
   // Testing for equality of int_type representations  
   bool b1 = char_traits<char>::eq_int_type ( int1 , int2 );  
   if ( b1 )  
      cout << "The int_type representation of character ch1\n "  
           << "is equal to the int_type representation of ch2."  
           << endl;  
   else  
      cout << "The int_type representation of character ch1\n is "  
           << "not equal to the int_type representation of ch2."  
           << endl;  
  
   // An equivalent and alternatively test procedure  
   if ( int1 == int3 )  
      cout << "The int_type representation of character ch1\n "  
           << "is equal to the int_type representation of ch3."  
           << endl;  
   else  
      cout << "The int_type representation of character ch1\n is "  
           << "not equal to the int_type representation of ch3."  
           << endl;  
}  
```  
  
```Output  
The char_types and corresponding int_types are:  
    ch1 = x corresponding to int1 = 120.  
    ch2 = y corresponding to int1 = 121.  
    ch3 = x corresponding to int1 = 120.  
  
The int_type representation of character ch1  
 is not equal to the int_type representation of ch2.  
The int_type representation of character ch1  
 is equal to the int_type representation of ch3.  
```  
  
##  <a name="find"></a>  char_traits::find  
 Busca la primera aparición de un carácter especificado en un intervalo de caracteres.  
  
```  
static const char_type* find(const char_type* str,
    size_t _Num,
    const char_type& _Ch);
```  
  
### <a name="parameters"></a>Parámetros  
 `str`  
 El primer carácter de la cadena que se buscará.  
  
 `_Num`  
 El número de posiciones, contando desde el principio, del intervalo que se buscará.  
  
 `_Ch`  
 El carácter que se va a buscar en el intervalo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la primera aparición del carácter especificado en el intervalo si se encuentra una coincidencia; de lo contrario, un puntero nulo.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// char_traits_find.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   const char* s1 = "f2d-1234-abcd";  
   const char* result1;  
   cout << "The string to be searched is: " << s1 << endl;  
  
   // Searching for a 'd' in the first 6 positions of string s1  
   result1 = char_traits<char>::find ( s1 , 6 , 'd');  
   cout << "The character searched for in s1 is: "  
        << *result1 << endl;  
   cout << "The string beginning with the first occurrence\n "  
        << "of the character 'd' is: " << result1 << endl;  
  
   // When no match is found the NULL value is returned  
   const char* result2;  
   result2 = char_traits<char>::find ( s1 , 3 , 'a');  
   if ( result2 == NULL )  
      cout << "The result2 of the search is NULL." << endl;  
   else  
      cout << "The result2 of the search  is: " << result1  
           << endl;  
}  
```  
  
```Output  
The string to be searched is: f2d-1234-abcd  
The character searched for in s1 is: d  
The string beginning with the first occurrence  
 of the character 'd' is: d-1234-abcd  
The result2 of the search is NULL.  
```  
  
##  <a name="int_type"></a>  char_traits::int_type  
 Tipo entero que puede representar un carácter de tipo `char_type` o un carácter de final de archivo (EOF).  
  
```  
typedef long int_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 Debe ser posible convertir en tipo un valor de tipo **CharType** a `int_type` y después de nuevo a **CharType** sin modificar el valor original.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [eq_int_type](#eq_int_type) para obtener un ejemplo de cómo declarar y usar `int_type`.  
  
##  <a name="length"></a>  char_traits::length  
 Devuelve la longitud de una cadena.  
  
```  
static size_t length(const char_type* str);
```  
  
### <a name="parameters"></a>Parámetros  
 `str`  
 La cadena de C cuya longitud se va a medir.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos de la secuencia que se está midiendo, sin incluir el terminador nulo.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// char_traits_length.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   const char* str1= "Hello";  
   cout << "The C-string str1 is: " << str1 << endl;  
  
   size_t lenStr1;  
   lenStr1 = char_traits<char>::length ( str1 );  
   cout << "The length of C-string str1 is: "   
        << lenStr1 << "." << endl;  
}  
```  
  
```Output  
The C-string str1 is: Hello  
The length of C-string str1 is: 5.  
```  
  
##  <a name="lt"></a>  char_traits::lt  
 Comprueba si un carácter es menor que otro.  
  
```  
static bool lt(const char_type& _Ch1, const char_type& _Ch2);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Ch1`  
 El primero de dos caracteres que se comprobará si son menores.  
  
 `_Ch2`  
 El segundo de dos caracteres que se comprobará si son menores.  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el primer carácter es menor que el segundo carácter; en caso contrario, **False**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// char_traits_lt.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   char_traits<char>::char_type ch1 =  'x';  
   char_traits<char>::char_type ch2 =  'y';  
   char_traits<char>::char_type ch3 =  'z';  
  
   // Testing for less than  
   bool b1 = char_traits<char>::lt ( ch1 , ch2 );  
   if ( b1 )  
      cout << "The character ch1 is less than "  
           << "the character ch2." << endl;  
   else  
      cout << "The character ch1 is not less "  
           << "than the character ch2." << endl;  
  
   // An equivalent and alternatively test procedure  
   if ( ch3 <  ch2 )  
      cout << "The character ch3 is less than "  
           << "the character ch2." << endl;  
   else  
      cout << "The character ch3 is not less "  
           << "than the character ch2." << endl;  
}  
```  
  
```Output  
The character ch1 is less than the character ch2.  
The character ch3 is not less than the character ch2.  
```  
  
##  <a name="move"></a>  char_traits::move  
 Copia un número especificado de caracteres de una secuencia en otra secuencia que puede que esté superpuesta.  
  
 Este método es potencialmente inseguro, ya que se basa en el llamador para comprobar que los valores pasados son correctos. Considere la opción de usar [use char_traits::_Move_s](#move_s) en su lugar.  
  
```  
static char_type *move(char_type* _To,
    const char_type* _From,
    size_t _Num);
```  
  
### <a name="parameters"></a>Parámetros  
 `_To`  
 El elemento situado al principio de la matriz de cadenas o caracteres destinada a recibir la secuencia de caracteres copiada.  
  
 `_From`  
 El elemento situado al principio de la matriz de cadenas o caracteres de origen que se va a copiar.  
  
 `_Num`  
 El número de elementos que se copiarán de la cadena de origen.  
  
### <a name="return-value"></a>Valor devuelto  
 El primer elemento `_To` copiado en la matriz de cadenas o caracteres destinada a recibir la secuencia de caracteres copiada.  
  
### <a name="remarks"></a>Comentarios  
 El origen y destino se pueden superponer.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// char_traits_move.cpp  
// compile with: /EHsc /W3  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";  
   char_traits<char>::char_type sTo1[] =  "ABCD-1234";  
   char_traits<char>::char_type* result1;  
   cout << "The source string sFrom1 is: " << sFrom1 << endl;  
   cout << "The destination stringsTo1 is: " << sTo1 << endl;  
   // Note: char_traits::move is potentially unsafe, consider  
   // using char_traits::_Move_s instead.  
   result1 = char_traits<char>::move ( sTo1 ,  sFrom1 , 4 );  // C4996  
   cout << "The result1 = move ( sTo1 , sFrom1 , 4 ) is: "  
        << result1 << endl << endl;  
  
   // When source and destination overlap  
   char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";  
   char_traits<char>::char_type* result2;  
   cout << "The source/destination string sToFrom2 is: "  
        << sToFrom2 << endl;  
   const char* findc = char_traits<char>::find ( sToFrom2 , 4 , 'c' );  
   // Note: char_traits::move is potentially unsafe, consider  
   // using char_traits::_Move_s instead.  
   result2 = char_traits<char>::move ( sToFrom2 , findc , 8 );  // C4996  
   cout << "The result2 = move ( sToFrom2 , findc , 8 ) is: "  
        << result2 << endl;  
}  
```  
  
```Output  
The source string sFrom1 is: abcd-1234-abcd  
The destination stringsTo1 is: ABCD-1234  
The result1 = move ( sTo1 , sFrom1 , 4 ) is: abcd-1234  
  
The source/destination string sToFrom2 is: abcd-1234-ABCD  
The result2 = move ( sToFrom2 , findc , 8 ) is: cd-1234-4-ABCD  
```  
  
##  <a name="move_s"></a>  char_traits::_Move_s  
 Copia un número especificado de caracteres de una secuencia en otra secuencia que puede que esté superpuesta.  
  
```  
static char_type *_Move_s(
    char_type* dest,  
    size_t dest_size,  
    const char_type* _From,  
    size_t count);
```  
  
### <a name="parameters"></a>Parámetros  
 `dest`  
 El elemento situado al principio de la matriz de cadenas o caracteres destinada a recibir la secuencia de caracteres copiada.  
  
 `dest_size`  
 Tamaño de `dest`. Si `char_type` es `char`, está en bytes. Si `char_type` es `wchar_t`, está en palabras.  
  
 `_From`  
 El elemento situado al principio de la matriz de cadenas o caracteres de origen que se va a copiar.  
  
 `count`  
 El número de elementos que se copiarán de la cadena de origen.  
  
### <a name="return-value"></a>Valor devuelto  
 El primer elemento `dest` copiado en la matriz de cadenas o caracteres destinada a recibir la secuencia de caracteres copiada.  
  
### <a name="remarks"></a>Comentarios  
 El origen y destino se pueden superponer.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// char_traits__Move_s.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
  
    char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";  
    char_traits<char>::char_type sTo1[] =  "ABCD-1234";  
    char_traits<char>::char_type* result1;  
    cout << "The source string sFrom1 is: " << sFrom1 << endl;  
    cout << "The destination stringsTo1 is: " << sTo1 << endl;  
    result1 = char_traits<char>::_Move_s(sTo1,  
        char_traits<char>::length(sTo1), sFrom1, 4);  
    cout << "The result1 = _Move_s(sTo1, "  
         << "char_traits<char>::length(sTo1), sFrom1, 4) is: "  
         << result1 << endl << endl;  
  
    // When source and destination overlap  
    char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";  
    char_traits<char>::char_type* result2;  
    cout << "The source/destination string sToFrom2 is: "  
         << sToFrom2 << endl;  
    const char* findc = char_traits<char>::find(sToFrom2, 4, 'c');  
    result2 = char_traits<char>::_Move_s(sToFrom2,  
        char_traits<char>::length(sToFrom2), findc, 8);  
    cout << "The result2 = _Move_s(sToFrom2, "  
        << "char_traits<char>::length(sToFrom2), findc, 8) is: "  
         << result2 << endl;  
}  
```  
  
```Output  
The source string sFrom1 is: abcd-1234-abcd  
The destination stringsTo1 is: ABCD-1234  
The result1 = _Move_s(sTo1, char_traits<char>::length(sTo1), sFrom1, 4) is: abcd-1234  
  
The source/destination string sToFrom2 is: abcd-1234-ABCD  
The result2 = _Move_s(sToFrom2, char_traits<char>::length(sToFrom2), findc, 8) is: cd-1234-4-ABCD  
```  
  
##  <a name="not_eof"></a>  char_traits::not_eof  
 Comprueba si un carácter es o no es el carácter de final de archivo (EOF).  
  
```  
static int_type not_eof(const int_type& _Ch);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Ch`  
 El carácter representado como un `int_type` que se va a probar si es o no es el carácter EOF.  
  
### <a name="return-value"></a>Valor devuelto  
 La representación `int_type` del carácter probado, si el **int_type** del carácter no es igual que el del carácter EOF.  
  
 Si el valor `int_type` del carácter es igual al valor `int_type` del EOF, entonces **False**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// char_traits_not_eof.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
  
   char_traits<char>::char_type ch1 =  'x';  
   char_traits<char>::int_type int1;  
   int1 = char_traits<char>:: to_int_type ( ch1 );  
   cout << "The char_type ch1 is " << ch1  
        << " corresponding to int_type: "   
        << int1 << "." << endl;  
  
   // EOF member function  
   char_traits <char>::int_type int2 = char_traits<char>::eof ( );  
   cout << "The eofReturn is: " << int2 << endl;  
  
   // Testing for EOF or another character  
   char_traits <char>::int_type eofTest1, eofTest2;  
   eofTest1 = char_traits<char>::not_eof ( int1 );  
   if ( !eofTest1 )  
      cout << "The eofTest1 indicates ch1 is an EOF character."  
              << endl;  
   else  
      cout << "The eofTest1 returns: " << eofTest1   
           << ", which is the character: "   
           <<  char_traits<char>::to_char_type ( eofTest1 )  
           << "." << endl;  
  
   eofTest2 = char_traits<char>::not_eof ( int2 );  
   if ( !eofTest2 )  
      cout << "The eofTest2 indicates int2 is an EOF character."   
           << endl;  
   else  
      cout << "The eofTest1 returns: " << eofTest2   
           << ", which is the character: "   
           <<  char_traits<char>::to_char_type ( eofTest2 )   
           << "." << endl;  
}  
```  
  
```Output  
The char_type ch1 is x corresponding to int_type: 120.  
The eofReturn is: -1  
The eofTest1 returns: 120, which is the character: x.  
The eofTest2 indicates int2 is an EOF character.  
```  
  
##  <a name="off_type"></a>  char_traits::off_type  
 Tipo entero que puede representar desplazamientos entre posiciones de una secuencia.  
  
```  
typedef streamoff off_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un entero con signo que describe un objeto que puede almacenar un desplazamiento de bytes implicado en varias operaciones de posicionamiento de flujo. Normalmente, es un sinónimo de [streamoff](../standard-library/ios-typedefs.md#streamoff), pero tiene esencialmente las mismas propiedades que ese tipo.  
  
##  <a name="pos_type"></a>  char_traits::pos_type  
 Tipo entero que puede representar posiciones de una secuencia.  
  
```  
typedef streampos pos_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto que puede almacenar toda la información necesaria para restaurar un indicador de posición de archivo arbitraria en un flujo. Normalmente, es un sinónimo de [streampos](../standard-library/ios-typedefs.md#streampos), pero, en cualquier caso, tiene esencialmente las mismas propiedades que ese tipo.  
  
##  <a name="state_type"></a>  char_traits::state_type  
 Tipo que representa el estado de conversión de caracteres multibyte de una secuencia.  
  
```  
typedef implementation-defined state_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto que puede representar un estado de conversión. Normalmente, es un sinónimo de `mbstate_t` pero, en cualquier caso, tiene esencialmente las mismas propiedades que ese tipo.  
  
##  <a name="to_char_type"></a>  char_traits::to_char_type  
 Convierte un carácter `int_type` en el carácter `char_type` correspondiente y devuelve el resultado.  
  
```  
static char_type to_char_type(const int_type& _Ch);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Ch`  
 El carácter `int_type` que se representará como un `char_type`.  
  
### <a name="return-value"></a>Valor devuelto  
 El carácter `char_type` correspondiente al carácter `int_type`.  
  
 Un valor de `_Ch` que no se puede representar como tal produce un resultado no especificado.  
  
### <a name="remarks"></a>Comentarios  
 Las operaciones de conversión [to_int_type](#to_int_type) y `to_char_type` son inversas entre sí, por lo que:  
  
 `to_int_type` ( `to_char_type` ( *x* ) ) == *x*  
  
 para cualquier `int_type` *x* y  
  
 `to_char_type` ( `to_int_type` ( *x* ) ) == *x*  
  
 para cualquier `char_type` *x*.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// char_traits_to_char_type.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   char_traits<char>::char_type ch1 =  'a';  
   char_traits<char>::char_type ch2 =  'b';  
   char_traits<char>::char_type ch3 =  'a';  
  
   // Converting from char_type to int_type  
   char_traits<char>::int_type int1, int2 , int3;  
   int1 =char_traits<char>:: to_int_type ( ch1 );  
   int2 =char_traits<char>:: to_int_type ( ch2 );  
   int3 =char_traits<char>:: to_int_type ( ch3 );  
  
   cout << "The char_types and corresponding int_types are:"  
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "   
        << int1 << "."  
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "   
        << int2 << "."  
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "   
        << int3 << "." << endl << endl;  
  
   // Converting from int_type back to char_type  
   char_traits<char>::char_type rec_ch1;  
   rec_ch1 = char_traits<char>:: to_char_type ( int1);  
   char_traits<char>::char_type rec_ch2;  
   rec_ch2 = char_traits<char>:: to_char_type ( int2);  
  
   cout << "The recovered char_types and corresponding int_types are:"  
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "   
        << int1 << "."  
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "   
        << int2 << "." << endl << endl;  
  
   // Testing that the conversions are inverse operations  
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );  
   if ( b1 )  
      cout << "The recovered char_type of ch1"  
           << " is equal to the original ch1." << endl;  
   else  
      cout << "The recovered char_type of ch1"  
           << " is not equal to the original ch1." << endl;  
  
   // An equivalent and alternatively test procedure  
   if ( rec_ch2 == ch2 )  
      cout << "The recovered char_type of ch2"  
           << " is equal to the original ch2." << endl;  
   else  
      cout << "The recovered char_type of ch2"  
           << " is not equal to the original ch2." << endl;  
}  
```  
  
```Output  
The char_types and corresponding int_types are:  
    ch1 = a corresponding to int1 = 97.  
    ch2 = b corresponding to int1 = 98.  
    ch3 = a corresponding to int1 = 97.  
  
The recovered char_types and corresponding int_types are:  
    recovered ch1 = a from int1 = 97.  
    recovered ch2 = b from int2 = 98.  
  
The recovered char_type of ch1 is equal to the original ch1.  
The recovered char_type of ch2 is equal to the original ch2.  
```  
  
##  <a name="to_int_type"></a>  char_traits::to_int_type  
 Convierte un carácter `char_type` en el carácter `int_type` correspondiente y devuelve el resultado.  
  
```  
static int_type to_int_type(const char_type& _Ch);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Ch`  
 El carácter `char_type` que se representará como un `int_type`.  
  
### <a name="return-value"></a>Valor devuelto  
 El carácter `int_type` correspondiente al carácter `char_type`.  
  
### <a name="remarks"></a>Comentarios  
 Las operaciones de conversión `to_int_type` y [to_char_type](#to_char_type) son inversas entre sí, por lo que:  
  
 `to_int_type` ( `to_char_type` ( *x* ) ) == *x*  
  
 para cualquier `int_type` *x*, y  
  
 `to_char_type` ( `to_int_type` ( *x* ) ) == *x*  
  
 para cualquier `char_type` *x*.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// char_traits_to_int_type.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   char_traits<char>::char_type ch1 = 'a';  
   char_traits<char>::char_type ch2 = 'b';  
   char_traits<char>::char_type ch3 = 'a';  
  
   // Converting from char_type to int_type  
   char_traits<char>::int_type int1, int2 , int3;  
   int1 =char_traits<char>:: to_int_type ( ch1 );  
   int2 =char_traits<char>:: to_int_type ( ch2 );  
   int3 =char_traits<char>:: to_int_type ( ch3 );  
  
   cout << "The char_types and corresponding int_types are:"  
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "   
        << int1 << "."  
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "   
        << int2 << "."  
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "   
        << int3 << "." << endl << endl;  
  
   // Converting from int_type back to char_type  
   char_traits<char>::char_type rec_ch1;  
   rec_ch1 = char_traits<char>:: to_char_type ( int1);  
   char_traits<char>::char_type rec_ch2;  
   rec_ch2 = char_traits<char>:: to_char_type ( int2);  
  
   cout << "The recovered char_types and corresponding int_types are:"  
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "   
        << int1 << "."  
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "   
        << int2 << "." << endl << endl;  
  
   // Testing that the conversions are inverse operations  
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );  
   if ( b1 )  
      cout << "The recovered char_type of ch1"  
           << " is equal to the original ch1." << endl;  
   else  
      cout << "The recovered char_type of ch1"  
           << " is not equal to the original ch1." << endl;  
  
   // An equivalent and alternatively test procedure  
   if ( rec_ch2 == ch2 )  
      cout << "The recovered char_type of ch2"  
           << " is equal to the original ch2." << endl;  
   else  
      cout << "The recovered char_type of ch2"  
           << " is not equal to the original ch2." << endl;  
}  
```  
  
```Output  
The char_types and corresponding int_types are:  
    ch1 = a corresponding to int1 = 97.  
    ch2 = b corresponding to int1 = 98.  
    ch3 = a corresponding to int1 = 97.  
  
The recovered char_types and corresponding int_types are:  
    recovered ch1 = a from int1 = 97.  
    recovered ch2 = b from int2 = 98.  
  
The recovered char_type of ch1 is equal to the original ch1.  
The recovered char_type of ch2 is equal to the original ch2.  
```  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)


