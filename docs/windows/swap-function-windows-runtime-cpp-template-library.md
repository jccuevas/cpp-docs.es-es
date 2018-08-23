---
title: Swap (función) (biblioteca de plantillas C++ de Windows en tiempo de ejecución) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Swap
dev_langs:
- C++
ms.assetid: ed134a08-ceb7-4279-aa02-a183c3a426ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6b5273127b4f4329427f50c82f1bb15a4ad2634e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590214"
---
# <a name="swap-function-windows-runtime-c-template-library"></a>Swap (Función) (Biblioteca de plantillas C++ de Windows Runtime)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
WRL_NOTHROW inline void Swap(
   _Inout_ T& left,
   _Inout_ T& right
);
```

### <a name="parameters"></a>Parámetros

*left*  
Primer argumento.

*right*  
Segundo argumento.

## <a name="return-value"></a>Valor devuelto

## <a name="remarks"></a>Comentarios

Intercambia los valores de los dos argumentos especificados.

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)