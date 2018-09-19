---
title: Decrementstrongreference (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- DecrementStrongReference method
ms.assetid: 97d70d9f-41b8-4f8d-a6fa-4137cc4f9029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b3620a4b82aabb0058773f68938f545119f90791
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605603"
---
# <a name="weakreferencedecrementstrongreference-method"></a>WeakReference::DecrementStrongReference (Método)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
ULONG DecrementStrongReference();
```

## <a name="remarks"></a>Comentarios

Disminuye el recuento de la referencia segura del actual **WeakReference** objeto.

Cuando el recuento de referencia segura se convierte en cero, la referencia segura se establece en **nullptr**.

## <a name="return-value"></a>Valor devuelto

El recuento de referencia segura disminuye.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[WeakReference (clase)](../windows/weakreference-class1.md)  
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)