---
title: _variant_t::Attach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e680f4f42881ea89510048f43d657d1579686527
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109267"
---
# <a name="varianttattach"></a>_variant_t::Attach

**Específicos de Microsoft**

Asocia un `VARIANT` objeto en el **_variant_t** objeto.

## <a name="syntax"></a>Sintaxis

```
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>Parámetros

*varSrc*<br/>
Un `VARIANT` se adjuntará a este objeto **_variant_t** objeto.

## <a name="remarks"></a>Comentarios

Toma posesión de la `VARIANT` encapsulándolo. Esta función miembro libera cualquier encapsulado existente `VARIANT`, a continuación, copia proporcionado `VARIANT`y establece su `VARTYPE` en VT_EMPTY para asegurarse de que sólo se pueden liberar sus recursos por la **_variant_t** destructor.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_variant_t (Clase)](../cpp/variant-t-class.md)