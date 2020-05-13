---
title: SafeIntException (Clase)
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeIntException Class
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
helpviewer_keywords:
- SafeIntException class
- SafeIntException, constructor
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
ms.openlocfilehash: e118d7e3cce47ebb93cef16319a8fc45aab1118b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349952"
---
# <a name="safeintexception-class"></a>SafeIntException (Clase)

La clase `SafeInt` usa `SafeIntException` para identificar por qué no se puede realizar una operación matemática.

> [!NOTE]
> La última versión de [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)esta biblioteca se encuentra en .

## <a name="syntax"></a>Sintaxis

```cpp
class SafeIntException;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                                                    | Descripción
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | Crea un objeto `SafeIntException` .

## <a name="remarks"></a>Observaciones

La [clase SafeInt](../safeint/safeint-class.md) es la única clase que usa la clase `SafeIntException`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SafeIntException`

## <a name="requirements"></a>Requisitos

**Encabezado:** safeint.h

**Espacio de nombres:** msl::utilities

## <a name="safeintexceptionsafeintexception"></a><a name="safeintexception"></a>SafeIntException::SafeIntException

Crea un objeto `SafeIntException` .

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>Parámetros

*Código*<br/>
[in] Un valor de datos enumerado que describe el error que se ha producido.

### <a name="remarks"></a>Observaciones

Los valores posibles de *code* se definen en el archivo Safeint.h. Por comodidad, también se muestran aquí los valores posibles.

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
