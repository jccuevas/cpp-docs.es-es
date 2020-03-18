---
title: Clase CContextMenuManager
ms.date: 11/04/2016
f1_keywords:
- CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::AddMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuById
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuByName
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuNames
- AFXCONTEXTMENUMANAGER/CContextMenuManager::LoadState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ResetState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SaveState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SetDontCloseActiveMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ShowPopupMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::TrackPopupMenu
helpviewer_keywords:
- CContextMenuManager [MFC], CContextMenuManager
- CContextMenuManager [MFC], AddMenu
- CContextMenuManager [MFC], GetMenuById
- CContextMenuManager [MFC], GetMenuByName
- CContextMenuManager [MFC], GetMenuNames
- CContextMenuManager [MFC], LoadState
- CContextMenuManager [MFC], ResetState
- CContextMenuManager [MFC], SaveState
- CContextMenuManager [MFC], SetDontCloseActiveMenu
- CContextMenuManager [MFC], ShowPopupMenu
- CContextMenuManager [MFC], TrackPopupMenu
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
ms.openlocfilehash: c8a51a33c69b09d0ecd61520b5f1c9ff18c290a0
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425986"
---
# <a name="ccontextmenumanager-class"></a>Clase CContextMenuManager

El objeto `CContextMenuManager` administra los menús contextuales, también conocidos como menús contextuales.

## <a name="syntax"></a>Sintaxis

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|Construye un objeto `CContextMenuManager`.|
|`CContextMenuManager::~CContextMenuManager`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CContextMenuManager:: AddMenu](#addmenu)|Agrega un nuevo menú contextual.|
|[CContextMenuManager::GetMenuById](#getmenubyid)|Devuelve un identificador para el menú asociado al identificador de recurso proporcionado.|
|[CContextMenuManager::GetMenuByName](#getmenubyname)|Devuelve un identificador para el menú que coincide con el nombre de menú proporcionado.|
|[CContextMenuManager::GetMenuNames](#getmenunames)|Devuelve una lista de nombres de menú.|
|[CContextMenuManager:: LoadState](#loadstate)|Carga los menús contextuales almacenados en el registro de Windows.|
|[CContextMenuManager:: ResetState](#resetstate)|Borra los menús contextuales del administrador de menús contextuales.|
|[CContextMenuManager:: SaveState](#savestate)|Guarda los menús contextuales en el registro de Windows.|
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|Controla si el `CContextMenuManager` cierra el menú contextual activo cuando muestra un nuevo menú contextual.|
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|Muestra el menú contextual especificado.|
|[CContextMenuManager:: TrackPopupMenu](#trackpopupmenu)|Muestra el menú contextual especificado. Devuelve el índice del comando de menú seleccionado.|

## <a name="remarks"></a>Observaciones

`CContextMenuManager` administra los menús contextuales y se asegura de que tienen una apariencia coherente.

No debe crear un objeto `CContextMenuManager` manualmente. El marco de trabajo de la aplicación crea el objeto de `CContextMenuManager`. Sin embargo, debe llamar a [CWinAppEx:: InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) cuando se inicializa la aplicación. Después de inicializar el administrador de contexto, use el método [CWinAppEx:: GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) para obtener un puntero al administrador de contexto de la aplicación.

Puede crear menús contextuales en tiempo de ejecución mediante una llamada a `AddMenu`. Si desea mostrar el menú sin recibir primero los datos proporcionados por el usuario, llame a `ShowPopupMenu`. `TrackPopupMenu` se usa cuando se desea crear un menú y esperar la entrada del usuario. `TrackPopupMenu` devuelve el índice del comando seleccionado o 0 si el usuario salió sin seleccionar nada.

El `CContextMenuManager` también puede guardar y cargar su estado en el registro de Windows.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo agregar un menú a un objeto `CContextMenuManager` y cómo no cerrar el menú emergente activo cuando el objeto `CContextMenuManager` muestra un nuevo menú emergente. Este fragmento de código forma parte del [ejemplo de páginas personalizadas](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcontextmenumanager. h

##  <a name="addmenu"></a>CContextMenuManager:: AddMenu

Agrega un nuevo menú contextual a [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
BOOL AddMenu(
    UINT uiMenuNameResId,
    UINT uiMenuResId);

BOOL AddMenu(
    LPCTSTR lpszName,
    UINT uiMenuResId);
```

### <a name="parameters"></a>Parámetros

*uiMenuNameResId*<br/>
de IDENTIFICADOR de recurso de una cadena que contiene el nombre del nuevo menú.

*uiMenuResId*<br/>
de IDENTIFICADOR del recurso de menú.

*lpszName*<br/>
de Cadena que contiene el nombre del nuevo menú.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método se realizó correctamente; 0 si se produce un error en el método.

### <a name="remarks"></a>Observaciones

Este método produce un error si *uiMenuResId* no es válido o si ya hay otro menú con el mismo nombre en el `CContextMenuManager`.

##  <a name="ccontextmenumanager"></a>CContextMenuManager::CContextMenuManager

Construye un objeto [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) .

```
CContextMenuManager();
```

### <a name="remarks"></a>Observaciones

En la mayoría de los casos, no debe crear una `CContextMenuManager` manualmente. El marco de trabajo de la aplicación crea el objeto de `CContextMenuManager`. Debe llamar a [CWinAppEx:: InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) durante la inicialización de la aplicación. Para obtener un puntero al administrador de contexto, llame a [CWinAppEx:: GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager).

##  <a name="getmenubyid"></a>CContextMenuManager::GetMenuById

Devuelve un identificador para el menú asociado a un identificador de recurso determinado.

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>Parámetros

*nMenuResId*<br/>
de El identificador de recurso para el menú.

### <a name="return-value"></a>Valor devuelto

Identificador del menú o `NULL` asociado si no se encuentra el menú.

##  <a name="getmenubyname"></a>CContextMenuManager::GetMenuByName

Devuelve un identificador para un menú específico.

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
de Cadena que contiene el nombre del menú que se va a recuperar.

*puiOrigResID*<br/>
enuncia Puntero a un UINT. Este parámetro contiene el identificador de recurso del menú especificado, si se encuentra.

### <a name="return-value"></a>Valor devuelto

Identificador del menú que coincide con el nombre especificado por *lpszName*. Es NULL si no hay ningún menú denominado *lpszName*.

### <a name="remarks"></a>Observaciones

Si este método encuentra un menú que coincide con *lpszName*, `GetMenuByName` almacena el identificador de recurso de menú en el parámetro *puiOrigResID*.

##  <a name="getmenunames"></a>CContextMenuManager::GetMenuNames

Devuelve la lista de nombres de menú agregados a [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parámetros

*listOfNames*<br/>
enuncia Referencia a un parámetro [CStringList](../../mfc/reference/cstringlist-class.md) . Este método escribe la lista de nombres de menú en este parámetro.

##  <a name="loadstate"></a>CContextMenuManager:: LoadState

Carga la información asociada a la [clase CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) del registro de Windows.

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
de Cadena que contiene la ruta de acceso relativa de una clave del registro.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

El parámetro *lpszProfileName* no es la ruta de acceso absoluta de una entrada del registro. Se trata de una ruta de acceso relativa que se agrega al final de la clave del registro predeterminada para la aplicación. Para obtener o establecer la clave del registro predeterminada, use los métodos [CWinAppEx:: GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) y [CWinAppEx:: SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) , respectivamente.

Use el método [CContextMenuManager:: SaveState](#savestate) para guardar los menús contextuales en el registro.

##  <a name="resetstate"></a>CContextMenuManager:: ResetState

Borra todos los elementos de los menús contextuales asociados a la [clase CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>Valor devuelto

TRUE si el método es correcto; FALSE si se produce un error.

### <a name="remarks"></a>Observaciones

Este método borra los menús emergentes y los quita del `CContextMenuManager`.

##  <a name="savestate"></a>CContextMenuManager:: SaveState

Guarda la información asociada a la [clase CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) en el registro de Windows.

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
de Cadena que contiene la ruta de acceso relativa de una clave del registro.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

El parámetro *lpszProfileName* no es la ruta de acceso absoluta de una entrada del registro. Se trata de una ruta de acceso relativa que se agrega al final de la clave del registro predeterminada para la aplicación. Para obtener o establecer la clave del registro predeterminada, use los métodos [CWinAppEx:: GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) y [CWinAppEx:: SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) , respectivamente.

Use el método [CContextMenuManager:: Loadstate](#loadstate) para cargar los menús contextuales del registro.

##  <a name="setdontcloseactivemenu"></a>CContextMenuManager::SetDontCloseActiveMenu

Controla si el [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) cierra el menú emergente activo cuando muestra un nuevo menú emergente.

```
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parámetros

*bSet*<br/>
de Parámetro booleano que controla si se debe cerrar el menú emergente activo. Un valor de TRUE indica que el menú emergente activo no está cerrado. FALSE indica que el menú emergente activo está cerrado.

### <a name="remarks"></a>Observaciones

De forma predeterminada, la `CContextMenuManager` cierra el menú emergente activo.

##  <a name="showpopupmenu"></a>CContextMenuManager::ShowPopupMenu

Muestra el menú contextual especificado.

```
virtual BOOL ShowPopupMenu(
    UINT uiMenuResId,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bRightAlign = FALSE);

virtual CMFCPopupMenu* ShowPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bAutoDestroy = TRUE,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>Parámetros

*uiMenuResId*<br/>
de IDENTIFICADOR de recurso del menú que este método mostrará.

*x*<br/>
de Desplazamiento horizontal del menú contextual en coordenadas de cliente.

*y*<br/>
de Desplazamiento vertical del menú contextual en coordenadas de cliente.

*pWndOwner*<br/>
de Puntero a la ventana primaria del menú contextual.

*bOwnMessage*<br/>
de Un parámetro booleano que indica cómo se enrutan los mensajes. Si *bOwnMessage* es false, se utiliza el enrutamiento de MFC estándar. De lo contrario, *pWndOwner* recibe los mensajes.

*hmenuPopup*<br/>
de Identificador del menú que este método va a mostrar.

*bAutoDestroy*<br/>
de Un parámetro booleano que indica si el menú se va A destruir automáticamente.

*bRightAlign*<br/>
de Un parámetro booleano que indica cómo se alinean los elementos de menú. Si *bRightAlign* es true, el menú se alinea a la derecha para el orden de lectura de derecha a izquierda.

### <a name="return-value"></a>Valor devuelto

La primera sobrecarga del método devuelve un valor distinto de cero si el método muestra el menú correctamente; de lo contrario, es 0. La segunda sobrecarga del método devuelve un puntero a [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) si el menú contextual se muestra correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Este método es similar al método [CContextMenuManager:: TrackPopupMenu](#trackpopupmenu) en que ambos métodos muestran un menú contextual. Sin embargo, `TrackPopupMenu` devuelve el índice del comando de menú seleccionado.

Si el parámetro *bAutoDestroy* es false, debe llamar manualmente al método `DestroyMenu` heredado para liberar recursos de memoria. La implementación predeterminada de `ShowPopupMenu` no usa el parámetro *bAutoDestroy*. Se proporciona para un uso futuro o para clases personalizadas derivadas de la clase `CContextMenuManager`.

##  <a name="trackpopupmenu"></a>CContextMenuManager:: TrackPopupMenu

Muestra el menú contextual especificado y devuelve el índice del comando de menú contextual seleccionado.

```
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>Parámetros

*hmenuPopup*<br/>
de Identificador del menú contextual que muestra este método.

*x*<br/>
de Desplazamiento horizontal del menú contextual en coordenadas de cliente.

*y*<br/>
de Desplazamiento vertical del menú contextual en coordenadas de cliente.

*pWndOwner*<br/>
de Puntero a la ventana primaria del menú contextual.

*bRightAlign*<br/>
de Un parámetro booleano que indica cómo se alinean los elementos de menú. Si *bRightAlign* es true, el menú se alinea a la derecha para el orden de lectura de derecha a izquierda. Si *bRightAlign* es false, el menú se alinea a la izquierda para el orden de lectura de izquierda a derecha.

### <a name="return-value"></a>Valor devuelto

IDENTIFICADOR de comando de menú del comando que el usuario elige; 0 si el usuario cierra el menú contextual sin seleccionar un comando de menú.

### <a name="remarks"></a>Observaciones

Este método funciona como una llamada modal para mostrar un menú contextual. La aplicación no continuará hasta la siguiente línea en el código hasta que el usuario cierre el menú contextual o seleccione un comando. Un método alternativo que puede usar para mostrar un menú contextual es [CContextMenuManager:: ShowPopupMenu](#showpopupmenu). Ese método no es una llamada modal y no devolverá el identificador del comando seleccionado.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx (clase)](../../mfc/reference/cwinappex-class.md)
