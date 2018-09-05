---
title: IID_PPV_ARGS_Helper (función) | Microsoft Docs
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
ms.openlocfilehash: 32970c9d30e1804071190ee5a57c42fd4b6334af
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677256"
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

*T*  
El tipo del argumento *pp*.

*perfil de puerto*  
Puntero indirecto doble.

## <a name="return-value"></a>Valor devuelto

Argumento *pp* convierte en un puntero a una de puntero a **void**.

## <a name="remarks"></a>Comentarios

Se genera un error de tiempo de compilación si el parámetro de plantilla *T* no se deriva de `IUnknown`.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

