---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: 0cd300a09c29668c496d93109d1bc862947e948c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187562"
---
# <a name="_variant_tsetstring"></a>_variant_t::SetString

**Específicos de Microsoft**

Asigna una cadena a este objeto `_variant_t`.

## <a name="syntax"></a>Sintaxis

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>Parámetros

*pSrc*<br/>
Puntero a la cadena de caracteres.

## <a name="remarks"></a>Observaciones

Convierte una cadena de caracteres ANSI en una cadena `BSTR` Unicode y la asigna a este objeto `_variant_t`.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_variant_t (Clase)](../cpp/variant-t-class.md)
