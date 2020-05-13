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
ms.openlocfilehash: 0fd1cd2fec31f9da0c2bec36d08586780f4f95c3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753569"
---
# <a name="cmfcribbonmainpanel-class"></a>CMFCRibbonMainPanel (clase)

Implementa un panel de la cinta de opciones que se muestra al hacer clic en [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md).

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonMainPanel : public CMFCRibbonPanel
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|Constructor predeterminado.|
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonMainPanel::Add](#add)|Agrega un elemento de la cinta de opciones al panel izquierdo del panel del botón de la aplicación. (Reemplaza [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).)|
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|Agrega una cadena de texto al menú de lista de archivos recientes.|
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|Agrega un elemento de la cinta de opciones al panel inferior del panel de aplicación de la cinta de opciones.|
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|Agrega un elemento de la cinta de opciones al panel derecho del panel del botón de la aplicación.|
|`CMFCRibbonMainPanel::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|Devuelve un rectángulo que representa el área del panel principal de la cinta de opciones.|
|`CMFCRibbonMainPanel::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|

## <a name="remarks"></a>Observaciones

El marco `CMFCRibbonMainPanel` de trabajo muestra el al abrir el panel de aplicación. Contiene tres paneles:

- El panel izquierdo contiene comandos asociados a archivos, como **Abrir**, **Guardar**, **Imprimir**y **Cerrar**. Para agregar un comando a este panel, llame a [CMFCRibbonMainPanel::Add](#add).

- El panel derecho contiene opciones que modifican el comando en el que se hace clic en el panel izquierdo. Por ejemplo, si hace clic en **Guardar como** en el panel izquierdo, el panel derecho puede mostrar los tipos de archivo disponibles. Para agregar un elemento a este panel, llame a [CMFCRibbonMainPanel::AddToRight](#addtoright).

- El panel inferior contiene botones que le permiten cambiar la configuración de la aplicación y salir del programa. Para agregar un elemento a este panel, llame a [CMFCRibbonMainPanel::AddToBottom](#addtobottom).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

[CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonMainPanel.h

## <a name="cmfcribbonmainpaneladd"></a><a name="add"></a>CMFCRibbonMainPanel::Add

Agrega un elemento de la cinta de opciones al panel izquierdo del panel del botón de la aplicación.

```
virtual void Add(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>Parámetros

*pElem*<br/>
[adentro, fuera] Puntero al elemento de la cinta de opciones que se va a agregar al panel principal.

### <a name="remarks"></a>Observaciones

Agrega un elemento de la cinta de opciones al panel. Los elementos añadidos con este método se ubicarán en la columna izquierda del panel principal.

## <a name="cmfcribbonmainpaneladdrecentfileslist"></a><a name="addrecentfileslist"></a>CMFCRibbonMainPanel::AddRecentFilesList

Agrega una cadena de texto al menú de lista de archivos recientes.

```cpp
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
Especifica la cadena que se va a agregar a la lista de archivos recientes.

*nAncho*<br/>
Especifica el ancho, en píxeles, del panel de lista de archivos recientes.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonmainpaneladdtobottom"></a><a name="addtobottom"></a>CMFCRibbonMainPanel::AddToBottom

Agrega un elemento de la cinta de opciones al panel inferior del panel de aplicación de la cinta de opciones.

```cpp
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>Parámetros

*pElem*<br/>
[adentro, fuera] Puntero al elemento de la cinta de opciones que se va a agregar a la parte inferior del panel principal.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonmainpaneladdtoright"></a><a name="addtoright"></a>CMFCRibbonMainPanel::AddToRight

Agrega un elemento de la cinta de opciones al panel derecho del panel del botón de la aplicación.

```cpp
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>Parámetros

*pElem*<br/>
Puntero a un elemento de la cinta de opciones que se agregará al lado derecho del panel principal.

*nAncho*<br/>
Especifica el ancho, en píxeles, del panel derecho.

### <a name="remarks"></a>Observaciones

Utilice esta función para agregar un elemento de la cinta de opciones al panel derecho. El panel derecho normalmente muestra la lista de archivos recientes, pero puede agregar cualquier otro elemento de la cinta de opciones aquí.

## <a name="cmfcribbonmainpanelgetcommandsframe"></a><a name="getcommandsframe"></a>CMFCRibbonMainPanel::GetCommandsFrame

Devuelve un rectángulo que representa el área del panel principal de la cinta de opciones.

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>Valor devuelto

Rectángulo que representa el área del panel principal de la cinta de opciones.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel Clase](../../mfc/reference/cmfcribbonpanel-class.md)
