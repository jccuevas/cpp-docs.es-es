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
ms.openlocfilehash: 593d1665751f7322fc2a9cee307620df88d46876
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376190"
---
# <a name="cmfctoolbarinfo-class"></a>CMFCToolBarInfo (clase)

Contiene los identificadores de recursos de las imágenes de la barra de herramientas en diversos estados. `CMFCToolBarInfo`es una clase auxiliar que se utiliza como parámetro de la [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) método.

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarInfo
```

## <a name="members"></a>Miembros

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|Identificador de recurso del mapa de bits de la barra de herramientas que contiene imágenes de barra de herramientas normales (frías).|
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|ID de recurso del mapa de bits de la barra de herramientas que contiene imágenes de barra de herramientas deshabilitadas.|
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|Id. de recurso del mapa de bits de la barra de herramientas que contiene imágenes de barra de herramientas seleccionadas (calientes).|
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|Id. de recurso del mapa de bits de la barra de herramientas que contiene imágenes de barra de herramientas grandes y regulares.|
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|Id. de recurso del mapa de bits de la barra de herramientas que contiene imágenes de barra de herramientas grandes y deshabilitadas.|
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|Id. de recurso del mapa de bits de la barra de herramientas que contiene imágenes de barra de herramientas grandes seleccionadas.|
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|ID de recurso del mapa de bits de la barra de herramientas que contiene imágenes de menú deshabilitadas.|
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|ID de recurso del mapa de bits de la barra de herramientas que contiene imágenes de menú.|

## <a name="remarks"></a>Observaciones

Un mapa de bits de barra de herramientas completo consta de pequeñas imágenes de barra de herramientas (botones) de un tamaño fijo. Cada identificador de recurso `CMFCToolBarInfo` que se almacena en un objeto es un mapa de bits que contiene un conjunto completo de imágenes de barra de herramientas en un único estado (por ejemplo, imágenes seleccionadas, deshabilitadas, grandes o de menú).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbar.h

## <a name="cmfctoolbarinfom_uicoldresid"></a><a name="m_uicoldresid"></a>CMFCToolBarInfo::m_uiColdResID

Especifica un identificador de recurso para todas las imágenes de botón normales de una barra de herramientas.

```
UINT m_uiColdResID;
```

## <a name="cmfctoolbarinfom_uidisabledresid"></a><a name="m_uidisabledresid"></a>CMFCToolBarInfo::m_uiDisabledResID

Especifica un identificador de recurso para las imágenes no disponibles de un botón de una barra de herramientas.

```
UINT m_uiDisabledResID;
```

## <a name="cmfctoolbarinfom_uihotresid"></a><a name="m_uihotresid"></a>CMFCToolBarInfo::m_uiHotResID

Especifica un identificador de recurso para todas las imágenes de botón resaltadas de una barra de herramientas.

```
UINT m_uiHotResID
```

## <a name="cmfctoolbarinfom_uilargecoldresid"></a><a name="m_uilargecoldresid"></a>CMFCToolBarInfo::m_uiLargeColdResID

Especifica un identificador de recurso para todas las imágenes de botones normales grandes de una barra de herramientas.

```
UINT m_uiLargeColdResID
```

## <a name="cmfctoolbarinfom_uilargedisabledresid"></a><a name="m_uilargedisabledresid"></a>CMFCToolBarInfo::m_uiLargeDisabledResID

Especifica un identificador de recurso para todas las imágenes de botones deshabilitados grandes de una barra de herramientas.

```
UINT m_uiLargeDisabledResID;
```

## <a name="cmfctoolbarinfom_uilargehotresid"></a><a name="m_uilargehotresid"></a>CMFCToolBarInfo::m_uiLargeHotResID

Especifica un identificador de recurso para todas las imágenes resaltadas grandes de una barra de herramientas.

```
UINT m_uiLargeHotResID;
```

## <a name="cmfctoolbarinfom_uimenudisabledresid"></a><a name="m_uimenudisabledresid"></a>CMFCToolBarInfo::m_uiMenuDisabledResID

Especifica un identificador de recurso para las imágenes de comando no disponibles de una barra de herramientas.

```
UINT m_uiMenuDisabledResID;
```

## <a name="cmfctoolbarinfom_uimenuresid"></a><a name="m_uimenuresid"></a>CMFCToolBarInfo::m_uiMenuResID

Especifica un identificador de recurso para todas las imágenes de elemento sin menú normales de una barra de herramientas.

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (Clase)](../../mfc/reference/cmfctoolbar-class.md)
