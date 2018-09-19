---
title: _variant_t::SetString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::SetString
dev_langs:
- C++
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 52ea719a2c9296ca1e64d881ac150994c041e206
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018735"
---
# <a name="varianttsetstring"></a>_variant_t::SetString

**Específicos de Microsoft**

Asigna una cadena a este objeto `_variant_t`.

## <a name="syntax"></a>Sintaxis

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>Parámetros

*pSrc*<br/>
Puntero a la cadena de caracteres.

## <a name="remarks"></a>Comentarios

Convierte una cadena de caracteres ANSI en una cadena `BSTR` Unicode y la asigna a este objeto `_variant_t`.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_variant_t (Clase)](../cpp/variant-t-class.md)