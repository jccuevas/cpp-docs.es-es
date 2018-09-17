---
title: SafeIntException::SafeIntException | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException, constructor
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 749ef965520732c37457613f44e0a23e213023db
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700978"
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException

Crea un **SafeIntException** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>Parámetros

*Código*<br/>
[in] Un valor de datos enumerado que describe el error que se ha producido.

## <a name="remarks"></a>Comentarios

Los valores posibles de *código* se definen en el archivo Safeint.h. Para mayor comodidad, también se muestran aquí los valores posibles.

- `SafeIntNoError`

- `SafeIntArithmeticOverflow`

- `SafeIntDivideByZero`

## <a name="requirements"></a>Requisitos

**Encabezado:** safeint.h

**Namespace:** msl::utilities

## <a name="see-also"></a>Vea también

[Biblioteca SafeInt](../windows/safeint-library.md)  
[SafeIntException (clase)](../windows/safeintexception-class.md)  
[SafeInt (clase)](../windows/safeint-class.md)