---
title: ActivateInstance (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
dev_langs:
- C++
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2ac6d8722bcdfed06ae97508b0ca7e5bb8ea00a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601457"
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

*T*  
Un tipo que se va a activar.

*activatableClassId*  
El nombre de la Id. de clase que define el parámetro *T*.

*Instancia*  
Cuando finalice esta operación, una referencia a una instancia de *T*.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un error HRESULT que indica la causa del error.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Namespace:** Windows::Foundation

## <a name="see-also"></a>Vea también

[Windows::Foundation (espacio de nombres)](../windows/windows-foundation-namespace.md)