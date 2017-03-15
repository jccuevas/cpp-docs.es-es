---
title: Clase CContextMenuManager | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CContextMenuManager
dev_langs:
- C++
helpviewer_keywords:
- CContextMenuManager class
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
caps.latest.revision: 32
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: fab322d0c60b33454504620170d9c77a98401ec8
ms.lasthandoff: 02/24/2017

---
# <a name="ccontextmenumanager-class"></a>Clase CContextMenuManager
La `CContextMenuManager` objeto administra menús contextuales, también conocidos como menús contextuales.  
  
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
|[CContextMenuManager::GetMenuById](#getmenubyid)|Devuelve un identificador para el menú asociado con el identificador de recurso proporcionado.|  
|[CContextMenuManager::GetMenuByName](#getmenubyname)|Devuelve un identificador para el menú que coincida con el nombre del menú proporcionado.|  
|[CContextMenuManager::GetMenuNames](#getmenunames)|Devuelve una lista de nombres de menú.|  
|[CContextMenuManager::LoadState](#loadstate)|Carga los menús contextuales almacenados en el registro de Windows.|  
|[CContextMenuManager::ResetState](#resetstate)|Borra los menús contextuales del Administrador de menú contextual.|  
|[CContextMenuManager::SaveState](#savestate)|Guarda los menús contextuales en el registro de Windows.|  
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|Controles si el `CContextMenuManager` cierra el menú contextual activo cuando se muestra un nuevo menú contextual.|  
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|Muestra el menú contextual especificado.|  
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|Muestra el menú contextual especificado. Devuelve el índice del comando de menú seleccionado.|  
  
## <a name="remarks"></a>Comentarios  
 `CContextMenuManager`administra los menús contextuales y se asegura de que tengan una apariencia coherente.  
  
 No debería crear un `CContextMenuManager` objeto manualmente. El marco de trabajo de la aplicación crea el `CContextMenuManager` objeto. Sin embargo, debe llamar a [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) cuando se inicializa la aplicación. Después de inicializar el Administrador de contexto, utilice el método [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) para obtener un puntero para el Administrador de contexto de la aplicación.  
  
 Puede crear menús contextuales en tiempo de ejecución mediante una llamada a `AddMenu`. Si desea mostrar el menú sin el primer receptor proporcionados por el usuario, llame a `ShowPopupMenu`. `TrackPopupMenu`se utiliza cuando desea crear un menú y esperar la entrada del usuario. `TrackPopupMenu`Devuelve el índice del comando seleccionado o 0 si el usuario sale sin seleccionar nada.  
  
 El `CContextMenuManager` también se puede guardar y cargar su estado en el registro de Windows.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar un menú a un `CContextMenuManager` objeto y cómo no se puede cerrar el menú emergente activo cuando el `CContextMenuManager` objeto muestra un menú emergente de nuevo. Este fragmento de código forma parte de la [ejemplo Custom Pages](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_CustomPages Nº&4;](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CContextMenuManager`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcontextmenumanager.h  
  
##  <a name="a-nameaddmenua--ccontextmenumanageraddmenu"></a><a name="addmenu"></a>CContextMenuManager::AddMenu  
 Agrega un nuevo menú contextual para el [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).  
  
```  
BOOL AddMenu(
    UINT uiMenuNameResId,  
    UINT uiMenuResId);

 
BOOL AddMenu(
    LPCTSTR lpszName,  
    UINT uiMenuResId);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiMenuNameResId`  
 Un identificador de recurso para una cadena que contiene el nombre del nuevo menú.  
  
 [in] `uiMenuResId`  
 El identificador de recurso de menú.  
  
 [in] `lpszName`  
 Cadena que contiene el nombre del nuevo menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el método se realizó correctamente; 0 si se produce un error en el método.  
  
### <a name="remarks"></a>Comentarios  
 Este método produce un error si `uiMenuResId` no es válida o si otro menú con el mismo nombre ya se encuentra en la `CContextMenuManager`.  
  
##  <a name="a-nameccontextmenumanagera--ccontextmenumanagerccontextmenumanager"></a><a name="ccontextmenumanager"></a>CContextMenuManager::CContextMenuManager  
 Construye un [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) objeto.  
  
```  
CContextMenuManager();
```  
  
### <a name="remarks"></a>Comentarios  
 En la mayoría de los casos, no debería crear un `CContextMenuManager` manualmente. El marco de trabajo de la aplicación crea el `CContextMenuManager` objeto. Debe llamar a [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) durante la inicialización de la aplicación. Para obtener un puntero al administrador de contexto, llame a [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager).  
  
##  <a name="a-namegetmenubyida--ccontextmenumanagergetmenubyid"></a><a name="getmenubyid"></a>CContextMenuManager::GetMenuById  
 Devuelve un identificador para el menú asociado con un identificador de recurso especificado.  
  
```  
HMENU GetMenuById(UINT nMenuResId) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nMenuResId`  
 El identificador de recurso para el menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador del menú asociado o `NULL` si no se encuentra el menú.  
  
##  <a name="a-namegetmenubynamea--ccontextmenumanagergetmenubyname"></a><a name="getmenubyname"></a>CContextMenuManager::GetMenuByName  
 Devuelve un identificador a un menú específico.  
  
```  
HMENU GetMenuByName(
    LPCTSTR lpszName,  
    UINT* puiOrigResID = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszName`  
 Cadena que contiene el nombre del menú que se va a recuperar.  
  
 [out] `puiOrigResID`  
 Puntero a una `UINT`. Este parámetro contiene el identificador de recurso del menú especificado, si se encuentra.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador del menú que coincide con el nombre especificado por `lpszName`. `NULL`Si no hay ningún menú llamado `lpszName`.  
  
### <a name="remarks"></a>Comentarios  
 Si este método encuentra un menú que coincida con `lpszName`, `GetMenuByName` almacena el identificador de recurso de menú en el parámetro `puiOrigResID`.  
  
##  <a name="a-namegetmenunamesa--ccontextmenumanagergetmenunames"></a><a name="getmenunames"></a>CContextMenuManager::GetMenuNames  
 Devuelve la lista de nombres de menú que se agregan a la [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).  
  
```  
void GetMenuNames(CStringList& listOfNames) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `listOfNames`  
 Una referencia a un [objeto CStringList](../../mfc/reference/cstringlist-class.md) parámetro. Este método escribe la lista de nombres de menú para este parámetro.  
  
##  <a name="a-nameloadstatea--ccontextmenumanagerloadstate"></a><a name="loadstate"></a>CContextMenuManager::LoadState  
 Carga la información asociada a la [CContextMenuManager clase](../../mfc/reference/ccontextmenumanager-class.md) del registro de Windows.  
  
```  
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Cadena que contiene la ruta de acceso relativa de una clave del registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El `lpszProfileName` parámetro no es la ruta de acceso absoluta para una entrada del registro. Es una ruta de acceso relativa a la que se agrega al final de la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) y [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) respectivamente.  
  
 Utilice el método [CContextMenuManager::SaveState](#savestate) para guardar los menús contextuales en el registro.  
  
##  <a name="a-nameresetstatea--ccontextmenumanagerresetstate"></a><a name="resetstate"></a>CContextMenuManager::ResetState  
 Borra todos los elementos de los menús contextuales asociados a la [CContextMenuManager clase](../../mfc/reference/ccontextmenumanager-class.md).  
  
```  
virtual BOOL ResetState();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método es correcto; `FALSE` si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Este método borra los menús emergentes y los quita de la `CContextMenuManager`.  
  
##  <a name="a-namesavestatea--ccontextmenumanagersavestate"></a><a name="savestate"></a>CContextMenuManager::SaveState  
 Guarda la información asociada a la [CContextMenuManager clase](../../mfc/reference/ccontextmenumanager-class.md) al registro de Windows.  
  
```  
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Cadena que contiene la ruta de acceso relativa de una clave del registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El `lpszProfileName` parámetro no es la ruta de acceso absoluta para una entrada del registro. Es una ruta de acceso relativa a la que se agrega al final de la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) y [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) respectivamente.  
  
 Utilice el método [CContextMenuManager::LoadState](#loadstate) para cargar los menús contextuales del registro.  
  
##  <a name="a-namesetdontcloseactivemenua--ccontextmenumanagersetdontcloseactivemenu"></a><a name="setdontcloseactivemenu"></a>CContextMenuManager::SetDontCloseActiveMenu  
 Controles si el [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) cierra el menú emergente activo cuando se muestra un menú emergente de nuevo.  
  
```  
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
 Parámetro booleano que controla si se debe cerrar el menú emergente activo. Un valor de `TRUE` indica que no se cierra el menú emergente activo. `FALSE`indica que se cierra el menú emergente activo.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, la `CContextMenuManager` cierra el menú emergente activo.  
  
##  <a name="a-nameshowpopupmenua--ccontextmenumanagershowpopupmenu"></a><a name="showpopupmenu"></a>CContextMenuManager::ShowPopupMenu  
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
 [in] `uiMenuResId`  
 El identificador de recurso del menú que se muestra este método.  
  
 [in] `x`  
 Horizontal de desplazamiento para el menú contextual, en coordenadas de cliente.  
  
 [in] `y`  
 El desplazamiento vertical del menú contextual, en coordenadas de cliente  
  
 [in] `pWndOwner`  
 Puntero a la ventana primaria del menú contextual.  
  
 [in] `bOwnMessage`  
 Parámetro booleano que indica cómo se enrutan los mensajes. Si `bOwnMessage` es `FALSE`, se usa el enrutamiento de MFC estándar. De lo contrario, `pWndOwner` recibe los mensajes.  
  
 [in] `hmenuPopup`  
 El identificador del menú que se mostrará este método.  
  
 [in] `bAutoDestroy`  
 Parámetro booleano que indica si el menú se destruirán automáticamente.  
  
 [in] `bRightAlign`  
 Parámetro booleano que indica cómo se alinean los elementos de menú. Si `bRightAlign` es `TRUE`, el menú está alineado a la derecha para el orden de lectura de derecha a izquierda.  
  
### <a name="return-value"></a>Valor devuelto  
 La primera sobrecarga de método devuelve cero si el método muestra el menú correctamente; en caso contrario, 0. La segunda sobrecarga del método devuelve un puntero a [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) si el menú contextual muestra correctamente; en caso contrario `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Este método es similar al método [CContextMenuManager::TrackPopupMenu](#trackpopupmenu) en que ambos métodos mostrar un menú contextual. Sin embargo, `TrackPopupMenu` devuelve el índice del comando de menú seleccionado.  
  
 Si el parámetro `bAutoDestroy` es `FALSE`, debe llamar manualmente heredadas `DestroyMenu` método para liberar los recursos de memoria. La implementación predeterminada de `ShowPopupMenu` no usa el parámetro `bAutoDestroy`. Se proporciona para su uso futuro o para clases personalizadas derivadas de la `CContextMenuManager` clase.  
  
##  <a name="a-nametrackpopupmenua--ccontextmenumanagertrackpopupmenu"></a><a name="trackpopupmenu"></a>CContextMenuManager::TrackPopupMenu  
 Muestra el menú contextual especificado y devuelve el índice del comando de menú de acceso directo seleccionado.  
  
```  
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,  
    int x,  
    int y,  
    CWnd* pWndOwner,  
    BOOL bRightAlign = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hmenuPopup`  
 El identificador del menú contextual que muestra este método.  
  
 [in] `x`  
 Horizontal de desplazamiento para el menú contextual, en coordenadas de cliente.  
  
 [in] `y`  
 Vertical de desplazamiento para el menú contextual, en coordenadas de cliente.  
  
 [in] `pWndOwner`  
 Puntero a la ventana primaria del menú contextual.  
  
 [in] `bRightAlign`  
 Parámetro booleano que indica cómo se alinean los elementos de menú. Si `bRightAlign` es `TRUE`, el menú está alineado a la derecha para el orden de lectura de derecha a izquierda. Si `bRightAlign` es `FALSE`, el menú está alineado a la izquierda para el orden de lectura de izquierda a derecha.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de comando de menú del comando que el usuario elige; 0 si el usuario cierra el menú contextual sin seleccionar un comando de menú.  
  
### <a name="remarks"></a>Comentarios  
 Este método funciona como una llamada modal para mostrar un menú contextual. La aplicación no continuará en la siguiente línea de código hasta que el usuario cierra el menú contextual o selecciona un comando. Un método alternativo que puede utilizar para mostrar un menú contextual es [CContextMenuManager::ShowPopupMenu](#showpopupmenu). Ese método no es una llamada modal y no devolverá el identificador del comando seleccionado.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CWinAppEx](../../mfc/reference/cwinappex-class.md)

