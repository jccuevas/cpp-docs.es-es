---
title: CMFCTabToolTipInfo (estructura)
ms.date: 11/04/2016
f1_keywords:
- CMFCTabToolTipInfo
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
ms.openlocfilehash: a507d1e69b3524074e50fde0e87fc5ebb6e5ca03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367342"
---
# <a name="cmfctabtooltipinfo-structure"></a>CMFCTabToolTipInfo (estructura)

Esta estructura proporciona información sobre la pestaña MDI sobre la que el usuario está pasando el cursor.

## <a name="syntax"></a>Sintaxis

```
struct CMFCTabToolTipInfo
```

## <a name="members"></a>Miembros

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCTabToolTipInfo::m_nTabIndex](#m_ntabindex)|Especifica el índice del control de ficha.|
|[CMFCTabToolTipInfo::m_pTabWnd](#m_ptabwnd)|Un puntero al control de ficha.|
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|Texto de la información sobre herramientas.|

## <a name="remarks"></a>Observaciones

Un puntero `CMFCTabToolTipInfo` a una estructura se pasa como un parámetro del mensaje de AFX_WM_ON_GET_TAB_TOOLTIP. Este mensaje se genera cuando las pestañas MDI están habilitadas y el usuario pasa el cursor sobre un control de ficha.

## <a name="example"></a>Ejemplo

En el ejemplo `CMFCTabToolTipInfo` siguiente se muestra cómo se utiliza en el [ejemplo MDITabsDemo: MFC Tabbed MDI Application](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxbasetabctrl.h

## <a name="cmfctabtooltipinfom_ntabindex"></a><a name="m_ntabindex"></a>CMFCTabToolTipInfo::m_nTabIndex

Especifica el índice del control de ficha.

```
int m_nTabIndex;
```

### <a name="remarks"></a>Observaciones

Indice de la pestaña sobre la que el usuario está pasando el ratón.

### <a name="example"></a>Ejemplo

En el ejemplo `m_nTabIndex` siguiente se muestra cómo se utiliza en el [ejemplo MDITabsDemo: MFC Tabbed MDI Application](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_ptabwnd"></a><a name="m_ptabwnd"></a>CMFCTabToolTipInfo::m_pTabWnd

Un puntero al control de ficha.

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>Ejemplo

En el ejemplo `m_pTabWnd` siguiente se muestra cómo se utiliza en el [ejemplo MDITabsDemo: MFC Tabbed MDI Application](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_strtext"></a><a name="m_strtext"></a>CMFCTabToolTipInfo::m_strText

Texto de la información sobre herramientas.

```
CString m_strText;
```

### <a name="remarks"></a>Observaciones

Si la cadena está vacía, no se muestra la información sobre herramientas.

### <a name="example"></a>Ejemplo

En el ejemplo `m_strText` siguiente se muestra cómo se utiliza en el [ejemplo MDITabsDemo: MFC Tabbed MDI Application](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
