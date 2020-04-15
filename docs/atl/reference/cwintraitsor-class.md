---
title: Clase CWinTraitsOR
ms.date: 11/04/2016
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
ms.openlocfilehash: 825f79190c6f68cd1372154e4e02f430f545aa48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330279"
---
# <a name="cwintraitsor-class"></a>Clase CWinTraitsOR

Esta clase proporciona un método para estandarizar los estilos utilizados al crear un objeto de ventana.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0,
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```

#### <a name="parameters"></a>Parámetros

*t_dwStyle*<br/>
Estilos de ventana predeterminados.

*t_dwExStyle*<br/>
Estilos de ventana extendidos predeterminados.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|Recupera los estilos `CWinTraitsOR` extendidos para el objeto.|
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|Recupera los estilos `CWinTraitsOR` estándar para el objeto.|

## <a name="remarks"></a>Observaciones

Esta clase de [rasgos](../../atl/understanding-window-traits.md) de ventana proporciona un método sencillo para estandarizar los estilos utilizados para la creación de un objeto de ventana ATL. Utilice una especialización de esta clase como parámetro de plantilla para [CWindowImpl](../../atl/reference/cwindowimpl-class.md) u otra de las clases de ventana de ATL para especificar el conjunto mínimo de estilos estándar y extendidos que se usará para las instancias de esa clase de ventana.

Utilice una especialización de esta plantilla si desea asegurarse de que se establecen determinados estilos para todas las instancias de la clase de ventana, al tiempo que permite que otros estilos se establezcan por instancia en la llamada a [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create).

Si desea proporcionar estilos de ventana predeterminados que se utilizarán solo `CWindowImpl::Create`cuando no se especifique ningún otro estilo en la llamada a , utilice [CWinTraits](../../atl/reference/cwintraits-class.md) en su lugar.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="cwintraitsorgetwndstyle"></a><a name="getwndstyle"></a>CWinTraitsOR::GetWndStyle

Llame a esta función para recuperar una combinación (mediante `CWinTraits` el operador OR lógico) de los estilos estándar del objeto y los estilos predeterminados especificados por *t_dwStyle*.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Estilos utilizados para la creación de una ventana.

### <a name="return-value"></a>Valor devuelto

Una combinación de estilos que se pasan en `t_dwStyle` *dwStyle* y los predeterminados especificados por , mediante el operador OR lógico.

## <a name="cwintraitsorgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraitsOR::GetWndExStyle

Llame a esta función para recuperar una combinación (mediante `CWinTraits` el operador OR lógico) de los estilos extendidos del objeto y los estilos predeterminados especificados por `t_dwStyle`.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Parámetros

*dwExStyle*<br/>
Estilos extendidos utilizados para la creación de una ventana.

### <a name="return-value"></a>Valor devuelto

Una combinación de estilos extendidos que se pasan `t_dwExStyle`en *dwExStyle* y los predeterminados especificados por , mediante el operador OR lógico

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Comprender los rasgos de la ventana](../../atl/understanding-window-traits.md)
