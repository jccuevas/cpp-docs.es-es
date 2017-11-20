---
title: Macros de control de excepciones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
dev_langs: C++
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 906f6d499da04a6bee9da18dbbb6ad4b463c8fa6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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

##  <a name="_atlcatch"></a>_ATLCATCH  
 Instrucciones para controlar los errores que se producen en el asociado `_ATLTRY`.  
  
```
_ATLCATCH(e)
```  
  
### <a name="parameters"></a>Parámetros  
 *e*  
 La excepción que se va a detectar.  
  
### <a name="remarks"></a>Comentarios  
 Usar junto con `_ATLTRY`. Se resuelve en C++ [catch (e CAtlException)](../../cpp/try-throw-and-catch-statements-cpp.md) para controlar un tipo determinado de excepciones de C++.  
  
##  <a name="_atlcatchall"></a>_ATLCATCHALL  
 Instrucciones para controlar los errores que se producen en el asociado `_ATLTRY`.  
  
```
_ATLCATCHALL
```  
  
### <a name="remarks"></a>Comentarios  
 Usar junto con `_ATLTRY`. Se resuelve en C++ [catch (...) ](../../cpp/try-throw-and-catch-statements-cpp.md) para controlar todos los tipos de excepciones de C++.  
  
##  <a name="_atltry"></a>_ATLTRY  
 Marca una sección de código protegido que posiblemente puede producirse un error.  
  
```
_ATLTRY
```  
  
### <a name="remarks"></a>Comentarios  
 Usar junto con [_ATLCATCH](#_atlcatch) o [_ATLCATCHALL](#_atlcatchall). Se resuelve en el símbolo de C++ [intente](../../cpp/try-throw-and-catch-statements-cpp.md).  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)
