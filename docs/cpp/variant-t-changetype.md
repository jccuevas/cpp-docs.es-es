---
title: _variant_t::ChangeType
ms.date: 11/04/2016
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
ms.openlocfilehash: 319c4fde808932e86021ee59b051261c43ca2edd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471245"
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType

**Específicos de Microsoft**

Cambia el tipo de la `_variant_t` objeto del `VARTYPE`.

## <a name="syntax"></a>Sintaxis

```
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>Parámetros

*VarType*<br/>
El `VARTYPE` para este `_variant_t` objeto.

*pSrc*<br/>
Un puntero al objeto `_variant_t` que se va a convertir. Si este valor es NULL, la conversión se realiza en su lugar.

## <a name="remarks"></a>Comentarios

Esta función miembro convierte un `_variant_t` objeto indicado `VARTYPE`. Si *pSrc* es NULL, la conversión se realiza en su lugar, en caso contrario `_variant_t` se copia el objeto de *pSrc* y, a continuación, puede convertir.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_variant_t (Clase)](../cpp/variant-t-class.md)