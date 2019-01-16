---
title: IID_PPV_ARGS_Helper (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: cae29c70c551701a351cdcf404342ed1634a0e3b
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337475"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper (función)

Comprueba que el tipo del argumento especificado que se deriva de la `IUnknown` interfaz.

> [!IMPORTANT]
> Esta especialización de plantilla admite la infraestructura WRL y no está pensada para utilizarse directamente desde el código. Use [IID_PPV_ARGS](https://msdn.microsoft.com/library/windows/desktop/ee330727.aspx) en su lugar.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo del argumento *pp*.

*pp*<br/>
Puntero indirecto doble.

## <a name="return-value"></a>Valor devuelto

Argumento *pp* convierte en un puntero a una de puntero a **void**.

## <a name="remarks"></a>Comentarios

Se genera un error de tiempo de compilación si el parámetro de plantilla *T* no se deriva de `IUnknown`.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

