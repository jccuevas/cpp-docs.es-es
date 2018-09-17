---
title: CMFCTasksPaneTask (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTask::m_bAutoDestroyWindow
- AFXTASKSPANE/CMFCTasksPaneTask::m_bIsBold
- AFXTASKSPANE/CMFCTasksPaneTask::m_dwUserData
- AFXTASKSPANE/CMFCTasksPaneTask::m_hwndTask
- AFXTASKSPANE/CMFCTasksPaneTask::m_nIcon
- AFXTASKSPANE/CMFCTasksPaneTask::m_nWindowHeight
- AFXTASKSPANE/CMFCTasksPaneTask::m_pGroup
- AFXTASKSPANE/CMFCTasksPaneTask::m_rect
- AFXTASKSPANE/CMFCTasksPaneTask::m_strName
- AFXTASKSPANE/CMFCTasksPaneTask::m_uiCommandID
dev_langs:
- C++
helpviewer_keywords:
- CMFCTasksPaneTask [MFC], CMFCTasksPaneTask
- CMFCTasksPaneTask [MFC], SetACCData
- CMFCTasksPaneTask [MFC], m_bAutoDestroyWindow
- CMFCTasksPaneTask [MFC], m_bIsBold
- CMFCTasksPaneTask [MFC], m_dwUserData
- CMFCTasksPaneTask [MFC], m_hwndTask
- CMFCTasksPaneTask [MFC], m_nIcon
- CMFCTasksPaneTask [MFC], m_nWindowHeight
- CMFCTasksPaneTask [MFC], m_pGroup
- CMFCTasksPaneTask [MFC], m_rect
- CMFCTasksPaneTask [MFC], m_strName
- CMFCTasksPaneTask [MFC], m_uiCommandID
ms.assetid: c5a7513b-cd8f-4e2e-b16f-650e1fe30954
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee7c04ee4cd581395ff03763c2ebe50b421986d2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711144"
---
# <a name="cmfctaskspanetask-class"></a>CMFCTasksPaneTask (clase)
El `CMFCTasksPaneTask` clase es una clase auxiliar que representa las tareas para el control de panel de tareas ( [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)). El objeto de tarea representa un elemento en el grupo de tareas ( [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)). Cada tarea puede tener un comando que el marco ejecuta cuando un usuario hace clic en la tarea y en un icono que aparece a la izquierda del nombre de tarea.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCTasksPaneTask : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCTasksPaneTask::CMFCTasksPaneTask](#cmfctaskspanetask)|Crea e inicializa un `CMFCTasksPaneTask` objeto.|  
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCTasksPaneTask::SetACCData](#setaccdata)|Determina los datos de accesibilidad para la tarea actual.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CMFCTasksPaneTask::m_bAutoDestroyWindow](#m_bautodestroywindow)|Determina si la ventana de la tarea se destruye automáticamente.|  
|[CMFCTasksPaneTask::m_bIsBold](#m_bisbold)|Determina si el marco de trabajo dibuja una etiqueta de la tarea en negrita.|  
|[CMFCTasksPaneTask::m_dwUserData](#m_dwuserdata)|Contiene los datos definidos por el usuario que el marco de trabajo se asocia a la tarea. Se establece en cero si la tarea no tiene ningún dato asociado.|  
|[CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)|Identificador de la ventana de tareas.|  
|[CMFCTasksPaneTask::m_nIcon](#m_nicon)|El índice en la lista de imágenes de la imagen que muestra el marco de trabajo junto a la tarea.|  
|[CMFCTasksPaneTask::m_nWindowHeight](#m_nwindowheight)|El alto de la ventana de la tarea. Si la tarea no tiene ninguna ventana de la tarea, este valor es cero.|  
|[CMFCTasksPaneTask::m_pGroup](#m_pgroup)|Un puntero a la `CMFCTasksPaneTaskGroup` que pertenece esta tarea.|  
|[CMFCTasksPaneTask::m_rect](#m_rect)|Especifica el rectángulo delimitador de la tarea.|  
|[CMFCTasksPaneTask::m_strName](#m_strname)|El nombre de la tarea.|  
|[CMFCTasksPaneTask::m_uiCommandID](#m_uicommandid)|Especifica el identificador de comando del comando que el marco de trabajo se ejecuta cuando el usuario hace clic en la tarea. Si este valor no es un identificador de comando válido, la tarea se trata como una etiqueta sencilla.|  
  
## <a name="remarks"></a>Comentarios  
 La siguiente ilustración muestra un grupo de tareas que contiene tres tareas:  
  
 ![Grupo de tareas, expandido](../../mfc/reference/media/nexttaskgrpexpand.png "nexttaskgrpexpand")  
  
> [!NOTE]
>  Si una tarea no tiene un identificador de comando válido, se trata como una etiqueta sencilla.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxTasksPane.h  
  
##  <a name="cmfctaskspanetask"></a>  CMFCTasksPaneTask::CMFCTasksPaneTask  
 Crea e inicializa un `CMFCTasksPaneTask` objeto.  
  
```  
CMFCTasksPaneTask(
    CMFCTasksPaneTaskGroup* pGroup,  
    LPCTSTR lpszName,  
    int nIcon,  
    UINT uiCommandID,  
    DWORD dwUserData = 0,  
    HWND hwndTask = NULL,  
    BOOL bAutoDestroyWindow = FALSE,  
    int nWindowHeight = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *pGroup*  
 Especifica el [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) al que pertenece la tarea.  
  
 *lpszName*  
 Especifica el nombre de la tarea.  
  
 *nIcon*  
 Especifica el índice de imagen de la tarea en la lista de imágenes.  
  
 *uiCommandID*  
 Especifica el identificador de comando del comando que se ejecuta cuando se hace clic en la tarea.  
  
 *dwUserData*  
 Datos definidos por el usuario.  
  
 *hwndTask*  
 Especifica el identificador de la ventana de tareas.  
  
 *bAutoDestroyWindow*  
 Si es TRUE, la ventana de la tarea se va a destruir automáticamente.  
  
 *nWindowHeight*  
 Especifica el alto de la ventana de la tarea.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_bautodestroywindow"></a>  CMFCTasksPaneTask::m_bAutoDestroyWindow  
 Determina si la ventana de la tarea se destruye automáticamente.  
  
```  
BOOL m_bAutoDestroyWindow;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establecer en TRUE para especificar que la ventana de la tarea ( [CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)) se debe destruir automáticamente; en caso contrario, FALSE.  
  
##  <a name="m_bisbold"></a>  CMFCTasksPaneTask::m_bIsBold  
 Determina si una etiqueta de la tarea se dibuja texto en negrita.  
  
```  
BOOL m_bIsBold;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establecer este miembro en True para mostrar texto de la etiqueta de la tarea en negrita.  
  
##  <a name="m_dwuserdata"></a>  CMFCTasksPaneTask::m_dwUserData  
 Contiene los datos definidos por el usuario que está asociados con la tarea. Se establece en cero si no hay datos están asociados con la tarea.  
  
```  
DWORD m_dwUserData;  
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_hwndtask"></a>  CMFCTasksPaneTask::m_hwndTask  
 Identificador de la ventana de tareas.  
  
```  
HWND m_hwndTask;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para agregar una ventana de tareas, llame al [CMFCTasksPane::AddWindow](../../mfc/reference/cmfctaskspane-class.md#addwindow).  
  
##  <a name="m_nicon"></a>  CMFCTasksPaneTask::m_nIcon  
 Posición de índice en una lista de imágenes que identifica una imagen que se muestra al lado de la tarea especificada.  
  
```  
int m_nIcon;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establece la lista de imágenes [CMFCTasksPane::SetIconsList](../../mfc/reference/cmfctaskspane-class.md#seticonslist).  
  
 Establecer `m_nIcon` en -1 si desea que aparezca la tarea sin una imagen.  
  
##  <a name="m_nwindowheight"></a>  CMFCTasksPaneTask::m_nWindowHeight  
 El alto de la ventana de la tarea. Si la tarea no tiene ninguna ventana de la tarea, este valor es cero.  
  
```  
int m_nWindowHeight;  
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_pgroup"></a>  CMFCTasksPaneTask::m_pGroup  
 Puntero a la [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) al que pertenece esta tarea.  
  
```  
CMFCTasksPaneTaskGroup* m_pGroup;  
```  
  
### <a name="remarks"></a>Comentarios  
 Cada tarea debe tener un grupo primario. Agregar grupos a un panel de tareas mediante una llamada a [cmfctaskspane:: addgroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).  
  
##  <a name="m_rect"></a>  CMFCTasksPaneTask::m_rect  
 Especifica el rectángulo delimitador de la tarea.  
  
```  
CRect m_rect;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este valor se calcula el marco de trabajo cuando se dibuje la tarea.  
  
##  <a name="m_strname"></a>  CMFCTasksPaneTask::m_strName  
 El nombre de la tarea.  
  
```  
CString m_strName;  
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_uicommandid"></a>  CMFCTasksPaneTask::m_uiCommandID  
 Especifica el identificador de comando del comando que se ejecuta cuando el usuario hace clic en la tarea. Si este valor no es un identificador de comando válido, la tarea se trata como una etiqueta sencilla.  
  
```  
UINT m_uiCommandID;  
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setaccdata"></a>  CMFCTasksPaneTask::SetACCData  
 Determina los datos de accesibilidad para la tarea actual.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parámetros  
*pParent*<br/>
[in] Representa la ventana primaria de la tarea actual.  
  
*data*<br/>
[out] Un objeto de tipo `CAccessibilityData` que se rellena con los datos de accesibilidad de la tarea actual.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el *datos* parámetro se rellena con los datos de accesibilidad de la tarea actual correctamente; de lo contrario, FALSE.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)
