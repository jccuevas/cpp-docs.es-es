---
title: _bstr_t::operator +=, +
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
ms.openlocfilehash: 0a2c374fc160a0575e0a17cc85ab51c65fa9392a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646139"
---
# <a name="bstrtoperator--"></a>_bstr_t::operator +=, +

**Específicos de Microsoft**

Anexa los caracteres al final del objeto `_bstr_t` o concatena dos cadenas.

## <a name="syntax"></a>Sintaxis

```
_bstr_t& operator+=( const _bstr_t& s1 );
_bstr_t operator+( const _bstr_t& s1 );
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);
```

#### <a name="parameters"></a>Parámetros

*s1*<br/>
Un objeto `_bstr_t`.

*s2*<br/>
Cadena multibyte.

*S3*<br/>
Cadena Unicode.

## <a name="remarks"></a>Comentarios

Estos operadores realizan la concatenación de cadenas:

- **Operator += (***s1***)** anexa los caracteres de encapsulado `BSTR` de *s1* al final de encapsulado esteobjeto`BSTR`.

- **Operator + (***s1***)** devuelve el nuevo `_bstr_t` que se forma concatenando este objeto `BSTR` con el de *s1*.

- **Operator + (***s2***&#124;***s1***)** devuelve un nuevo `_bstr_t` que se forma concatenando una cadena multibyte *s2*, convertido a Unicode, con el `BSTR` encapsulada en *s1*.

- **Operator + (***s3* **,***s1***)** devuelve un nuevo `_bstr_t` que se forma concatenando una cadena Unicode *s3* con el `BSTR` encapsulada en *s1*.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)