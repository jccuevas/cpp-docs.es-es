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
ms.openlocfilehash: b50466fc2c357c1d57fca272ff343cd56f3689c5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604271"
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

*T*  
Un tipo que implementa el identificador de interfaz especificado por el parámetro *riid*.

*Implementa*  
Una variable del tipo especificado por el parámetro de plantilla *T*.

*riid*  
Para recuperar el identificador de interfaz.

*ppvObject*  
Si esta operación se realiza correctamente, un puntero a una de puntero a la interfaz especificada por el parámetro *riid*.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un valor HRESULT que describe el error.

## <a name="remarks"></a>Comentarios

Recupera un puntero al identificador de interfaz especificado.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[RuntimeClassBaseT (estructura)](../windows/runtimeclassbaset-structure.md)  
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)