---
title: 'Comptr:: operator == (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator==
dev_langs:
- C++
ms.assetid: 6a26e936-29d4-4b7d-b44a-7c575ad07509
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2e0fd86cb8a9c9fa86da0a1781f49fe57c5ce6d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394450"
---
# <a name="comptroperator-operator"></a>ComPtr::operator== (Operador)

Indica si dos **ComPtr** objetos son iguales.

## <a name="syntax"></a>Sintaxis

```cpp
bool operator==(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator==(
   const ComPtr<T>& a,
   decltype(__nullptr)  
);

bool operator==(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>Parámetros

*a*<br/>
Una referencia a un **ComPtr** objeto.

*b*<br/>
Una referencia a otro **ComPtr** objeto.

## <a name="return-value"></a>Valor devuelto

El primer rendimientos de operador **true** si objeto *un* es igual al objeto *b*; en caso contrario, **false**.

Los operadores de la segundo y terceros yield **true** si objeto *un* es igual a **nullptr**; en caso contrario, **false**.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)<br/>
[ComPtr (clase)](../windows/comptr-class.md)