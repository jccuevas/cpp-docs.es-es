---
title: regex_error (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
dev_langs:
- C++
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7358af41e1a7172daec619bec3e701ff4541fd0c
ms.sourcegitcommit: 27b5712badd09a09c499d887e2e4cf2208a28603
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2018
ms.locfileid: "44384987"
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

|Constructor|Descripción|
|-|-|
|[regex_error](#regex_error)|Construye el objeto.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[Código](#code)|Devuelve el código de error.|

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

*Error*<br/>
Código de error.

### <a name="remarks"></a>Comentarios

El constructor crea un objeto que contiene el valor *error*.

## <a name="see-also"></a>Vea también

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants (Clase)](../standard-library/regex-constants-class.md)<br/>
[Funciones de \<regex>](../standard-library/regex-functions.md)<br/>
[regex_iterator (Clase)](../standard-library/regex-iterator-class.md)<br/>
[Operadores de \<regex>](../standard-library/regex-operators.md)<br/>
[regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits (Clase)](../standard-library/regex-traits-class.md)<br/>
[Definiciones de tipo \<regex>](../standard-library/regex-typedefs.md)<br/>
