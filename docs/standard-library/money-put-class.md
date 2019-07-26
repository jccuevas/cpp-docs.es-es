---
title: money_put (Clase)
ms.date: 11/01/2018
f1_keywords:
- xlocmon/std::money_put
- xlocmon/std::money_put::char_type
- xlocmon/std::money_put::iter_type
- xlocmon/std::money_put::string_type
- xlocmon/std::money_put::do_put
- xlocmon/std::money_put::put
helpviewer_keywords:
- std::money_put [C++]
- std::money_put [C++], char_type
- std::money_put [C++], iter_type
- std::money_put [C++], string_type
- std::money_put [C++], do_put
- std::money_put [C++], put
ms.assetid: f439fd56-c9b1-414c-95e1-66c918c6eee6
ms.openlocfilehash: b9dff8a871895eee6774b75ca1c83dca6fd42ff3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460235"
---
# <a name="moneyput-class"></a>money_put (Clase)

La clase de plantilla describe un objeto que puede actuar como una faceta de la configuración regional para controlar las conversiones de valores monetarios en secuencias de tipo `CharType`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class money_put : public locale::facet;
```

### <a name="parameters"></a>Parámetros

*CharType*\
Tipo usado dentro de un programa para codificar los caracteres de una configuración regional.

*OutputIterator*\
Tipo de iterador en el que las funciones monetary put escriben sus resultados.

## <a name="remarks"></a>Comentarios

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[money_put](#money_put)|Constructor para los objetos de tipo `money_put`.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|DESCRIPCIÓN|
|-|-|
|[char_type](#char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|
|[iter_type](#iter_type)|Tipo que describe un iterador de salida.|
|[string_type](#string_type)|Tipo que describe una cadena que contiene caracteres de tipo `CharType`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[do_put](#do_put)|Una función virtual a la que se llama para convertir un número o una cadena en una secuencia de caracteres que representa un valor monetario.|
|[put](#put)|Convierte un número o una cadena en una secuencia de caracteres que representa un valor monetario.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="char_type"></a> money_put::char_type

Tipo que se usa para describir un carácter empleado por una configuración regional.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla **CharType**.

## <a name="do_put"></a> money_put::do_put

Una función virtual a la que se llama para convertir un número o una cadena en una secuencia de caracteres que representa un valor monetario.

```cpp
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

*Nueva*\
Un iterador que se dirige al primer elemento de la cadena insertada.

*_Intl*\
Un valor booleano que indica el tipo de símbolo de moneda que se espera en la secuencia: **true** si es internacional, **false** si es nacional.

*_Iosbase*\
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

*_Fill*\
Un carácter que se usa para el espaciado.

*Val*\
Un objeto de cadena que se va a convertir.

### <a name="return-value"></a>Valor devuelto

Un iterador de salida que se dirige a la posición siguiente del último elemento que se ha producido.

### <a name="remarks"></a>Comentarios

La primera función miembro virtual protegida genera elementos secuenciales que comienzan en el *siguiente* para generar un campo de salida monetaria a partir del *Val*del objeto [string_type](#string_type) . La secuencia controlada por *Val* debe comenzar con uno o más dígitos decimales, de manera opcional precedida por un signo menos (-), que representa la cantidad. La función devuelve un iterador que designa el primer elemento más allá del campo de salida monetario que se ha generado.

La segunda función miembro virtual protegida se comporta igual que la primera, salvo que primero convierte de forma eficaz el valor de *Val* en una secuencia de dígitos decimales, opcionalmente precedido por un signo menos, y después convierte esa secuencia como arriba.

El formato de un campo de salida monetario se determina por la [faceta de configuración regional](../standard-library/locale-class.md#facet_class) fac devuelta mediante la llamada (eficaz) a [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, **intl**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)).

De manera específica:

- **fac**. [pos_format](../standard-library/moneypunct-class.md#pos_format) determina el orden en el que se generan los componentes del campo para un valor no negativo.

- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) determina el orden en el que se generan los componentes del campo para un valor negativo.

- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) determina la secuencia de elementos que se va a generar para un símbolo de moneda.

- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) determina la secuencia de elementos que se va a generar para un signo positivo.

- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) determina la secuencia de elementos que se va a generar para un signo negativo.

- **fac**. [grouping](../standard-library/moneypunct-class.md#grouping) determina cómo se agrupan los dígitos a la izquierda de cualquier separador decimal.

- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) determina el elemento que separa grupos de dígitos a la izquierda de cualquier separador decimal.

- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) determina el elemento que separa los dígitos enteros de cualquier dígito de fracción.

- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) determina el número de dígitos de fracción significativos a la derecha de cualquier separador decimal.

Si la cadena de signo ( **fac**. `negative_sign` o **fac**. `positive_sign`) tiene más de un elemento, solo se genera el primer elemento donde el elemento igual a **money_base::sign** aparece en el patrón de formato ( **fac**. `neg_format` o **fac**. `pos_format`). Cualquier elemento restante se genera al final del campo de salida monetario.

Si **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) es distinto de cero, la cadena **fac**. `curr_symbol` se genera donde el elemento igual a **money_base::symbol** aparece en el patrón de formato. De otro modo, no se genera ningún símbolo de moneda.

Si no se impone ninguna restricción de agrupación mediante **fac**. **grouping** (su primer elemento tiene el valor CHAR_MAX), entonces ninguna instancia de **fac**. `thousands_sep` se genera en la parte de valor del campo de salida monetario (donde el elemento igual a **money_base::value** aparece en el patrón de formato). Si **fac**. `frac_digits` es cero, entonces ninguna instancia de **fac**. `decimal_point` se genera después de los dígitos decimales. De otro modo, el campo de salida monetario resultante coloca los dígitos decimales **fac**. `frac_digits` de nivel bajo a la derecha del separador decimal.

El relleno se produce en cualquier campo de salida numérico, excepto si **iosbase**. **flags** & **iosbase**. [internal](../standard-library/ios-functions.md#internal) es distinto de cero, cualquier relleno interno se genera donde el elemento igual a **money_base::space** aparece en el patrón de formato, si aparece. De otro modo, el relleno interno se produce antes de la secuencia generada. El carácter de relleno es **fill**.

La función llama a **iosbase**. **width**(0) para restablecer el ancho de campo a cero.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [put](#put), donde **put** llama a la función miembro virtual.

## <a name="iter_type"></a> money_put::iter_type

Tipo que describe un iterador de salida.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla **OutputIterator**.

## <a name="money_put"></a> money_put::money_put

Constructor para los objetos de tipo `money_put`.

```cpp
explicit money_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parámetros

*_Refs*\
Valor entero que se usa para especificar el tipo de administración de memoria del objeto.

### <a name="remarks"></a>Comentarios

Los valores posibles para el parámetro *_Refs* y su importancia son:

- 0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: la vigencia del objeto se debe administrar de manera manual.

- \>1: estos valores no están definidos.

No es posible mostrar ejemplos directos, porque el destructor está protegido.

El constructor inicializa su objeto base con **locale::** [facet](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="put"></a> money_put::put

Convierte un número o una cadena en una secuencia de caracteres que representa un valor monetario.

```cpp
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

*Nueva*\
Un iterador que se dirige al primer elemento de la cadena insertada.

*_Intl*\
Un valor booleano que indica el tipo de símbolo de moneda que se espera en la secuencia: **true** si es internacional, **false** si es nacional.

*_Iosbase*\
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

*_Fill*\
Un carácter que se usa para el espaciado.

*Val*\
Un objeto de cadena que se va a convertir.

### <a name="return-value"></a>Valor devuelto

Un iterador de salida que se dirige a la posición siguiente del último elemento que se ha producido.

### <a name="remarks"></a>Comentarios

Ambas funciones miembro devuelven [do_put](#do_put)( `next`, `_Intl`, `_Iosbase`, `_Fill`, `val`).

### <a name="example"></a>Ejemplo

```cpp
// money_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

int main()
{
    std::locale loc( "german_germany" );
    std::basic_stringstream<char> psz;

    psz.imbue(loc);
    psz.flags(psz.flags() | std::ios_base::showbase); // force the printing of the currency symbol
    std::use_facet<std::money_put<char> >(loc).put(std::basic_ostream<char>::_Iter(psz.rdbuf()), true, psz, ' ', 100012);
    if (psz.fail())
        std::cout << "money_put() FAILED" << std::endl;
    else
        std::cout << "money_put() = \"" << psz.rdbuf()->str() << "\"" << std::endl;
}
```

```Output
money_put() = "EUR1.000,12"
```

## <a name="string_type"></a> money_put::string_type

Tipo que describe una cadena que contiene caracteres de tipo `CharType`.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [basic_string](../standard-library/basic-string-class.md) cuyos objetos pueden almacenar secuencias de elementos de la secuencia de origen.

## <a name="see-also"></a>Vea también

[\<locale>](../standard-library/locale.md)\
[facet (Clase)](../standard-library/locale-class.md#facet_class)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
