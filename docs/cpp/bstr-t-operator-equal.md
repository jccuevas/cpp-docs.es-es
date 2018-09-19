---
title: _bstr_t::operator = | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35778fe3bdf75738f67b280cbbe4c8ceeb498634
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017006"
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

*S3*<br/>
Una cadena Unicode que se va a asignar a un objeto `_bstr_t` existente.

*var*<br/>
Un objeto `_variant_t` que se va a asignar a un objeto `_bstr_t` existente.

**FIN de Específicos de Microsoft**

## <a name="example"></a>Ejemplo

Consulte [_bstr_t:: Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo del uso de **operador =**.

## <a name="see-also"></a>Vea también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)