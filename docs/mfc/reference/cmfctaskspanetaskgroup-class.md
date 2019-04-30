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
ms.openlocfilehash: a28f00fb732727ec1334946a9e752679307cd3a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222253"
---
# <a name="cmfctaskspanetaskgroup-class"></a>CMFCTasksPaneTaskGroup (clase)

El `CMFCTasksPaneTaskGroup` clase es una clase auxiliar usada por el [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) control. Los objetos de tipo `CMFCTasksPaneTaskGroup` representan un *grupo de tareas*. El grupo de tareas es una lista de elementos que el marco muestra en un cuadro independiente con un botón de contraer. El cuadro puede tener una leyenda opcional (nombre de grupo). Si un grupo está contraído, la lista de tareas no está visible.

## <a name="syntax"></a>Sintaxis

```
class CMFCTasksPaneTaskGroup : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup](#cmfctaskspanetaskgroup)|Construye un objeto `CMFCTasksPaneTaskGroup`.|
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::SetACCData](#setaccdata)|Determina los datos de accesibilidad para el grupo de tareas actual.|

### <a name="data-members"></a>Miembros de datos

|Name|Descripción|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|Determina si el grupo de tareas se alinea a la parte inferior del control del panel de tareas.|
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|Determina si se contrae el grupo de tareas.|
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|Determina si el grupo de tareas es *especial.* El marco de trabajo muestra los subtítulos especiales en un color diferente.|
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|Contiene la lista interna de tareas.|
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|Especifica el rectángulo delimitador del título de grupo.|
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|Especifica el rectángulo delimitador del grupo.|
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|Especifica el nombre del grupo.|

## <a name="remarks"></a>Comentarios

La siguiente ilustración muestra un grupo de tareas expandido:

![Grupo de tareas, expandido](../../mfc/reference/media/nexttaskgrpexpand.png "grupo de tareas, expandido")

La siguiente ilustración muestra un grupo de tareas contraído:

![Grupo de tareas contraído](../../mfc/reference/media/nexttaskgrpcollapse.png "grupo de tareas contraído")

La siguiente ilustración muestra un grupo de tareas sin título:

![Grupo de tareas sin título](../../mfc/reference/media/nexttaskgrpnocapt.png "grupo de tareas sin título")

La siguiente ilustración muestra dos grupos de tareas. El primer grupo de tareas está marcado como especial estableciendo el `m_bIsSpecial` marca en TRUE, mientras que el segundo grupo de tareas no es especial. Tenga en cuenta cómo el título para el primer grupo de tareas es más oscuro que el segundo grupo de tareas:

![Grupo de tareas especiales](../../mfc/reference/media/nexttaskgrpspecial.png "grupo de tareas especial")

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxTasksPane.h

##  <a name="cmfctaskspanetaskgroup"></a>  CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup

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
Especifica si el grupo está alineado a la parte inferior del control del panel de tareas.

*bIsSpecial*<br/>
Especifica si el grupo se designa como *especial* y por lo tanto, si el título del grupo se rellena con un color diferente.

*bIsCollapsed*<br/>
Especifica si el grupo está contraído.

*pPage*<br/>
Especifica la página de propiedades al que pertenece este grupo de tareas.

*hIcon*<br/>
Especifica el icono que se muestra en el título del grupo.

### <a name="remarks"></a>Comentarios

##  <a name="m_bisbottom"></a>  CMFCTasksPaneTaskGroup::m_bIsBottom

Determina si el grupo de tareas se alinea a la parte inferior del control del panel de tareas.

```
BOOL m_bIsBottom;
```

### <a name="remarks"></a>Comentarios

Solo un grupo se puede alinear a la parte inferior del control del panel de tareas. Este grupo de tareas debe agregarse por última vez. Para obtener más información, consulte [cmfctaskspane:: addgroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).

##  <a name="m_biscollapsed"></a>  CMFCTasksPaneTaskGroup::m_bIsCollapsed

Determina si se contrae el grupo de tareas.

```
BOOL m_bIsCollapsed;
```

### <a name="remarks"></a>Comentarios

Puede habilitar o deshabilitar la capacidad de contraer grupos en el panel de tareas mediante una llamada a [cmfctaskspane:: Enablegroupcollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse).

##  <a name="m_bisspecial"></a>  CMFCTasksPaneTaskGroup::m_bIsSpecial

Determina si el grupo de tareas es *especial* y si el título de un grupo de tareas especiales debe identificarse mediante un color diferente.

```
BOOL m_bIsSpecial;
```

### <a name="remarks"></a>Comentarios

Si la aplicación utiliza el tema visual de Windows XP y `m_bIsSpecial` es FALSE, las llamadas de framework `DrawThemeBackground` con la marca EBP_NORMALGROUPBACKGROUND. Si `m_bIsSpecial` es TRUE, las llamadas de framework `DrawThemeBackground` con la marca EBP_SPECIALGROUPBACKGROUND.

##  <a name="m_lsttasks"></a>  CMFCTasksPaneTaskGroup::m_lstTasks

Contiene la lista interna de tareas.

```
CObList m_lstTasks;
```

### <a name="remarks"></a>Comentarios

Para rellenar esta lista, llame a [cmfctaskspane:: Addtask](../../mfc/reference/cmfctaskspane-class.md#addtask).

##  <a name="m_rect"></a>  CMFCTasksPaneTaskGroup::m_rect

Especifica el rectángulo delimitador del título de grupo.

```
CRect m_rect;
```

### <a name="remarks"></a>Comentarios

Este valor se calcula automáticamente el marco de trabajo.

##  <a name="m_rectgroup"></a>  CMFCTasksPaneTaskGroup::m_rectGroup

Especifica el rectángulo delimitador del grupo.

```
CRect m_rectGroup;
```

### <a name="remarks"></a>Comentarios

Este valor se calcula automáticamente el marco de trabajo.

##  <a name="m_strname"></a>  CMFCTasksPaneTaskGroup::m_strName

Especifica el nombre del grupo.

```
CString m_strName;
```

### <a name="remarks"></a>Comentarios

Si este valor está vacío, no se muestra el título del grupo y no se puede contraer el grupo.

##  <a name="setaccdata"></a>  CMFCTasksPaneTaskGroup::SetACCData

Determina los datos de accesibilidad para el grupo de tareas actual.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parámetros

*pParent*<br/>
[in] Representa la ventana principal del grupo de tareas actual.

*data*<br/>
[out] Un objeto de tipo `CAccessibilityData` que se rellena con los datos de accesibilidad del grupo de tareas actual.

### <a name="return-value"></a>Valor devuelto

TRUE si el *datos* parámetro se rellena con los datos de accesibilidad del grupo de tareas actual correctamente; de lo contrario, FALSE.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTasksPane (clase)](../../mfc/reference/cmfctaskspane-class.md)<br/>
[CMFCTasksPaneTask (clase)](../../mfc/reference/cmfctaskspanetask-class.md)<br/>
[CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)
