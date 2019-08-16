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
ms.openlocfilehash: 3e138eee9e5bc02971cd1eb34c78f2be4ad5c9a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398425"
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

*factory*<br/>
Cuando finalice esta operación, una referencia a la factoría de activación para el tipo *T*.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un error HRESULT que indica el motivo del error de esta operación.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres**: Windows::Foundation

## <a name="see-also"></a>Vea también

[Windows::Foundation (espacio de nombres)](windows-foundation-namespace.md)