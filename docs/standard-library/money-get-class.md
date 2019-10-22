---
title: money_get (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_get
- xlocmon/std::money_get::char_type
- xlocmon/std::money_get::iter_type
- xlocmon/std::money_get::string_type
- xlocmon/std::money_get::do_get
- xlocmon/std::money_get::get
helpviewer_keywords:
- std::money_get [C++]
- std::money_get [C++], char_type
- std::money_get [C++], iter_type
- std::money_get [C++], string_type
- std::money_get [C++], do_get
- std::money_get [C++], get
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
ms.openlocfilehash: d882edd5ce55b15d03512ca9a55a49bc3424ee7a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687667"
---
# <a name="money_get-class"></a>money_get (Clase)

La plantilla de clase describe un objeto que puede actuar como una faceta de configuración regional para controlar las conversiones de secuencias de tipo `CharType` a valores monetarios.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>Parámetros

@No__t_1 *CharType*
Tipo usado dentro de un programa para codificar los caracteres de una configuración regional.

@No__t_1 *InputIterator*
Tipo de iterador del que las funciones get leen su entrada.

## <a name="remarks"></a>Comentarios

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[money_get](#money_get)|Constructor de objetos de tipo `money_get` que se usan para extraer valores numéricos de secuencias que representan valores monetarios.|

### <a name="typedefs"></a>Definiciones de tipo

|Nombre de tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|
|[iter_type](#iter_type)|Tipo que describe un iterador de entrada.|
|[string_type](#string_type)|Tipo que describe una cadena que contiene caracteres de tipo `CharType`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[do_get](#do_get)|Función virtual a la que se llama para extraer un valor numérico de una secuencia de caracteres que representa un valor monetario.|
|[get](#get)|Extrae un valor numérico de una secuencia de caracteres que representa un valor monetario.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="char_type"></a> money_get::char_type

Tipo que se usa para describir un carácter empleado por una configuración regional.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla *CharType*.

## <a name="do_get"></a> money_get::do_get

Función virtual a la que se llama para extraer un valor numérico de una secuencia de caracteres que representa un valor monetario.

```cpp
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

*primer* \
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*última* \
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

@No__t_1 *Intl*
Un valor booleano que indica el tipo de símbolo de moneda que se espera en la secuencia: **true** si es internacional, **false** si es nacional.

@No__t_1 *Iosbase*
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

@No__t_1 de *Estado*
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente o no.

\ *Val*
Una cadena que almacena la secuencia convertida.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada monetario.

### <a name="remarks"></a>Comentarios

La primera función miembro virtual protegida intenta hacer coincidir los elementos secuenciales, empezando al principio de la secuencia [ `first`, `last`) hasta que reconoce un campo de entrada monetario completo y que no esté vacío. Si se realiza correctamente, convierte este campo en una secuencia de uno o más dígitos decimales, de manera opcional precedida por un signo menos (`-`), para representar la cantidad y almacena el resultado en el objeto [string_type](#string_type) *Val*. Devuelve un iterador que designa el primer elemento más allá del campo de entrada monetario. De lo contrario, la función almacena una secuencia vacía en *Val* y establece `ios_base::failbit` en el *Estado*. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de campo de entrada monetario válido. En cualquier caso, si el valor devuelto es igual a `last`, la función establece `ios_base::eofbit` en `State`.

La segunda función miembro virtual protegida se comporta igual que la primera, salvo que, si se ejecuta correctamente, convierte la secuencia de dígitos con signo opcional en un valor de tipo **Long Double** y almacena ese valor en *Val*.

El formato de un campo de entrada monetario se determina por la [faceta de configuración regional](../standard-library/locale-class.md#facet_class)**fac** devuelta mediante la llamada eficaz a [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, **intl**>>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)).

De manera específica:

- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) determina el orden en el que aparecen los componentes del campo.

- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) determina la secuencia de elementos que constituye un símbolo de moneda.

- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) determina la secuencia de elementos que constituye un signo positivo.

- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) determina la secuencia de elementos que constituye un signo negativo.

- **fac**. [grouping](../standard-library/moneypunct-class.md#grouping) determina cómo se agrupan los dígitos a la izquierda de cualquier separador decimal.

- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) determina el elemento que separa grupos de dígitos a la izquierda de cualquier separador decimal.

- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) determina el elemento que separa los dígitos enteros de los dígitos de fracción.

- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) determina el número de dígitos de fracción significativos a la derecha de cualquier separador decimal. Al analizar una cantidad monetaria con más dígitos de fracción que a los que se llama mediante `frac_digits`, `do_get` detiene el análisis después de consumir `frac_digits` caracteres como máximo.

Si la cadena de signo ( **fac**. `negative_sign` o **fac**. `positive_sign`) tiene más de un elemento, solo coincide con el primer elemento donde el elemento igual a **money_base::sign** aparece en el patrón de formato ( **fac**. `neg_format`). Coincide con cualquier elemento restante al final del campo de entrada monetario. Si ninguna cadena tiene un primer elemento que coincide con el siguiente elemento del campo de entrada monetario, la cadena de signo se toma como vacía y el signo es positivo.

Si **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) es distinto de cero, la cadena **fac**. `curr_symbol` debe coincidir donde el elemento igual a **money_base::symbol** aparece en el patrón de formato. De otro modo, si **money_base::symbol** se produce al final del patrón de formato y, si ningún elemento de la cadena de signo debe coincidir, no coincide con el símbolo de moneda. De otro modo, coincide con el símbolo de moneda de manera opcional.

Si ninguna instancia de **fac**. `thousands_sep` se produce en la parte de valor del campo de entrada monetario (donde el elemento igual a **money_base::value** aparece en el patrón de formato), no se impone ninguna restricción de agrupación. De otro modo, cualquier restricción de agrupación impuesta por **fac**. **grouping** se aplica. Tenga en cuenta que la secuencia de dígitos resultante representa un entero cuyos dígitos decimales **fac**. `frac_digits` de nivel bajo se colocan a la derecha del separador decimal.

Coincide con el espacio en blanco arbitrario donde el elemento igual a **money_base::space** aparece en el patrón de formato, si aparece en otro lugar diferente que al final del patrón de formato. De otro modo, no coincide con ningún espacio en blanco interno. Un elemento *ch* se considera un espacio en blanco si [use_facet](../standard-library/locale-functions.md#use_facet) < [ctype](../standard-library/ctype-class.md)\< **CharType**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). [is](../standard-library/ctype-class.md#is)( **ctype_base::space**, *ch*) es **true**.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get](#get), que llama a `do_get`.

## <a name="get"></a> money_get::get

Extrae un valor numérico de una secuencia de caracteres que representa un valor monetario.

```cpp
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

*primer* \
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*última* \
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

@No__t_1 *Intl*
Un valor booleano que indica el tipo de símbolo de moneda que se espera en la secuencia: **true** si es internacional, **false** si es nacional.

@No__t_1 *Iosbase*
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

@No__t_1 de *Estado*
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

\ *Val*
Una cadena que almacena la secuencia convertida.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada monetario.

### <a name="remarks"></a>Comentarios

Ambas funciones miembro devuelven [do_get](#do_get) `(first, last, Intl, Iosbase, State, val)`.

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

## <a name="iter_type"></a> money_get::iter_type

Tipo que describe un iterador de entrada.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla **InputIterator**.

## <a name="money_get"></a> money_get::money_get

Constructor de objetos de tipo `money_get` que se usan para extraer valores numéricos de secuencias que representan valores monetarios.

```cpp
explicit money_get(size_t _Refs = 0);
```

### <a name="parameters"></a>Parámetros

@No__t_1 *_Refs*
Valor entero que se usa para especificar el tipo de administración de memoria del objeto.

### <a name="remarks"></a>Comentarios

Los valores posibles para el parámetro *_Refs* y su importancia son:

- 0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: la vigencia del objeto se debe administrar de manera manual.

- \> 1: estos valores no están definidos.

No es posible mostrar ejemplos directos, porque el destructor está protegido.

El constructor inicializa su objeto base con **locale::** [Facet](../standard-library/locale-class.md#facet_class)( *_Refs*).

## <a name="string_type"></a> money_get::string_type

Un tipo que describe una cadena que contiene caracteres de tipo **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de la plantilla de clase [basic_string](../standard-library/basic-string-class.md).

## <a name="see-also"></a>Vea también

[\<locale>](../standard-library/locale.md)\
[facet (Clase)](../standard-library/locale-class.md#facet_class)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
