---
title: _bstr_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator=
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
ms.openlocfilehash: 5b7f499dd84a67020232aab84966647378daadad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181075"
---
# <a name="_bstr_toperator-"></a>_bstr_t::operator =

**Específicos de Microsoft**

Asigna un nuevo valor a un objeto `_bstr_t` existente.

## <a name="syntax"></a>Sintaxis

```
_bstr_t& operator=(const _bstr_t& s1) throw ( );
_bstr_t& operator=(const char* s2);
_bstr_t& operator=(const wchar_t* s3);
_bstr_t& operator=(const _variant_t& var);
```

#### <a name="parameters"></a>Parámetros

*s1*<br/>
Un objeto `_bstr_t` que se va a asignar a un objeto `_bstr_t` existente.

*s2*<br/>
Una cadena multibyte que se va a asignar a un objeto `_bstr_t` existente.

*S3*<br/>
Una cadena Unicode que se va a asignar a un objeto `_bstr_t` existente.

*var*<br/>
Un objeto `_variant_t` que se va a asignar a un objeto `_bstr_t` existente.

**FIN de Específicos de Microsoft**

## <a name="example"></a>Ejemplo

Vea [_bstr_t:: Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo de uso del **operador =** .

## <a name="see-also"></a>Consulte también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)
