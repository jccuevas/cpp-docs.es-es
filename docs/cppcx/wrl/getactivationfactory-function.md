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
ms.openlocfilehash: 430b4ed3f6a02fd3db2bcab05fbb7f21f5367b5c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213985"
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
Parámetro de plantilla que especifica el tipo del generador de activación.

*activatableClassId*<br/>
Nombre de la clase que puede generar el generador de activación.

*Factory*<br/>
Cuando se completa esta operación, se hace referencia al generador de activación para el tipo *T*.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, devuelve un error HRESULT que indica por qué se produjo un error en esta operación.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Windows:: Foundation

## <a name="see-also"></a>Consulte también

[Windows::Foundation (espacio de nombres)](windows-foundation-namespace.md)
