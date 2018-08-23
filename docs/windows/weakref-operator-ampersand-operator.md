---
title: 'Weakref:: operator&amp; operador | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 900afb73-3801-4d08-9b41-2e6a62011ccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f8bb81ca1591fc398b1d0814fca918309169e82c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600989"
---
# <a name="weakrefoperatoramp-operator"></a>Weakref:: operator&amp; operador

Devuelve un `ComPtrRef` objeto que representa el actual **WeakRef** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()  
```

## <a name="return-value"></a>Valor devuelto

Un `ComPtrRef` objeto que representa el actual **WeakRef** objeto.

## <a name="remarks"></a>Comentarios

Se trata de un operador de aplicación auxiliar interna que no está pensado para usarse en el código.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[WeakRef (clase)](../windows/weakref-class.md)