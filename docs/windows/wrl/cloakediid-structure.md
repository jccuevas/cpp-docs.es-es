---
title: CloakedIid (estructura)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
ms.openlocfilehash: a47b9e5fdb4a6e7f49b9704244b4e62e3647a04e
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337502"
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

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)