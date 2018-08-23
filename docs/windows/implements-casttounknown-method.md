---
title: Casttounknown (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: ca3324f7-4136-406b-8698-7389f4f3d3c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 988580a34c030c84c50adfff2741408be4b249cd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586363"
---
# <a name="implementscasttounknown-method"></a>Implements::CastToUnknown (Método)

Obtiene un puntero subyacente `IUnknown` interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
__forceinline IUnknown* CastToUnknown();
```

## <a name="return-value"></a>Valor devuelto

Esta operación siempre se realiza correctamente y devuelve el `IUnknown` puntero.

## <a name="remarks"></a>Comentarios

Función auxiliar interno.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Implements (estructura)](../windows/implements-structure.md)