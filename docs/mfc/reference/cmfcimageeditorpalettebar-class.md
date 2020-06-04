---
title: CMFCImageEditorPaletteBar (Clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::GetRowHeight
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable
helpviewer_keywords:
- CMFCImageEditorPaletteBar [MFC], GetRowHeight
- CMFCImageEditorPaletteBar [MFC], IsButtonExtraSizeAvailable
ms.assetid: 3fb7ba8e-f254-4d56-b913-9941b4ed8138
ms.openlocfilehash: 33d4bc0c72718d028031ac11bc67da6aec5e4907
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374427"
---
# <a name="cmfcimageeditorpalettebar-class"></a>CMFCImageEditorPaletteBar (Clase)

Proporciona funcionalidad de barra de paletas a un cuadro de diálogo del editor de imágenes.

## <a name="syntax"></a>Sintaxis

```
class CMFCImageEditorPaletteBar : public CMFCToolBar
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCImageEditorPaletteBar::GetRowHeight](#getrowheight)|Devuelve el alto de los botones de la barra de herramientas. (Reemplaza [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Determina si la barra de herramientas puede mostrar botones que tienen bordes extendidos. (Reemplaza [CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|

### <a name="remarks"></a>Observaciones

Esta clase no está pensada para utilizarla directamente desde el código.

El marco de trabajo utiliza esta clase para mostrar una barra de paletas en un cuadro de diálogo del editor de imágenes. Para obtener más información sobre el cuadro de diálogo del editor de imágenes, vea [CMFCImageEditorDialog (Clase)](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBa](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCImageEditorPaletteBar](../../mfc/reference/cmfcimageeditorpalettebar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afximageeditordialog.h

## <a name="cmfcimageeditorpalettebargetrowheight"></a><a name="getrowheight"></a>CMFCImageEditorPaletteBar::GetRowHeight

Devuelve el alto de los botones de la barra de herramientas.

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>Valor devuelto

La altura de cada botón de la barra de herramientas.

## <a name="cmfcimageeditorpalettebarisbuttonextrasizeavailable"></a><a name="isbuttonextrasizeavailable"></a>CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable

Determina si la barra de herramientas puede mostrar botones que tienen bordes extendidos.

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>Valor devuelto

Este método devuelve FALSE.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog (Clase)](../../mfc/reference/cmfcimageeditordialog-class.md)
