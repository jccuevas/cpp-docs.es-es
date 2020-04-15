---
title: CContextMenuManager (clase)
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
ms.openlocfilehash: f322f40beabeb9a837dda01c95e9f950a07585d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369422"
---
# <a name="ccontextmenumanager-class"></a>CContextMenuManager (clase)

El `CContextMenuManager` objeto administra los menús contextuales, también conocidos como menús contextuales.

## <a name="syntax"></a>Sintaxis

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|Construye un objeto `CContextMenuManager`.|
|`CContextMenuManager::~CContextMenuManager`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CContextMenuManager::AddMenu](#addmenu)|Agrega un nuevo menú contextual.|
|[CContextMenuManager::GetMenuById](#getmenubyid)|Devuelve un identificador al menú asociado con el identificador de recurso proporcionado.|
|[CContextMenuManager::GetMenuByName](#getmenubyname)|Devuelve un identificador al menú que coincide con el nombre del menú proporcionado.|
|[CContextMenuManager::GetMenuNames](#getmenunames)|Devuelve una lista de nombres de menú.|
|[CContextMenuManager::LoadState](#loadstate)|Carga los menús contextuales almacenados en el registro de Windows.|
|[CContextMenuManager::ResetState](#resetstate)|Borra los menús contextuales del administrador de menús contextuales.|
|[CContextMenuManager::SaveState](#savestate)|Guarda los menús contextuales en el registro de Windows.|
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|Controla `CContextMenuManager` si se cierra el menú contextual activo cuando se muestra un nuevo menú contextual.|
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|Muestra el menú contextual especificado.|
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|Muestra el menú contextual especificado. Devuelve el índice del comando de menú seleccionado.|

## <a name="remarks"></a>Observaciones

`CContextMenuManager`administra los menús contextuales y se asegura de que tengan una apariencia coherente.

No debe crear `CContextMenuManager` un objeto manualmente. El marco de trabajo `CContextMenuManager` de la aplicación crea el objeto. Sin embargo, debe llamar a [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) cuando se inicializa la aplicación. Después de inicializar el administrador de contexto, utilice el método [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) para obtener un puntero al administrador de contexto de la aplicación.

Puede crear menús contextuales `AddMenu`en tiempo de ejecución llamando a . Si desea mostrar el menú sin recibir `ShowPopupMenu`primero la entrada del usuario, llame a . `TrackPopupMenu`se utiliza cuando se desea crear un menú y esperar a la entrada del usuario. `TrackPopupMenu`devuelve el índice del comando seleccionado o 0 si el usuario salió sin seleccionar nada.

También `CContextMenuManager` puede guardar y cargar su estado en el registro de Windows.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CContextMenuManager` cómo agregar un menú a un objeto y `CContextMenuManager` cómo no cerrar el menú emergente activo cuando el objeto muestra un nuevo menú emergente. Este fragmento de código forma parte del [ejemplo Páginas personalizadas.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcontextmenumanager.h

## <a name="ccontextmenumanageraddmenu"></a><a name="addmenu"></a>CContextMenuManager::AddMenu

Agrega un nuevo menú contextual al [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

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
[en] Identificador de recurso para una cadena que contiene el nombre del nuevo menú.

*uiMenuResId*<br/>
[en] El identificador de recurso de menú.

*lpszName*<br/>
[en] Cadena que contiene el nombre del nuevo menú.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método se realizó correctamente; 0 si se produce un error en el método.

### <a name="remarks"></a>Observaciones

Este método produce un error si *uiMenuResId* no es válido `CContextMenuManager`o si otro menú con el mismo nombre ya está en el archivo .

## <a name="ccontextmenumanagerccontextmenumanager"></a><a name="ccontextmenumanager"></a>CContextMenuManager::CContextMenuManager

Construye un [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) objeto.

```
CContextMenuManager();
```

### <a name="remarks"></a>Observaciones

En la mayoría de los `CContextMenuManager` casos, no debe crear un manualmente. El marco de trabajo `CContextMenuManager` de la aplicación crea el objeto. Debe llamar a [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) durante la inicialización de la aplicación. Para obtener un puntero al administrador de contexto, llame a [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager).

## <a name="ccontextmenumanagergetmenubyid"></a><a name="getmenubyid"></a>CContextMenuManager::GetMenuById

Devuelve un identificador al menú asociado a un identificador de recurso determinado.

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>Parámetros

*nMenuResId*<br/>
[en] El identificador de recurso del menú.

### <a name="return-value"></a>Valor devuelto

Un identificador del menú `NULL` asociado o si no se encuentra el menú.

## <a name="ccontextmenumanagergetmenubyname"></a><a name="getmenubyname"></a>CContextMenuManager::GetMenuByName

Devuelve un identificador a un menú específico.

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
[en] Cadena que contiene el nombre del menú que se va a recuperar.

*puiOrigResID*<br/>
[fuera] Un puntero a un UINT. Este parámetro contiene el identificador de recurso del menú especificado, si se encuentra.

### <a name="return-value"></a>Valor devuelto

Identificador del menú que coincide con el nombre especificado por *lpszName*. NULL si no hay ningún menú denominado *lpszName*.

### <a name="remarks"></a>Observaciones

Si este método encuentra un menú que `GetMenuByName` coincide con *lpszName*, almacena el identificador de recurso de menú en el parámetro *puiOrigResID*.

## <a name="ccontextmenumanagergetmenunames"></a><a name="getmenunames"></a>CContextMenuManager::GetMenuNames

Devuelve la lista de nombres de menú agregados a [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parámetros

*listOfNames*<br/>
[fuera] Una referencia a un [CStringList](../../mfc/reference/cstringlist-class.md) parámetro. Este método escribe la lista de nombres de menú en este parámetro.

## <a name="ccontextmenumanagerloadstate"></a><a name="loadstate"></a>CContextMenuManager::LoadState

Carga información asociada a la [clase CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) desde el registro de Windows.

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
[en] Cadena que contiene la ruta de acceso relativa de una clave del Registro.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El parámetro *lpszProfileName* no es la ruta de acceso absoluta para una entrada del Registro. Es una ruta de acceso relativa que se agrega al final de la clave de registro predeterminada para la aplicación. Para obtener o establecer la clave de registro predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) y [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) respectivamente.

Utilice el método [CContextMenuManager::SaveState](#savestate) para guardar los menús contextuales en el registro.

## <a name="ccontextmenumanagerresetstate"></a><a name="resetstate"></a>CContextMenuManager::ResetState

Borra todos los elementos de los menús contextuales asociados a la [clase CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realiza correctamente; FALSE si se produce un error.

### <a name="remarks"></a>Observaciones

Este método borra los menús emergentes y `CContextMenuManager`los elimina del archivo .

## <a name="ccontextmenumanagersavestate"></a><a name="savestate"></a>CContextMenuManager::SaveState

Guarda la información asociada con la [clase CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) en el registro de Windows.

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
[en] Cadena que contiene la ruta de acceso relativa de una clave del Registro.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El parámetro *lpszProfileName* no es la ruta de acceso absoluta para una entrada del Registro. Es una ruta de acceso relativa que se agrega al final de la clave de registro predeterminada para la aplicación. Para obtener o establecer la clave de registro predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) y [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) respectivamente.

Utilice el método [CContextMenuManager::LoadState](#loadstate) para cargar los menús contextuales desde el registro.

## <a name="ccontextmenumanagersetdontcloseactivemenu"></a><a name="setdontcloseactivemenu"></a>CContextMenuManager::SetDontCloseActiveMenu

Controla si el [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) cierra el menú emergente activo cuando muestra un nuevo menú emergente.

```
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parámetros

*Bset*<br/>
[en] Parámetro booleano que controla si se debe cerrar el menú emergente activo. Un valor de TRUE indica que el menú emergente activo no está cerrado. FALSE indica que el menú emergente activo está cerrado.

### <a name="remarks"></a>Observaciones

De forma `CContextMenuManager` predeterminada, se cierra el menú emergente activo.

## <a name="ccontextmenumanagershowpopupmenu"></a><a name="showpopupmenu"></a>CContextMenuManager::ShowPopupMenu

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
[en] El identificador de recurso del menú que mostrará este método.

*X*<br/>
[en] El desplazamiento horizontal para el menú contextual en las coordenadas de cliente.

*y y*<br/>
[en] El desplazamiento vertical para el menú contextual en las coordenadas de cliente

*pWndOwner*<br/>
[en] Un puntero a la ventana principal del menú contextual.

*bOwnMessage*<br/>
[en] Un parámetro booleano que indica cómo se enrutan los mensajes. Si *bOwnMessage* es FALSE, se utiliza el enrutamiento MFC estándar. De lo contrario, *pWndOwner* recibe los mensajes.

*hmenuPopup*<br/>
[en] El identificador del menú que mostrará este método.

*bAutoDestroy*<br/>
[en] Un parámetro booleano que indica si el menú se destruirá automáticamente.

*bRightAlign*<br/>
[en] Parámetro booleano que indica cómo se alinean los elementos de menú. Si *bRightAlign* es TRUE, el menú está alineado a la derecha para el orden de lectura de derecha a izquierda.

### <a name="return-value"></a>Valor devuelto

La primera sobrecarga del método devuelve distinto de cero si el método muestra el menú correctamente; de lo contrario 0. La segunda sobrecarga del método devuelve un puntero a [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) si el menú contextual se muestra correctamente; NULL.

### <a name="remarks"></a>Observaciones

Este método es similar al método [CContextMenuManager::TrackPopupMenu](#trackpopupmenu) en que ambos métodos muestran un menú contextual. Sin `TrackPopupMenu` embargo, devuelve el índice del comando de menú seleccionado.

Si el parámetro *bAutoDestroy* es FALSE, debe `DestroyMenu` llamar manualmente al método heredado para liberar recursos de memoria. La implementación `ShowPopupMenu` predeterminada de no utiliza el parámetro *bAutoDestroy*. Se proporciona para uso futuro o para `CContextMenuManager` clases personalizadas derivadas de la clase.

## <a name="ccontextmenumanagertrackpopupmenu"></a><a name="trackpopupmenu"></a>CContextMenuManager::TrackPopupMenu

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
[en] Identificador del menú contextual que muestra este método.

*X*<br/>
[en] El desplazamiento horizontal para el menú contextual en las coordenadas de cliente.

*y y*<br/>
[en] El desplazamiento vertical para el menú contextual en coordenadas de cliente.

*pWndOwner*<br/>
[en] Un puntero a la ventana principal del menú contextual.

*bRightAlign*<br/>
[en] Parámetro booleano que indica cómo se alinean los elementos de menú. Si *bRightAlign* es TRUE, el menú está alineado a la derecha para el orden de lectura de derecha a izquierda. Si *bRightAlign* es FALSE, el menú se alinea a la izquierda para el orden de lectura de izquierda a derecha.

### <a name="return-value"></a>Valor devuelto

El ID de comando de menú del comando que el usuario elige; 0 Si el usuario cierra el menú contextual sin seleccionar un comando de menú.

### <a name="remarks"></a>Observaciones

Este método funciona como una llamada modal para mostrar un menú contextual. La aplicación no continuará con la siguiente línea en el código hasta que el usuario cierre el menú contextual o seleccione un comando. Un método alternativo que puede utilizar para mostrar un menú contextual es [CContextMenuManager::ShowPopupMenu](#showpopupmenu). Ese método no es una llamada modal y no devolverá el identificador del comando seleccionado.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CWinAppEx](../../mfc/reference/cwinappex-class.md)
