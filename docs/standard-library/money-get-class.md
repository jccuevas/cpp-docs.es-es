---
title: money_get (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocmon/std::money_get
- money_get
- std.money_get
- std::money_get
dev_langs:
- C++
helpviewer_keywords:
- money_get class
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: f9e122dbeb68fb4ed33d9e652af21c1b9474e3a5
ms.lasthandoff: 02/24/2017

---
# <a name="moneyget-class"></a>money_get (Clase)
La clase de plantilla describe un objeto que puede actuar como una faceta de la configuración regional para controlar las conversiones de secuencias de tipo `CharType` en valores monetarios.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>  
class money_get : public locale::facet;
```  
  
#### <a name="parameters"></a>Parámetros  
 `CharType`  
 Tipo usado dentro de un programa para codificar los caracteres de una configuración regional.  
  
 `InputIterator`  
 Tipo de iterador del que las funciones get leen su entrada.  
  
## <a name="remarks"></a>Comentarios  
 Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[money_get](#money_get__money_get)|Constructor de objetos de tipo `money_get` que se usan para extraer valores numéricos de secuencias que representan valores monetarios.|  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[char_type](#money_get__char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|  
|[iter_type](#money_get__iter_type)|Tipo que describe un iterador de entrada.|  
|[string_type](#money_get__string_type)|Tipo que describe una cadena que contiene caracteres de tipo `CharType`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[do_get](#money_get__do_get)|Función virtual a la que se llama para extraer un valor numérico de una secuencia de caracteres que representa un valor monetario.|  
|[get](#money_get__get)|Extrae un valor numérico de una secuencia de caracteres que representa un valor monetario.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<locale>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namemoneygetchartypea--moneygetchartype"></a><a name="money_get__char_type"></a> money_get::char_type  
 Tipo que se usa para describir un carácter empleado por una configuración regional.  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **CharType**.  
  
##  <a name="a-namemoneygetdogeta--moneygetdoget"></a><a name="money_get__do_get"></a> money_get::do_get  
 Función virtual a la que se llama para extraer un valor numérico de una secuencia de caracteres que representa un valor monetario.  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const
```  
  
### <a name="parameters"></a>Parámetros  
 `first`  
 Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.  
  
 `last`  
 Iterador de entrada que se dirige al final de la secuencia que se va a convertir.  
  
 `Intl`  
 Un valor booleano que indica el tipo de símbolo de moneda que se espera en la secuencia: **true** si es internacional, **false** si es nacional.  
  
 `Iosbase`  
 Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.  
  
 `State`  
 Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente o no.  
  
 `val`  
 Una cadena que almacena la secuencia convertida.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada monetario.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro virtual protegida intenta hacer coincidir los elementos secuenciales, empezando al principio de la secuencia [ `first`, `last`) hasta que reconoce un campo de entrada monetario completo y que no esté vacío. Si se realiza correctamente, convierte este campo en una secuencia de uno o más dígitos decimales, opcionalmente precedido por un signo menos (`–`), para representar la cantidad y almacena el resultado en el objeto [string_type](#money_get__string_type) `val`. Devuelve un iterador que designa el primer elemento más allá del campo de entrada monetario. De otro modo, la función almacena una secuencia vacía en `val` y establece `ios_base::failbit` en `State`. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de campo de entrada monetario válido. En cualquier caso, si el valor devuelto es igual a `last`, la función establece `ios_base::eofbit` en `State`.  
  
 La segunda función miembro virtual protegida se comporta de la misma manera que la primera, a excepción de que, si se realiza correctamente, convierte la secuencia de dígitos con signo opcional en un valor de tipo `long double` y almacena ese valor en `val`.  
  
 El formato de un campo de entrada monetario se determina por la [faceta de configuración regional](../standard-library/locale-class.md#facet_class)**fac** devuelta mediante la llamada eficaz a [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, **intl**>>( **iosbase**. [getloc](../standard-library/ios-base-class.md#ios_base__getloc)).  
  
 De manera específica:  
  
- **fac**. [neg_format](../standard-library/moneypunct-class.md#moneypunct__neg_format) determina el orden en el que aparecen los componentes del campo.  
  
- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#moneypunct__curr_symbol) determina la secuencia de elementos que constituye un símbolo de moneda.  
  
- **fac**. [positive_sign](../standard-library/moneypunct-class.md#moneypunct__positive_sign) determina la secuencia de elementos que constituye un signo positivo.  
  
- **fac**. [negative_sign](../standard-library/moneypunct-class.md#moneypunct__negative_sign) determina la secuencia de elementos que constituye un signo negativo.  
  
- **fac**. [grouping](../standard-library/moneypunct-class.md#moneypunct__grouping) determina cómo se agrupan los dígitos a la izquierda de cualquier separador decimal.  
  
- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#moneypunct__thousands_sep) determina el elemento que separa grupos de dígitos a la izquierda de cualquier separador decimal.  
  
- **fac**. [decimal_point](../standard-library/moneypunct-class.md#moneypunct__decimal_point) determina el elemento que separa los dígitos enteros de los dígitos de fracción.  
  
- **fac**. [frac_digits](../standard-library/moneypunct-class.md#moneypunct__frac_digits) determina el número de dígitos de fracción significativos a la derecha de cualquier separador decimal. Al analizar una cantidad monetaria con más dígitos de fracción que a los que se llama mediante `frac_digits`, `do_get` detiene el análisis después de consumir `frac_digits` caracteres como máximo.  
  
 Si la cadena de signo ( **fac**. `negative_sign` o **fac**. `positive_sign`) tiene más de un elemento, solo coincide con el primer elemento donde el elemento igual a **money_base::sign** aparece en el patrón de formato ( **fac**. `neg_format`). Coincide con cualquier elemento restante al final del campo de entrada monetario. Si ninguna cadena tiene un primer elemento que coincide con el siguiente elemento del campo de entrada monetario, la cadena de signo se toma como vacía y el signo es positivo.  
  
 Si **iosbase**. [flags](../standard-library/ios-base-class.md#ios_base__flags) & [showbase](../standard-library/ios-functions.md#showbase) es distinto de cero, la cadena **fac**. `curr_symbol` debe coincidir donde el elemento igual a **money_base::symbol** aparece en el patrón de formato. De otro modo, si **money_base::symbol** se produce al final del patrón de formato y, si ningún elemento de la cadena de signo debe coincidir, no coincide con el símbolo de moneda. De otro modo, coincide con el símbolo de moneda de manera opcional.  
  
 Si ninguna instancia de **fac**. `thousands_sep` se produce en la parte de valor del campo de entrada monetario (donde el elemento igual a **money_base::value** aparece en el patrón de formato), no se impone ninguna restricción de agrupación. De otro modo, cualquier restricción de agrupación impuesta por **fac**. **grouping** se aplica. Tenga en cuenta que la secuencia de dígitos resultante representa un entero cuyos dígitos decimales **fac**. `frac_digits` de nivel bajo se colocan a la derecha del separador decimal.  
  
 Coincide con el espacio en blanco arbitrario donde el elemento igual a **money_base::space** aparece en el patrón de formato, si aparece en otro lugar diferente que al final del patrón de formato. De otro modo, no coincide con ningún espacio en blanco interno. Un elemento *ch* se considera un espacio en blanco si [use_facet](../standard-library/locale-functions.md#use_facet) < [ctype](../standard-library/ctype-class.md)\< **CharType**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#ios_base__getloc)). [is](../standard-library/ctype-class.md#ctype__is)( **ctype_base::space**, *ch*) es **true**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [get](#money_get__get), que llama a `do_get`.  
  
##  <a name="a-namemoneygetgeta--moneygetget"></a><a name="money_get__get"></a> money_get::get  
 Extrae un valor numérico de una secuencia de caracteres que representa un valor monetario.  
  
```
iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const;

iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `first`  
 Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.  
  
 `last`  
 Iterador de entrada que se dirige al final de la secuencia que se va a convertir.  
  
 `Intl`  
 Un valor booleano que indica el tipo de símbolo de moneda que se espera en la secuencia: **true** si es internacional, **false** si es nacional.  
  
 `Iosbase`  
 Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.  
  
 `State`  
 Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.  
  
 `val`  
 Una cadena que almacena la secuencia convertida.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada monetario.  
  
### <a name="remarks"></a>Comentarios  
 Ambas funciones miembro devuelven [do_get](#money_get__do_get)( `first``,` `last``,` `Intl`, `Iosbase`, `State`, `val`).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// money_get_get.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
  
int main( )  
{  
   locale loc( "german_germany" );  
  
   basic_stringstream< char > psz;  
   psz << use_facet<moneypunct<char, 1> >(loc).curr_symbol() << "-1.000,56";  
   basic_stringstream< char > psz2;  
   psz2 << "-100056" << use_facet<moneypunct<char, 1> >(loc).curr_symbol();  
  
   ios_base::iostate st = 0;  
   long double fVal;  
  
   psz.flags( psz.flags( )|ios_base::showbase );   
   // Which forced the READING the currency symbol  
   psz.imbue(loc);  
   use_facet < money_get < char > >( loc ).  
      get( basic_istream<char>::_Iter( psz.rdbuf( ) ),     
           basic_istream<char>::_Iter( 0 ), true, psz, st, fVal );  
  
   if ( st & ios_base::failbit )  
      cout << "money_get(" << psz.str( ) << ", intl = 1) FAILED"  
           << endl;  
   else  
      cout << "money_get(" << psz.str( ) << ", intl = 1) = "   
           << fVal/100.0 << endl;  
  
   use_facet < money_get < char > >( loc ).  
      get(basic_istream<char>::_Iter(psz2.rdbuf( )),     
          basic_istream<char>::_Iter(0), false, psz2, st, fVal);  
  
   if ( st & ios_base::failbit )  
      cout << "money_get(" << psz2.str( ) << ", intl = 0) FAILED"   
           << endl;  
   else  
      cout << "money_get(" << psz2.str( ) << ", intl = 0) = "   
           << fVal/100.0 << endl;  
};  
```  
  
##  <a name="a-namemoneygetitertypea--moneygetitertype"></a><a name="money_get__iter_type"></a> money_get::iter_type  
 Tipo que describe un iterador de entrada.  
  
```
typedef InputIterator iter_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **InputIterator**.  
  
##  <a name="a-namemoneygetmoneygeta--moneygetmoneyget"></a><a name="money_get__money_get"></a> money_get::money_get  
 Constructor de objetos de tipo `money_get` que se usan para extraer valores numéricos de secuencias que representan valores monetarios.  
  
```
explicit money_get(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Refs`  
 Valor entero que se usa para especificar el tipo de administración de memoria del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Los valores posibles del parámetro `_Refs` y su importancia son:  
  
-   0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.  
  
-   1: la vigencia del objeto se debe administrar de manera manual.  
  
-   \> 0: estos valores no están definidos.  
  
 No es posible mostrar ejemplos directos, porque el destructor está protegido.  
  
 El constructor inicializa su objeto base con **locale::**[facet](../standard-library/locale-class.md#facet_class)( **_***Refs*).  
  
##  <a name="a-namemoneygetstringtypea--moneygetstringtype"></a><a name="money_get__string_type"></a> money_get::string_type  
 Un tipo que describe una cadena que contiene caracteres de tipo **CharType**.  
  
```
typedef basic_string<CharType, Traits, Allocator> string_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [basic_string](../standard-library/basic-string-class.md).  
  
## <a name="see-also"></a>Vea también  
 [\<locale>](../standard-library/locale.md)   
 [facet (Clase)](../standard-library/locale-class.md#facet_class)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)




