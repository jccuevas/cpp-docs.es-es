---
title: ActivateInstance (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
ms.openlocfilehash: 65648d62657bf989d4a08660e0fd7724511350c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666302"
---
# <a name="activateinstance-function"></a>ActivateInstance (función)

Registra y recupera una instancia de un tipo especificado definido en un identificador de clase especificado.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T>
inline HRESULT ActivateInstance(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Un tipo que se va a activar.

*activatableClassId*<br/>
El nombre de la Id. de clase que define el parámetro *T*.

*Instancia*<br/>
Cuando finalice esta operación, una referencia a una instancia de *T*.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un error HRESULT que indica la causa del error.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Namespace:** Windows::Foundation

## <a name="see-also"></a>Vea también

[Windows::Foundation (espacio de nombres)](../windows/windows-foundation-namespace.md)