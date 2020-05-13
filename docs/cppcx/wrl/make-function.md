---
title: Make (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
ms.openlocfilehash: ffd0967b741475b260eef80ec24d56874a6bcb1f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213816"
---
# <a name="make-function"></a>Make (función)

Inicializa la clase de Windows Runtime especificada. Utilice esta función para crear una instancia de un componente que se define en el mismo módulo.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8,
   typename TArg9
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8,
   TArg9 &&arg9
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3
);
template <
   typename T,
   typename TArg1,
   typename TArg2
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2
);
template <
   typename T,
   typename TArg1
>
ComPtr<T> Make(
   TArg1 &&arg1
);
template <
   typename T
>
ComPtr<T> Make();
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

Objeto `ComPtr<T>` si es correcto; de lo contrario, `nullptr`.

## <a name="remarks"></a>Observaciones

Consulte [Cómo: crear instancias de componentes WRL directamente](how-to-instantiate-wrl-components-directly.md) para obtener información sobre las diferencias entre esta función y [Microsoft:: WRL::D etalles:: MakeAndInitialize](makeandinitialize-function.md), y para obtener un ejemplo.

## <a name="requirements"></a>Requisitos

**Encabezado:** implementa. h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Consulte también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)
