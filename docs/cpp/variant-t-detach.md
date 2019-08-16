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
ms.openlocfilehash: 8426c80af04b2c0906af150ea3e91304335e9f69
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500560"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Específicos de Microsoft**

Desasocia el `VARIANT` objeto encapsulado de este `_variant_t` objeto.

## <a name="syntax"></a>Sintaxis

```
VARIANT Detach( );
```

## <a name="return-value"></a>Valor devuelto

Encapsulado `VARIANT`.

## <a name="remarks"></a>Comentarios

Extrae y devuelve el encapsulado `VARIANT`y, a continuación, borra este `_variant_t` objeto sin destruirlo. Esta función miembro quita de `VARIANT` la encapsulación de y establece `VARTYPE` el de `_variant_t` este objeto en VT_EMPTY. Depende de usted que libere el devuelto `VARIANT` mediante una llamada a la función [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) .

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_variant_t (Clase)](../cpp/variant-t-class.md)