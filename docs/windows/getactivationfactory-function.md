---
title: GetActivationFactory (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
ms.openlocfilehash: a2581fce3c15c96317bf68de0ed918b19edd8b38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481718"
---
# <a name="getactivationfactory-function"></a>GetActivationFactory (función)

Recupera un generador de activación para el tipo especificado por el parámetro de plantilla.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T>
inline HRESULT GetActivationFactory(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Un parámetro de plantilla que especifica el tipo de la factoría de activación.

*activatableClassId*<br/>
El nombre de la clase que puede producir el generador de activación.

*Factory*<br/>
Cuando finalice esta operación, una referencia a la factoría de activación para el tipo *T*.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un error HRESULT que indica el motivo del error de esta operación.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Namespace:** Windows::Foundation

## <a name="see-also"></a>Vea también

[Windows::Foundation (espacio de nombres)](../windows/windows-foundation-namespace.md)