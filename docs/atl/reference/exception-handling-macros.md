---
title: Macros de control de excepciones
ms.date: 11/04/2016
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
ms.openlocfilehash: 2beffbbed0efee799005190bd7fd071a2087e4d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330083"
---
# <a name="exception-handling-macros"></a>Macros de control de excepciones

Estas macros proporcionan compatibilidad para el control de excepciones.

|||
|-|-|
|[_ATLCATCH](#_atlcatch)|Instrucción(s) para controlar los `_ATLTRY`errores que se producen en el archivo .|
|[_ATLCATCHALL](#_atlcatchall)|Instrucción(s) para controlar los `_ATLTRY`errores que se producen en el archivo .|
|[_ATLTRY](#_atltry)|Marca una sección de código protegido donde podría producirse un error.|

## <a name="requirements"></a>Requisitos:

**Encabezado:** atldef.h

## <a name="_atlcatch"></a><a name="_atlcatch"></a>_ATLCATCH

Instrucción(s) para controlar los `_ATLTRY`errores que se producen en el archivo .

```
_ATLCATCH(e)
```

### <a name="parameters"></a>Parámetros

*e*<br/>
La excepción para catch.

### <a name="remarks"></a>Observaciones

Se utiliza junto con `_ATLTRY`. Resuelve a C++ [catch(CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md) para controlar un tipo determinado de excepciones C++.

## <a name="_atlcatchall"></a><a name="_atlcatchall"></a>_ATLCATCHALL

Instrucción(s) para controlar los `_ATLTRY`errores que se producen en el archivo .

```
_ATLCATCHALL
```

### <a name="remarks"></a>Observaciones

Se utiliza junto con `_ATLTRY`. Resuelve a C++ [catch(...)](../../cpp/try-throw-and-catch-statements-cpp.md) para controlar todos los tipos de excepciones de C++.

## <a name="_atltry"></a><a name="_atltry"></a>_ATLTRY

Marca una sección de código protegido donde podría producirse un error.

```
_ATLTRY
```

### <a name="remarks"></a>Observaciones

Se utiliza junto con [_ATLCATCH](#_atlcatch) o [_ATLCATCHALL](#_atlcatchall). Resuelve en el símbolo C++ [intentar](../../cpp/try-throw-and-catch-statements-cpp.md).

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
