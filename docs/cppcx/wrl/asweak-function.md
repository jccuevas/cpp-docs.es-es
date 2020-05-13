---
title: AsWeak (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
ms.openlocfilehash: d11f55d57f4053fd6d46b727a8ed91b340d1764b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214180"
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
Instancia de un tipo.

*pWeak*<br/>
Cuando se completa esta operación, un puntero a una referencia débil al parámetro *p*.

## <a name="return-value"></a>Valor devuelto

S_OK, si esta operación se realiza correctamente; de lo contrario, devuelve un error HRESULT que indica la causa del error.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Consulte también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)
