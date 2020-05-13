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
ms.openlocfilehash: d1109e769352d412df8348822e05b66063159ee8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214232"
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
Tipo que se va a activar.

*activatableClassId*<br/>
Nombre del identificador de clase que define el parámetro *T*.

*instancia*<br/>
Cuando se completa esta operación, se realiza una referencia a una instancia de *T*.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, devuelve un error HRESULT que indica la causa del error.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Windows:: Foundation

## <a name="see-also"></a>Consulte también

[Windows::Foundation (espacio de nombres)](windows-foundation-namespace.md)
