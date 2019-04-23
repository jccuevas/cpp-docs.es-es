---
title: MakeAndInitialize (Función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
ms.openlocfilehash: 14ae5117194748748ceecf97ac83fc8813bba2d3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037489"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize (Función)

Inicializa la clase en tiempo de ejecución de Windows especificada. Utilice esta función para crear una instancia de un componente que se define en el mismo módulo.

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename T,
    typename I,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9>
HRESULT MakeAndInitialize(
    _Outptr_result_nullonfailure_ I** ppvObject,
    TArg1 &&arg1,
    TArg2 &&arg2,
    TArg3 &&arg3,
    TArg4 &&arg4,
    TArg5 &&arg5,
    TArg6 &&arg6,
    TArg7 &&arg7,
    TArg8 &&arg8,
    TArg9 &&arg9) throw()
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Una clase especificada por el usuario que hereda de `WRL::RuntimeClass`.

*TArg1*<br/>
Tipo de argumento 1 que se pasa a la clase en tiempo de ejecución especificado.

*TArg2*<br/>
Tipo de argumento 2 que se pasa a la clase en tiempo de ejecución especificado.

*TArg3*<br/>
Tipo de argumento 3 que se pasa a la clase en tiempo de ejecución especificado.

*TArg4*<br/>
Tipo de argumento 4 que se pasa a la clase en tiempo de ejecución especificado.

*TArg5*<br/>
Tipo de argumento 5 que se pasa a la clase en tiempo de ejecución especificado.

*TArg6*<br/>
Tipo de argumento 6 que se pasa a la clase en tiempo de ejecución especificado.

*TArg7*<br/>
Tipo de argumento 7 que se pasa a la clase en tiempo de ejecución especificado.

*TArg8*<br/>
Tipo de argumento 8 que se pasa a la clase en tiempo de ejecución especificado.

*TArg9*<br/>
Tipo de argumento 9 que se pasa a la clase en tiempo de ejecución especificado.

*arg1*<br/>
Argumento 1 que se pasa a la clase en tiempo de ejecución especificado.

*arg2*<br/>
Argumento 2 que se pasa a la clase en tiempo de ejecución especificado.

*arg3*<br/>
Argumento 3 que se pasa a la clase en tiempo de ejecución especificado.

*arg4*<br/>
Argumento 4 que se pasa a la clase en tiempo de ejecución especificado.

*arg5*<br/>
Argumento 5 que se pasa a la clase en tiempo de ejecución especificado.

*arg6*<br/>
Argumento 6 que se pasa a la clase en tiempo de ejecución especificado.

*arg7*<br/>
Argumento 7 que se pasa a la clase en tiempo de ejecución especificado.

*arg8*<br/>
Argumento 8 que se pasa a la clase en tiempo de ejecución especificado.

*arg9*<br/>
Argumento 9 que se pasa a la clase en tiempo de ejecución especificado.

## <a name="return-value"></a>Valor devuelto

Valor HRESULT.

## <a name="remarks"></a>Comentarios

Vea [Cómo: Crear instancias directamente de los componentes de WRL](how-to-instantiate-wrl-components-directly.md) para obtener información sobre las diferencias entre esta función y [Microsoft::WRL::Make](make-function.md)y para obtener un ejemplo.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)