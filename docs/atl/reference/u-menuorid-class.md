---
title: Clase _U_MENUorID
ms.date: 11/04/2016
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
ms.openlocfilehash: 419c9e79178db12efe278838ec8630e04ac3c461
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325835"
---
# <a name="_u_menuorid-class"></a>Clase _U_MENUorID

Esta clase proporciona `CreateWindow` contenedores para y `CreateWindowEx`.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class _U_MENUorID
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|El constructor.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|Un identificador de un menú.|

## <a name="remarks"></a>Observaciones

Esta clase de adaptador de argumento permite que los identificadores (UINT) o los identificadores de menú (HBAU) se pasen a una función sin necesidad de una conversión explícita por parte del autor de la llamada.

Esta clase está diseñada para implementar contenedores en la API de Windows, especialmente las funciones [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) y [CreateWindowEx,](/windows/win32/api/winuser/nf-winuser-createwindowexw) que aceptan un argumento HMENU que puede ser un identificador de ventana secundario (UINT) en lugar de un identificador de menú. Por ejemplo, puede ver esta clase en uso como parámetro para [CWindowImpl::Create](cwindowimpl-class.md#create).

La clase define dos sobrecargas de constructor: una acepta un argumento UINT y la otra acepta un argumento HMENU. El argumento UINT se convierte en un HMENU en el constructor y el resultado se almacena en el único miembro de datos de la clase, [m_hMenu](#_u_menuorid__m_hmenu). El argumento para el constructor HMENU se almacena directamente sin conversión.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="_u_menuoridm_hmenu"></a><a name="_u_menuorid__m_hmenu"></a>_U_MENUorID::m_hMenu

La clase contiene el valor pasado a cualquiera de sus constructores como un miembro de datos HMENU público.

```
HMENU m_hMenu;
```

## <a name="_u_menuorid_u_menuorid"></a><a name="_u_menuorid___u_menuorid"></a>_U_MENUorID::_U_MENUorID

El argumento UINT se convierte en un HMENU en el constructor y el resultado se almacena en el único miembro de datos de la clase, [m_hMenu](#_u_menuorid__m_hmenu).

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador de ventana secundaria.

*hMenú*<br/>
Un controlador de menú.

### <a name="remarks"></a>Observaciones

El argumento para el constructor HMENU se almacena directamente sin conversión.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
