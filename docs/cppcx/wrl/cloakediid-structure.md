---
title: CloakedIid (estructura)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
ms.openlocfilehash: 1cc9e79384bbf4aae44199c2f35331e3afd8fd8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214115"
---
# <a name="cloakediid-structure"></a>CloakedIid (estructura)

Indica al `RuntimeClass`, `Implements` y `ChainInterfaces` plantillas a las que no se puede tener acceso a la interfaz especificada en la lista de IID.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T>
struct CloakedIid : T;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La interfaz que está oculta (escondida).

## <a name="remarks"></a>Observaciones

El siguiente es un ejemplo de cómo se usa **cloakediid (** : `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`T`

`CloakedIid`

## <a name="requirements"></a>Requisitos

**Encabezado:** implementa. h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Consulte también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)
