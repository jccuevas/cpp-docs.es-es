---
title: 'Comptrref:: operator void ** (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
dev_langs:
- C++
helpviewer_keywords:
- operator void** operator
ms.assetid: f020045c-9de4-4392-8783-73f0fc0761c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 977e04b923a99cab3eb42544de99c4fcee974e82
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408874"
---
# <a name="comptrrefoperator-void-operator"></a>Comptrref:: operator void\* \* operador

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
operator void**() const;
```

## <a name="remarks"></a>Comentarios

Elimina la actual **ComPtrRef** de objetos, convierte el puntero a la interfaz que se ha representado por la **ComPtrRef** objeto como un puntero-a-puntero-to **void**y, a continuación, Devuelve el puntero de conversión.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[ComPtrRef (clase)](../windows/comptrref-class.md)<br/>
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)