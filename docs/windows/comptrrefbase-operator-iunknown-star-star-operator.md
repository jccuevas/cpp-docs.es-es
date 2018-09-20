---
title: 'Comptrrefbase:: operator IUnknown ** (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
dev_langs:
- C++
helpviewer_keywords:
- operator IUnknown** operator
ms.assetid: c2950abf-a7aa-480a-ba41-615703e7f931
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 839b0220497db7ff0355ea7ed3ab923126e3175e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420938"
---
# <a name="comptrrefbaseoperator-iunknown-operator"></a>ComPtrRefBase::operator IUnknown** (Operador)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
operator IUnknown**() const;
```

## <a name="remarks"></a>Comentarios

Convierte la actual [ptr_](../windows/comptrrefbase-ptr-data-member.md) miembro de datos a un puntero-a-a-puntero-to del `IUnknown` interfaz.

Se genera un error si el actual **ComPtrRefBase** no se deriva de `IUnknown`.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[ComPtrRefBase (clase)](../windows/comptrrefbase-class.md)<br/>
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)