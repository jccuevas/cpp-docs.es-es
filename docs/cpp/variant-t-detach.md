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
ms.openlocfilehash: 9737db6b77483fa55e1dad90b9464752cd8537a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187744"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Específicos de Microsoft**

Desasocia el objeto `VARIANT` encapsulado de este objeto `_variant_t`.

## <a name="syntax"></a>Sintaxis

```
VARIANT Detach( );
```

## <a name="return-value"></a>Valor devuelto

`VARIANT`encapsulado.

## <a name="remarks"></a>Observaciones

Extrae y devuelve el `VARIANT`encapsulado y, a continuación, borra este objeto `_variant_t` sin destruirlo. Esta función miembro quita la `VARIANT` de la encapsulación y establece el `VARTYPE` de este objeto `_variant_t` en VT_EMPTY. Depende de usted liberar el `VARIANT` devuelto mediante una llamada a la función [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) .

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_variant_t (Clase)](../cpp/variant-t-class.md)
