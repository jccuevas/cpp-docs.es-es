---
title: _bstr_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator=
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
ms.openlocfilehash: 97f0100d8a34253f3a1375d34b887d3d31a77f43
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350876"
---
# <a name="bstrtoperator-"></a>_bstr_t::operator =

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

*s3*<br/>
Una cadena Unicode que se va a asignar a un objeto `_bstr_t` existente.

*var*<br/>
Un objeto `_variant_t` que se va a asignar a un objeto `_bstr_t` existente.

**FIN de Específicos de Microsoft**

## <a name="example"></a>Ejemplo

Consulte [_bstr_t:: Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo del uso de **operador =**.

## <a name="see-also"></a>Vea también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)