---
title: _variant_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
ms.openlocfilehash: 4b19e3c1615912550cdf1eb6a2b0b3f906ee4af9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522335"
---
# <a name="varianttdetach"></a>_variant_t::Detach

**Específicos de Microsoft**

Desasocia el objeto encapsulado `VARIANT` objeto desde este `_variant_t` objeto.

## <a name="syntax"></a>Sintaxis

```
VARIANT Detach( );
```

## <a name="return-value"></a>Valor devuelto

Encapsulado `VARIANT`.

## <a name="remarks"></a>Comentarios

Extrae y devuelve encapsulado `VARIANT`, a continuación, borra este `_variant_t` objeto sin destruirlo. Esta función miembro quita el `VARIANT` de encapsulación y establece el `VARTYPE` esto `_variant_t` objeto en VT_EMPTY. Depende de usted para liberar el valor devuelto `VARIANT` mediante una llamada a la [VariantClear](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantclear) función.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_variant_t (Clase)](../cpp/variant-t-class.md)