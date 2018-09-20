---
title: Argtraits constante | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits::args
dev_langs:
- C++
helpviewer_keywords:
- args constant
ms.assetid: a68100ab-254b-4571-a0bc-946f1633a46b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 504909cba41588c0ccefccabfbd541a39d4327b2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387352"
---
# <a name="argtraitsargs-constant"></a>ArgTraits::args (Constante)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
static const int args = -1; ;
```

## <a name="remarks"></a>Comentarios

Mantiene un recuento del número de parámetros el `Invoke` al método de interfaz de un delegado.

## <a name="remarks"></a>Comentarios

Cuando **args** es igual a -1 indica que no puede haber ninguna coincidencia para el `Invoke` firma del método.

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[ArgTraits (estructura)](../windows/argtraits-structure.md)<br/>
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)