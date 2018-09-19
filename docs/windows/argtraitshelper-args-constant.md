---
title: Argtraitshelper constante | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper::args
dev_langs:
- C++
helpviewer_keywords:
- args constant
ms.assetid: 1c0efa32-c072-43e3-bbd9-a3f6aec069a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e4817d0f0082ef4ec0a9a588982405772d733fe0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598037"
---
# <a name="argtraitshelperargs-constant"></a>ArgTraitsHelper::args (Constante)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
static const int args = Traits::args;
```

## <a name="remarks"></a>Comentarios

Ayuda a [Argtraitshelper](../windows/argtraitshelper-args-constant.md) mantener el recuento del número de parámetros en el `Invoke` al método de interfaz de un delegado.

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[ArgTraitsHelper (estructura)](../windows/argtraitshelper-structure.md)  
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)