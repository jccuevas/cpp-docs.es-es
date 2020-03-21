---
title: IID_PPV_ARGS_Helper (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: 68dbd0b5b2e9d4fc04821a7e7e0193840b55e312
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077126"
---
# <a name="iid_ppv_args_helper-function"></a>IID_PPV_ARGS_Helper (función)

Comprueba que el tipo del argumento especificado deriva de la interfaz `IUnknown`.

> [!IMPORTANT]
> Esta especialización de plantilla es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código. En su lugar, use [IID_PPV_ARGS](/windows/win32/api/combaseapi/nf-combaseapi-iid_ppv_args) .

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

*páginas*<br/>
Puntero doble indirecto.

## <a name="return-value"></a>Valor devuelto

Argumento *PP* convertido a un puntero a un puntero a **void**.

## <a name="remarks"></a>Observaciones

Si el parámetro de plantilla *T* no deriva de `IUnknown`, se genera un error en tiempo de compilación.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h
