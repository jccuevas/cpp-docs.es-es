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
ms.openlocfilehash: c2283158856a6781ab2e12c51f4e2ad0e4f1d531
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750727"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**Microsoft Specific**

Cambia el tipo `_variant_t` del objeto `VARTYPE`al archivo .

## <a name="syntax"></a>Sintaxis

```cpp
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>Parámetros

*Vartype*<br/>
El `VARTYPE` para `_variant_t` este objeto.

*pSrc*<br/>
Un puntero al objeto `_variant_t` que se va a convertir. Si este valor es NULL, la conversión se realiza en contexto.

## <a name="remarks"></a>Observaciones

Esta función miembro `_variant_t` convierte un `VARTYPE`objeto en el archivo . Si *pSrc* es NULL, la conversión `_variant_t` se realiza en su lugar, de lo contrario este objeto se copia de *pSrc* y, a continuación, se convierte.

**END Microsoft Specific**

## <a name="see-also"></a>Vea también

[Clase _variant_t](../cpp/variant-t-class.md)
