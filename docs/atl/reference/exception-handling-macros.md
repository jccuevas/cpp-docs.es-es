---
title: Macros de control de excepciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
dev_langs:
- C++
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05ee381aa792c252fc9b80107d25e15e7d1ecfca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358982"
---
# <a name="exception-handling-macros"></a>Macros de control de excepciones
Estas macros proporcionan compatibilidad para control de excepciones.  
  
|||  
|-|-|  
|[_ATLCATCH](#_atlcatch)|Instrucciones para controlar los errores que se producen en el asociado `_ATLTRY`.|  
|[_ATLCATCHALL](#_atlcatchall)|Instrucciones para controlar los errores que se producen en el asociado `_ATLTRY`.|  
|[_ATLTRY](#_atltry)|Marca una sección de código protegido que posiblemente puede producirse un error.|  
  
## <a name="requirements"></a>Requisitos:
**Encabezado:** atldef.h

##  <a name="_atlcatch"></a>  _ATLCATCH  
 Instrucciones para controlar los errores que se producen en el asociado `_ATLTRY`.  
  
```
_ATLCATCH(e)
```  
  
### <a name="parameters"></a>Parámetros  
 *e*  
 La excepción que se va a detectar.  
  
### <a name="remarks"></a>Comentarios  
 Usar junto con `_ATLTRY`. Se resuelve en C++ [catch (e CAtlException)](../../cpp/try-throw-and-catch-statements-cpp.md) para controlar un tipo determinado de excepciones de C++.  
  
##  <a name="_atlcatchall"></a>  _ATLCATCHALL  
 Instrucciones para controlar los errores que se producen en el asociado `_ATLTRY`.  
  
```
_ATLCATCHALL
```  
  
### <a name="remarks"></a>Comentarios  
 Usar junto con `_ATLTRY`. Se resuelve en C++ [catch (...) ](../../cpp/try-throw-and-catch-statements-cpp.md) para controlar todos los tipos de excepciones de C++.  
  
##  <a name="_atltry"></a>  _ATLTRY  
 Marca una sección de código protegido que posiblemente puede producirse un error.  
  
```
_ATLTRY
```  
  
### <a name="remarks"></a>Comentarios  
 Usar junto con [_ATLCATCH](#_atlcatch) o [_ATLCATCHALL](#_atlcatchall). Se resuelve en el símbolo de C++ [intente](../../cpp/try-throw-and-catch-statements-cpp.md).  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)
