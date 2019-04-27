---
title: _U_STRINGorID (clase)
ms.date: 11/04/2016
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
ms.openlocfilehash: 4e6c086f9d2ff4061c6404444a3b4c61dd91fe1c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197123"
---
# <a name="ustringorid-class"></a>_U_STRINGorID (clase)

Esta clase de adaptador de argumento permite que los nombres de recursos (LPCTSTRs) o identificadores de recursos (unidades) que se pasará a una función sin necesidad de convertir el identificador en una cadena mediante la macro MAKEINTRESOURCE al llamador.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class _U_STRINGorID
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|El constructor.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|El identificador de recursos.|

## <a name="remarks"></a>Comentarios

Esta clase está diseñada para implementar contenedores de la API de administración de recursos de Windows, como el [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea), [LoadIcon](/windows/desktop/api/winuser/nf-winuser-loadicona), y [LoadMenu](/windows/desktop/api/winuser/nf-winuser-loadmenua) funciones, que acepten un argumento LPCTSTR que puede ser el nombre de un recurso o su identificador.

La clase define dos sobrecargas del constructor: uno acepta un argumento LPCTSTR y otra que acepta un argumento UINT. El argumento UINT se convierte en un tipo de recurso compatible con las funciones de administración de recursos de Windows mediante la macro MAKEINTRESOURCE y el resultado almacenado en el miembro de datos única de la clase, [m_lpstr](#_u_stringorid__m_lpstr). El argumento del constructor LPCTSTR se almacena directamente sin conversión.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="_u_stringorid__m_lpstr"></a>  _U_STRINGorID::m_lpstr

La clase contiene el valor pasado a cualquiera de sus constructores como un miembro de datos LPCTSTR público.

```
LPCTSTR m_lpstr;
```

##  <a name="_u_stringorid___u_stringorid"></a>  _U_STRINGorID::_U_STRINGorID

El constructor UINT convierte su argumento en un tipo de recurso compatible con las funciones de administración de recursos de Windows mediante la macro MAKEINTRESOURCE y el resultado se almacena en el miembro de datos única de la clase, [m_lpstr](#_u_stringorid__m_lpstr).

```
_U_STRINGorID(UINT nID);
_U_STRINGorID(LPCTSTR lpString);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Un identificador de recurso.

*lpString*<br/>
Un nombre de recurso.

### <a name="remarks"></a>Comentarios

El argumento del constructor LPCTSTR se almacena directamente sin conversión.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
