---
title: Método Chaininterfaces | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e6dbc595714cbecf2ad13db13051866e31e5ebcd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42581063"
---
# <a name="chaininterfacesverify-method"></a>ChainInterfaces::Verify (Método)

Comprueba que cada interfaz definida por los parámetros de plantilla *I0* a través de *I9* hereda `IUnknown` o `IInspectable`y que *I0* hereda de *I1* a través de *I9*.

## <a name="syntax"></a>Sintaxis

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

## <a name="remarks"></a>Comentarios

Si se produce un error en la operación de comprobación, un **static_assert** emite un mensaje de error que describe el error.

Parámetros de plantilla *I0* y *I1* son necesarios y los parámetros *I2* a través de *I9* son opcionales.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[ChainInterfaces (estructura)](../windows/chaininterfaces-structure.md)