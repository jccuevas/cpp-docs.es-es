---
title: CMFCTasksPaneTaskGroup (clase)
ms.date: 11/19/2018
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
helpviewer_keywords:
- CMFCTasksPaneTaskGroup [MFC], CMFCTasksPaneTaskGroup
- CMFCTasksPaneTaskGroup [MFC], SetACCData
- CMFCTasksPaneTaskGroup [MFC], m_bIsBottom
- CMFCTasksPaneTaskGroup [MFC], m_bIsCollapsed
- CMFCTasksPaneTaskGroup [MFC], m_bIsSpecial
- CMFCTasksPaneTaskGroup [MFC], m_lstTasks
- CMFCTasksPaneTaskGroup [MFC], m_rect
- CMFCTasksPaneTaskGroup [MFC], m_rectGroup
- CMFCTasksPaneTaskGroup [MFC], m_strName
ms.assetid: 2111640b-a46e-4b27-b033-29e88632b86a
ms.openlocfilehash: 4c24eba646bede462a5f3cfb85715278cfa7daee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366264"
---
# <a name="cmfctaskspanetaskgroup-class"></a>CMFCTasksPaneTaskGroup (clase)

La `CMFCTasksPaneTaskGroup` clase es una clase auxiliar utilizada por el [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) control. Los objetos de tipo `CMFCTasksPaneTaskGroup` representan un *grupo de tareas*. El grupo de tareas es una lista de elementos que el marco muestra en un cuadro independiente con un botón de contraer. El cuadro puede tener una leyenda opcional (nombre de grupo). Si un grupo está contraído, la lista de tareas no está visible.

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
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|Determina si el grupo de tareas está alineado con la parte inferior del control del panel de tareas.|
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|Determina si el grupo de tareas está contraído.|
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|Determina si el grupo de tareas es *especial.* El marco de trabajo muestra subtítulos especiales en un color diferente.|
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|Contiene la lista interna de tareas.|
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|Especifica el rectángulo delimitador del título del grupo.|
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|Especifica el rectángulo delimitador del grupo.|
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|Especifica el nombre del grupo.|

## <a name="remarks"></a>Observaciones

La siguiente ilustración muestra un grupo de tareas expandido:

![Grupo de tareas, ampliado](../../mfc/reference/media/nexttaskgrpexpand.png "Grupo de tareas, expandido")

En la ilustración siguiente se muestra un grupo de tareas contraído:

![Grupo de tareas contraído](../../mfc/reference/media/nexttaskgrpcollapse.png "Grupo de tareas contraído")

En la ilustración siguiente se muestra un grupo de tareas sin título:

![Grupo de tareas sin título](../../mfc/reference/media/nexttaskgrpnocapt.png "Grupo de tareas sin título")

En la ilustración siguiente se muestran dos grupos de tareas. El primer grupo de tareas se `m_bIsSpecial` marca como especial estableciendo la marca en TRUE, mientras que el segundo grupo de tareas no es especial. Observe cómo el título del primer grupo de tareas es más oscuro que el segundo grupo de tareas:

![Grupo de tareas especial](../../mfc/reference/media/nexttaskgrpspecial.png "Grupo de tareas especial")

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxTasksPane.h

## <a name="cmfctaskspanetaskgroupcmfctaskspanetaskgroup"></a><a name="cmfctaskspanetaskgroup"></a>CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup

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

*lpszName*<br/>
Especifica el nombre del grupo en el título del grupo.

*bIsBottom*<br/>
Especifica si el grupo está alineado con la parte inferior del control del panel de tareas.

*bIsSpecial*<br/>
Especifica si el grupo se designa como *especial* y, por lo tanto, si el título del grupo se rellena con un color diferente.

*bIsCollapsed*<br/>
Especifica si el grupo está contraído.

*pPage*<br/>
Especifica la página de propiedades a la que pertenece este grupo de tareas.

*hIcon*<br/>
Especifica el icono que se muestra en el título del grupo.

### <a name="remarks"></a>Observaciones

## <a name="cmfctaskspanetaskgroupm_bisbottom"></a><a name="m_bisbottom"></a>CMFCTasksPaneTaskGroup::m_bIsBottom

Determina si el grupo de tareas está alineado con la parte inferior del control del panel de tareas.

```
BOOL m_bIsBottom;
```

### <a name="remarks"></a>Observaciones

Solo se puede alinear un grupo con la parte inferior del control del panel de tareas. Este grupo de tareas debe agregarse en último lugar. Para obtener más información, vea [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).

## <a name="cmfctaskspanetaskgroupm_biscollapsed"></a><a name="m_biscollapsed"></a>CMFCTasksPaneTaskGroup::m_bIsCollapsed

Determina si el grupo de tareas está contraído.

```
BOOL m_bIsCollapsed;
```

### <a name="remarks"></a>Observaciones

Puede habilitar o deshabilitar la capacidad de contraer grupos en el panel de tareas llamando a [CMFCTasksPane::EnableGroupCollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse).

## <a name="cmfctaskspanetaskgroupm_bisspecial"></a><a name="m_bisspecial"></a>CMFCTasksPaneTaskGroup::m_bIsSpecial

Determina si el grupo de tareas es *especial* y si el título de un grupo de tareas especial debe identificarse con un color diferente.

```
BOOL m_bIsSpecial;
```

### <a name="remarks"></a>Observaciones

Si la aplicación utiliza el tema `m_bIsSpecial` visual de Windows `DrawThemeBackground` XP y es FALSE, el marco de trabajo llama con la marca EBP_NORMALGROUPBACKGROUND. Si `m_bIsSpecial` es TRUE, `DrawThemeBackground` el marco de trabajo llama con la marca EBP_SPECIALGROUPBACKGROUND.

## <a name="cmfctaskspanetaskgroupm_lsttasks"></a><a name="m_lsttasks"></a>CMFCTasksPaneTaskGroup::m_lstTasks

Contiene la lista interna de tareas.

```
CObList m_lstTasks;
```

### <a name="remarks"></a>Observaciones

Para rellenar esta lista, llame a [CMFCTasksPane::AddTask](../../mfc/reference/cmfctaskspane-class.md#addtask).

## <a name="cmfctaskspanetaskgroupm_rect"></a><a name="m_rect"></a>CMFCTasksPaneTaskGroup::m_rect

Especifica el rectángulo delimitador del título del grupo.

```
CRect m_rect;
```

### <a name="remarks"></a>Observaciones

El marco de trabajo calcula automáticamente este valor.

## <a name="cmfctaskspanetaskgroupm_rectgroup"></a><a name="m_rectgroup"></a>CMFCTasksPaneTaskGroup::m_rectGroup

Especifica el rectángulo delimitador del grupo.

```
CRect m_rectGroup;
```

### <a name="remarks"></a>Observaciones

El marco de trabajo calcula automáticamente este valor.

## <a name="cmfctaskspanetaskgroupm_strname"></a><a name="m_strname"></a>CMFCTasksPaneTaskGroup::m_strName

Especifica el nombre del grupo.

```
CString m_strName;
```

### <a name="remarks"></a>Observaciones

Si este valor está vacío, no se muestra el título del grupo y el grupo no se puede contraer.

## <a name="cmfctaskspanetaskgroupsetaccdata"></a><a name="setaccdata"></a>CMFCTasksPaneTaskGroup::SetACCData

Determina los datos de accesibilidad para el grupo de tareas actual.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parámetros

*pParent*<br/>
[en] Representa la ventana primaria del grupo de tareas actual.

*datos*<br/>
[fuera] Objeto de `CAccessibilityData` tipo que se rellena con los datos de accesibilidad del grupo de tareas actual.

### <a name="return-value"></a>Valor devuelto

TRUESi el parámetro *de datos* se ha rellenado correctamente con los datos de accesibilidad del grupo de tareas actual; de lo contrario, FALSE.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)<br/>
[CMFCTasksPaneTask (clase)](../../mfc/reference/cmfctaskspanetask-class.md)<br/>
[CMFCOutlookBar Clase](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[Clase CObject](../../mfc/reference/cobject-class.md)
