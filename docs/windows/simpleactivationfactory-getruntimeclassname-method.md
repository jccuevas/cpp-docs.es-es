---
title: 'Simpleactivationfactory:: Getruntimeclassname (método) | Documentos de Microsoft'
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
ms.openlocfilehash: e001d0269c21026bdd00abcdd4d257f11d601cf6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889038"
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

Si &#95; &#95;WRL_STRICT&#95; &#95; está definido, se genera un error de aserción si la clase especificada por el `Base` parámetro de plantilla de clase no se deriva [RuntimeClass](../windows/runtimeclass-class.md), o no está configurado con el WinRt o WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valor de enumeración.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[SimpleActivationFactory (clase)](../windows/simpleactivationfactory-class.md)