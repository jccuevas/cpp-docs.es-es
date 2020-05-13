---
title: MakeAndInitialize (Función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
ms.openlocfilehash: 28d9e586a766a131e7ab6280859845810c1d9814
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213803"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize (Función)

Inicializa la clase de Windows Runtime especificada. Utilice esta función para crear una instancia de un componente que se define en el mismo módulo.

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
Tipo de argumento 1 que se pasa a la clase en tiempo de ejecución especificada.

*TArg2*<br/>
Tipo de argumento 2 que se pasa a la clase en tiempo de ejecución especificada.

*TArg3*<br/>
Tipo de argumento 3 que se pasa a la clase en tiempo de ejecución especificada.

*TArg4*<br/>
Tipo de argumento 4 que se pasa a la clase en tiempo de ejecución especificada.

*TArg5*<br/>
Tipo de argumento 5 que se pasa a la clase en tiempo de ejecución especificada.

*TArg6*<br/>
Tipo de argumento 6 que se pasa a la clase en tiempo de ejecución especificada.

*TArg7*<br/>
Tipo de argumento 7 que se pasa a la clase en tiempo de ejecución especificada.

*TArg8*<br/>
Tipo de argumento 8 que se pasa a la clase en tiempo de ejecución especificada.

*TArg9*<br/>
Tipo de argumento 9 que se pasa a la clase en tiempo de ejecución especificada.

*arg1*<br/>
Argumento 1 que se pasa a la clase en tiempo de ejecución especificada.

*arg2*<br/>
Argumento 2 que se pasa a la clase en tiempo de ejecución especificada.

*arg3*<br/>
Argumento 3 que se pasa a la clase en tiempo de ejecución especificada.

*arg4*<br/>
Argumento 4 que se pasa a la clase en tiempo de ejecución especificada.

*arg5*<br/>
Argumento 5 que se pasa a la clase en tiempo de ejecución especificada.

*arg6*<br/>
Argumento 6 que se pasa a la clase en tiempo de ejecución especificada.

*arg7*<br/>
Argumento 7 que se pasa a la clase en tiempo de ejecución especificada.

*arg8*<br/>
Argumento 8 que se pasa a la clase en tiempo de ejecución especificada.

*arg9*<br/>
Argumento 9 que se pasa a la clase en tiempo de ejecución especificada.

## <a name="return-value"></a>Valor devuelto

Valor HRESULT.

## <a name="remarks"></a>Observaciones

Consulte [Cómo: crear instancias de componentes de WRL directamente](how-to-instantiate-wrl-components-directly.md) para obtener información sobre las diferencias entre esta función y [Microsoft:: WRL:: make](make-function.md), y para obtener un ejemplo.

## <a name="requirements"></a>Requisitos

**Encabezado:** implementa. h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)
