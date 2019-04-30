---
title: _U_RECT (clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
ms.openlocfilehash: 306092a00a1e119263f4563eea181d7d3ee2b4b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274530"
---
# <a name="urect-class"></a>_U_RECT (clase)

Esta clase de adaptador de argumento permite `RECT` punteros o referencias a pasarse a una función que se implementa en términos de punteros.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class _U_RECT
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[_U_RECT::_U_RECT](#_u_rect___u_rect)|El constructor.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|Puntero a un `RECT`.|

## <a name="remarks"></a>Comentarios

La clase define dos sobrecargas del constructor: uno acepta un **RECT &** argumento y la otra acepta un `LPRECT` argumento. El primer constructor almacena la dirección del argumento de referencia en el miembro de datos única de la clase, [m_lpRect](#_u_rect__m_lprect). El argumento del constructor de puntero se almacena directamente sin conversión.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="_u_rect__m_lprect"></a>  _U_RECT::m_lpRect

La clase contiene el valor pasado a cualquiera de sus constructores como pública `LPRECT` miembro de datos.

```
LPRECT m_lpRect;
```

##  <a name="_u_rect___u_rect"></a>  _U_RECT::_U_RECT

La dirección del argumento de referencia se almacena en el miembro de datos única de la clase, [m_lpRect](#_u_rect__m_lprect).

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*rc*<br/>
Un `RECT` referencia.

*lpRect*<br/>
Un `RECT` puntero.

### <a name="remarks"></a>Comentarios

El argumento del constructor de puntero se almacena directamente sin conversión.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
