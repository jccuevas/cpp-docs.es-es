---
title: Clase _U_STRINGorID
ms.date: 11/04/2016
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
ms.openlocfilehash: 57363dbe2a1e7166b8da401900c3a7f913e63a9d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495110"
---
# <a name="_u_stringorid-class"></a>Clase _U_STRINGorID

Esta clase de adaptador de argumentos permite pasar nombres de recursos (LPCTSTRs) o identificadores de recursos (UINT) a una función sin necesidad de que el autor de la llamada convierta el identificador en una cadena mediante la macro MAKEINTRESOURCE.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class _U_STRINGorID
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|El constructor.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|Identificador de recursos.|

## <a name="remarks"></a>Comentarios

Esta clase está diseñada para implementar contenedores en la API de administración de recursos de Windows, como las funciones [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcew), [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)y [LoadMenu](/windows/win32/api/winuser/nf-winuser-loadmenuw) , que aceptan un argumento LPCTSTR que puede ser el nombre de un recurso o su identificador.

La clase define dos sobrecargas de constructor: una acepta un argumento LPCTSTR y la otra acepta un argumento UINT. El argumento UINT se convierte en un tipo de recurso compatible con las funciones de administración de recursos de Windows mediante la macro MAKEINTRESOURCE y el resultado almacenado en el miembro de datos único de la clase, [m_lpstr](#_u_stringorid__m_lpstr). El argumento para el constructor LPCTSTR se almacena directamente sin conversión.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin. h

##  <a name="_u_stringorid__m_lpstr"></a>  _U_STRINGorID::m_lpstr

La clase contiene el valor pasado a cualquiera de sus constructores como un miembro de datos LPCTSTR público.

```
LPCTSTR m_lpstr;
```

##  <a name="_u_stringorid___u_stringorid"></a>  _U_STRINGorID::_U_STRINGorID

El constructor UINT convierte su argumento en un tipo de recurso compatible con las funciones de administración de recursos de Windows mediante la macro MAKEINTRESOURCE y el resultado se almacena en el miembro de datos único de la clase, [m_lpstr](#_u_stringorid__m_lpstr).

```
_U_STRINGorID(UINT nID);
_U_STRINGorID(LPCTSTR lpString);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
IDENTIFICADOR de recurso.

*lpString*<br/>
Nombre del recurso.

### <a name="remarks"></a>Comentarios

El argumento para el constructor LPCTSTR se almacena directamente sin conversión.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
