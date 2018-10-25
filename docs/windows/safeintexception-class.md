---
title: SafeIntException (clase) | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
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
ms.openlocfilehash: 2a1890bc20c0737007075656dcbefa20ad81a9bf
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068065"
---
# <a name="safeintexception-class"></a>SafeIntException (Clase)

El `SafeInt` clase utiliza `SafeIntException` identificar por qué no se puede completar una operación matemática.

> [!NOTE]
> La versión más reciente de esta biblioteca se encuentra en [ https://github.com/dcleblanc/SafeInt ](https://github.com/dcleblanc/SafeInt).

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

*code*<br/>
[in] Un valor de datos enumerado que describe el error que se ha producido.

### <a name="remarks"></a>Comentarios

Los valores posibles de *código* se definen en el archivo Safeint.h. Para mayor comodidad, también se muestran aquí los valores posibles.

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
