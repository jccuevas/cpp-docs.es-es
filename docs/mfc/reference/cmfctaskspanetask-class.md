---
title: CMFCTasksPaneTask (clase)
ms.date: 11/19/2018
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
ms.openlocfilehash: 49fccdf161da7deb1fd88a12a107df40bafdae92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375869"
---
# <a name="cmfctaskspanetask-class"></a>CMFCTasksPaneTask (clase)

La `CMFCTasksPaneTask` clase es una clase auxiliar que representa tareas para el control de panel de tareas ( [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)). El objeto de tarea representa un elemento del grupo de tareas ( [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)). Cada tarea puede tener un comando que el marco ejecuta cuando un usuario hace clic en la tarea y en un icono que aparece a la izquierda del nombre de tarea.

## <a name="syntax"></a>Sintaxis

```
class CMFCTasksPaneTask : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCTasksPaneTask::CMFCTasksPaneTask](#cmfctaskspanetask)|Crea e inicializa un objeto `CMFCTasksPaneTask`.|
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCTasksPaneTask::SetACCData](#setaccdata)|Determina los datos de accesibilidad de la tarea actual.|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCTasksPaneTask::m_bAutoDestroyWindow](#m_bautodestroywindow)|Determina si la ventana de tareas se destruye automáticamente.|
|[CMFCTasksPaneTask::m_bIsBold](#m_bisbold)|Determina si el marco de trabajo dibuja una etiqueta de tarea en negrita.|
|[CMFCTasksPaneTask::m_dwUserData](#m_dwuserdata)|Contiene datos definidos por el usuario que el marco de trabajo asocia a la tarea. Establezca en cero si la tarea no tiene datos asociados.|
|[CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)|Identificador de la ventana de tareas.|
|[CMFCTasksPaneTask::m_nIcon](#m_nicon)|El índice de la lista de imágenes de la imagen que muestra el marco de trabajo junto a la tarea.|
|[CMFCTasksPaneTask::m_nWindowHeight](#m_nwindowheight)|Altura de la ventana de tareas. Si la tarea no tiene ninguna ventana de tarea, este valor es cero.|
|[CMFCTasksPaneTask::m_pGroup](#m_pgroup)|Un puntero `CMFCTasksPaneTaskGroup` a la que pertenece esta tarea.|
|[CMFCTasksPaneTask::m_rect](#m_rect)|Especifica el rectángulo delimitador de la tarea.|
|[CMFCTasksPaneTask::m_strName](#m_strname)|El nombre del servidor.|
|[CMFCTasksPaneTask::m_uiCommandID](#m_uicommandid)|Especifica el identificador de comando del comando que se ejecuta el marco de trabajo cuando el usuario hace clic en la tarea. Si este valor no es un identificador de comando válido, la tarea se trata como una etiqueta simple.|

## <a name="remarks"></a>Observaciones

En la ilustración siguiente se muestra un grupo de tareas que contiene tres tareas:

![Grupo de tareas, ampliado](../../mfc/reference/media/nexttaskgrpexpand.png "Grupo de tareas, expandido")

> [!NOTE]
> Si una tarea no tiene un identificador de comando válido, se trata como una etiqueta simple.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxTasksPane.h

## <a name="cmfctaskspanetaskcmfctaskspanetask"></a><a name="cmfctaskspanetask"></a>CMFCTasksPaneTask::CMFCTasksPaneTask

Crea e inicializa un objeto `CMFCTasksPaneTask`.

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

*pGroup*<br/>
Especifica el [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) al que pertenece la tarea.

*lpszName*<br/>
Especifica el nombre de la tarea.

*nIcon*<br/>
Especifica el índice de la imagen de la tarea en la lista de imágenes.

*uiCommandID*<br/>
Especifica el identificador de comando del comando que se ejecuta cuando se hace clic en la tarea.

*dwUserData*<br/>
Datos definidos por el usuario.

*hwndTask*<br/>
Especifica el identificador de la ventana de tareas.

*bAutoDestroyWindow*<br/>
Si es TRUE, la ventana de tareas se destruirá automáticamente.

*nWindowHeight*<br/>
Especifica el alto de la ventana de tareas.

### <a name="remarks"></a>Observaciones

## <a name="cmfctaskspanetaskm_bautodestroywindow"></a><a name="m_bautodestroywindow"></a>CMFCTasksPaneTask::m_bAutoDestroyWindow

Determina si la ventana de tareas se destruye automáticamente.

```
BOOL m_bAutoDestroyWindow;
```

### <a name="remarks"></a>Observaciones

Establecer en TRUE para especificar que la ventana de tarea ( [CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)) debe destruirse automáticamente; de lo contrario, FALSE.

## <a name="cmfctaskspanetaskm_bisbold"></a><a name="m_bisbold"></a>CMFCTasksPaneTask::m_bIsBold

Determina si una etiqueta de tarea se dibuja en negrita.

```
BOOL m_bIsBold;
```

### <a name="remarks"></a>Observaciones

Establezca este miembro en TRUE para mostrar texto en negrita para la etiqueta de tarea.

## <a name="cmfctaskspanetaskm_dwuserdata"></a><a name="m_dwuserdata"></a>CMFCTasksPaneTask::m_dwUserData

Contiene datos definidos por el usuario asociados a la tarea. Establézcalo en cero si no hay datos asociados a la tarea.

```
DWORD m_dwUserData;
```

### <a name="remarks"></a>Observaciones

## <a name="cmfctaskspanetaskm_hwndtask"></a><a name="m_hwndtask"></a>CMFCTasksPaneTask::m_hwndTask

Identificador de la ventana de tareas.

```
HWND m_hwndTask;
```

### <a name="remarks"></a>Observaciones

Para agregar una ventana de tareas, llame a [CMFCTasksPane::AddWindow](../../mfc/reference/cmfctaskspane-class.md#addwindow).

## <a name="cmfctaskspanetaskm_nicon"></a><a name="m_nicon"></a>CMFCTasksPaneTask::m_nIcon

Posición de índice en una lista de imágenes que identifica una imagen que se muestra junto a la tarea especificada.

```
int m_nIcon;
```

### <a name="remarks"></a>Observaciones

La lista de imágenes se establece mediante [CMFCTasksPane::SetIconsList](../../mfc/reference/cmfctaskspane-class.md#seticonslist).

Establézalo `m_nIcon` en -1 si desea mostrar la tarea sin una imagen.

## <a name="cmfctaskspanetaskm_nwindowheight"></a><a name="m_nwindowheight"></a>CMFCTasksPaneTask::m_nWindowHeight

Altura de la ventana de tareas. Si la tarea no tiene ninguna ventana de tarea, este valor es cero.

```
int m_nWindowHeight;
```

### <a name="remarks"></a>Observaciones

## <a name="cmfctaskspanetaskm_pgroup"></a><a name="m_pgroup"></a>CMFCTasksPaneTask::m_pGroup

Puntero a [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) al que pertenece esta tarea.

```
CMFCTasksPaneTaskGroup* m_pGroup;
```

### <a name="remarks"></a>Observaciones

Cada tarea debe tener un grupo primario. Para agregar grupos a un panel de tareas, llame a [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).

## <a name="cmfctaskspanetaskm_rect"></a><a name="m_rect"></a>CMFCTasksPaneTask::m_rect

Especifica el rectángulo delimitador de la tarea.

```
CRect m_rect;
```

### <a name="remarks"></a>Observaciones

El marco de trabajo calcula este valor cuando se dibuja la tarea.

## <a name="cmfctaskspanetaskm_strname"></a><a name="m_strname"></a>CMFCTasksPaneTask::m_strName

El nombre del servidor.

```
CString m_strName;
```

### <a name="remarks"></a>Observaciones

## <a name="cmfctaskspanetaskm_uicommandid"></a><a name="m_uicommandid"></a>CMFCTasksPaneTask::m_uiCommandID

Especifica el identificador de comando del comando que se ejecuta cuando el usuario hace clic en la tarea. Si este valor no es un identificador de comando válido, la tarea se trata como una etiqueta simple.

```
UINT m_uiCommandID;
```

### <a name="remarks"></a>Observaciones

## <a name="cmfctaskspanetasksetaccdata"></a><a name="setaccdata"></a>CMFCTasksPaneTask::SetACCData

Determina los datos de accesibilidad de la tarea actual.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parámetros

*pParent*<br/>
[en] Representa la ventana primaria de la tarea actual.

*datos*<br/>
[fuera] Objeto de `CAccessibilityData` tipo que se rellena con los datos de accesibilidad de la tarea actual.

### <a name="return-value"></a>Valor devuelto

TRUESi el parámetro *de datos* se ha rellenado correctamente con los datos de accesibilidad de la tarea actual; de lo contrario, FALSE.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CObject](../../mfc/reference/cobject-class.md)
