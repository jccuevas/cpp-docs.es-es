---
title: IID_PPV_ARGS_Helper (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
dev_langs:
- C++
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0cef979ae284a303b120df7d14ae71f311498423
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper (función)
Comprueba que el tipo del argumento especificado que se deriva de la `IUnknown` interfaz.  
  
> [!IMPORTANT]
>  Esta especialización de plantilla es compatible con la infraestructura WRL y no está diseñada para utilizarse directamente desde el código. Use [IID_PPV_ARGS](http://msdn.microsoft.com/library/windows/desktop/ee330727.aspx) en su lugar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename T>  
void** IID_PPV_ARGS_Helper(  
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo del argumento `pp`.  
  
 `pp`  
 Un puntero indirecto doble.  
  
## <a name="return-value"></a>Valor devuelto  
 Argumento `pp` convierte en un puntero-a-a-puntero a `void`.  
  
## <a name="remarks"></a>Comentarios  
 Se genera un error de tiempo de compilación si el parámetro de plantilla `T` no derivan de `IUnknown`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (biblioteca de tiempo de ejecución de Windows)](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)