---
title: CloakedIid (estructura)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
ms.openlocfilehash: 10dc2af1897147045382e8463b6602fa015fc899
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033728"
---
# <a name="cloakediid-structure"></a>CloakedIid (estructura)

Indica a la `RuntimeClass`, `Implements` y `ChainInterfaces` plantillas que la interfaz especificada no es accesible en la lista IID.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T>
struct CloakedIid : T;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La interfaz que está oculto (escondida).

## <a name="remarks"></a>Comentarios

El siguiente es un ejemplo de cómo **CloakedIid** sirve: `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`T`

`CloakedIid`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (Espacio de nombres)](microsoft-wrl-namespace.md)