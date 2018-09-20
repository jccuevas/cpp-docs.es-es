---
title: 'Comptrref:: operator == (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator==
dev_langs:
- C++
ms.assetid: 95fcf781-b473-4317-88cd-e938778d3c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78daa0ad22ad3bb6a63900d4c2f69d5eafb5cb6b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372128"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator== (Operador)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)  
);

bool operator==(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator==(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Parámetros

*a*<br/>
Una referencia a un **ComPtrRef** objeto.

*b*<br/>
Una referencia a otro **ComPtrRef** objeto o un puntero a un tipo anónimo (`void*`).

## <a name="return-value"></a>Valor devuelto

El primer rendimientos de operador **true** si objeto *un* es igual al objeto *b*; en caso contrario, **false**.

Los operadores de la segundo y terceros yield **true** si objeto *un* es igual a **nullptr**; en caso contrario, **false**.

El cuarto y quinto operadores producen **true** si objeto *un* es igual al objeto *b*; en caso contrario, **false**.

## <a name="remarks"></a>Comentarios

Indica si dos **ComPtrRef** objetos son iguales.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)<br/>
[ComPtrRef (clase)](../windows/comptrref-class.md)