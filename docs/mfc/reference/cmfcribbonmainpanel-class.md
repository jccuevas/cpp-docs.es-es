---
title: CMFCRibbonMainPanel (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::Add
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddRecentFilesList
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToBottom
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToRight
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::GetCommandsFrame
helpviewer_keywords:
- CMFCRibbonMainPanel [MFC], Add
- CMFCRibbonMainPanel [MFC], AddRecentFilesList
- CMFCRibbonMainPanel [MFC], AddToBottom
- CMFCRibbonMainPanel [MFC], AddToRight
- CMFCRibbonMainPanel [MFC], GetCommandsFrame
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
ms.openlocfilehash: e4bd1ab8cffc87d5079518cf9a1d6e430ca40fd9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403599"
---
# <a name="cmfcribbonmainpanel-class"></a>CMFCRibbonMainPanel (clase)

Implementa un panel de cinta de opciones que se muestra al hacer clic en el [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md).

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonMainPanel : public CMFCRibbonPanel
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|Constructor predeterminado.|
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonMainPanel::Add](#add)|Agrega un elemento de la cinta de opciones en el panel izquierdo del panel de botones de la aplicación. (Invalida [cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).)|
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|Agrega una cadena de texto en el menú de lista de archivos recientes.|
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|Agrega un elemento de la cinta de opciones en el panel inferior del panel de la aplicación de cinta.|
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|Agrega un elemento de la cinta de opciones en el panel derecho del panel de botones de la aplicación.|
|`CMFCRibbonMainPanel::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|Devuelve un rectángulo que representa el área del panel principal de la cinta.|
|`CMFCRibbonMainPanel::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|

## <a name="remarks"></a>Comentarios

El marco de trabajo muestra el `CMFCRibbonMainPanel` al abrir el panel de la aplicación. Contiene tres paneles:

- El panel izquierdo contiene comandos asociados, como archivos, **abierto**, **guardar**, **impresión**, y **cerrar**. Para agregar un comando a este panel, llame [CMFCRibbonMainPanel::Add](#add).

- El panel derecho contiene las opciones que modifican el comando que se hace clic en el panel izquierdo. Por ejemplo, si hace clic en **Guardar como** desde el panel izquierdo, el panel derecho puede mostrar tipos de archivo disponibles. Para agregar un elemento a este panel, llame [CMFCRibbonMainPanel::AddToRight](#addtoright).

- El panel inferior contiene botones que le permiten cambiar la configuración de la aplicación y para salir del programa. Para agregar un elemento a este panel, llame [CMFCRibbonMainPanel::AddToBottom](#addtobottom).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

[CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonMainPanel.h

##  <a name="add"></a>  CMFCRibbonMainPanel::Add

Agrega un elemento de la cinta de opciones en el panel izquierdo del panel de botones de la aplicación.

```
virtual void Add(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>Parámetros

*pElem*<br/>
[in, out] Un puntero al elemento de cinta de opciones para agregar el panel principal.

### <a name="remarks"></a>Comentarios

Agrega un elemento de la cinta de opciones en el panel. Los elementos agregados con este método se ubicará en la columna izquierda del panel principal.

##  <a name="addrecentfileslist"></a>  CMFCRibbonMainPanel::AddRecentFilesList

Agrega una cadena de texto en el menú de lista de archivos recientes.

```
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
Especifica la cadena que se agregará a la lista de archivos recientes.

*nWidth*<br/>
Especifica el ancho, en píxeles, del panel de lista de archivos recientes.

### <a name="remarks"></a>Comentarios

##  <a name="addtobottom"></a>  CMFCRibbonMainPanel::AddToBottom

Agrega un elemento de la cinta de opciones en el panel inferior del panel de la aplicación de cinta.

```
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>Parámetros

*pElem*<br/>
[in, out] Un puntero al elemento de cinta de opciones para agregar a la parte inferior del panel principal.

### <a name="remarks"></a>Comentarios

##  <a name="addtoright"></a>  CMFCRibbonMainPanel::AddToRight

Agrega un elemento de la cinta de opciones en el panel derecho del panel de botones de la aplicación.

```
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>Parámetros

*pElem*<br/>
Un puntero a un elemento de la cinta que se agregarán a la derecha del panel principal.

*nWidth*<br/>
Especifica el ancho, en píxeles, del panel derecho.

### <a name="remarks"></a>Comentarios

Utilice esta función para agregar un elemento de la cinta en el panel derecho. Normalmente, el panel derecho muestra la lista de archivos recientes, pero puede agregar aquí cualquier otro elemento de cinta de opciones.

##  <a name="getcommandsframe"></a>  CMFCRibbonMainPanel::GetCommandsFrame

Devuelve un rectángulo que representa el área del panel principal de la cinta.

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>Valor devuelto

Un rectángulo que representa el área del panel principal de la cinta.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel (clase)](../../mfc/reference/cmfcribbonpanel-class.md)
