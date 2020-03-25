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
ms.openlocfilehash: b0692c9befaa6b7e787ada624dcbb56b074c9f9d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160468"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**Específicos de Microsoft**

Cambia el tipo del objeto `_variant_t` a la `VARTYPE`indicada.

## <a name="syntax"></a>Sintaxis

```
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>Parámetros

*VarType*<br/>
`VARTYPE` para este objeto `_variant_t`.

*pSrc*<br/>
Un puntero al objeto `_variant_t` que se va a convertir. Si este valor es NULL, la conversión se realiza en contexto.

## <a name="remarks"></a>Observaciones

Esta función miembro convierte un objeto `_variant_t` en el `VARTYPE`indicado. Si *pSrc* es null, la conversión se realiza en contexto; en caso contrario, este objeto `_variant_t` se copia de *pSrc* y, a continuación, se convierte.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_variant_t (Clase)](../cpp/variant-t-class.md)
