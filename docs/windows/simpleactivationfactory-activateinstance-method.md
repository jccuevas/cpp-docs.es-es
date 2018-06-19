---
title: 'Simpleactivationfactory:: Activateinstance (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
dev_langs:
- C++
helpviewer_keywords:
- ActivateInstance method
ms.assetid: 4f836e51-5a6c-4bad-b871-9f25199298b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5af4bfd22302b7694b9bafbc1452d636b19cb3c7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889428"
---
# <a name="simpleactivationfactoryactivateinstance-method"></a>SimpleActivationFactory::ActivateInstance (Método)

Crea una instancia de la interfaz especificada.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>Parámetros

*ppvObject*  
Cuando se completa esta operación, puntero a una instancia del objeto especificado por el `Base` parámetro de plantilla de clase.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="remarks"></a>Comentarios

Si &#95; &#95;WRL_STRICT&#95; &#95; está definido, se genera un error de aserción si no se deriva la clase base especificada en el parámetro de plantilla de clase [RuntimeClass](../windows/runtimeclass-class.md), o no está configurado con el elemento WinRt o WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valor de enumeración.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[SimpleActivationFactory (clase)](../windows/simpleactivationfactory-class.md)