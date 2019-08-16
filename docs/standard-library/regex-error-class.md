---
title: regex_error (Clase)
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
ms.openlocfilehash: 52b6bfd74a08200f7d924d2601b85718a941dd85
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451653"
---
# <a name="regexerror-class"></a>regex_error (Clase)

Informa de un objeto basic_regex incorrecto.

## <a name="syntax"></a>Sintaxis

```cpp
class regex_error
: public std::runtime_error
```

## <a name="remarks"></a>Comentarios

La clase describe un objeto de excepción que se produce para notificar un error en la construcción o el uso de un objeto `basic_regex` .

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[regex_error](#regex_error)|Construye el objeto.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[code](#code)|Devuelve el código de error.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<regex>

**Espacio de nombres:** std

## <a name="example"></a>Ejemplo

```cpp
// std__regex__regex_error.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex_error paren(std::regex_constants::error_paren);

    try
        {
        std::regex rx("(a");
        }
    catch (const std::regex_error& rerr)
        {
        std::cout << "regex error: "
            << (rerr.code() == paren.code() ? "unbalanced parentheses" : "")
            << std::endl;
        }
    catch (...)
        {
        std::cout << "unknown exception" << std::endl;
        }

    return (0);
    }
```

```Output
regex error: unbalanced parentheses
```

## <a name="code"></a> regex_error::code

Devuelve el código de error.

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el valor que se pasó al constructor del objeto.

## <a name="regex_error"></a> regex_error::regex_error

Construye el objeto.

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>Parámetros

*error*\
Código de error.

### <a name="remarks"></a>Comentarios

El constructor crea un objeto que contiene el valor de *error*.

## <a name="see-also"></a>Vea también

[\<regex>](../standard-library/regex.md)\
[Clase regex_constants](../standard-library/regex-constants-class.md)\
[\<funciones regex >](../standard-library/regex-functions.md)\
[Clase regex_iterator](../standard-library/regex-iterator-class.md)\
[\<operadores regex >](../standard-library/regex-operators.md)\
[Clase regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Clase regex_traits](../standard-library/regex-traits-class.md)\
[Definiciones de tipo \<regex>](../standard-library/regex-typedefs.md)
