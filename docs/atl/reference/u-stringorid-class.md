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
ms.openlocfilehash: 4e46ceec077b8daf8ef2a76110d2fc19dd39ae26
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325824"
---
# <a name="_u_stringorid-class"></a>Clase _U_STRINGorID

Esta clase de adaptador de argumento permite que los nombres de recursos (LPCTSTR) o los identificadores de recursos (UINT) se pasen a una función sin necesidad de que el autor de la llamada convierta el identificador en una cadena mediante la macro MAKEINTRESOURCE.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

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

## <a name="remarks"></a>Observaciones

Esta clase está diseñada para implementar contenedores en la API de administración de recursos de Windows, como las funciones [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea), [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)y [LoadMenu,](/windows/win32/api/winuser/nf-winuser-loadmenuw) que aceptan un argumento LPCTSTR que puede ser el nombre de un recurso o su identificador.

La clase define dos sobrecargas de constructor: una acepta un argumento LPCTSTR y la otra acepta un argumento UINT. El argumento UINT se convierte en un tipo de recurso compatible con las funciones de administración de recursos de Windows mediante la macro MAKEINTRESOURCE y el resultado almacenado en el único miembro de datos de la clase, [m_lpstr](#_u_stringorid__m_lpstr). El argumento para el constructor LPCTSTR se almacena directamente sin conversión.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="_u_stringoridm_lpstr"></a><a name="_u_stringorid__m_lpstr"></a>_U_STRINGorID::m_lpstr

La clase contiene el valor pasado a cualquiera de sus constructores como un miembro de datos LPCTSTR público.

```
LPCTSTR m_lpstr;
```

## <a name="_u_stringorid_u_stringorid"></a><a name="_u_stringorid___u_stringorid"></a>_U_STRINGorID::_U_STRINGorID

El constructor UINT convierte su argumento en un tipo de recurso compatible con las funciones de administración de recursos de Windows mediante la macro MAKEINTRESOURCE y el resultado se almacena en el único miembro de datos de la clase, [m_lpstr](#_u_stringorid__m_lpstr).

```
_U_STRINGorID(UINT nID);
_U_STRINGorID(LPCTSTR lpString);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Un identificador de recurso.

*lpString*<br/>
Un nombre de recurso.

### <a name="remarks"></a>Observaciones

El argumento para el constructor LPCTSTR se almacena directamente sin conversión.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
