---
title: CMFCToolBarInfo (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo::m_uiColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuResID
helpviewer_keywords:
- CMFCToolBarInfo [MFC], m_uiColdResID
- CMFCToolBarInfo [MFC], m_uiDisabledResID
- CMFCToolBarInfo [MFC], m_uiHotResID
- CMFCToolBarInfo [MFC], m_uiLargeColdResID
- CMFCToolBarInfo [MFC], m_uiLargeDisabledResID
- CMFCToolBarInfo [MFC], m_uiLargeHotResID
- CMFCToolBarInfo [MFC], m_uiMenuDisabledResID
- CMFCToolBarInfo [MFC], m_uiMenuResID
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
ms.openlocfilehash: e1e460fe3efb5401227e91f49d8f7c4f6689fa27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651170"
---
# <a name="cmfctoolbarinfo-class"></a>CMFCToolBarInfo (clase)

Contiene los identificadores de recursos de las imágenes de la barra de herramientas en diversos estados. `CMFCToolBarInfo` es una clase auxiliar que se usa como un parámetro de la [cmfctoolbar:: Loadtoolbarex](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) método.

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarInfo
```

## <a name="members"></a>Miembros

### <a name="data-members"></a>Miembros de datos

|nombre|Descripción|
|----------|-----------------|
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|Identificador de recurso del mapa de bits de barra de herramientas que contiene imágenes normales de barra de herramientas (inactiva).|
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|Identificador de recurso del mapa de bits de barra de herramientas que contiene imágenes de barra de herramientas deshabilitada.|
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|Identificador de recurso del mapa de bits de barra de herramientas que contiene imágenes de barra de herramientas seleccionado (activo).|
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|Identificador de recurso del mapa de bits de barra de herramientas que contiene imágenes de barra de herramientas regulares y grandes.|
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|Id. de recurso del mapa de bits de barra de herramientas que contiene grandes, deshabilita las imágenes de barra de herramientas.|
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|Identificador de recurso del mapa de bits de barra de herramientas que contiene imágenes grandes, seleccionada de barra de herramientas.|
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|Identificador de recurso del mapa de bits de barra de herramientas que contiene imágenes de menú deshabilitado.|
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|Identificador de recurso del mapa de bits de barra de herramientas que contiene imágenes de menú.|

## <a name="remarks"></a>Comentarios

Un mapa de bits de la barra de herramientas completa consta de imágenes pequeñas de la barra de herramientas (botones) de un tamaño fijo. Cada identificador de recurso que se almacena en un `CMFCToolBarInfo` objeto es un mapa de bits que contiene un conjunto completo de las imágenes de barra de herramientas en un único estado (por ejemplo, seleccionado, deshabilitado, grande o imágenes de menú).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbar.h

##  <a name="m_uicoldresid"></a>  CMFCToolBarInfo::m_uiColdResID

Especifica un identificador de recurso para todas las imágenes de botón normal de una barra de herramientas.

```
UINT m_uiColdResID;
```

##  <a name="m_uidisabledresid"></a>  CMFCToolBarInfo::m_uiDisabledResID

Especifica un identificador de recurso para las imágenes disponibles para el botón de barra de herramientas.

```
UINT m_uiDisabledResID;
```

##  <a name="m_uihotresid"></a>  CMFCToolBarInfo::m_uiHotResID

Especifica un identificador de recurso para todas las imágenes del botón resaltado de una barra de herramientas.

```
UINT m_uiHotResID
```

##  <a name="m_uilargecoldresid"></a>  CMFCToolBarInfo::m_uiLargeColdResID

Especifica un identificador de recurso para todas las imágenes de gran tamaño de botón normal de una barra de herramientas.

```
UINT m_uiLargeColdResID
```

##  <a name="m_uilargedisabledresid"></a>  CMFCToolBarInfo::m_uiLargeDisabledResID

Especifica un identificador de recurso para todas las imágenes de gran tamaño de botón deshabilitado de una barra de herramientas.

```
UINT m_uiLargeDisabledResID;
```

##  <a name="m_uilargehotresid"></a>  CMFCToolBarInfo::m_uiLargeHotResID

Especifica un identificador de recurso para todas las imágenes resaltados grandes de una barra de herramientas.

```
UINT m_uiLargeHotResID;
```

##  <a name="m_uimenudisabledresid"></a>  CMFCToolBarInfo::m_uiMenuDisabledResID

Especifica un identificador de recurso para las imágenes disponibles para el comando de una barra de herramientas.

```
UINT m_uiMenuDisabledResID;
```

##  <a name="m_uimenuresid"></a>  CMFCToolBarInfo::m_uiMenuResID

Especifica un identificador de recurso para todas las imágenes de una barra de herramientas de elemento de menú regular.

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)
