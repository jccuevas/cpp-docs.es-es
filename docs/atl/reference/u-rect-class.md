---
title: Clase _U_RECT
ms.date: 11/04/2016
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
ms.openlocfilehash: 8a4d5b2a770b3f0ecfe10be0fbad22a702aa0531
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325808"
---
# <a name="_u_rect-class"></a>Clase _U_RECT

Esta clase de `RECT` adaptador de argumento permite que los punteros o referencias se pasen a una función que se implementa en términos de punteros.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class _U_RECT
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[_U_RECT::_U_RECT](#_u_rect___u_rect)|El constructor.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|Puntero a `RECT`un archivo .|

## <a name="remarks"></a>Observaciones

La clase define dos sobrecargas de constructor: una acepta un `LPRECT` argumento de&**RECT** y la otra acepta un argumento. El primer constructor almacena la dirección del argumento de referencia en el único miembro de datos de la clase, [m_lpRect](#_u_rect__m_lprect). El argumento para el constructor de puntero se almacena directamente sin conversión.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="_u_rectm_lprect"></a><a name="_u_rect__m_lprect"></a>_U_RECT::m_lpRect

La clase contiene el valor pasado a cualquiera `LPRECT` de sus constructores como miembro de datos públicos.

```
LPRECT m_lpRect;
```

## <a name="_u_rect_u_rect"></a><a name="_u_rect___u_rect"></a>_U_RECT::_U_RECT

La dirección del argumento de referencia se almacena en el miembro de datos único de la clase, [m_lpRect](#_u_rect__m_lprect).

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*Rc*<br/>
Referencia `RECT`.

*lpRect*<br/>
Un `RECT` puntero.

### <a name="remarks"></a>Observaciones

El argumento para el constructor de puntero se almacena directamente sin conversión.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
