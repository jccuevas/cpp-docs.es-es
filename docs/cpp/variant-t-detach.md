---
title: _variant_t::Detach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
dev_langs:
- C++
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ab1e4f83025dcc3e4bc65274746e0617cf31b5b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065028"
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