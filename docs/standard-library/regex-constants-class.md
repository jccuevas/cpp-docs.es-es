---
title: regex_constants (Clase)
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_constants
- regex/std::regex_constants::error_collate
- regex/std::regex_constants::error_ctype
- regex/std::regex_constants::error_escape
- regex/std::regex_constants::error_backref
- regex/std::regex_constants::error_brack
- regex/std::regex_constants::error_paren
- regex/std::regex_constants::error_brace
- regex/std::regex_constants::error_badbrace
- regex/std::regex_constants::error_range
- regex/std::regex_constants::error_space
- regex/std::regex_constants::error_badrepeat
- regex/std::regex_constants::error_complexity
- regex/std::regex_constants::error_stack
- regex/std::regex_constants::error_parse
- regex/std::regex_constants::error_syntax
- regex/std::regex_constants::match_default
- regex/std::regex_constants::match_not_bol
- regex/std::regex_constants::match_not_eol
- regex/std::regex_constants::match_not_bow
- regex/std::regex_constants::match_not_eow
- regex/std::regex_constants::match_any
- regex/std::regex_constants::match_not_null
- regex/std::regex_constants::match_continuous
- regex/std::regex_constants::match_prev_avail
- regex/std::regex_constants::format_default
- regex/std::regex_constants::format_sed
- regex/std::regex_constants::format_no_copy
- regex/std::regex_constants::format_first_only
- regex/std::regex_constants::ECMAScript
- regex/std::regex_constants::basic
- regex/std::regex_constants::extended
- regex/std::regex_constants::awk
- regex/std::regex_constants::grep
- regex/std::regex_constants::egrep
- regex/std::regex_constants::icase
- regex/std::regex_constants::nosubs
- regex/std::regex_constants::optimize
- regex/std::regex_constants::collate
helpviewer_keywords:
- std::regex_constants [C++]
- std::regex_constants [C++], error_collate
- std::regex_constants [C++], error_ctype
- std::regex_constants [C++], error_escape
- std::regex_constants [C++], error_backref
- std::regex_constants [C++], error_brack
- std::regex_constants [C++], error_paren
- std::regex_constants [C++], error_brace
- std::regex_constants [C++], error_badbrace
- std::regex_constants [C++], error_range
- std::regex_constants [C++], error_space
- std::regex_constants [C++], error_badrepeat
- std::regex_constants [C++], error_complexity
- std::regex_constants [C++], error_stack
- std::regex_constants [C++], error_parse
- std::regex_constants [C++], error_syntax
- std::regex_constants [C++], match_default
- std::regex_constants [C++], match_not_bol
- std::regex_constants [C++], match_not_eol
- std::regex_constants [C++], match_not_bow
- std::regex_constants [C++], match_not_eow
- std::regex_constants [C++], match_any
- std::regex_constants [C++], match_not_null
- std::regex_constants [C++], match_continuous
- std::regex_constants [C++], match_prev_avail
- std::regex_constants [C++], format_default
- std::regex_constants [C++], format_sed
- std::regex_constants [C++], format_no_copy
- std::regex_constants [C++], format_first_only
- std::regex_constants [C++], ECMAScript
- std::regex_constants [C++], basic
- std::regex_constants [C++], extended
- std::regex_constants [C++], awk
- std::regex_constants [C++], grep
- std::regex_constants [C++], egrep
- std::regex_constants [C++], icase
- std::regex_constants [C++], nosubs
- std::regex_constants [C++], optimize
- std::regex_constants [C++], collate
ms.assetid: 4a69c0ba-c46d-46e4-bd29-6f4efb805f26
ms.openlocfilehash: c8abca8109db9c781d63721b795feb01161fdb40
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451665"
---
# <a name="regexconstants-namespace"></a>regex_constants (Espacio de nombres)

Espacio de nombres para las marcas de expresiones regulares.

## <a name="syntax"></a>Sintaxis

```cpp
namespace regex_constants {
    enum syntax_option_type;
    enum match_flag_type;
    enum error_type;
}
```

## <a name="remarks"></a>Comentarios

El espacio de nombres `regex_constants` encapsula varios tipos de marca y sus valores de marca asociados.

|||
|-|-|
|[error_type](#error_type)|Marcas para notificar errores de sintaxis de expresión regular.|
|[match_flag_type](#match_flag_type)|Marcadores para las opciones de coincidencia de expresión regular.|
|[syntax_option_type](#syntax_option_type)|Marcas para seleccionar las opciones de sintaxis.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<regex>

**Espacio de nombres:** std

## <a name="error_type"></a> regex_constants::error_type

Marcas para notificar errores de sintaxis de expresión regular.

```cpp
enum error_type
    {    // identify error
    error_collate,
    error_ctype,
    error_escape,
    error_backref,
    error_brack,
    error_paren,
    error_brace,
    error_badbrace,
    error_range,
    error_space,
    error_badrepeat,
    error_complexity,
    error_stack,
    error_parse,
    error_syntax
    };
```

### <a name="remarks"></a>Comentarios

El tipo es un tipo enumerado que describe un objeto que puede contener marcadores de error. Los diferentes valores de marca son:

`error_backref`: la expresión contenía una referencia inversa no válida

`error_badbrace`: la expresión contenía un recuento no válido en una expresión { }

`error_badrepeat`: una expresión de repetición (uno de "*", '', "+", "{" en la mayoría de los contextos) no estaba precedida por una expresión

`error_brace`: la expresión contenía un "{" o un "}" desemparejado

`error_brack`: la expresión contenía un "[" o un "]" desemparejado

`error_collate`: la expresión contenía un nombre de elemento de intercalación no válido

`error_complexity`: error en intento de coincidencia porque era demasiado compleja

`error_ctype`: la expresión contenía un nombre de clase de carácter no válido

`error_escape`: la expresión contenía una secuencia de escape no válido

`error_paren`: la expresión contenía un "(" o un ")" desemparejado

`error_parse`: la expresión no se pudo analizar

`error_range`: la expresión contenía un especificador de rango de carácter no válido

`error_space`: error al analizar una expresión regular porque no había suficientes recursos disponibles

`error_stack`: error en intento de coincidencia porque no había suficiente memoria disponible

`error_syntax`: error en el análisis de un error de sintaxis

`error_backref`: la expresión contenía una referencia inversa no válida

## <a name="match_flag_type"></a> regex_constants::match_flag_type

Marcadores para las opciones de coincidencia de expresión regular.

```cpp
enum match_flag_type
    {    // specify matching and formatting rules
    match_default = 0x0000,
    match_not_bol = 0x0001,
    match_not_eol = 0x0002,
    match_not_bow = 0x0004,
    match_not_eow = 0x0008,
    match_any = 0x0010,
    match_not_null = 0x0020,
    match_continuous = 0x0040,
    match_prev_avail = 0x0100,
    format_default = 0x0000,
    format_sed = 0x0400,
    format_no_copy = 0x0800,
    format_first_only = 0x1000,
    _Match_not_null = 0x2000
    };
```

### <a name="remarks"></a>Comentarios

El tipo es un tipo de máscara de bits que describe las opciones que se van a usar al buscar coincidencias entre una secuencia de texto y una expresión regular, así como las marcas de formato que se usarán al reemplazar texto. Las opciones pueden combinarse con `|`.

Las opciones de coincidencia son las siguientes:

`match_default`

`match_not_bol`: no tratar la primera posición de la secuencia de destino como el principio de una línea

`match_not_eol`: no tratar la posición más allá del final de la secuencia de destino como el final de una línea

`match_not_bow`: no tratar la primera posición de la secuencia de destino como el principio de una palabra

`match_not_eow`: no tratar la posición más allá del final de la secuencia de destino como el final de una palabra

`match_any`: si se permite más de una coincidencia, cualquier coincidencia es aceptable

`match_not_null`: no tratar una subsecuencia vacía como una coincidencia

`match_continuous`: solo buscar coincidencias en el principio de la secuencia de destino

`match_prev_avail` -- `--first` es un iterador válido; omitir las opciones `match_not_bol` y `match_not_bow` si están establecidas

Las marcas de formato son las siguientes:

`format_default`: usar reglas de formato de ECMAScript

`format_sed`: usar reglas de formato usadas

`format_no_copy`: no copiar texto que no coincide con la expresión regular

`format_first_only`: no buscar coincidencias después de la primera

## <a name="syntax_option_type"></a> regex_constants::syntax_option_type

Marcas para seleccionar las opciones de sintaxis.

```cpp
enum syntax_option_type
    {    // specify RE syntax rules
    ECMAScript = 0x01,
    basic = 0x02,
    extended = 0x04,
    awk = 0x08,
    grep = 0x10,
    egrep = 0x20,
    _Gmask = 0x3F,

    icase = 0x0100,
    nosubs = 0x0200,
    optimize = 0x0400,
    collate = 0x0800
    };
```

### <a name="remarks"></a>Comentarios

El tipo es un tipo de máscara de bits que describe los especificadores de idioma y los modificadores de sintaxis que se usarán al compilar una expresión regular. Las opciones pueden combinarse con `|`. Debe usarse un especificador de idioma a la vez.

Los especificadores de idioma son:

`ECMAScript`: compila como ECMAScript

`basic`: compila como BRE

`extended`: compila como ERE

`awk`: compila como awk

`grep`: compila como grep

`egrep`: compila como egrep

Los modificadores de sintaxis son los siguientes:

`icase`: genera coincidencias sin distinción entre mayúsculas y minúsculas

`nosubs`: no es necesario que la implementación haga un seguimiento de los contenidos de los grupos de captura

`optimize`: la implementación debe dar prioridad a la velocidad de coincidencia, en lugar de la velocidad de compilación de expresiones regulares

`collate`: genera coincidencias dependientes de la configuración regional

## <a name="see-also"></a>Vea también

[\<regex>](../standard-library/regex.md)\
[Clase regex_error](../standard-library/regex-error-class.md)\
[\<funciones regex >](../standard-library/regex-functions.md)\
[Clase regex_iterator](../standard-library/regex-iterator-class.md)\
[\<operadores regex >](../standard-library/regex-operators.md)\
[Clase regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Clase regex_traits](../standard-library/regex-traits-class.md)\
[Definiciones de tipo \<regex>](../standard-library/regex-typedefs.md)
