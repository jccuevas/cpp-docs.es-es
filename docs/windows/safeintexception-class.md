---
title: SafeIntException (clase) | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException Class
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException class
- SafeIntException, constructor
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4ffd82f80b8af0b53ca86ca3daded84580e1e07b
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235742"
---
# <a name="safeintexception-class"></a>SafeIntException (Clase)

El `SafeInt` clase utiliza `SafeIntException` identificar por qué no se puede completar una operación matemática.

## <a name="syntax"></a>Sintaxis

```cpp
class SafeIntException;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                                    | Descripción
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | Crea un objeto `SafeIntException`.

## <a name="remarks"></a>Comentarios

El [clase SafeInt](../windows/safeint-class.md) es la única clase que usa el `SafeIntException` clase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SafeIntException`

## <a name="requirements"></a>Requisitos

**Encabezado:** safeint.h

**Namespace:** msl::utilities

## <a name="safeintexception"></a>SafeIntException::SafeIntException

Crea un objeto `SafeIntException`.

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>Parámetros

*Código*<br/>
[in] Un valor de datos enumerado que describe el error que se ha producido.

### <a name="remarks"></a>Comentarios

Los valores posibles de *código* se definen en el archivo Safeint.h. Para mayor comodidad, también se muestran aquí los valores posibles.

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
