---
title: SafeModulus | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeModulus
dev_langs:
- C++
helpviewer_keywords:
- SafeModulus function
ms.assetid: ae5c81eb-5dcf-45a5-aa76-465fdfe68654
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b807f24f03c5880b4b60708d6919052183ec564f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605215"
---
# <a name="safemodulus"></a>SafeModulus

Realiza la operación de módulo en dos números.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T, typename U>
inline bool SafeModulus (
   const T t,
   const U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parámetros

[in] *t*  
Divisor. Esto debe ser de tipo `T`.

[in] *u*  
Dividendo. Esto debe ser de tipo `U`.

[out] *resultado*  
El parámetro donde **SafeModulus** almacena el resultado.

## <a name="return-value"></a>Valor devuelto

**True** si se produce ningún error; **false** si se produce un error.

## <a name="remarks"></a>Comentarios

Este método forma parte de [Biblioteca SafeInt](../windows/safeint-library.md) y está diseñado para una operación de módulo único sin necesidad de crear una instancia de la [clase SafeInt](../windows/safeint-class.md).

> [!NOTE]
> Este método solo debe usarse cuando una operación matemática solo debe estar protegida. Si hay varias operaciones, se debe utilizar el `SafeInt` clase en lugar de llamar a las funciones individuales independientes.

Para obtener más información acerca de los tipos de plantilla `T` y `U`, consulte [SafeInt (funciones)](../windows/safeint-functions.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** safeint.h

**Namespace:** Microsoft::Utilities

## <a name="see-also"></a>Vea también

[SafeInt (funciones)](../windows/safeint-functions.md)  
[Biblioteca SafeInt](../windows/safeint-library.md)  
[SafeInt (clase)](../windows/safeint-class.md)  
[SafeDivide](../windows/safedivide.md)