---
title: 'Comptrrefbase:: operator IInspectable ** (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
dev_langs:
- C++
helpviewer_keywords:
- operator IInspectable** operator
ms.assetid: 06ac1051-606c-449b-a566-cac78ca53762
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f711a9d1f5fe92e5f35bf333fc0b3473fc0eebf4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604411"
---
# <a name="comptrrefbaseoperator-iinspectable-operator"></a>Comptrrefbase:: operator IInspectable\* \* operador

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
operator IInspectable**() const;
```

## <a name="remarks"></a>Comentarios

Convierte la actual [ptr_](../windows/comptrrefbase-ptr-data-member.md) miembro de datos a un puntero-a-a-puntero-to del `IInspectable` interfaz.

Se genera un error si el actual **ComPtrRefBase** no se deriva de `IInspectable`.

En esta difusión está disponible solo si `__WRL_CLASSIC_COM__` está definido.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[ComPtrRefBase (clase)](../windows/comptrrefbase-class.md)  
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)