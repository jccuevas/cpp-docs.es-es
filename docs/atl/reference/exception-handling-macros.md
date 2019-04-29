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
ms.openlocfilehash: 8afb2019e38f7548467e85d9a2c1c12c538cf744
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276267"
---
# <a name="exception-handling-macros"></a>Macros de control de excepciones

Estas macros proporcionan compatibilidad para control de excepciones.

|||
|-|-|
|[_ATLCATCH](#_atlcatch)|Instrucciones para controlar los errores que ocurren en el asociado `_ATLTRY`.|
|[_ATLCATCHALL](#_atlcatchall)|Instrucciones para controlar los errores que ocurren en el asociado `_ATLTRY`.|
|[_ATLTRY](#_atltry)|Marca una sección de código protegido que posiblemente podría producirse un error.|

## <a name="requirements"></a>Requisitos:

**Encabezado:** atldef.h

##  <a name="_atlcatch"></a>  _ATLCATCH

Instrucciones para controlar los errores que ocurren en el asociado `_ATLTRY`.

```
_ATLCATCH(e)
```

### <a name="parameters"></a>Parámetros

*e*<br/>
Para detectar la excepción.

### <a name="remarks"></a>Comentarios

Usar junto con `_ATLTRY`. Se resuelve en C++ [catch (e CAtlException)](../../cpp/try-throw-and-catch-statements-cpp.md) para controlar un tipo determinado de excepciones de C++.

##  <a name="_atlcatchall"></a>  _ATLCATCHALL

Instrucciones para controlar los errores que ocurren en el asociado `_ATLTRY`.

```
_ATLCATCHALL
```

### <a name="remarks"></a>Comentarios

Usar junto con `_ATLTRY`. Se resuelve en C++ [catch (...) ](../../cpp/try-throw-and-catch-statements-cpp.md) para controlar todos los tipos de excepciones de C++.

##  <a name="_atltry"></a>  _ATLTRY

Marca una sección de código protegido que posiblemente podría producirse un error.

```
_ATLTRY
```

### <a name="remarks"></a>Comentarios

Usar junto con [_ATLCATCH](#_atlcatch) o [_ATLCATCHALL](#_atlcatchall). Se resuelve en el símbolo de C++ [intente](../../cpp/try-throw-and-catch-statements-cpp.md).

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)
