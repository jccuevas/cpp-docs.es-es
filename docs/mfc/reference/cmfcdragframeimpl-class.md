---
title: CMFCDragFrameImpl Clase
ms.date: 10/18/2018
f1_keywords:
- CMFCDragFrameImpl
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
ms.openlocfilehash: 527fd089962e05c44a7e47b1ae52345116da4470
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752441"
---
# <a name="cmfcdragframeimpl-class"></a>CMFCDragFrameImpl Clase

La `CMFCDragFrameImpl` clase dibuja el rectángulo de arrastre que aparece cuando el usuario arrastra un panel en el modo de acoplamiento estándar.
Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CMFCDragFrameImpl
```

## <a name="remarks"></a>Observaciones

Un objeto de esta clase se incrusta en cada [CPane Clase](../../mfc/reference/cpane-class.md) objeto. Por lo tanto, `CanFloat` cada panel que utiliza el método muestra un rectángulo de arrastre cuando el usuario lo arrastra.

Puede controlar el grosor del rectángulo de arrastre utilizando [AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat) y [AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdragframeimpl.h

## <a name="cmfcdragframeimplenddrawdragframe"></a><a name="enddrawdragframe"></a>CMFCDragFrameImpl::EndDrawDragFrame

```cpp
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```

### <a name="parameters"></a>Parámetros

[en] *bClearInternalRects*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcdragframeimplinit"></a><a name="init"></a>CMFCDragFrameImpl::Init

```cpp
void Init(CWnd* pDraggedWnd);
```

### <a name="parameters"></a>Parámetros

[en] *pDraggedWnd*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcdragframeimplmovedragframe"></a><a name="movedragframe"></a>CMFCDragFrameImpl::MoveDragFrame

```cpp
void MoveDragFrame(BOOL bForceMove = FALSE);
```

### <a name="parameters"></a>Parámetros

[en] *bForceMove*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcdragframeimplplacetabpredocking"></a><a name="placetabpredocking"></a>CMFCDragFrameImpl::PlaceTabPreDocking

```cpp
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,
    BOOL bFirstTime);

void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```

### <a name="parameters"></a>Parámetros

[en] *pTabbedBar*<br/>

[en] *bFirstTime*<br/>

[en] *pCBarToPlaceOn*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcdragframeimplremovetabpredocking"></a><a name="removetabpredocking"></a>CMFCDragFrameImpl::RemoveTabPreDocking

```cpp
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```

### <a name="parameters"></a>Parámetros

[en] *pOldTargetBar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcdragframeimplresetstate"></a><a name="resetstate"></a>CMFCDragFrameImpl::ResetState

```cpp
void ResetState();
```

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)
