---
title: IID_PPV_ARGS_Helper (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: e7733ae6084b64c20dff5a2c35d7a31c614d6e44
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500503"
---
# <a name="iid_ppv_args_helper-function"></a>IID_PPV_ARGS_Helper (función)

Comprueba que el tipo del argumento especificado deriva de la `IUnknown` interfaz.

> [!IMPORTANT]
> Esta especialización de plantilla es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código. Use [IID_PPV_ARGS](/windows/win32/api/combaseapi/nf-combaseapi-iid_ppv_args) en su lugar.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de argumento *PP*.

*pp*<br/>
Puntero doble indirecto.

## <a name="return-value"></a>Valor devuelto

Argumento *PP* convertido a un puntero a un puntero a **void**.

## <a name="remarks"></a>Comentarios

Si el parámetro de plantilla *T* no deriva de, se genera un error en `IUnknown`tiempo de compilación.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

