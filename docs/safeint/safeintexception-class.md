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
ms.openlocfilehash: 2998bbb83fd568d7ff627d6598c32fb5b17c1e40
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515570"
---
# <a name="safeintexception-class"></a>SafeIntException (Clase)

La clase `SafeInt` usa `SafeIntException` para identificar por qué no se puede realizar una operación matemática.

> [!NOTE]
> La versión más reciente de esta biblioteca se encuentra en [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt).

## <a name="syntax"></a>Sintaxis

```cpp
class SafeIntException;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

nombre                                                    | Descripción
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | Crea un objeto `SafeIntException`.

## <a name="remarks"></a>Comentarios

La [clase SafeInt](../safeint/safeint-class.md) es la única clase que usa la clase `SafeIntException`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SafeIntException`

## <a name="requirements"></a>Requisitos

**Encabezado:** safeint.h

**Espacio de nombres:** msl::utilities

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

Los valores posibles de *code* se definen en el archivo Safeint.h. Por comodidad, también se muestran aquí los valores posibles.

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
