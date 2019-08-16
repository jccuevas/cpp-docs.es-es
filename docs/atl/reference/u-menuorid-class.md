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
ms.openlocfilehash: 9388ca1751ee27fb25d6751c961d23e5243f2918
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495134"
---
# <a name="_u_menuorid-class"></a>Clase _U_MENUorID

Esta clase proporciona contenedores para `CreateWindow` y. `CreateWindowEx`

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class _U_MENUorID
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|El constructor.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|Identificador de un menú.|

## <a name="remarks"></a>Comentarios

Esta clase de adaptador de argumentos permite pasar identificadores (UINT) o identificadores de menú (HMENUs) a una función sin necesidad de una conversión explícita en la parte del llamador.

Esta clase está diseñada para implementar contenedores en la API de Windows, especialmente las funciones [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) y [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) , las cuales aceptan un argumento HMENU que puede ser un identificador de ventana secundaria (uint) en lugar de un identificador de menú. Por ejemplo, puede ver que esta clase se usa como un parámetro para [CWindowImpl:: Create](cwindowimpl-class.md#create).

La clase define dos sobrecargas de constructor: una acepta un argumento UINT y la otra acepta un argumento HMENU. El argumento UINT simplemente se convierte en un HMENU en el constructor y el resultado almacenado en el miembro de datos de la clase, [m_hMenu](#_u_menuorid__m_hmenu). El argumento para el constructor HMENU se almacena directamente sin conversión.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin. h

##  <a name="_u_menuorid__m_hmenu"></a>  _U_MENUorID::m_hMenu

La clase contiene el valor pasado a cualquiera de sus constructores como un miembro de datos HMENU público.

```
HMENU m_hMenu;
```

##  <a name="_u_menuorid___u_menuorid"></a>  _U_MENUorID::_U_MENUorID

El argumento UINT simplemente se convierte en un HMENU en el constructor y el resultado almacenado en el miembro de datos de la clase, [m_hMenu](#_u_menuorid__m_hmenu).

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador de la ventana secundaria.

*hMenu*<br/>
Un identificador de menú.

### <a name="remarks"></a>Comentarios

El argumento para el constructor HMENU se almacena directamente sin conversión.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
