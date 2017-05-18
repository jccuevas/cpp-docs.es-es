---
title: Estructura de CMFCTabToolTipInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCTabToolTipInfo
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
caps.latest.revision: 27
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b9750cd9369313a3ed6ea9474d401cd0068a75fa
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctabtooltipinfo-structure"></a>CMFCTabToolTipInfo (estructura)
Esta estructura proporciona información sobre la ficha MDI que el usuario sitúa el mouse.  
  
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
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|El texto de información sobre herramientas.|  
  
## <a name="remarks"></a>Comentarios  
 Un puntero a un `CMFCTabToolTipInfo` estructura se pasa como un parámetro de la `AFX_WM_ON_GET_TAB_TOOLTIP` mensaje. Este mensaje se genera cuando se habilitan las fichas MDI y el usuario se desplaza sobre un control de ficha.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `CMFCTabToolTipInfo` se utiliza en el [ejemplo de MDITabsDemo: aplicación MDI con fichas de MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo&#2;](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxbasetabctrl.h  
  
##  <a name="m_ntabindex"></a>CMFCTabToolTipInfo::m_nTabIndex  
 Especifica el índice del control de ficha.  
  
```  
int m_nTabIndex;  
```  
  
### <a name="remarks"></a>Comentarios  
 Índice de la ficha en la que se desplaza el usuario.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `m_nTabIndex` se utiliza en el [ejemplo de MDITabsDemo: aplicación MDI con fichas de MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo&#2;](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
##  <a name="m_ptabwnd"></a>CMFCTabToolTipInfo::m_pTabWnd  
 Un puntero al control de ficha.  
  
```  
CMFCBaseTabCtrl* m_pTabWnd;  
```  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `m_pTabWnd` se utiliza en el [ejemplo de MDITabsDemo: aplicación MDI con fichas de MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo&#2;](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
##  <a name="m_strtext"></a>CMFCTabToolTipInfo::m_strText  
 El texto de información sobre herramientas.  
  
```  
CString m_strText;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si la cadena está vacía, no se muestra la información sobre herramientas.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `m_strText` se utiliza en el [ejemplo de MDITabsDemo: aplicación MDI con fichas de MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo&#2;](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)

