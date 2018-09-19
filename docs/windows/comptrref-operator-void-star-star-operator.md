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
ms.openlocfilehash: 468b38dac2082e47e94e4bd52af50d77327f5ef4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590694"
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

[ComPtrRef (clase)](../windows/comptrref-class.md)  
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)