---
title: CWinTraitsOR (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
dev_langs:
- C++
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48303c6115ac1d2314e3038556b8f98330a6182e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062675"
---
# <a name="cwintraitsor-class"></a>CWinTraitsOR (clase)

Esta clase proporciona un método de normalización de los estilos usados al crear un objeto de ventana.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0, 
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```

#### <a name="parameters"></a>Parámetros

*t_dwStyle*<br/>
Estilos de ventana predeterminado.

*t_dwExStyle*<br/>
De forma predeterminada, los estilos de ventana extendidos.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|Recupera los estilos extendidos para el `CWinTraitsOR` objeto.|
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|Recupera los estilos estándar para el `CWinTraitsOR` objeto.|

## <a name="remarks"></a>Comentarios

Esto [rasgos de las ventanas](../../atl/understanding-window-traits.md) clase proporciona un método sencillo para estandarizar los estilos utilizados para la creación de un objeto de ventana ATL. Usar una especialización de esta clase como un parámetro de plantilla [CWindowImpl](../../atl/reference/cwindowimpl-class.md) u otra de las clases de ventana de ATL para especificar el conjunto mínimo de estilos estándares y extendidos que se usará para las instancias de esa clase de ventana.

Usar una especialización de esta plantilla si desea asegurarse de que determinados estilos se establecen para todas las instancias de la clase de ventana al tiempo que permite a otros estilos debe establecerse en una base por instancia en la llamada a [CWindowImpl:: Create](../../atl/reference/cwindowimpl-class.md#create).

Si desea proporcionar predeterminado estilos de ventana que se usará sólo cuando ningún otro estilo se especifica en la llamada a `CWindowImpl::Create`, utilice [CWinTraits](../../atl/reference/cwintraits-class.md) en su lugar.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="getwndstyle"></a>  CWinTraitsOR::GetWndStyle

Llame a esta función para recuperar una combinación (mediante el operador lógico OR) de los estilos estándar de la `CWinTraits` objeto y los estilos predeterminados especificados por *t_dwStyle*.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Estilos utilizados para la creación de una ventana.

### <a name="return-value"></a>Valor devuelto

Una combinación de estilos que se pasan en *dwStyle* y el valor predeterminado los especificados por `t_dwStyle`, mediante el operador lógico OR.

##  <a name="getwndexstyle"></a>  CWinTraitsOR::GetWndExStyle

Llame a esta función para recuperar una combinación (mediante el operador lógico OR) de los estilos extendidos de la `CWinTraits` objeto y los estilos predeterminados especificados por `t_dwStyle`.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Parámetros

*dwExStyle*<br/>
Estilos extendidos que se usa para la creación de una ventana.

### <a name="return-value"></a>Valor devuelto

Una combinación de los estilos extendidos que se pasan en *dwExStyle* y predeterminados especificados por `t_dwExStyle`, mediante el operador lógico OR

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Descripción de rasgos de las ventanas](../../atl/understanding-window-traits.md)

