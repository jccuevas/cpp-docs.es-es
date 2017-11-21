---
title: Clase _U_STRINGorID | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
dev_langs: C++
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b02d539ae2a067c015988a847407bf631b6e8c1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ustringorid-class"></a>Clase _U_STRINGorID
Esta clase de adaptador de argumento permite a ambos nombres de recursos ( `LPCTSTR`s) o identificadores de recursos ( **UINT**s) que se pasan a una función sin necesidad de autor de la llamada convertir el identificador en una cadena mediante el **MAKEINTRESOURCE** macro.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class _U_STRINGorID
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|El constructor.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|El identificador de recurso.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase está diseñada para implementar contenedores de la API de administración de recursos de Windows como el [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042), [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072), y [LoadMenu](http://msdn.microsoft.com/library/windows/desktop/ms647990) funciones, que acepten un `LPCTSTR` argumento que puede ser el nombre de un recurso o su identificador.  
  
 La clase define dos sobrecargas del constructor: uno acepta un `LPCTSTR` acepta argumentos y el otro un **UINT** argumento. El **UINT** argumento se convierte en un tipo de recurso compatible con las funciones de administración de recursos de Windows mediante el **MAKEINTRESOURCE** macro y el resultado almacenado en el miembro de datos único de la clase, [m_lpstr](#_u_stringorid__m_lpstr). El argumento para el `LPCTSTR` constructor se almacena directamente sin realizar ninguna conversión.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="_u_stringorid__m_lpstr"></a>_U_STRINGorID::m_lpstr  
 La clase contiene el valor pasado a cualquiera de sus constructores como un complemento público `LPCTSTR` miembro de datos.  
  
```
LPCTSTR m_lpstr;
```  
  
##  <a name="_u_stringorid___u_stringorid"></a>_U_STRINGorID::_U_STRINGorID  
 El **UINT** constructor convierte su argumento en un tipo de recurso compatible con las funciones de administración de recursos de Windows mediante el **MAKEINTRESOURCE** macro y el resultado se almacena en única de la clase miembro de datos, [m_lpstr](#_u_stringorid__m_lpstr).  
  
```
_U_STRINGorID(UINT nID);  
_U_STRINGorID(LPCTSTR lpString);
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 Un identificador de recurso.  
  
 `lpString`  
 Un nombre de recurso.  
  
### <a name="remarks"></a>Comentarios  
 El argumento para el `LPCTSTR` constructor se almacena directamente sin realizar ninguna conversión.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
