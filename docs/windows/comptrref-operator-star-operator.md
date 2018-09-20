---
title: 'Operador de comptrref:: operator | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator*
dev_langs:
- C++
helpviewer_keywords:
- operator* operator
ms.assetid: 0287ca7a-4ce1-47f7-bab6-714fca3e04bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e2af57b698558a33115cfcfc20ebc7136e72dc6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400747"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator* (Operador)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
InterfaceType* operator *();
```

## <a name="return-value"></a>Valor devuelto

Puntero a la interfaz representada por el actual **ComPtrRef** objeto.

## <a name="remarks"></a>Comentarios

Recupera el puntero a la interfaz representada por el actual **ComPtrRef** objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[ComPtrRef (clase)](../windows/comptrref-class.md)<br/>
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)