---
title: AsWeak (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
ms.openlocfilehash: 1332aa140a8298590ad83158e0ec1b75035c4e92
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785878"
---
# <a name="asweak-function"></a>AsWeak (función)

Recupera una referencia débil a una instancia especificada.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T>
HRESULT AsWeak(
   _In_ T* p,
   _Out_ WeakRef* pWeak
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Un puntero al tipo de parámetro *p*.

*p*<br/>
Una instancia de un tipo.

*pWeak*<br/>
Cuando finalice esta operación, un puntero a una referencia débil al parámetro *p*.

## <a name="return-value"></a>Valor devuelto

S_OK si esta operación se realiza correctamente; en caso contrario, un error HRESULT que indica la causa del error.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)