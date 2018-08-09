---
title: Método Simpleactivationfactory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
dev_langs:
- C++
ms.assetid: 3aa07487-9a42-46f8-8893-37ba6315e50b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9c8bc1962e946a48b6ebebaf072e4cb32559a6de
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014713"
---
# <a name="simpleactivationfactorygetruntimeclassname-method"></a>SimpleActivationFactory::GetRuntimeClassName (Método)

Obtiene el nombre de clase en tiempo de ejecución de una instancia de la clase especificada por el `Base` parámetro de plantilla de clase.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Parámetros
*runtimeName*  
Cuando se completa esta operación, el nombre de clase en tiempo de ejecución.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="remarks"></a>Comentarios

Si `__WRL_STRICT__` está definido, se genera un error de aserción si la clase especificada por el `Base` no se deriva de parámetro de plantilla de clase [RuntimeClass](../windows/runtimeclass-class.md), o no está configurado con el WinRt o WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valor de enumeración.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también
 [SimpleActivationFactory (clase)](../windows/simpleactivationfactory-class.md)