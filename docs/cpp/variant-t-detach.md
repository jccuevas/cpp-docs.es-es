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
ms.openlocfilehash: 719852c4556291747b612d54c44d4bf82caa9188
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165936"
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

Extrae y devuelve encapsulado `VARIANT`, a continuación, borra este `_variant_t` objeto sin destruirlo. Esta función miembro quita el `VARIANT` de encapsulación y establece el `VARTYPE` esto `_variant_t` objeto en VT_EMPTY. Depende de usted para liberar el valor devuelto `VARIANT` mediante una llamada a la [VariantClear](/windows/desktop/api/oleauto/nf-oleauto-variantclear) función.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_variant_t (Clase)](../cpp/variant-t-class.md)