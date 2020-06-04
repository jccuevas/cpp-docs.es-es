---
title: Clase CWinTraits
ms.date: 11/04/2016
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
ms.openlocfilehash: fd73f733e4eff21da92937d1e1b0cce21552a48c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330312"
---
# <a name="cwintraits-class"></a>Clase CWinTraits

Esta clase proporciona un método para estandarizar los estilos utilizados al crear un objeto de ventana.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```

#### <a name="parameters"></a>Parámetros

*t_dwStyle*<br/>
Estilos de ventana estándar predeterminados.

*t_dwExStyle*<br/>
Estilos de ventana extendidos predeterminados.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWinTraits::GetWndExStyle](#getwndexstyle)|(Estático) Recupera los estilos `CWinTraits` extendidos para el objeto.|
|[CWinTraits::GetWndStyle](#getwndstyle)|(Estático) Recupera los estilos `CWinTraits` estándar para el objeto.|

## <a name="remarks"></a>Observaciones

Esta clase de [rasgos](../../atl/understanding-window-traits.md) de ventana proporciona un método sencillo para estandarizar los estilos utilizados para la creación de un objeto de ventana ATL. Utilice una especialización de esta clase como parámetro de plantilla para [CWindowImpl](../../atl/reference/cwindowimpl-class.md) u otra de las clases de ventana de ATL para especificar los estilos estándar y extendidos predeterminados utilizados para las instancias de esa clase de ventana.

Utilice esta plantilla cuando desee proporcionar estilos de ventana predeterminados que se usarán solo cuando no se especifique ningún otro estilo en la llamada a [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create).

ATL proporciona tres especializaciones predefinidas de esta plantilla para combinaciones de estilos de ventana de uso común:

- `CControlWinTraits`

   Diseñado para una ventana de control estándar. Se utilizan los siguientes estilos estándar: WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN y WS_CLIPSIBLINGS. No hay estilos extendidos.

- `CFrameWinTraits`

   Diseñado para una ventana de marco estándar. Los estilos estándar utilizados incluyen: WS_OVERLAPPEDWINDOW, WS_CLIPCHILDREN y WS_CLIPSIBLINGS. Los estilos extendidos utilizados incluyen: WS_EX_APPWINDOW y WS_EX_WINDOWEDGE.

- `CMDIChildWinTraits`

   Diseñado para una ventana secundaria MDI estándar. Los estilos estándar utilizados incluyen: WS_OVERLAPPEDWINDOW, WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN y WS_CLIPSIBLINGS. Los estilos extendidos utilizados incluyen: WS_EX_MDICHILD.

Si desea asegurarse de que se establecen determinados estilos para todas las instancias de la clase de ventana mientras permite que otros estilos se establezcan por instancia, utilice [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) en su lugar.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="cwintraitsgetwndstyle"></a><a name="getwndstyle"></a>CWinTraits::GetWndStyle

Llame a esta función para `CWinTraits` recuperar los estilos estándar del objeto.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Estilos estándar utilizados para la creación de una ventana. Si *dwStyle* es 0, se`t_dwStyle`devuelven los valores de estilo de plantilla ( ). Si *dwStyle* es distinto de cero, se devuelve *dwStyle.*

### <a name="return-value"></a>Valor devuelto

Los estilos de ventana estándar del objeto.

## <a name="cwintraitsgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraits::GetWndExStyle

Llame a esta función para `CWinTraits` recuperar los estilos extendidos del objeto.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Parámetros

*dwExStyle*<br/>
Estilos extendidos utilizados para la creación de una ventana. Si *dwExStyle* es 0, se`t_dwExStyle`devuelven los valores de estilo de plantilla ( ). Si *dwExStyle* es distinto de cero, se devuelve *dwExStyle.*

### <a name="return-value"></a>Valor devuelto

Los estilos de ventana extendida del objeto.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Comprender los rasgos de la ventana](../../atl/understanding-window-traits.md)
