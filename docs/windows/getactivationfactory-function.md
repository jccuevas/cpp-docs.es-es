---
title: GetActivationFactory (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f5afaa14d926cc7dde86cdbdb6b5ca8162f81d7c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402153"
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