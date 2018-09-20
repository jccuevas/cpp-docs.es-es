---
title: Método Runtimeclassbaset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 90d7df8a-cf9e-4eef-8837-bc1a25f3fa1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7092153e49fdb40fc32fb1cbee5bc2376080ff4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391883"
---
# <a name="runtimeclassbasetasiid-method"></a>RuntimeClassBaseT::AsIID (Método)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T>
__forceinline static HRESULT AsIID(
   _In_ T* implements,
   REFIID riid,
   _Deref_out_ void **ppvObject
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Un tipo que implementa el identificador de interfaz especificado por el parámetro *riid*.

*Implementa*<br/>
Una variable del tipo especificado por el parámetro de plantilla *T*.

*riid*<br/>
Para recuperar el identificador de interfaz.

*ppvObject*<br/>
Si esta operación se realiza correctamente, un puntero a una de puntero a la interfaz especificada por el parámetro *riid*.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un valor HRESULT que describe el error.

## <a name="remarks"></a>Comentarios

Recupera un puntero al identificador de interfaz especificado.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[RuntimeClassBaseT (estructura)](../windows/runtimeclassbaset-structure.md)<br/>
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)