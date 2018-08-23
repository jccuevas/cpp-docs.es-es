---
title: Método Criticalsectiontraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- GetInvalidValue method
ms.assetid: 665f30a6-ca9c-4968-8c03-8f84e6b2329b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4a23445cc9df0553a40d4f78a7ce3095a343d5d0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599241"
---
# <a name="criticalsectiontraitsgetinvalidvalue-method"></a>CriticalSectionTraits::GetInvalidValue (Método)

Se especializa un **CriticalSection** plantilla para que la plantilla no siempre es válida.

## <a name="syntax"></a>Sintaxis

```cpp
inline static Type GetInvalidValue();
```

## <a name="return-value"></a>Valor devuelto

Siempre devuelve un puntero a una sección crítica no válida.

## <a name="remarks"></a>Comentarios

El `Type` modificador se define como `typedef CRITICAL_SECTION* Type;`.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** handletraits

## <a name="see-also"></a>Vea también

[CriticalSectionTraits (estructura)](../windows/criticalsectiontraits-structure.md)