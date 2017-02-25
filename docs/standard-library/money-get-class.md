---
title: "money_get (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xlocmon/std::money_get"
  - "money_get"
  - "std.money_get"
  - "std::money_get"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "money_get (clase)"
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# money_get (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

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
 Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento para tener acceso a su valor almacenado almacena un valor positivo único en **id.**  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[money_get](#money_get__money_get)|Constructor de objetos de tipo `money_get` que se usan para extraer valores numéricos de secuencias que representan valores monetarios.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#money_get__char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|  
|[iter_type](#money_get__iter_type)|Tipo que describe un iterador de entrada.|  
|[STRING_TYPE](#money_get__string_type)|Tipo que describe una cadena que contiene caracteres de tipo `CharType`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[do_get](#money_get__do_get)|Función virtual a la que se llama para extraer un valor numérico de una secuencia de caracteres que representa un valor monetario.|  
|[Obtener](#money_get__get)|Extrae un valor numérico de una secuencia de caracteres que representa un valor monetario.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< configuración regional>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namemoneygetchartypea-moneygetchartype"></a><a name="money_get__char_type"></a>  money_get:: char_type  
 Tipo que se usa para describir un carácter empleado por una configuración regional.  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **CharType**.  
  
##  <a name="a-namemoneygetdogeta-moneygetdoget"></a><a name="money_get__do_get"></a>  money_get:: do_get  
 Función virtual que se llama para extrae un valor numérico de una secuencia de caracteres que representa un valor monetario.  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    bool _Intl,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const virtual iter_type do_get(iter_type first,
    iter_type last,
    bool _Intl,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    string_type& val) const
```  
  
### <a name="parameters"></a>Parámetros  
 `first`  
 Iterador de entrada que direcciona el principio de la secuencia que se va a convertir.  
  
 `last`  
 Iterador de entrada que direcciona al final de la secuencia que se va a convertir.  
  
 `_Intl`  
 Un valor booleano que indica el tipo de símbolo de moneda esperado en la secuencia: **true** Si internacionales, **false** Si nacionales.  
  
 `_Iosbase`  
 Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional; de lo contrario, es necesario.  
  
 `_State`  
 Establece los elementos de la máscara de bits apropiada para el estado de la secuencia según si las operaciones se realizó correctamente o no.  
  
 `val`  
 Una cadena de almacenar la secuencia convertida.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de entrada que direcciona el primer elemento más allá de un campo monetario de entrada.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro protegido virtual intenta hacer coincidir elementos secuenciales, empezando al principio de la secuencia [ `first`, `last`) hasta que se reconoce una completa, el campo de entrada de moneda vacía. Si tiene éxito, convierte este campo en una secuencia de uno o más dígitos decimales, opcionalmente precedido de un signo menos ( `–`), para representar la cantidad y almacena el resultado en la [string_type](#money_get__string_type) objeto `val`. Devuelve un iterador que designa el primer elemento más allá de un campo monetario de entrada. De lo contrario, la función almacena una secuencia vacía en `val` y establece `ios_base::failbit` en `_State`. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de un campo monetario de entrada válido. En cualquier caso, si el valor devuelto es igual a `last`, la función establece `ios_base::eofbit` en `_State`.  
  
 La segunda función miembro protegido virtual comporta igual que la primera, excepto en que si se realiza correctamente convierte la secuencia de dígitos, opcionalmente, con signo en un valor de tipo `long double` y almacena ese valor en `val`.  
  
 El formato de un campo monetario de entrada viene determinado por la [faceta de configuración regional](../standard-library/locale-class.md#facet_class)**servicio** devuelto por la llamada efectiva [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, **intl**>> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#ios_base__getloc)).  
  
 De manera específica:  
  
- **servicio**. [neg_format](../standard-library/moneypunct-class.md#moneypunct__neg_format) determina el orden en que aparecen los componentes del campo.  
  
- **servicio**. [curr_symbol](../standard-library/moneypunct-class.md#moneypunct__curr_symbol) determina la secuencia de elementos que constituye un símbolo de moneda.  
  
- **servicio**. [positive_sign](../standard-library/moneypunct-class.md#moneypunct__positive_sign) determina la secuencia de elementos que constituye un signo positivo.  
  
- **servicio**. [negative_sign](../standard-library/moneypunct-class.md#moneypunct__negative_sign) determina la secuencia de elementos que constituye un signo negativo.  
  
- **servicio**. [agrupar](../standard-library/moneypunct-class.md#moneypunct__grouping) determina cómo se agrupan los dígitos a la izquierda del separador decimal.  
  
- **servicio**. [thousands_sep](../standard-library/moneypunct-class.md#moneypunct__thousands_sep) determina el elemento que separa grupos de dígitos a la izquierda del separador decimal.  
  
- **servicio**. [decimal_point](../standard-library/moneypunct-class.md#moneypunct__decimal_point) determina el elemento que separa los dígitos enteros de los dígitos de fracción.  
  
- **servicio**. [frac_digits](../standard-library/moneypunct-class.md#moneypunct__frac_digits) determina el número de dígitos de fracción considerable a la derecha del separador decimal. Al analizar un importe monetario con más de los dígitos de fracción que se llama para `frac_digits`, `do_get` detiene el análisis después de consumir a lo sumo `frac_digits` caracteres.  
  
 Si la cadena de inicio de sesión ( **servicio**. `negative_sign` o **servicio**. `positive_sign`) tiene más de un elemento, sólo el primer elemento que coincide el elemento igual a **money_base::sign** aparece en el modelo de formato ( **servicio**. `neg_format`). Los elementos restantes se asocian al final del campo monetario de entrada. Si ninguna cadena tiene un primer elemento que coincide con el elemento siguiente en el campo monetario de entrada, la cadena de inicio de sesión se realiza como vacía y el inicio de sesión es positivo.  
  
 Si **iosbase**. [marcas de](../standard-library/ios-base-class.md#ios_base__flags) & [showbase](../Topic/%3Cios%3E%20functions.md#showbase) es distinto de cero, la cadena **servicio**. `curr_symbol` debe coincidir con donde el elemento igual a **money_base::symbol** aparece en el modelo de formato. De lo contrario, si **money_base::symbol** se produce al final del patrón de formato, y si no queda ningún elemento de la cadena de inicio de sesión debe coincidir, no coincide con el símbolo de moneda. De lo contrario, opcionalmente se compara el símbolo de moneda.  
  
 Si no hay instancias de **servicio**. `thousands_sep` se producen en la parte del valor del campo monetario de entrada (donde el elemento igual a **money_base::value** aparece en el modelo de formato), no se impone ninguna restricción de agrupación. De lo contrario, cualquier agrupación de restricciones impuestas por **servicio**. **agrupación de** se aplica. Tenga en cuenta que la secuencia de dígitos resultante representa un entero cuyo orden inferior **servicio**. `frac_digits` se consideran dígitos decimales a la derecha del separador decimal.  
  
 Se hace coincidir el espacio en blanco arbitrario en el elemento igual a **money_base::space** aparece en el modelo de formato, si otro que aparece al final del patrón de formato. De lo contrario, no se asocia ningún espacio en blanco interno. Un elemento *ch* se consideran espacios en blanco si [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) < [ctype](../standard-library/ctype-class.md)\< **CharType**>> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#ios_base__getloc)). [es](../standard-library/ctype-class.md#ctype__is)( **ctype_base::space**, *ch*) es **true**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [obtener](#money_get__get), que llama `do_get`.  
  
##  <a name="a-namemoneygetgeta-moneygetget"></a><a name="money_get__get"></a>  money_get:: Get  
 Extrae un valor numérico de una secuencia de caracteres que representa un valor monetario.  
  
```
iter_type get(iter_type first,
    iter_type last,
    bool _Intl,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

iter_type get(iter_type first,
    iter_type last,
    bool _Intl,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    string_type& val) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `first`  
 Iterador de entrada que direcciona el principio de la secuencia que se va a convertir.  
  
 `last`  
 Iterador de entrada que direcciona al final de la secuencia que se va a convertir.  
  
 `_Intl`  
 Un valor booleano que indica el tipo de símbolo de moneda esperado en la secuencia: **true** Si internacionales, **false** Si nacionales.  
  
 `_Iosbase`  
 Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional; de lo contrario, es necesario  
  
 `_State`  
 Establece los elementos de la máscara de bits apropiada para el estado de la secuencia según si las operaciones se realizó correctamente.  
  
 `val`  
 Una cadena de almacenar la secuencia convertida.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de entrada que direcciona el primer elemento más allá de un campo monetario de entrada.  
  
### <a name="remarks"></a>Comentarios  
 Ambas funciones miembro devuelven [do_get](#money_get__do_get)( `first``,` `last``,` `_Intl`, `_Iosbase`, `_State`, `val`).  
  
### <a name="example"></a>Ejemplo  
  
```  
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
  
##  <a name="a-namemoneygetitertypea-moneygetitertype"></a><a name="money_get__iter_type"></a>  money_get:: iter_type  
 Tipo que describe un iterador de entrada.  
  
```
typedef InputIterator iter_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **InputIterator**.  
  
##  <a name="a-namemoneygetmoneygeta-moneygetmoneyget"></a><a name="money_get__money_get"></a>  money_get:: money_get  
 Constructor de objetos de tipo `money_get` que se usan para extraer valores numéricos de secuencias que representan valores monetarios.  
  
```
explicit money_get(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Refs`  
 Valor entero que se utiliza para especificar el tipo de administración de memoria para el objeto.  
  
### <a name="remarks"></a>Comentarios  
 Los valores posibles de la `_Refs` parámetro y su importancia son:  
  
-   0: la duración del objeto administra las configuraciones regionales que lo contienen.  
  
-   1: se debe administrar manualmente la duración del objeto.  
  
-   \> 0: no se definen estos valores.  
  
 No hay ejemplos directos son posibles, porque está protegido el destructor.  
  
 El constructor inicializa su objeto base con **locale::**[faceta](../standard-library/locale-class.md#facet_class)( **_***Refs*).  
  
##  <a name="a-namemoneygetstringtypea-moneygetstringtype"></a><a name="money_get__string_type"></a>  money_get:: STRING_TYPE  
 Un tipo que describe una cadena que contiene caracteres de tipo **CharType**.  
  
```
typedef basic_string<CharType, Traits, Allocator> string_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [basic_string](../standard-library/basic-string-class.md).  
  
## <a name="see-also"></a>Vea también  
 [\< configuración regional>](../standard-library/locale.md)   
 [Facet (clase)](../standard-library/locale-class.md#facet_class)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



