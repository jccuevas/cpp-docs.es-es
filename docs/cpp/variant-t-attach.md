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
ms.openlocfilehash: 3792ed4d0fcd86c4a4e846771c450413fda130b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187770"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**Específicos de Microsoft**

Adjunta un objeto `VARIANT` al objeto **_variant_t** .

## <a name="syntax"></a>Sintaxis

```
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>Parámetros

*varSrc*<br/>
Objeto `VARIANT` que se va a adjuntar a este objeto **_variant_t** .

## <a name="remarks"></a>Observaciones

Toma posesión del `VARIANT` mediante su encapsulado. Esta función miembro libera cualquier `VARIANT`encapsulado existente y, a continuación, copia el `VARIANT`proporcionado y establece su `VARTYPE` en VT_EMPTY para asegurarse de que sus recursos solo pueden ser liberados por el destructor **_variant_t** .

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_variant_t (Clase)](../cpp/variant-t-class.md)
