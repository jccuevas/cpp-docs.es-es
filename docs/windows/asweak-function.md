---
title: AsWeak (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
dev_langs:
- C++
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dfd626a3e0ca1866f6db046554220c6e631c18b4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394314"
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

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)