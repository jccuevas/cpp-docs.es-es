---
title: ActivationFactoryCallback (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
ms.openlocfilehash: 8da0f3f54e142673a44909f3fe2141b09a71d388
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586451"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback (función)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(
   HSTRING activationId,
   IActivationFactory **ppFactory
);
```

### <a name="parameters"></a>Parámetros

*activationId*<br/>
Identificador de una cadena que especifica un nombre de clase en tiempo de ejecución.

*ppFactory*<br/>
Cuando finalice esta operación, un generador de activación que corresponde al parámetro *activationId*.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error. Valores HRESULT de error probable son CLASS_E_CLASSNOTAVAILABLE y E_INVALIDARG.

## <a name="remarks"></a>Comentarios

Obtiene el generador de activación para el identificador de activación especificado.

El tiempo de ejecución de Windows llama a esta función de devolución de llamada para solicitar un objeto especificado por su nombre de clase en tiempo de ejecución.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)