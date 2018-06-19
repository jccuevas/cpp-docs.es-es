---
title: Estructura de CMFCTabToolTipInfo | Documentos de Microsoft
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
ms.openlocfilehash: fb2d1a139a5bc61d665a28f21ab10979802045b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373734"
---
# <a name="cmfctabtooltipinfo-structure"></a>Estructura de CMFCTabToolTipInfo
Esta estructura proporciona información acerca de la ficha MDI que el usuario sitúa el mouse sobre.  
  
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
 Un puntero a un `CMFCTabToolTipInfo` estructura se pasa como un parámetro de la `AFX_WM_ON_GET_TAB_TOOLTIP` mensaje. Este mensaje se genera cuando se habilitan las fichas MDI y el usuario mantiene el mouse sobre un control de ficha.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo se muestra cómo `CMFCTabToolTipInfo` se utiliza en el [ejemplo de MDITabsDemo: aplicación MDI con fichas de MFC](../../visual-cpp-samples.md).  
  
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
 Índice de la pestaña en la que el usuario sitúa el mouse.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo se muestra cómo `m_nTabIndex` se utiliza en el [ejemplo de MDITabsDemo: aplicación MDI con fichas de MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
##  <a name="m_ptabwnd"></a>  CMFCTabToolTipInfo::m_pTabWnd  
 Un puntero al control de ficha.  
  
```  
CMFCBaseTabCtrl* m_pTabWnd;  
```  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo se muestra cómo `m_pTabWnd` se utiliza en el [ejemplo de MDITabsDemo: aplicación MDI con fichas de MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
##  <a name="m_strtext"></a>  CMFCTabToolTipInfo::m_strText  
 El texto de información sobre herramientas.  
  
```  
CString m_strText;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si la cadena está vacía, no se muestra la información sobre herramientas.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo se muestra cómo `m_strText` se utiliza en el [ejemplo de MDITabsDemo: aplicación MDI con fichas de MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)
