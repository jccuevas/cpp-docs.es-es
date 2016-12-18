---
title: "money_put (Clase) | Microsoft Docs"
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
  - "std::money_put"
  - "xlocmon/std::money_put"
  - "money_put"
  - "std.money_put"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "money_put (clase)"
ms.assetid: f439fd56-c9b1-414c-95e1-66c918c6eee6
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# money_put (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que puede actuar como una faceta de la configuración regional para controlar las conversiones de valores monetarios en secuencias de tipo `CharType`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class CharType,  
    class OutputIterator = ostreambuf_iterator<CharType>>  
class money_put : public locale::facet;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `CharType`  
 Tipo usado dentro de un programa para codificar los caracteres de una configuración regional.  
  
 `OutputIterator`  
 Tipo de iterador en el que las funciones monetary put escriben sus resultados.  
  
## <a name="remarks"></a>Comentarios  
 Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento para tener acceso a su valor almacenado almacena un valor positivo único en **id.**  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[money_put](#money_put__money_put)|Constructor para los objetos de tipo `money_put`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#money_put__char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|  
|[iter_type](#money_put__iter_type)|Tipo que describe un iterador de salida.|  
|[STRING_TYPE](#money_put__string_type)|Tipo que describe una cadena que contiene caracteres de tipo `CharType`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[do_put](#money_put__do_put)|Una función virtual a la que se llama para convertir un número o una cadena en una secuencia de caracteres que representa un valor monetario.|  
|[PUT](#money_put__put)|Convierte un número o una cadena en una secuencia de caracteres que representa un valor monetario.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< configuración regional>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namemoneyputchartypea-moneyputchartype"></a><a name="money_put__char_type"></a>  money_put:: char_type  
 Tipo que se usa para describir un carácter empleado por una configuración regional.  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **CharType**.  
  
##  <a name="a-namemoneyputdoputa-moneyputdoput"></a><a name="money_put__do_put"></a>  money_put:: do_put  
 Una función virtual a la que se llama para convertir un número o una cadena en una secuencia de caracteres que representa un valor monetario.  
  
```  
virtual iter_type do_put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,   
    const string_type& val) const;

 
virtual iter_type do_put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,  
    long double val) const;
```  
  
### <a name="parameters"></a>Parámetros  
 ` next`  
 Un iterador que direcciona el primer elemento de la cadena insertada.  
  
 `_Intl`  
 Un valor booleano que indica el tipo de símbolo de moneda esperado en la secuencia: **true** Si internacionales, **false** Si nacionales.  
  
 `_Iosbase`  
 Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional; de lo contrario, es necesario  
  
 `_Fill`  
 Carácter que se utiliza para el espaciado.  
  
 ` val`  
 Un objeto de cadena que se va a convertir.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de salida generado de la posición más allá del último elemento de las direcciones.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro protegido virtual genera elementos secuenciales, empezando por ` next` para producir un campo monetario de salida desde el [string_type](#money_put__string_type) objeto ` val`. La secuencia controlada por ` val` debe comenzar con uno o más dígitos decimales, opcionalmente precedidos de un signo menos (-), que representa la cantidad. La función devuelve un iterador que designa el primer elemento más allá del campo monetario de salida generado.  
  
 La segunda función miembro protegido virtual comporta igual que la primera, excepto que TI eficazmente primera convierte ` val` en una secuencia de dígitos decimales, opcionalmente precedido de un signo menos, a continuación, convierte esa secuencia anterior.  
  
 El formato de un campo monetario de salida viene determinado por la [faceta de configuración regional](../standard-library/locale-class.md#facet_class) servicio devuelto por la llamada (efectiva) [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, **intl**>> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#ios_base__getloc)).  
  
 De manera específica:  
  
- **servicio**. [pos_format](../standard-library/moneypunct-class.md#moneypunct__pos_format) determina el orden en el que se generan los componentes del campo para un valor no negativo.  
  
- **servicio**. [neg_format](../standard-library/moneypunct-class.md#moneypunct__neg_format) determina el orden en el que se generan los componentes del campo para un valor negativo.  
  
- **servicio**. [curr_symbol](../standard-library/moneypunct-class.md#moneypunct__curr_symbol) determina la secuencia de elementos que se van a generar para un símbolo de moneda.  
  
- **servicio**. [positive_sign](../standard-library/moneypunct-class.md#moneypunct__positive_sign) determina la secuencia de elementos que se van a generar para un signo positivo.  
  
- **servicio**. [negative_sign](../standard-library/moneypunct-class.md#moneypunct__negative_sign) determina la secuencia de elementos que se van a generar para un signo negativo.  
  
- **servicio**. [agrupar](../standard-library/moneypunct-class.md#moneypunct__grouping) determina cómo se agrupan los dígitos a la izquierda del separador decimal.  
  
- **servicio**. [thousands_sep](../standard-library/moneypunct-class.md#moneypunct__thousands_sep) determina el elemento que separa grupos de dígitos a la izquierda del separador decimal.  
  
- **servicio**. [decimal_point](../standard-library/moneypunct-class.md#moneypunct__decimal_point) determina el elemento que separa los dígitos enteros de los dígitos de fracción.  
  
- **servicio**. [frac_digits](../standard-library/moneypunct-class.md#moneypunct__frac_digits) determina el número de dígitos de fracción considerable a la derecha del separador decimal.  
  
 Si la cadena de inicio de sesión ( **servicio**. `negative_sign` o **servicio**. `positive_sign`) tiene más de un elemento, sólo el primer elemento se genera en el elemento igual a **money_base::sign** aparece en el modelo de formato ( **servicio**. `neg_format` o **servicio**. `pos_format`). Los elementos restantes se generan al final del campo monetario de salida.  
  
 Si **iosbase**. [marcas de](../standard-library/ios-base-class.md#ios_base__flags) & [showbase](../Topic/%3Cios%3E%20functions.md#showbase) es distinto de cero, la cadena **servicio**. `curr_symbol` se genera en el elemento igual a **money_base::symbol** aparece en el modelo de formato. De lo contrario, no se genera ningún símbolo de moneda.  
  
 Si no hay ninguna restricción de agrupación se imponen por **servicio**. **agrupar** (el primer elemento tiene el valor CHAR_MAX), a continuación, no hay instancias de **servicio**. `thousands_sep` se generan en la parte del valor del campo monetario de salida (donde el elemento igual a **money_base::value** aparece en el modelo de formato). Si **servicio**. `frac_digits` es cero, entonces ninguna instancia de **servicio**. `decimal_point` se genera después de los dígitos decimales. De lo contrario, el campo monetario de salida resultante coloca el orden inferior **servicio**. `frac_digits` dígitos decimales a la derecha del separador decimal.  
  
 Se produce el relleno que para cualquier campo numérico de salida, pero si **iosbase**. **marcas de** & **iosbase**. [interna](../Topic/%3Cios%3E%20functions.md#internal) está relleno distinto de cero, cualquier interno se genera en el elemento igual a **money_base::space** aparece en el modelo de formato, si aparece. En caso contrario, el espaciado interno se produce antes de la secuencia generada. El carácter de relleno es **relleno**.  
  
 Las llamadas de función **iosbase**. **ancho**(0) para restablecer el ancho de campo a cero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [colocar](#money_put__put), donde se llama a la función miembro virtual **colocar**.  
  
##  <a name="a-namemoneyputitertypea-moneyputitertype"></a><a name="money_put__iter_type"></a>  money_put:: iter_type  
 Tipo que describe un iterador de salida.  
  
```  
typedef OutputIterator iter_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **OutputIterator.**  
  
##  <a name="a-namemoneyputmoneyputa-moneyputmoneyput"></a><a name="money_put__money_put"></a>  money_put:: money_put  
 Constructor para los objetos de tipo `money_put`.  
  
```  
explicit money_put(size_t _Refs = 0);
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
  
 El constructor inicializa su objeto base con **locale::**[faceta](../standard-library/locale-class.md#facet_class)( `_Refs`).  
  
##  <a name="a-namemoneyputputa-moneyputput"></a><a name="money_put__put"></a>  money_put:: Put  
 Convierte un número o una cadena en una secuencia de caracteres que representa un valor monetario.  
  
```  
iter_type put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,   
    const string_type& val) const;

 
iter_type put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,  
    long double val) const;
```  
  
### <a name="parameters"></a>Parámetros  
 ` next`  
 Un iterador que direcciona el primer elemento de la cadena insertada.  
  
 `_Intl`  
 Un valor booleano que indica el tipo de símbolo de moneda esperado en la secuencia: **true** Si internacionales, **false** Si nacionales.  
  
 `_Iosbase`  
 Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional; de lo contrario, es necesario  
  
 `_Fill`  
 Carácter que se utiliza para el espaciado.  
  
 ` val`  
 Un objeto de cadena que se va a convertir.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de salida generado de la posición más allá del último elemento de las direcciones.  
  
### <a name="remarks"></a>Comentarios  
 Ambas funciones miembro devuelven [do_put](#money_put__do_put)( ` next`, `_Intl`, `_Iosbase`, `_Fill`, ` val`).  
  
### <a name="example"></a>Ejemplo  
  
```  
// money_put_put.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
//   locale loc( "german_germany" );  
   locale loc( "english_canada" );  
   basic_stringstream<char> psz, psz2;  
   ios_base::iostate st = 0;  
  
   psz2.imbue( loc );  
   psz2.flags( psz2.flags( )|ios_base::showbase ); // force the printing of the currency symbol  
   use_facet < money_put < char > >(loc).put(basic_ostream<char>::_Iter( psz2.rdbuf( ) ), true, psz2, st, 100012);  
   if (st & ios_base::failbit)  
      cout << "money_put( ) FAILED" << endl;  
   else  
      cout << "money_put( ) = \"" << psz2.rdbuf( )->str( ) <<"\""<< endl;     
  
   st = 0;  
};  
```  
  
```Output  
money_put( ) = "CAD1,000.12"  
```  
  
##  <a name="a-namemoneyputstringtypea-moneyputstringtype"></a><a name="money_put__string_type"></a>  money_put:: STRING_TYPE  
 Un tipo que describe una cadena que contiene caracteres de tipo **CharType**.  
  
```  
typedef basic_string<CharType, Traits, Allocator> string_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [basic_string](../standard-library/basic-string-class.md) cuyos objetos pueden almacenar secuencias de elementos de la secuencia de origen.  
  
## <a name="see-also"></a>Vea también  
 [\< configuración regional>](../standard-library/locale.md)   
 [Facet (clase)](../standard-library/locale-class.md#facet_class)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

