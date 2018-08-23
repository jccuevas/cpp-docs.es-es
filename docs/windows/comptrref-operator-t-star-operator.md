---
title: 'Comptrref:: operator T * operador | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator T*
dev_langs:
- C++
helpviewer_keywords:
- operator T* operator
ms.assetid: b4f83370-0ebc-4d56-87c6-1a8ea2d0079b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 54c370029b4e6fc90d1f210164de7d7ecb22f3a5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595424"
---
# <a name="comptrrefoperator-t-operator"></a>ComPtrRef::operator T* (Operador)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
operator T*();
```

## <a name="remarks"></a>Comentarios

Devuelve el valor de la [ptr_](../windows/comptrrefbase-ptr-data-member.md) miembro de datos del elemento actual **ComPtrRef** objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[ComPtrRef (clase)](../windows/comptrref-class.md)  
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)