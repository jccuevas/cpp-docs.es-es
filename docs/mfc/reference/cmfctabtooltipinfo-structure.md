---
title: CMFCTabToolTipInfo (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTabToolTipInfo
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21e612615110370922d71e1acaebcda56b2e692e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435459"
---
# <a name="cmfctabtooltipinfo-structure"></a>CMFCTabToolTipInfo (estructura)

Esta estructura proporciona información acerca de la ficha MDI que se está desplazando sobre el usuario.

## <a name="syntax"></a>Sintaxis

```
struct CMFCTabToolTipInfo
```

## <a name="members"></a>Miembros

### <a name="data-members"></a>Miembros de datos

|nombre|Descripción|
|----------|-----------------|
|[CMFCTabToolTipInfo::m_nTabIndex](#m_ntabindex)|Especifica el índice del control de ficha.|
|[CMFCTabToolTipInfo::m_pTabWnd](#m_ptabwnd)|Un puntero al control de ficha.|
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|El texto de información sobre herramientas.|

## <a name="remarks"></a>Comentarios

Un puntero a un `CMFCTabToolTipInfo` estructura se pasa como un parámetro del mensaje AFX_WM_ON_GET_TAB_TOOLTIP. Este mensaje se genera cuando se habilitan las pestañas MDI y el usuario se desplaza sobre un control de ficha.

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra cómo `CMFCTabToolTipInfo` se utiliza en el [ejemplo MDITabsDemo: aplicación de MFC con fichas MDI](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxbasetabctrl.h

##  <a name="m_ntabindex"></a>  CMFCTabToolTipInfo::m_nTabIndex

Especifica el índice del control de ficha.

```
int m_nTabIndex;
```

### <a name="remarks"></a>Comentarios

Índice de la pestaña en el que se está desplazando el usuario.

### <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra cómo `m_nTabIndex` se utiliza en el [ejemplo MDITabsDemo: aplicación de MFC con fichas MDI](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_ptabwnd"></a>  CMFCTabToolTipInfo::m_pTabWnd

Un puntero al control de ficha.

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra cómo `m_pTabWnd` se utiliza en el [ejemplo MDITabsDemo: aplicación de MFC con fichas MDI](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_strtext"></a>  CMFCTabToolTipInfo::m_strText

El texto de información sobre herramientas.

```
CString m_strText;
```

### <a name="remarks"></a>Comentarios

Si la cadena está vacía, no se muestra la información sobre herramientas.

### <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra cómo `m_strText` se utiliza en el [ejemplo MDITabsDemo: aplicación de MFC con fichas MDI](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
