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
ms.openlocfilehash: b9eddca85d66f4978e1b33299ca655cd880cf45e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181153"
---
# <a name="_bstr_toperator--"></a>_bstr_t::operator +=, +

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
Objeto `_bstr_t` .

*s2*<br/>
Cadena multibyte.

*S3*<br/>
Cadena Unicode.

## <a name="remarks"></a>Observaciones

Estos operadores realizan la concatenación de cadenas:

- **operador + = (**  *S1*  **)** Anexa los caracteres del `BSTR` encapsulado de *S1* al final del `BSTR`encapsulado de este objeto.

- **operador + (**  *S1*  **)** Devuelve el nuevo `_bstr_t` que se forma mediante la concatenación de la `BSTR` de este objeto con la de *S1*.

- **operador + (**  *S2*  **&#124;**  *S1*  **)** Devuelve un nuevo `_bstr_t` que se forma concatenando una cadena multibyte *S2*, convertida en Unicode, con la `BSTR` encapsulada en *S1*.

- **operador + (**  *S3* **,**  *S1*  **)** Devuelve un nuevo `_bstr_t` que se forma mediante la concatenación de una cadena Unicode *S3* con la `BSTR` encapsulada en *S1*.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)
