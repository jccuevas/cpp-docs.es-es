---
title: _variant_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
ms.openlocfilehash: d0822dfc730cbbb64f8364e6fa8fe8bc7207f9f9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750743"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**Microsoft Specific**

Asocia un `VARIANT` objeto al objeto **_variant_t.**

## <a name="syntax"></a>Sintaxis

```cpp
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>Parámetros

*varSrc*<br/>
Objeto `VARIANT` que se va a adjuntar a este **objeto _variant_t.**

## <a name="remarks"></a>Observaciones

Toma la `VARIANT` propiedad de la encapsulando. Esta función miembro libera `VARIANT`cualquier encapsulado `VARIANT`existente y, a continuación, copia el proporcionado y establece su `VARTYPE` en VT_EMPTY para asegurarse de que sus recursos solo se pueden liberar por el destructor **_variant_t.**

**END Microsoft Specific**

## <a name="see-also"></a>Vea también

[Clase _variant_t](../cpp/variant-t-class.md)
