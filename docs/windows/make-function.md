---
title: MAKE (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
dev_langs:
- C++
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f381a00b5ac1f105080355f1d3e3cd15efa5abf8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878078"
---
# <a name="make-function"></a>Make (Función)
Inicializa la clase en tiempo de ejecución de Windows especificada. Utilice esta función para crear una instancia de un componente que se define en el mismo módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Una clase especificada por el usuario que hereda de `WRL::RuntimeClass`.  
  
 `TArg1`  
 Tipo de argumento 1 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `TArg2`  
 Tipo de argumento 2 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `TArg3`  
 Tipo de argumento 3 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `TArg4`  
 Tipo de argumento 4 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `TArg5`  
 Tipo de argumento 5 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `TArg6`  
 Tipo de argumento 6 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `TArg7`  
 Tipo de argumento 7 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `TArg8`  
 Tipo de argumento 8 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `TArg9`  
 Tipo de argumento 9 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `arg1`  
 Argumento 1 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `arg2`  
 Argumento 2 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `arg3`  
 Argumento 3 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `arg4`  
 Argumento 4 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `arg5`  
 Argumento 5 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `arg6`  
 Argumento 6 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `arg7`  
 Argumento pasado 7 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `arg8`  
 Argumento 8 que se pasa a la clase en tiempo de ejecución especificado.  
  
 `arg9`  
 Argumento 9 que se pasa a la clase en tiempo de ejecución especificado.  
  
## <a name="return-value"></a>Valor devuelto  
 A `ComPtr<T>` objeto si es correcto; en caso contrario, `nullptr`.  
  
## <a name="remarks"></a>Comentarios  
 Vea [Cómo: crear instancias de componentes de WRL directamente](../windows/how-to-instantiate-wrl-components-directly.md) para obtener información sobre las diferencias entre esta función y [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)y para obtener un ejemplo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)