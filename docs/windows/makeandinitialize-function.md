---
title: MakeAndInitialize (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
dev_langs:
- C++
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 196834a5181164d141c1b9ee025cee5b6f1a5bd9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591051"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize (Función)

Inicializa la clase en tiempo de ejecución de Windows especificada. Utilice esta función para crear una instancia de un componente que se define en el mismo módulo.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T, typename I,
typename TArg1,
typename TArg2,
typename TArg3,
typename TArg4,
typename TArg5,
typename TArg6,
typename TArg7,
typename TArg8,
typename TArg9> HRESULT MakeAndInitialize(_Outptr_result_nullonfailure_ I** ppvObject, TArg1 &&arg1, TArg2 &&arg2, TArg3 &&arg3, TArg4 &&arg4, TArg5 &&arg5, TArg6 &&arg6, TArg7 &&arg7, TArg8 &&arg8, TArg9 &&arg9) throw()  
```

### <a name="parameters"></a>Parámetros

*T*  
Una clase especificada por el usuario que hereda de `WRL::RuntimeClass`.

*TArg1*  
Tipo de argumento 1 que se pasa a la clase en tiempo de ejecución especificado.

*TArg2*  
Tipo de argumento 2 que se pasa a la clase en tiempo de ejecución especificado.

*TArg3*  
Tipo de argumento 3 que se pasa a la clase en tiempo de ejecución especificado.

*TArg4*  
Tipo de argumento 4 que se pasa a la clase en tiempo de ejecución especificado.

*TArg5*  
Tipo de argumento 5 que se pasa a la clase en tiempo de ejecución especificado.

*TArg6*  
Tipo de argumento 6 que se pasa a la clase en tiempo de ejecución especificado.

*TArg7*  
Tipo de argumento 7 que se pasa a la clase en tiempo de ejecución especificado.

*TArg8*  
Tipo de argumento 8 que se pasa a la clase en tiempo de ejecución especificado.

*TArg9*  
Tipo de argumento 9 que se pasa a la clase en tiempo de ejecución especificado.

*Arg1*  
Argumento 1 que se pasa a la clase en tiempo de ejecución especificado.

*Arg2*  
Argumento 2 que se pasa a la clase en tiempo de ejecución especificado.

*Arg3*  
Argumento 3 que se pasa a la clase en tiempo de ejecución especificado.

*Arg4*  
Argumento 4 que se pasa a la clase en tiempo de ejecución especificado.

*Arg5*  
Argumento 5 que se pasa a la clase en tiempo de ejecución especificado.

*Arg6*  
Argumento 6 que se pasa a la clase en tiempo de ejecución especificado.

*Arg7*  
Argumento 7 que se pasa a la clase en tiempo de ejecución especificado.

*Arg8*  
Argumento 8 que se pasa a la clase en tiempo de ejecución especificado.

*Arg9*  
Argumento 9 que se pasa a la clase en tiempo de ejecución especificado.

## <a name="return-value"></a>Valor devuelto

Valor HRESULT.

## <a name="remarks"></a>Comentarios

Consulte [Cómo: crear instancias de componentes de WRL directamente](../windows/how-to-instantiate-wrl-components-directly.md) para obtener información sobre las diferencias entre esta función y [Microsoft::WRL::Make](../windows/make-function.md)y para obtener un ejemplo.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)