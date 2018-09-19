---
title: Método Makeallocator | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
dev_langs:
- C++
helpviewer_keywords:
- Allocate method
ms.assetid: a01997bc-4ff1-4ed0-9def-e4aaa15b0598
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4422dea0b0bfb07904d0c4defad8f33281a51bec
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609867"
---
# <a name="makeallocatorallocate-method"></a>MakeAllocator::Allocate (Método)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
__forceinline void* Allocate();
```

## <a name="return-value"></a>Valor devuelto

Si es correcto, un puntero a la memoria asignada; en caso contrario, **nullptr**.

## <a name="remarks"></a>Comentarios

Asigna memoria y lo asocia con el actual **MakeAllocator** objeto.

El tamaño de la memoria asignada es el tamaño del tipo especificado por el actual **MakeAllocator** parámetro de plantilla.

Un desarrollador necesita sobrescribir sólo el **Allocate()** método para implementar un modelo de asignación de memoria diferente.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[MakeAllocator (clase)](../windows/makeallocator-class.md)  
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)