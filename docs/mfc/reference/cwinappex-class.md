---
title: Clase CWinAppEx | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinAppEx
- AFXWINAPPEX/CWinAppEx
- AFXWINAPPEX/CWinAppEx::CWinAppEx
- AFXWINAPPEX/CWinAppEx::CleanState
- AFXWINAPPEX/CWinAppEx::EnableLoadWindowPlacement
- AFXWINAPPEX/CWinAppEx::EnableTearOffMenus
- AFXWINAPPEX/CWinAppEx::EnableUserTools
- AFXWINAPPEX/CWinAppEx::ExitInstance
- AFXWINAPPEX/CWinAppEx::GetBinary
- AFXWINAPPEX/CWinAppEx::GetContextMenuManager
- AFXWINAPPEX/CWinAppEx::GetDataVersion
- AFXWINAPPEX/CWinAppEx::GetDataVersionMajor
- AFXWINAPPEX/CWinAppEx::GetDataVersionMinor
- AFXWINAPPEX/CWinAppEx::GetInt
- AFXWINAPPEX/CWinAppEx::GetKeyboardManager
- AFXWINAPPEX/CWinAppEx::GetMouseManager
- AFXWINAPPEX/CWinAppEx::GetObject
- AFXWINAPPEX/CWinAppEx::GetRegSectionPath
- AFXWINAPPEX/CWinAppEx::GetRegistryBase
- AFXWINAPPEX/CWinAppEx::GetSectionBinary
- AFXWINAPPEX/CWinAppEx::GetSectionInt
- AFXWINAPPEX/CWinAppEx::GetSectionObject
- AFXWINAPPEX/CWinAppEx::GetSectionString
- AFXWINAPPEX/CWinAppEx::GetShellManager
- AFXWINAPPEX/CWinAppEx::GetString
- AFXWINAPPEX/CWinAppEx::GetTooltipManager
- AFXWINAPPEX/CWinAppEx::GetUserToolsManager
- AFXWINAPPEX/CWinAppEx::InitContextMenuManager
- AFXWINAPPEX/CWinAppEx::InitKeyboardManager
- AFXWINAPPEX/CWinAppEx::InitMouseManager
- AFXWINAPPEX/CWinAppEx::InitShellManager
- AFXWINAPPEX/CWinAppEx::InitTooltipManager
- AFXWINAPPEX/CWinAppEx::IsResourceSmartUpdate
- AFXWINAPPEX/CWinAppEx::IsStateExists
- AFXWINAPPEX/CWinAppEx::LoadState
- AFXWINAPPEX/CWinAppEx::OnAppContextHelp
- AFXWINAPPEX/CWinAppEx::OnViewDoubleClick
- AFXWINAPPEX/CWinAppEx::OnWorkspaceIdle
- AFXWINAPPEX/CWinAppEx::SaveState
- AFXWINAPPEX/CWinAppEx::SetRegistryBase
- AFXWINAPPEX/CWinAppEx::ShowPopupMenu
- AFXWINAPPEX/CWinAppEx::WriteBinary
- AFXWINAPPEX/CWinAppEx::WriteInt
- AFXWINAPPEX/CWinAppEx::WriteObject
- AFXWINAPPEX/CWinAppEx::WriteSectionBinary
- AFXWINAPPEX/CWinAppEx::WriteSectionInt
- AFXWINAPPEX/CWinAppEx::WriteSectionObject
- AFXWINAPPEX/CWinAppEx::WriteSectionString
- AFXWINAPPEX/CWinAppEx::WriteString
- AFXWINAPPEX/CWinAppEx::LoadCustomState
- AFXWINAPPEX/CWinAppEx::LoadWindowPlacement
- AFXWINAPPEX/CWinAppEx::OnClosingMainFrame
- AFXWINAPPEX/CWinAppEx::PreLoadState
- AFXWINAPPEX/CWinAppEx::PreSaveState
- AFXWINAPPEX/CWinAppEx::ReloadWindowPlacement
- AFXWINAPPEX/CWinAppEx::SaveCustomState
- AFXWINAPPEX/CWinAppEx::StoreWindowPlacement
- AFXWINAPPEX/CWinAppEx::m_bForceImageReset
dev_langs:
- C++
helpviewer_keywords:
- CWinAppEx class
ms.assetid: a3d3e053-3e22-463f-9444-c73abb1bb9d7
caps.latest.revision: 37
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
ms.openlocfilehash: 6931f1e794116882722e402c9cb95acec1ebdfd5
ms.lasthandoff: 02/24/2017

---
# <a name="cwinappex-class"></a>Clase CWinAppEx
`CWinAppEx`Controla el estado de la aplicación, guarda el estado en el registro, carga el estado del registro, inicializa los administradores de la aplicación y proporciona vínculos a esos mismos administradores de aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CWinAppEx : public CWinApp  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWinAppEx::CWinAppEx](#cwinappex)|Construye un objeto `CWinAppEx`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWinAppEx::CleanState](#cleanstate)|Quita la información acerca de la aplicación del registro de Windows.|  
|[CWinAppEx::EnableLoadWindowPlacement](#enableloadwindowplacement)|Especifica si la aplicación cargará el tamaño inicial y la ubicación de la ventana de marco principal del registro.|  
|[CWinAppEx::EnableTearOffMenus](#enabletearoffmenus)|Habilita desplazable menús de la aplicación.|  
|[CWinAppEx::EnableUserTools](#enableusertools)|Permite al usuario crear los comandos de menú personalizado en la aplicación.|  
|[CWinAppEx::ExitInstance](#exitinstance)|Llamado por el marco desde el `Run` la función miembro para salir de esta instancia de la aplicación. (Invalida [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).)|  
|[CWinAppEx::GetBinary](#getbinary)|Lee los datos binarios que está asociados con el valor del registro especificado.|  
|[CWinAppEx::GetContextMenuManager](#getcontextmenumanager)|Devuelve un puntero a la plantilla global [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) objeto.|  
|[CWinAppEx::GetDataVersion](#getdataversion)||  
|[CWinAppEx::GetDataVersionMajor](#getdataversionmajor)|Devuelve la versión principal de la aplicación que se guarda en el registro de Windows.|  
|[CWinAppEx::GetDataVersionMinor](#getdataversionminor)|Devuelve la versión secundaria de la aplicación que se guarda en el registro de Windows.|  
|[CWinAppEx::GetInt](#getint)|Lee los datos numéricos que está asociados con el valor especificado en el registro.|  
|[CWinAppEx::GetKeyboardManager](#getkeyboardmanager)|Devuelve un puntero a la plantilla global [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md) objeto.|  
|[CWinAppEx::GetMouseManager](#getmousemanager)|Devuelve un puntero a la plantilla global [CMouseManager](../../mfc/reference/cmousemanager-class.md) objeto.|  
|[CWinAppEx::GetObject](#getobject)|Lee `CObject`-derivada los datos que está asociados con el valor especificado en el registro.|  
|[CWinAppEx::GetRegSectionPath](#getregsectionpath)|Devuelve una cadena que es la ruta de acceso de una clave del registro. Esta ruta de acceso concatena la ruta de acceso relativa proporcionada con la ruta de acceso de la aplicación.|  
|[CWinAppEx::GetRegistryBase](#getregistrybase)|Devuelve la ruta de acceso del registro para la aplicación.|  
|[CWinAppEx::GetSectionBinary](#getsectionbinary)|Lee los datos binarios que está asociados con la clave especificada y el valor del registro.|  
|[CWinAppEx::GetSectionInt](#getsectionint)|Lee datos numéricos del registro asociado a la clave y valor especificados.|  
|[CWinAppEx::GetSectionObject](#getsectionobject)|Lee `CObject` datos que están asociados con la clave especificada y el valor del registro.|  
|[CWinAppEx::GetSectionString](#getsectionstring)|Lee datos de cadena que está asociados con la clave especificada y el valor del registro.|  
|[CWinAppEx::GetShellManager](#getshellmanager)|Devuelve un puntero a la plantilla global [CShellManager](../../mfc/reference/cshellmanager-class.md) objeto.|  
|[CWinAppEx::GetString](#getstring)|Lee datos de cadena que está asociados con el valor especificado en el registro.|  
|[CWinAppEx::GetTooltipManager](#gettooltipmanager)|Devuelve un puntero a la plantilla global [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) objeto.|  
|[CWinAppEx::GetUserToolsManager](#getusertoolsmanager)|Devuelve un puntero a la plantilla global [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) objeto.|  
|[CWinAppEx::InitContextMenuManager](#initcontextmenumanager)|Inicializa el `CContextMenuManager` objeto.|  
|[CWinAppEx::InitKeyboardManager](#initkeyboardmanager)|Inicializa el `CKeyboardManager` objeto.|  
|[CWinAppEx::InitMouseManager](#initmousemanager)|Inicializa el `CMouseManager` objeto.|  
|[CWinAppEx::InitShellManager](#initshellmanager)|Inicializa el `CShellManager` (clase)|  
|[CWinAppEx::InitTooltipManager](#inittooltipmanager)|Inicializa la `CTooltipManager` clase.|  
|[CWinAppEx::IsResourceSmartUpdate](#isresourcesmartupdate)||  
|[CWinAppEx::IsStateExists](#isstateexists)|Indica si la clave especificada está en el registro.|  
|[CWinAppEx::LoadState](#loadstate)|Carga el estado de la aplicación desde el registro.|  
|[CWinAppEx::OnAppContextHelp](#onappcontexthelp)|Llamado por el marco de trabajo cuando el usuario solicita ayuda contextual para el **personalización** cuadro de diálogo.|  
|[CWinAppEx::OnViewDoubleClick](#onviewdoubleclick)|Llama al comando definido por el usuario cuando el usuario hace doble clic en cualquier parte de la aplicación.|  
|[CWinAppEx::OnWorkspaceIdle](#onworkspaceidle)||  
|[CWinAppEx::SaveState](#savestate)|Escribe el estado del marco de la aplicación en el registro de Windows.|  
|[CWinAppEx::SetRegistryBase](#setregistrybase)|Establece la ruta de acceso de la clave del registro de forma predeterminada. Esta clave servirá como raíz para todas las llamadas de registro posteriores.|  
|[CWinAppEx::ShowPopupMenu](#showpopupmenu)|Muestra un menú emergente.|  
|[CWinAppEx::WriteBinary](#writebinary)|Escribe los datos binarios en el valor del registro especificado.|  
|[CWinAppEx::WriteInt](#writeint)|Escribe los datos numéricos en el valor del registro especificado.|  
|[CWinAppEx::WriteObject](#writeobject)|Escribe los datos que se derivan el [CObject (clase)](../../mfc/reference/cobject-class.md) al valor del registro especificado.|  
|[CWinAppEx::WriteSectionBinary](#writesectionbinary)|Escribe los datos binarios en un valor de la clave del registro especificada.|  
|[CWinAppEx::WriteSectionInt](#writesectionint)|Escribe los datos numéricos en un valor de la clave del registro especificada.|  
|[CWinAppEx::WriteSectionObject](#writesectionobject)|Escribe los datos derivados de la `CObject` clase a un valor de la clave del registro especificada.|  
|[CWinAppEx::WriteSectionString](#writesectionstring)|Escribe los datos de cadena en un valor de la clave del registro especificada.|  
|[CWinAppEx::WriteString](#writestring)|Escribe los datos de cadena en el valor del registro especificado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWinAppEx::LoadCustomState](#loadcustomstate)|Lo llama el marco de trabajo cuando el estado de la aplicación se ha cargado.|  
|[CWinAppEx::LoadWindowPlacement](#loadwindowplacement)|Llamado por el marco cuando carga el tamaño y la ubicación de la aplicación desde el registro. Los datos cargados incluyen el tamaño y la ubicación del marco principal en el momento en que la aplicación se cerró por última vez.|  
|[CWinAppEx::OnClosingMainFrame](#onclosingmainframe)|Llamado por el marco de trabajo cuando está procesando una ventana de marco principal `WM_CLOSE`.|  
|[CWinAppEx::PreLoadState](#preloadstate)|El marco de trabajo llama inmediatamente antes de que se carga el estado de aplicación.|  
|[CWinAppEx::PreSaveState](#presavestate)|El marco llama inmediatamente antes de que se guarda el estado de aplicación.|  
|[CWinAppEx::ReloadWindowPlacement](#reloadwindowplacement)|Vuelve a cargar el tamaño y la ubicación de la ventana del Registro proporcionada|  
|[CWinAppEx::SaveCustomState](#savecustomstate)|Llamado por el marco de trabajo cuando escribe el estado de la aplicación en el registro.|  
|[CWinAppEx::StoreWindowPlacement](#storewindowplacement)|Llamado por el marco para escribir el tamaño y la ubicación del marco principal en el registro.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWinAppEx::m_bForceImageReset](#m_bforceimagereset)|Especifica si el marco de trabajo restablece todas las imágenes de la barra de herramientas cuando se cargue la ventana de marco que contiene la barra de herramientas.|  
  
## <a name="remarks"></a>Comentarios  
 Gran parte de la funcionalidad proporcionada por el marco de trabajo MFC depende de la `CWinAppEx` clase. Puede incorporar la `CWinAppEx` clase en la aplicación de dos maneras:  
  
-   Construir un `CWinAppEx` clase en el subproceso principal.  
  
-   Derive la clase de aplicación principal de `CWinAppEx`.  
  
 Después de incorporar `CWinAppEx` en su aplicación, puede inicializar uno de los administradores de la aplicación. Antes de utilizar un administrador de la aplicación, debe inicializar llamando al método initialize adecuado. Para obtener un puntero a un administrador específico, llame al método get asociado. El `CWinAppEx` clase administra los siguientes administradores de aplicación: [CMouseManager clase](../../mfc/reference/cmousemanager-class.md), [CContextMenuManager clase](../../mfc/reference/ccontextmenumanager-class.md), [CKeyboardManager clase](../../mfc/reference/ckeyboardmanager-class.md), [CUserToolsManager clase](../../mfc/reference/cusertoolsmanager-class.md), y [CMenuTearOffManager (clase)](../../mfc/reference/cmenutearoffmanager-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 [CWinAppEx](../../mfc/reference/cwinappex-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwinappex.h  
  
##  <a name="cleanstate"></a>CWinAppEx::CleanState  
 Quita toda la información acerca de la aplicación del registro de Windows.  
  
```  
virtual BOOL CleanState(LPCTSTR lpszSectionName=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszSectionName`  
 Cadena que contiene una ruta de acceso de una clave del registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el método se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método borra los datos de aplicación de una sección concreta del registro. Puede especificar la sección Borrar mediante el parámetro `lpszSectionName`. Si `lpszSectionName` es `NULL`, este método usará la ruta de acceso predeterminada del registro almacenado en la `CWinAppEx` objeto. Para obtener la ruta de acceso del registro de forma predeterminada, use [CWinAppEx::GetRegistryBase](#getregistrybase).  
  
##  <a name="cwinappex"></a>CWinAppEx::CWinAppEx  
 Construye un objeto `CWinAppEx`.  
  
```  
CWinAppEx(BOOL bResourceSmartUpdate = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bResourceSmartUpdate`  
 Parámetro booleano que especifica si el objeto de área de trabajo debe detectar y controlar las actualizaciones de recursos.  
  
### <a name="remarks"></a>Comentarios  
 La `CWinAppEx` clase tiene métodos de inicialización, proporciona funcionalidad para guardar y cargar la información de la aplicación en el registro y controla la configuración global de la aplicación. También le permite utilizar los administradores globales, como la [CKeyboardManager clase](../../mfc/reference/ckeyboardmanager-class.md) y [CUserToolsManager clase](../../mfc/reference/cusertoolsmanager-class.md). Cada aplicación puede tener sólo una instancia de la `CWinAppEx` clase.  
  
##  <a name="enableloadwindowplacement"></a>CWinAppEx::EnableLoadWindowPlacement  
 Especifica si la aplicación cargará el tamaño inicial y la ubicación de la ventana de marco principal del registro.  
  
```  
void EnableLoadWindowPlacement(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 Especifica si la aplicación carga el tamaño inicial y la ubicación de la ventana de marco principal desde el registro.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el tamaño y la ubicación del marco principal se carga desde el registro junto con otras configuraciones de aplicaciones. Esto se produce durante la [CWinAppEx::LoadState](#loadstate). Si no desea cargar la colocación de la ventana inicial del registro, llame a este método con `bEnable` establecido en `false`.  
  
##  <a name="enabletearoffmenus"></a>CWinAppEx::EnableTearOffMenus  
 Crea e inicializa un [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) objeto.  
  
```  
BOOL EnableTearOffMenus(
    LPCTSTR lpszRegEntry,  
    const UINT uiCmdFirst,  
    const UINT uiCmdLast);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszRegEntry`  
 Cadena que contiene la ruta de acceso de una clave del registro. La aplicación utiliza esta clave del registro para almacenar información de los menús desplazable.  
  
 [in] `uiCmdFirst`  
 Identificador de la desactivación del primer menú.  
  
 [in] `uiCmdLast`  
 Identificador de la última arrancar de menú.  
  
### <a name="return-value"></a>Valor devuelto  
 `True`Si el `CMenuTearOffManager` se crea y se inicializa correctamente; `false` si se produce un error o si el `CMenuTearOffManager` ya existe.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para habilitar menús desplazable de la aplicación. Debería llamar a esta función desde `InitInstance`.  
  
##  <a name="enableusertools"></a>CWinAppEx::EnableUserTools  
 Permite al usuario crear los comandos de menú personalizado que reducen las pulsaciones de teclas en la aplicación. Este método crea un [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) objeto.  
  
```  
BOOL EnableUserTools(
    const UINT uiCmdToolsDummy,  
    const UINT uiCmdFirst,  
    const UINT uiCmdLast,  
    CRuntimeClass* pToolRTC = RUNTIME_CLASS(CUserTool),  
    UINT uArgMenuID = 0,  
    UINT uInitDirMenuID = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdToolsDummy`  
 Un entero sin signo que el marco de trabajo se usa como marcador de posición para el identificador de comando del menú de herramientas de usuario.  
  
 [in] `uiCmdFirst`  
 El identificador de comando para el primer comando de la herramienta de usuario.  
  
 [in] `uiCmdLast`  
 El identificador de comando para el último comando de herramienta de usuario.  
  
 [in] `pToolRTC`  
 Una clase que la `CUserToolsManager` objeto se usa para crear nuevas herramientas de usuario.  
  
 [in] `uArgMenuID`  
 El identificador del menú de argumento.  
  
 [in] `uInitDirMenuID`  
 El identificador de menú para el directorio inicial de herramienta.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método crea e inicializa un `CUserToolsManager` objeto; `FALSE` si se produce un error en el método o si un `CUserToolsManager` objeto ya existe.  
  
### <a name="remarks"></a>Comentarios  
 Al habilitar herramientas definidas por el usuario, el marco de trabajo admite automáticamente un menú dinámico que se puede extender durante la personalización. El marco de trabajo asocia cada nuevo elemento con un comando externo. El marco de trabajo, estos comandos invoca cuando el usuario selecciona el elemento apropiado de la **herramientas** menú.  
  
 Cada vez que el usuario agrega un nuevo elemento, el marco de trabajo crea un nuevo objeto. El tipo de clase para el nuevo objeto se define por `pToolRTC`. El `pToolRTC` tipo de clase debe derivarse de la [CUserTool clase](../../mfc/reference/cusertool-class.md).  
  
 Para obtener más información sobre las herramientas de usuario y cómo incorporarlos a su aplicación, consulte [herramientas definidas por el usuario](../../mfc/user-defined-tools.md).  
  
##  <a name="exitinstance"></a>CWinAppEx::ExitInstance  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int ExitInstance();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getbinary"></a>CWinAppEx::GetBinary  
 Lee los datos binarios de una clave del registro especificada.  
  
```  
BOOL GetBinary(
    LPCTSTR lpszEntry,  
    LPBYTE* ppData,  
    UINT* pBytes);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszEntry`  
 Una cadena que contiene el nombre de una clave del registro.  
  
 [out] `ppData`  
 Puntero al búfer que el método rellena con los datos binarios.  
  
 [out] `pBytes`  
 Puntero a un entero sin signo que el método se utiliza para escribir el número de bytes leídos.  
  
### <a name="return-value"></a>Valor devuelto  
 `True`Si es correcto; `false` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Este método lee los datos binarios que se escriben en el registro. Para escribir datos en el registro, utilice los métodos [CWinAppEx::WriteBinary](#writebinary) y [CWinAppEx::WriteSectionBinary](#writesectionbinary).  
  
 El `lpszEntry` parámetro es el nombre de una entrada del registro que se encuentra bajo la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase) respectivamente.  
  
##  <a name="getcontextmenumanager"></a>CWinAppEx::GetContextMenuManager  
 Devuelve un puntero a la plantilla global [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) objeto.  
  
```  
CContextMenuManager* GetContextMenuManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la plantilla global `CContextMenuManager` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si no se inicializa el objeto CContextMenuManager, esta función llama a [CWinAppEx::InitContextMenuManager](#initcontextmenumanager) antes de devolver un puntero.  
  
##  <a name="getdataversion"></a>CWinAppEx::GetDataVersion  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetDataVersion() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getdataversionmajor"></a>CWinAppEx::GetDataVersionMajor  
 Devuelve la versión principal de la aplicación que se guarda en el registro de Windows cuando se llama a [CWinAppEx::SaveState](#savestate).  
  
```  
int GetDataVersionMajor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor entero que contiene el número de versión principal.  
  
##  <a name="getdataversionminor"></a>CWinAppEx::GetDataVersionMinor  
 Devuelve la versión secundaria de la aplicación que se guarda en el registro de Windows cuando se llama a [CWinAppEx::SaveState](#savestate).  
  
```  
int GetDataVersionMinor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor entero que contiene el número de versión secundaria.  
  
##  <a name="getint"></a>CWinAppEx::GetInt  
 Lee datos de entero de una clave del registro especificada.  
  
```  
int GetInt(
    LPCTSTR lpszEntry,  
    int nDefault = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszEntry`  
 Una cadena que contiene el nombre de una entrada del registro.  
  
 [in] `nDefault`  
 El valor predeterminado que devuelve el método si la entrada del registro especificada no existe.  
  
### <a name="return-value"></a>Valor devuelto  
 Los datos del registro si el método se realizó correctamente; de lo contrario, `nDefault`.  
  
### <a name="remarks"></a>Comentarios  
 Este método lee datos enteros desde el registro. Si no hay ningún dato de entero asociado a la clave del Registro indicada por `lpszEntry`, este método devuelve `nDefault`. Para escribir datos en el registro, utilice los métodos [CWinAppEx::WriteSectionInt](#writesectionint) y [CWinAppEx::WriteInt](#writeint).  
  
 El `lpszEntry` parámetro es el nombre de una entrada del registro que se encuentra bajo la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase) respectivamente.  
  
##  <a name="getkeyboardmanager"></a>CWinAppEx::GetKeyboardManager  
 Devuelve un puntero a la plantilla global [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md) objeto.  
  
```  
CKeyboardManager* GetKeyboardManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la plantilla global `CKeyboardManager` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si no se ha inicializado el Administrador de teclado, esta función llama a [CWinAppEx::InitKeyboardManager](#initkeyboardmanager) antes de devolver un puntero.  
  
##  <a name="getmousemanager"></a>CWinAppEx::GetMouseManager  
 Devuelve un puntero a la plantilla global [CMouseManager](../../mfc/reference/cmousemanager-class.md) objeto.  
  
```  
CMouseManager* GetMouseManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la plantilla global `CMouseManager` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si no se ha inicializado el Administrador de mouse, esta función llama a [CWinAppEx::InitMouseManager](#initmousemanager) antes de devolver un puntero.  
  
##  <a name="getobject"></a>CWinAppEx::GetObject  
 Lee [CObject](../../mfc/reference/cobject-class.md)- dervied datos del registro.  
  
```  
BOOL GetObject(
    LPCTSTR lpszEntry,  
    CObject& obj);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszEntry`  
 Cadena que contiene la ruta de acceso relativa de una entrada del registro.  
  
 [out] `obj`  
 Una referencia a un `CObject`. El método usa esta referencia para almacenar los datos del registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el método se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método lee los datos del registro que se deriva de `CObject`. Escribir `CObject` datos en el registro, utilice uno [CWinAppEx::WriteObject](#writeobject) o [CWinAppEx::WriteSectionObject](#writesectionobject).  
  
 El `lpszEntry` parámetro es el nombre de una entrada del registro que se encuentra bajo la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase) respectivamente.  
  
##  <a name="getregistrybase"></a>CWinAppEx::GetRegistryBase  
 Recupera la ruta de acceso de registro predeterminado para la aplicación.  
  
```  
LPCTSTR GetRegistryBase();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Cadena que contiene la ruta de acceso de la ubicación del registro de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Todos los métodos de la [CWinAppEx Class](../../mfc/reference/cwinappex-class.md) que tener acceso el inicio del registro en una ubicación predeterminada. Utilice este método para recuperar una ruta de acceso de la ubicación del registro de forma predeterminada. Utilice [CWinAppEx::SetRegistryBase](#setregistrybase) para cambiar la ubicación del registro de forma predeterminada.  
  
##  <a name="getregsectionpath"></a>CWinAppEx::GetRegSectionPath  
 Crea y devuelve la ruta de acceso absoluta de una clave del registro.  
  
```  
CString GetRegSectionPath(LPCTSTR szSectionAdd = _T(""));
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `szSectionAdd`  
 Cadena que contiene la ruta de acceso relativa de una clave del registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene la ruta de acceso absoluta de una clave del registro.  
  
### <a name="remarks"></a>Comentarios  
 Este método define la ruta de acceso absoluta de la clave del registro anexando la ruta relativa de `szSectionAdd` a la ubicación del registro de forma predeterminada para la aplicación. Para obtener la clave del registro de forma predeterminada, utilice el método [CWinAppEx::GetRegistryBase](#getregistrybase).  
  
##  <a name="getsectionbinary"></a>CWinAppEx::GetSectionBinary  
 Lee datos binarios desde el registro.  
  
```  
BOOL GetSectionBinary(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    LPBYTE* ppData,  
    UINT* pBytes);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszSubSection`  
 Cadena que contiene la ruta de acceso relativa de una clave del registro.  
  
 [in] `lpszEntry`  
 Cadena que contiene el valor que se va a leer.  
  
 [out] `ppData`  
 Un puntero al búfer donde el método almacena los datos.  
  
 [out] `pBytes`  
 Puntero a un entero sin signo. El método escribe el tamaño de `ppData` para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 `True` si es correcto; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método lee los datos binarios que se escriben en el registro mediante los métodos [CWinAppEx::WriteBinary](#writebinary) y [CWinAppEx::WriteSectionBinary](#writesectionbinary).  
  
 El `lpszSubSection` parámetro no es una ruta de acceso absoluta para una entrada del registro. Es una ruta de acceso relativa que se anexa al final de la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase) respectivamente.  
  
##  <a name="getsectionint"></a>CWinAppEx::GetSectionInt  
 Lee datos enteros desde el registro.  
  
```  
int GetSectionInt(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    int nDefault = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszSubSection`  
 Cadena que contiene la ruta de acceso relativa de una clave del registro.  
  
 [in] `lpszEntry`  
 Cadena que contiene el valor que se va a leer.  
  
 [in] `nDefault`  
 El valor predeterminado para devolver si el valor especificado no existe.  
  
### <a name="return-value"></a>Valor devuelto  
 Los datos de entero que se almacenan en el valor del registro especificada; `nDefault` si los datos no existen.  
  
### <a name="remarks"></a>Comentarios  
 Utilice los métodos [CWinAppEx::WriteInt](#writeint) y [CWinAppEx::WriteSectionInt](#writesectionint) para escribir datos de entero en el registro.  
  
 El `lpszSubSection` parámetro no es una ruta de acceso absoluta de una entrada del registro. Es una ruta de acceso relativa a la que se agrega al final de la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase) respectivamente.  
  
##  <a name="getsectionobject"></a>CWinAppEx::GetSectionObject  
 Lee [CObject](../../mfc/reference/cobject-class.md) datos de registro del registro.  
  
```  
BOOL GetSectionObject(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    CObject& obj);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszSubSection`  
 Cadena que contiene la ruta de acceso relativa de una clave del registro.  
  
 [in] `lpszEntry`  
 Cadena que contiene el valor que se va a leer.  
  
 [out] `obj`  
 Una referencia a un `CObject`. Use el método `CObject` para almacenar los datos del registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Este método lee los datos del registro. Los datos de lectura es `CObject` datos o datos de una clase derivada de `CObject`. Escribir `CObject` datos en el registro, utilice uno [CWinAppEx::WriteObject](#writeobject) o [CWinAppEx::WriteSectionObject](#writesectionobject).  
  
 El `lpszSubSection` parámetro no es una ruta de acceso absoluta para una entrada del registro. Es una ruta de acceso relativa que se anexa al final de la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase) respectivamente.  
  
##  <a name="getsectionstring"></a>CWinAppEx::GetSectionString  
 Lee los datos del registro de cadena.  
  
```  
CString GetSectionString(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    LPCTSTR lpszDefault = _T(""));
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszSubSection`  
 Cadena que contiene la ruta de acceso relativa de una clave del registro.  
  
 [in] `lpszEntry`  
 Cadena que contiene el valor que se va a leer.  
  
 [in] `lpszDefault`  
 El valor predeterminado para devolver si el valor especificado no existe.  
  
### <a name="return-value"></a>Valor devuelto  
 Los datos de cadena almacenados en el valor del registro especificada si existen los datos; de lo contrario, `lpszDefault`.  
  
### <a name="remarks"></a>Comentarios  
 Este método lee los datos de cadena que se escribe en el registro. Utilice [CWinAppEx::WriteString](#writestring) y [CWinAppEx::WriteSectionString](#writesectionstring) para escribir datos de cadena en el registro.  
  
 El `lpszSubSection` parámetro no es una ruta de acceso absoluta para una entrada del registro. Es una ruta de acceso relativa que se anexa al final de la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase) respectivamente.  
  
##  <a name="getshellmanager"></a>CWinAppEx::GetShellManager  
 Devuelve un puntero a la plantilla global [CShellManager](../../mfc/reference/cshellmanager-class.md) objeto.  
  
```  
CShellManager* GetShellManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la plantilla global `CShellManager` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si el `CShellManager` objeto no está inicializado, se llama a esta función [CWinAppEx::InitShellManager](#initshellmanager) antes de devolver un puntero.  
  
##  <a name="getstring"></a>CWinAppEx::GetString  
 Lee los datos de una clave del registro especificada de cadena.  
  
```  
CString GetString(
    LPCTSTR lpszEntry,  
    LPCTSTR lpzDefault= _T(""));
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszEntry`  
 Una cadena que contiene el nombre de una clave del registro  
  
 [in] `lpzDefault`  
 El valor predeterminado que devuelve el método si la entrada del registro especificada no existe.  
  
### <a name="return-value"></a>Valor devuelto  
 Los datos de la cadena almacenados en el registro si se realiza correctamente; `lpszDefault` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Este método lee los datos de cadena que se escribe en el registro. Para escribir datos en el registro, utilice los métodos [CWinAppEx::WriteString](#writestring) o [CWinAppEx::WriteSectionString](#writesectionstring).  
  
 El `lpszEntry` parámetro es el nombre de una entrada del registro que se encuentra bajo la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase) respectivamente.  
  
##  <a name="gettooltipmanager"></a>CWinAppEx::GetTooltipManager  
 Devuelve un puntero a la plantilla global [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) objeto.  
  
```  
CTooltipManager* GetTooltipManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la plantilla global `CTooltipManager` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si el `CTooltipManager` objeto no está inicializado, se llama a esta función [CWinAppEx::InitTooltipManager](#inittooltipmanager) antes de devolver un puntero.  
  
##  <a name="getusertoolsmanager"></a>CWinAppEx::GetUserToolsManager  
 Devuelve un puntero a la plantilla global [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) objeto.  
  
```  
CUserToolsManager* GetUserToolsManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la plantilla global `CUserToolsManager` objeto; `NULL` si no está habilitada la administración de herramientas de usuario para la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Antes de recuperar un puntero a la `CUserToolsManager` de objeto, el administrador debe inicializar llamando a [CWinAppEx::EnableUserTools](#enableusertools).  
  
##  <a name="initcontextmenumanager"></a>CWinAppEx::InitContextMenuManager  
 Inicializa el [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) objeto.  
  
```  
BOOL InitContextMenuManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método crea el objeto CContextMenuManager; 0 si el `CContextMenuManager` ya existe un objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si se llama a [CWinAppEx::GetContextMenuManager](#getcontextmenumanager), llama a la implementación predeterminada de ese método `InitContextMenuManager`.  
  
 Si la aplicación ya tiene un administrador de menú de contexto y se llama `InitContextMenuManager`, la aplicación tendrá un [ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) error. Por lo tanto, no debería llamar `InitContextMenuManager` si crea un `CContextMenuManager` objeto directamente. Si no usa un personalizado `CContextMenuManager`, debe usar `GetContextMenuManager` para crear un `CContextMenuManager` objeto.  
  
##  <a name="initkeyboardmanager"></a>CWinAppEx::InitKeyboardManager  
 Inicializa el [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md) objeto.  
  
```  
BOOL InitKeyboardManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método crea el `CKeyboardManager` objeto; 0 si la `CKeyboardManager` objeto ya existe.  
  
### <a name="remarks"></a>Comentarios  
 Si se llama a [CWinAppEx::GetKeyboardManager](#getkeyboardmanager), llama a la implementación predeterminada de ese método `InitKeyboardManager`.  
  
 Si la aplicación ya tiene un administrador de teclado y se llama `InitKeyboardManager`, la aplicación tendrá un [ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) error. Por lo tanto, no debería llamar `InitKeyboardManager` si crea un `CKeyboardManager` objeto directamente. Si no usa un personalizado `CKeyboardManager`, debe usar `GetKeyboardManager` para crear un `CKeyboardManager` objeto.  
  
##  <a name="initmousemanager"></a>CWinAppEx::InitMouseManager  
 Inicializa el [CMouseManager](../../mfc/reference/cmousemanager-class.md) objeto.  
  
```  
BOOL InitMouseManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método crea el `CMouseManager` objeto; 0 si la `CMouseManager` objeto ya existe.  
  
### <a name="remarks"></a>Comentarios  
 Si se llama a [CWinAppEx::GetMouseManager](#getmousemanager), llama a la implementación predeterminada de ese método `InitMouseManager`.  
  
 Si la aplicación ya tiene un administrador de mouse (ratón) y se llama `InitMouseManager`, la aplicación tendrá un [ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) error. Por lo tanto, no debería llamar `InitMouseManager` si crea un `CMouseManager` objeto directamente. Si no usa un personalizado `CMouseManager`, debe usar `GetMouseManager` para crear un `CMouseManager` objeto.  
  
##  <a name="initshellmanager"></a>CWinAppEx::InitShellManager  
 Inicializa el [CShellManager](../../mfc/reference/cshellmanager-class.md) objeto.  
  
```  
BOOL InitShellManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método crea el `CShellManager` objeto; 0 si la `CShellManager` objeto ya existe.  
  
### <a name="remarks"></a>Comentarios  
 Si se llama a [CWinAppEx::GetShellManager](#getshellmanager), llama a la implementación predeterminada de ese método `InitShellManager`.  
  
 Si la aplicación ya tiene un administrador de shell y se llama `InitShellManager`, la aplicación se produce un [ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) error. Por lo tanto, no se llama a `InitShellManager` si crea un `CShellManager` objeto directamente. Si no usa un personalizado `CShellManager`, utilice `GetShellManager` para crear un `CShellManager` objeto.  
  
##  <a name="inittooltipmanager"></a>CWinAppEx::InitTooltipManager  
 Inicializa el [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) objeto.  
  
```  
BOOL InitTooltipManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método crea el `CTooltipManager` objeto; 0 si la `CTooltipManager` objeto ya existe.  
  
### <a name="remarks"></a>Comentarios  
 Si se llama a [CWinAppEx::GetTooltipManager](#gettooltipmanager), llama a la implementación predeterminada de ese método `InitTooltipManager`.  
  
 Si la aplicación ya tiene un administrador de información sobre herramientas y se llama `InitTooltipManager`, la aplicación tendrá un [ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) error. Por lo tanto, no debería llamar `InitTooltipManager` si crea un `CTooltipManager` objeto directamente. Si no usa un personalizado `CTooltipManager`, debe usar `GetTooltipManager` para crear un `CTooltipManager` objeto.  
  
##  <a name="isresourcesmartupdate"></a>CWinAppEx::IsResourceSmartUpdate  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsResourceSmartUpdate() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isstateexists"></a>CWinAppEx::IsStateExists  
 Indica si la clave especificada está en el registro.  
  
```  
BOOL IsStateExists(LPCTSTR lpszSectionName);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszSectionName`  
 Cadena que contiene una ruta de acceso de una clave del registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la clave está en el registro; en caso contrario, 0.  
  
##  <a name="loadcustomstate"></a>CWinAppEx::LoadCustomState  
 El marco de trabajo llama a este método después de que carga el estado de la aplicación desde el registro.  
  
```  
virtual void LoadCustomState();
```  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea que realice el procesamiento después de que la aplicación carga el estado del registro. De forma predeterminada, este método no hace nada.  
  
 Para cargar la información de estado personalizada desde el registro, la información en primer lugar debe guardarse utilizando [CWinAppEx::SaveCustomState](#savecustomstate).  
  
##  <a name="loadstate"></a>CWinAppEx::LoadState  
 Lee el estado de la aplicación desde el registro de Windows.  
  
```  
BOOL LoadState(
    CMDIFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);

 
BOOL LoadState(
    CFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);

 
BOOL LoadState(
    COleIPFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);

 
virtual BOOL LoadState(
    LPCTSTR lpszSectionName = NULL,  
    CFrameImpl* pFrameImpl = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pFrame`  
 Puntero a un objeto de ventana de marco. El método aplica a la información de estado en el registro a esta ventana de marco.  
  
 [in] `lpszSectionName`  
 Cadena que contiene la ruta de acceso relativa de una clave del registro.  
  
 [in] `pFrameImpl`  
 Un puntero a un `CFrameImpl` objeto. El método aplica a la información de estado en el registro a esta ventana de marco.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método carga el estado de la aplicación y cualquier información de estado para una ventana de marco. La información de la ventana de marco cargada se aplica a la ventana de marco proporcionado. Si no se proporciona una ventana de marco, se cargará únicamente la información de estado de aplicación. La información de la aplicación incluye el estado de la [CMouseManager clase](../../mfc/reference/cmousemanager-class.md), [CContextMenuManager clase](../../mfc/reference/ccontextmenumanager-class.md), [CKeyboardManager clase](../../mfc/reference/ckeyboardmanager-class.md)y el [CUserToolsManager clase](../../mfc/reference/cusertoolsmanager-class.md).  
  
 La implementación predeterminada de `CFrameImpl::OnLoadFrame` llamadas `LoadState`.  
  
 El `lpszSectionName` parámetro no es la ruta de acceso absoluta para una entrada del registro. Es una ruta de acceso relativa a la que se agrega al final de la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase) respectivamente.  
  
##  <a name="loadwindowplacement"></a>CWinAppEx::LoadWindowPlacement  
 Llamado por el marco cuando carga el tamaño y la ubicación de la ventana de marco principal del registro.  
  
```  
virtual BOOL LoadWindowPlacement(
    CRect& rectNormalPosition,  
    int& nFlags,  
    int& nShowCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rectNormalPosition`  
 Un rectángulo que contiene las coordenadas de la ventana de marco principal cuando se encuentra en la posición restaurada.  
  
 [out] `nFlags`  
 Marcas que controlan la posición de la ventana minimizada y cómo el sistema operativo cambia entre una ventana minimizada y una ventana restaurada.  
  
 [out] `nShowCmd`  
 Un entero que especifica el estado de presentación de la ventana. Para obtener más información acerca de los valores posibles, consulte [CWnd:: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow).  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, MFC carga automáticamente la posición anterior y el estado de la ventana de marco principal cuando se inicia la aplicación. Para obtener más información acerca de cómo esta información se almacena en el registro, consulte [CWinAppEx::StoreWindowPlacement](#storewindowplacement).  
  
 Invalide este método si desea cargar la información adicional acerca de la ventana de marco principal.  
  
##  <a name="m_bforceimagereset"></a>CWinAppEx::m_bForceImageReset  
 Especifica si el marco de trabajo restablece todas las imágenes de la barra de herramientas cuando se vuelva a cargar la ventana de marco que contiene la barra de herramientas.  
  
```  
BOOL m_bForceImageReset;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `m_bForceImageReset` miembro de datos es una variable protegida.  
  
##  <a name="onappcontexthelp"></a>CWinAppEx::OnAppContextHelp  
 El marco de trabajo llama a este método cuando el usuario solicita ayuda contextual para el **personalización** cuadro de diálogo.  
  
```  
virtual void OnAppContextHelp(
    CWnd* pWndControl,  
    const DWORD dwHelpIDArray[]);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndControl`  
 Puntero a un objeto de ventana para el que el usuario invoca la Ayuda contextual.  
  
 [in] `dwHelpIDArray[]`  
 Un valor reservado.  
  
### <a name="remarks"></a>Comentarios  
 Actualmente, este método está reservado para uso futuro. La implementación predeterminada no hace nada y actualmente no se llama el marco de trabajo.  
  
##  <a name="onclosingmainframe"></a>CWinAppEx::OnClosingMainFrame  
 El marco de trabajo llama a este método cuando se está procesando una ventana de marco `WM_CLOSE`.  
  
```  
virtual void OnClosingMainFrame(CFrameImpl* pFrameImpl);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pFrameImpl`  
 Un puntero a un `CFrameImpl` objeto.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de este método guarda el estado de `pFrameImpl`.  
  
##  <a name="onviewdoubleclick"></a>CWinAppEx::OnViewDoubleClick  
 Llama al comando definido por el usuario que está asociado a una vista cuando el usuario hace doble clic en cualquier lugar dentro de esa vista.  
  
```  
virtual BOOL OnViewDoubleClick(
    CWnd* pWnd,  
    int iViewId);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Un puntero a un objeto derivado de la [CView (clase)](../../mfc/reference/cview-class.md).  
  
 [in] `iViewId`  
 El identificador de la vista.  
  
### <a name="return-value"></a>Valor devuelto  
 `True`Si el marco de trabajo busca un comando; en caso contrario, false.  
  
### <a name="remarks"></a>Comentarios  
 Para admitir el comportamiento del mouse personalizado, debe llamar a esta función cuando se procesa el `WM_LBUTTONDBLCLK` mensaje. Este método ejecutará el comando asociado con el Id. de vista proporcionado por `iViewId`. Para obtener más información sobre el comportamiento personalizado del mouse, consulte [personalización del teclado y Mouse](../../mfc/keyboard-and-mouse-customization.md).  
  
##  <a name="onworkspaceidle"></a>CWinAppEx::OnWorkspaceIdle  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnWorkspaceIdle(CWnd*);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CWnd*`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="preloadstate"></a>CWinAppEx::PreLoadState  
 El marco de trabajo llama a este método inmediatamente antes de que carga el estado de la aplicación desde el registro.  
  
```  
virtual void PreLoadState();
```  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea que realice el procesamiento antes de que el marco de trabajo carga el estado de la aplicación.  
  
##  <a name="presavestate"></a>CWinAppEx::PreSaveState  
 El marco de trabajo llama a este método inmediatamente antes de guardar el estado de la aplicación.  
  
```  
virtual void PreSaveState();
```  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea que realice el procesamiento antes de que el marco de trabajo guarda el estado de la aplicación.  
  
##  <a name="reloadwindowplacement"></a>CWinAppEx::ReloadWindowPlacement  
 Vuelve a cargar el tamaño y la ubicación de una ventana del registro.  
  
```  
virtual BOOL ReloadWindowPlacement(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pFrame`  
 Puntero a una ventana de marco.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el método se realizó correctamente; 0 si no hay datos para cargar la carga con errores o no existen.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la función [CWinAppEx::StoreWindowPlacement](#storewindowplacement) para escribir el tamaño y la ubicación de una ventana en el registro.  
  
##  <a name="savecustomstate"></a>CWinAppEx::SaveCustomState  
 El marco de trabajo llama a este método después de que guarda el estado de la aplicación en el registro.  
  
```  
virtual void SaveCustomState();
```  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea que realice el procesamiento después de que la aplicación guarda el estado en el registro. De forma predeterminada, este método no hace nada.  
  
##  <a name="savestate"></a>CWinAppEx::SaveState  
 Escribe el estado de la aplicación en el registro de Windows.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszSectionName = NULL,  
    CFrameImpl* pFrameImpl = NULL);

 
BOOL SaveState(
    CMDIFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);

 
BOOL SaveState(
    CFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);

 
BOOL SaveState(
    COleIPFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszSectionName`  
 Cadena que contiene la ruta de acceso relativa de una clave del registro.  
  
 [in] `pFrameImpl`  
 Un puntero a un `CFrameImpl` objeto. Este marco se guarda en el registro de Windows.  
  
 [in] `pFrame`  
 Puntero a un objeto de ventana de marco. Este marco se guarda en el registro de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 `True`Si es correcto; `false` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Este método guarda el estado de la aplicación y cualquier información de estado de la ventana de marco proporcionado. Si no se proporciona una ventana de marco, el método sólo guarda el estado de la aplicación. La información de la aplicación incluye el estado de la [CMouseManager clase](../../mfc/reference/cmousemanager-class.md), [CContextMenuManager clase](../../mfc/reference/ccontextmenumanager-class.md), [CKeyboardManager clase](../../mfc/reference/ckeyboardmanager-class.md)y el [CUserToolsManager clase](../../mfc/reference/cusertoolsmanager-class.md).  
  
 El `lpszSectionName` parámetro no es la ruta de acceso absoluta para una entrada del registro. Es una ruta de acceso relativa que se anexa al final de la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase) respectivamente.  
  
##  <a name="setregistrybase"></a>CWinAppEx::SetRegistryBase  
 Establece la ruta de acceso de registro predeterminado para la aplicación.  
  
```  
LPCTSTR SetRegistryBase(LPCTSTR lpszSectionName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszSectionName`  
 Cadena que contiene la ruta de acceso de una clave del registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Cadena que contiene la ruta de acceso de la ubicación del registro de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Todos los métodos de la [CWinAppEx Class](../../mfc/reference/cwinappex-class.md) que tener acceso el inicio del registro en una ubicación predeterminada. Utilice este método para cambiar esa ubicación de registro predeterminado. Utilice [CWinAppEx::GetRegistryBase](#getregistrybase) para recuperar la ubicación del registro de forma predeterminada.  
  
##  <a name="showpopupmenu"></a>CWinAppEx::ShowPopupMenu  
 Muestra un menú emergente.  
  
```  
virtual BOOL ShowPopupMenu(
    UINT uiMenuResId,  
    const CPoint& point,  
    CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiMenuResId`  
 Un identificador de recurso de menú.  
  
 [in] `point`  
 Un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) que especifica la posición del menú en coordenadas de pantalla.  
  
 [in] `pWnd`  
 Puntero a la ventana que posee el menú emergente.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el menú emergente se muestra correctamente; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método muestra el menú asociado a `uiMenuResId`.  
  
 Para admitir los menús emergentes, debe tener un [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) objeto. Si no se ha inicializado el `CContextMenuManager` objeto, `ShowPopupMenu` se producirá un error.  
  
##  <a name="storewindowplacement"></a>CWinAppEx::StoreWindowPlacement  
 Llamado por el marco para escribir el tamaño y la ubicación de la ventana de marco principal en el registro.  
  
```  
virtual BOOL StoreWindowPlacement(
    const CRect& rectNormalPosition,  
    int nFlags,  
    int nShowCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nFlags`  
 Marcas que controlan la posición de la ventana minimizada y cómo el sistema operativo cambia entre una ventana minimizada y una ventana restaurada.  
  
 [in] `nShowCmd`  
 Un entero que especifica el estado de presentación de la ventana. Para obtener más información acerca de los valores posibles, consulte [CWnd:: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow).  
  
 [in] `rectNormalPosition`  
 Un rectángulo que contiene las coordenadas de la ventana de marco principal cuando se encuentra en el estado restaurado.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, MFC guarda automáticamente la posición y el estado de la ventana de marco principal antes de salir de la aplicación. Esta información se almacena en el registro de Windows bajo la clave WindowPlacement en la ubicación del registro de forma predeterminada para la aplicación. Para obtener más información acerca de la ubicación de registro predeterminado de la aplicación, consulte [CWinAppEx::GetRegistryBase](#getregistrybase).  
  
 Invalide este método si desea almacenar información adicional acerca de la ventana de marco principal.  
  
##  <a name="writebinary"></a>CWinAppEx::WriteBinary  
 Escribe datos binarios en el registro.  
  
```  
BOOL WriteBinary(
    LPCTSTR lpszEntry,  
    LPBYTE pData,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszEntry`  
 Una cadena que contiene el nombre de una clave del registro.  
  
 [in] `pData`  
 Los datos a almacenar.  
  
 [in] `nBytes`  
 El tamaño de `pData` en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El `lpszEntry` parámetro es el nombre de una entrada del registro que se encuentra bajo la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase) respectivamente.  
  
 Si la clave especificada por `lpszEntry` no existe, este método lo creará.  
  
##  <a name="writeint"></a>CWinAppEx::WriteInt  
 Escribe datos numéricos en el registro.  
  
```  
BOOL WriteInt(
    LPCTSTR lpszEntry,  
    int nValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszEntry`  
 Una cadena que contiene el nombre de una clave del registro.  
  
 [in] `nValue`  
 Los datos a almacenar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El `lpszEntry` parámetro es el nombre de una entrada del registro que se encuentra bajo la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase) respectivamente.  
  
 Si la clave especificada por `lpszEntry` no existe, este método lo creará.  
  
##  <a name="writeobject"></a>CWinAppEx::WriteObject  
 Escribe los datos derivados de la [CObject (clase)](../../mfc/reference/cobject-class.md) en el registro.  
  
```  
BOOL WriteObject(
    LPCTSTR lpszEntry,  
    CObject& obj);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszEntry`  
 Cadena que contiene el valor que se va a establecer.  
  
 [in] `obj`  
 Una referencia a `CObject` datos que almacenará el método.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método escribe el `obj` datos en el valor especificado en la clave del registro de forma predeterminada. Utilice [CWinAppEx::GetRegistryBase](#getregistrybase) para determinar la clave del registro actual.  
  
##  <a name="writesectionbinary"></a>CWinAppEx::WriteSectionBinary  
 Escribe datos binarios en un valor en el registro.  
  
```  
BOOL WriteSectionBinary(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    LPBYTE pData,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszSubSection`  
 Una cadena que contiene el nombre de una clave del registro  
  
 [in] `lpszEntry`  
 Cadena que contiene el valor que se va a establecer.  
  
 [in] `pData`  
 Los datos para escribir en el registro.  
  
 [in] `nBytes`  
 El tamaño de `pData` en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El `lpszSubSection` parámetro no es la ruta de acceso absoluta para una entrada del registro. Es una ruta de acceso relativa que se anexa al final de la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase) respectivamente.  
  
 Si la clave especificada por `lpszEntry` no existe, este método lo creará.  
  
##  <a name="writesectionint"></a>CWinAppEx::WriteSectionInt  
 Escribe datos numéricos en el registro.  
  
```  
BOOL WriteSectionInt(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    int nValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszSubSection`  
 Cadena que contiene la ruta de acceso relativa de una clave del registro.  
  
 [in] `lpszEntry`  
 Cadena que contiene el valor que se va a establecer.  
  
 [in] `nValue`  
 Los datos para escribir en el registro.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El `lpszSubSection` parámetro no es una ruta de acceso absoluta para una entrada del registro. Es una ruta de acceso relativa que se anexa a la clave de registro predeterminado para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase) respectivamente.  
  
 Si la clave especificada por `lpszEntry` no existe, este método lo creará.  
  
##  <a name="writesectionobject"></a>CWinAppEx::WriteSectionObject  
 Escribe los datos derivados de la [CObject (clase)](../../mfc/reference/cobject-class.md) a un valor del Registro específica.  
  
```  
BOOL WriteSectionObject(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    CObject& obj);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszSubSection`  
 Una cadena que contiene el nombre de una clave del registro.  
  
 [in] `lpszEntry`  
 Cadena que contiene el nombre del valor que se va a establecer.  
  
 [in] `obj`  
 Los datos a almacenar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El `lpszSubSection` parámetro no es una ruta de acceso absoluta para una entrada del registro. Es una ruta de acceso relativa que se anexa al final de la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase), respectivamente.  
  
 Si el valor especificado por `lpszEntry` no existe en la clave del registro especificada por `lpszSubSection`, este método creará ese valor.  
  
##  <a name="writesectionstring"></a>CWinAppEx::WriteSectionString  
 Escribe los datos de cadena en un valor en el registro.  
  
```  
BOOL WriteSectionString(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    LPCTSTR lpszValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszSubSection`  
 Una cadena que contiene el nombre de una clave del registro.  
  
 [in] `lpszEntry`  
 Cadena que contiene el valor que se va a establecer.  
  
 [in] `lpszValue`  
 Los datos de cadena para escribir en el registro.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El `lpszSubSection` parámetro no es una ruta de acceso absoluta para una entrada del registro. Es una ruta de acceso relativa que se anexa al final de la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase), respectivamente.  
  
 Si el valor especificado por `lpszEntry` no existe en `lpszSubSection`, este método lo creará.  
  
##  <a name="writestring"></a>CWinAppEx::WriteString  
 Escribe los datos de cadena en el registro.  
  
```  
BOOL WriteString(
    LPCTSTR lpszEntry,  
    LPCTSTR lpszValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszEntry`  
 Una cadena que contiene el nombre de una clave del registro.  
  
 [in] `lpszValue`  
 Los datos a almacenar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El `lpszEntry` parámetro es el nombre de una entrada del registro que se encuentra bajo la clave del registro de forma predeterminada para la aplicación. Para obtener o establecer la clave del registro de forma predeterminada, utilice los métodos [CWinAppEx::GetRegistryBase](#getregistrybase) y [CWinAppEx::SetRegistryBase](#setregistrybase) respectivamente.  
  
 Si la clave especificada por `lspzEntry` no existe, este método lo creará.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CWinApp (clase)](../../mfc/reference/cwinapp-class.md)   
 [Clase CMouseManager](../../mfc/reference/cmousemanager-class.md)   
 [Clase CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)   
 [Clase CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)   
 [Clase CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)

