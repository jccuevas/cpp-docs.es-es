---
title: regex_error (Clase)
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
ms.openlocfilehash: f8f3c88c1b203ed7fcea148843fa99590e27b888
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331863"
---
# <a name="regex_error-class"></a>regex_error (Clase)

Informa de un objeto basic_regex incorrecto.

## <a name="syntax"></a>Sintaxis

```cpp
class regex_error
: public std::runtime_error
```

## <a name="remarks"></a>Observaciones

La clase describe un objeto de excepción que se produce para notificar un error en la construcción o el uso de un objeto `basic_regex` .

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[regex_error](#regex_error)|Construye el objeto.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[código](#code)|Devuelve el código de error.|

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

## <a name="regex_errorcode"></a><a name="code"></a>regex_error::código

Devuelve el código de error.

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve el valor que se pasó al constructor del objeto.

## <a name="regex_errorregex_error"></a><a name="regex_error"></a>regex_error::regex_error

Construye el objeto.

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>Parámetros

*Error*\
Código de error.

### <a name="remarks"></a>Observaciones

El constructor construye un objeto que contiene el *error*de valor .

## <a name="see-also"></a>Consulte también

[\<regex>](../standard-library/regex.md)\
[Clase regex_constants](../standard-library/regex-constants-class.md)\
[\<funciones de> regex](../standard-library/regex-functions.md)\
[Clase regex_iterator](../standard-library/regex-iterator-class.md)\
[\<operadores de> regex](../standard-library/regex-operators.md)\
[Clase regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Clase regex_traits](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
