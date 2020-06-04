---
title: ActivationFactoryCallback (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
ms.openlocfilehash: 0be4bebcc561cdf1df3f2502c8cc1927bdc65564
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214219"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback (función)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(
   HSTRING activationId,
   IActivationFactory **ppFactory
);
```

### <a name="parameters"></a>Parámetros

*Activationid (*<br/>
Identificador de una cadena que especifica un nombre de clase en tiempo de ejecución.

*ppFactory*<br/>
Cuando se completa esta operación, un generador de activación que corresponde al parámetro *activationid (* .

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error. Los valores HRESULT de error probables son CLASS_E_CLASSNOTAVAILABLE y E_INVALIDARG.

## <a name="remarks"></a>Observaciones

Obtiene el generador de activación para el identificador de activación especificado.

El Windows Runtime llama a esta función de devolución de llamada para solicitar un objeto especificado por su nombre de clase en tiempo de ejecución.

## <a name="requirements"></a>Requisitos

**Encabezado:** Module. h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)
