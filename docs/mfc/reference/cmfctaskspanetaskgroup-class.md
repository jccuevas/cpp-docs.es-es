---
title: Clase CMFCTasksPaneTaskGroup | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsBottom
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsCollapsed
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsSpecial
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_lstTasks
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rect
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rectGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_strName
dev_langs:
- C++
helpviewer_keywords:
- CMFCTasksPaneTaskGroup class
ms.assetid: 2111640b-a46e-4b27-b033-29e88632b86a
caps.latest.revision: 33
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
ms.openlocfilehash: 405a69a0c7d8c4179b36e1beec09fdfa7acd2d7b
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctaskspanetaskgroup-class"></a>Clase CMFCTasksPaneTaskGroup
El `CMFCTasksPaneTaskGroup` clase es una clase auxiliar utilizada por la [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) control. Los objetos de tipo `CMFCTasksPaneTaskGroup` representan un *grupo de tareas*. El grupo de tareas es una lista de elementos que el marco muestra en un cuadro independiente con un botón de contraer. El cuadro puede tener una leyenda opcional (nombre de grupo). Si un grupo está contraído, la lista de tareas no está visible.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCTasksPaneTaskGroup : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup](#cmfctaskspanetaskgroup)|Construye un objeto `CMFCTasksPaneTaskGroup`.|  
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::SetACCData](#setaccdata)|Determina los datos de accesibilidad para el grupo de tareas actual.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|Determina si el grupo de tareas está alineado en la parte inferior del control del panel de tareas.|  
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|Determina si se contrae el grupo de tareas.|  
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|Determina si el grupo de tareas es *especial.* El marco de trabajo muestra títulos especiales en un color diferente.|  
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|Contiene la lista interna de tareas.|  
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|Especifica el rectángulo delimitador del título de grupo.|  
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|Especifica el rectángulo delimitador del grupo.|  
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|Especifica el nombre del grupo.|  
  
## <a name="remarks"></a>Comentarios  
 La ilustración siguiente muestra un grupo de tareas expandido:  
  
 ![Grupo de tareas, expandido](../../mfc/reference/media/nexttaskgrpexpand.png "nexttaskgrpexpand")  
  
 La siguiente ilustración muestra un grupo de tareas contraído:  
  
 ![Grupo de tareas contraído](../../mfc/reference/media/nexttaskgrpcollapse.png "nexttaskgrpcollapse")  
  
 La ilustración siguiente muestra un grupo de tareas sin título:  
  
 ![Grupo de tareas sin título](../../mfc/reference/media/nexttaskgrpnocapt.png "nexttaskgrpnocapt")  
  
 La ilustración siguiente muestra dos grupos de tareas. El primer grupo de tareas está marcado como especial estableciendo la `m_bIsSpecial` marca `TRUE`, mientras que el segundo grupo de tareas no es especial. Tenga en cuenta cómo el título para el primer grupo de tareas es más oscuro que el segundo grupo de tareas:  
  
 ![Grupo de tareas especial](../../mfc/reference/media/nexttaskgrpspecial.png "nexttaskgrpspecial")  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxTasksPane.h  
  
##  <a name="cmfctaskspanetaskgroup"></a>CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup  
 Construye un objeto `CMFCTasksPaneTaskGroup`.  
  
```  
CMFCTasksPaneTaskGroup(
    LPCTSTR lpszName,  
    BOOL bIsBottom,  
    BOOL bIsSpecial=FALSE,  
    BOOL bIsCollapsed=FALSE,  
    CMFCTasksPanePropertyPage* pPage=NULL,  
    HICON hIcon=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Especifica el nombre del grupo en el título del grupo.  
  
 `bIsBottom`  
 Especifica si el grupo está alineado en la parte inferior del control del panel de tareas.  
  
 `bIsSpecial`  
 Especifica si el grupo se designa como *especial* y por lo tanto, si el título del grupo se rellena con un color diferente.  
  
 `bIsCollapsed`  
 Especifica si el grupo está contraído.  
  
 `pPage`  
 Especifica la página de propiedades al que pertenece este grupo de tareas.  
  
 `hIcon`  
 Especifica el icono que se muestra en el título del grupo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_bisbottom"></a>CMFCTasksPaneTaskGroup::m_bIsBottom  
 Determina si el grupo de tareas está alineado en la parte inferior del control del panel de tareas.  
  
```  
BOOL m_bIsBottom;  
```  
  
### <a name="remarks"></a>Comentarios  
 Sólo un grupo se puede alinear a la parte inferior del control del panel de tareas. Este grupo de tareas debe agregarse en último lugar. Para obtener más información, consulte [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).  
  
##  <a name="m_biscollapsed"></a>CMFCTasksPaneTaskGroup::m_bIsCollapsed  
 Determina si se contrae el grupo de tareas.  
  
```  
BOOL m_bIsCollapsed;  
```  
  
### <a name="remarks"></a>Comentarios  
 Puede habilitar o deshabilitar la capacidad de contraer grupos en el panel de tareas mediante una llamada a [CMFCTasksPane::EnableGroupCollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse).  
  
##  <a name="m_bisspecial"></a>CMFCTasksPaneTaskGroup::m_bIsSpecial  
 Determina si el grupo de tareas es *especial* y si el título de un grupo de tareas especiales debe ser identificado mediante un color diferente.  
  
```  
BOOL m_bIsSpecial;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si la aplicación está utilizando el tema visual de Windows XP y `m_bIsSpecial` es `FALSE`, el marco llama `DrawThemeBackground` con el `EBP_NORMALGROUPBACKGROUND` marca. Si `m_bIsSpecial` es `TRUE`, el marco llama `DrawThemeBackground` con el `EBP_SPECIALGROUPBACKGROUND` marca.  
  
##  <a name="m_lsttasks"></a>CMFCTasksPaneTaskGroup::m_lstTasks  
 Contiene la lista interna de tareas.  
  
```  
CObList m_lstTasks;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para rellenar esta lista, llame a [CMFCTasksPane::AddTask](../../mfc/reference/cmfctaskspane-class.md#addtask).  
  
##  <a name="m_rect"></a>CMFCTasksPaneTaskGroup::m_rect  
 Especifica el rectángulo delimitador del título de grupo.  
  
```  
CRect m_rect;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este valor se calcula automáticamente por el marco de trabajo.  
  
##  <a name="m_rectgroup"></a>CMFCTasksPaneTaskGroup::m_rectGroup  
 Especifica el rectángulo delimitador del grupo.  
  
```  
CRect m_rectGroup;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este valor se calcula automáticamente el marco de trabajo.  
  
##  <a name="m_strname"></a>CMFCTasksPaneTaskGroup::m_strName  
 Especifica el nombre del grupo.  
  
```  
CString m_strName;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si este valor está vacío, no se muestra el título del grupo y no se puede contraer el grupo.  
  
##  <a name="setaccdata"></a>CMFCTasksPaneTaskGroup::SetACCData  
 Determina los datos de accesibilidad para el grupo de tareas actual.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParent`  
 Representa la ventana principal del grupo de tareas actual.  
  
 [out] `data`  
 Un objeto del tipo `CAccessibilityData` que se rellena con los datos de la accesibilidad del grupo de tareas actual.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el `data` parámetro era correctamente rellenado con los datos de la accesibilidad del grupo de tareas actual; en caso contrario, `FALSE`.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)   
 [Clase CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)   
 [Clase CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)

