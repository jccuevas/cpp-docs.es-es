---
title: 'Comptr:: operator! = (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator!=
dev_langs:
- C++
ms.assetid: 63647240-dec7-4eb9-9272-96c07d01493c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4874121f22daa8e4a13bf7a1d332c9b8e3db60ba
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42578112"
---
# <a name="comptroperator-operator"></a>ComPtr::operator!= (Operador)

Indica si dos **ComPtr** objetos no son iguales.

## <a name="syntax"></a>Sintaxis

```cpp
bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)  
);

bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>Parámetros

*a*  
Una referencia a un **ComPtr** objeto.

*b*  
Una referencia a otro **ComPtr** objeto.

## <a name="return-value"></a>Valor devuelto

El primer rendimientos de operador **true** si objeto *un* no es igual al objeto *b*; en caso contrario, **false**.

Los operadores de la segundo y terceros yield **true** si objeto *un* no es igual a **nullptr**; en caso contrario, **false**.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)  
[ComPtr (clase)](../windows/comptr-class.md)