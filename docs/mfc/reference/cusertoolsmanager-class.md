---
title: Clase CUserToolsManager | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUserToolsManager
dev_langs:
- C++
helpviewer_keywords:
- CUserToolsManager class
ms.assetid: bdfa37ae-efca-4616-abb5-9d0dcd2d335b
caps.latest.revision: 26
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
ms.openlocfilehash: 0b82adf0f9eba5ee334ada2c169546f27894c1dd
ms.lasthandoff: 02/24/2017

---
# <a name="cusertoolsmanager-class"></a>Clase CUserToolsManager
Mantiene la colección de [CUserTool clase](../../mfc/reference/cusertool-class.md) objetos en una aplicación. Una herramienta de usuario es un elemento de menú que ejecuta una aplicación externa. El objeto `CUserToolsManager` permite al usuario o al programador agregar nuevas herramientas de usuario a la aplicación. Admite la ejecución de los comandos asociados a las herramientas de usuario y también guarda información sobre las herramientas de usuario en el Registro de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CUserToolsManager : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CUserToolsManager::CUserToolsManager](#cusertoolsmanager)|Construye un objeto `CUserToolsManager`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CUserToolsManager::CreateNewTool](#createnewtool)|Crea una nueva herramienta de usuario.|  
|[CUserToolsManager::FindTool](#findtool)|Devuelve el puntero a la `CMFCUserTool` objeto que está asociado con un identificador de comando especificado.|  
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|Devuelve el identificador de recursos que está asociado el **argumentos** menú en el **herramientas** ficha de la **personalizar** cuadro de diálogo.|  
|[CUserToolsManager::GetDefExt](#getdefext)|Devuelve la extensión predeterminada que el **abrir archivo** cuadro de diálogo ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) se utiliza en el **comando** en el **herramientas** ficha de la **personalizar** cuadro de diálogo.|  
|[CUserToolsManager::GetFilter](#getfilter)|Devuelve el filtro de archivos que la **abrir archivo** cuadro de diálogo ( [CFileDialog (clase)](../../mfc/reference/cfiledialog-class.md)) se utiliza en el **comando** en el **herramientas** ficha de la **personalizar** cuadro de diálogo.|  
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|Devuelve el identificador de recursos que está asociado el **directorio inicial** menú en el **herramientas** ficha de la **personalizar** cuadro de diálogo.|  
|[CUserToolsManager::GetMaxTools](#getmaxtools)|Devuelve el número máximo de las herramientas de usuario que se pueden asignar en la aplicación.|  
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|Devuelve el identificador de comando del marcador de posición de elemento de menú para herramientas de usuario.|  
|[CUserToolsManager::GetUserTools](#getusertools)|Devuelve una referencia a la lista de herramientas de usuario.|  
|[CUserToolsManager::InvokeTool](#invoketool)|Ejecuta una aplicación asociada con la herramienta de usuario que tiene un identificador de comando especificado.|  
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|Determina si un identificador de comando está asociado a una herramienta de usuario.|  
|[CUserToolsManager::LoadState](#loadstate)|Carga información acerca de las herramientas de usuario desde el registro de Windows.|  
|[CUserToolsManager::MoveToolDown](#movetooldown)|Baja la herramienta de usuario especificado en la lista de herramientas de usuario.|  
|[CUserToolsManager::MoveToolUp](#movetoolup)|Sube la herramienta de usuario especificado en la lista de herramientas de usuario.|  
|[CUserToolsManager::RemoveTool](#removetool)|Quita la herramienta de usuario especificado de la aplicación.|  
|[CUserToolsManager::SaveState](#savestate)|Almacena información acerca de las herramientas de usuario en el registro de Windows.|  
|[CUserToolsManager::SetDefExt](#setdefext)|Especifica la extensión predeterminada que el **abrir archivo** cuadro de diálogo ( [CFileDialog (clase)](../../mfc/reference/cfiledialog-class.md)) se utiliza en el **comando** en el **herramientas** ficha de la **personalizar** cuadro de diálogo.|  
|[CUserToolsManager::SetFilter](#setfilter)|Especifica el archivo de filtro que el **abrir archivo** cuadro de diálogo ( [clase CFileDialog](../../mfc/reference/cfiledialog-class.md)) usa en la **comando** en el **herramientas** ficha de la **personalizar** cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Para incorporar las herramientas de usuario en la aplicación, debe:  
  
 1. Reserve un elemento de menú y un identificador de comando asociado para una entrada de menú de la herramienta de usuario.  
  
 2. Reserve un Id. de comando secuencial para cada herramienta de usuario que un usuario puede definir en la aplicación.  
  
 3. Llame a la [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) método y proporcione los parámetros siguientes: menú Id. de comando, primer identificador de comando de herramienta de usuario y último Id. de comando de herramienta de usuario  
  
 Debería haber sólo uno global `CUserToolsManager` objeto por aplicación.  
  
 Para obtener un ejemplo de herramientas de usuario, consulte el proyecto de ejemplo VisualStudioDemo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo recuperar una referencia a un `CUserToolsManager` objeto y cómo crear nuevas herramientas de usuario. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#38;](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CUserToolsManager`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxusertoolsmanager.h  
  
##  <a name="a-namecreatenewtoola--cusertoolsmanagercreatenewtool"></a><a name="createnewtool"></a>CUserToolsManager::CreateNewTool  
 Crea una nueva herramienta de usuario.  
  
```  
CUserTool* CreateNewTool();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la herramienta de usuario recién creado, o `NULL` si el número de herramientas de usuario ha superado el máximo. El tipo devuelto es el mismo que el tipo que se pasa a `CWinAppEx::EnableUserTools` como el `pToolRTC` parámetro.  
  
### <a name="remarks"></a>Comentarios  
 Este método busca el primer identificador de comando de menú disponibles en el intervalo que se suministra en la llamada a [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) y asigna este Id. de la herramienta de usuario  
  
 El método produce un error si el número de herramientas ha alcanzado el máximo. Esto ocurre cuando todos los identificadores de comando dentro del intervalo se asignan a herramientas de usuario. Puede recuperar el número máximo de herramientas llamando a [CUserToolsManager::GetMaxTools](#getmaxtools). Puede obtener acceso a la lista de herramientas mediante una llamada a la [CUserToolsManager::GetUserTools](#getusertools) método.  
  
##  <a name="a-namecusertoolsmanagera--cusertoolsmanagercusertoolsmanager"></a><a name="cusertoolsmanager"></a>CUserToolsManager::CUserToolsManager  
 Construye un objeto `CUserToolsManager`. Cada aplicación debe tener al menos un usuario herramientas director.  
  
```  
CUserToolsManager();

 
CUserToolsManager(
    const UINT uiCmdToolsDummy,  
    const UINT uiCmdFirst,  
    const UINT uiCmdLast,  
    CRuntimeClass* pToolRTC=RUNTIME_CLASS(CUserTool),  
    UINT uArgMenuID=0,  
    UINT uInitDirMenuID=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdToolsDummy`  
 Un entero sin signo que el marco de trabajo se usa como marcador de posición para el identificador de comando del menú de herramientas de usuario.  
  
 [in] `uiCmdFirst`  
 El identificador de comando para el primer comando de la herramienta de usuario.  
  
 [in] `uiCmdLast`  
 El identificador de comando para el último comando de herramienta de usuario.  
  
 [in] `pToolRTC`  
 La clase que [CUserToolsManager::CreateNewTool](#createnewtool) crea. Mediante esta clase, puede utilizar un tipo derivado de [CUserTool clase](../../mfc/reference/cusertool-class.md) en lugar de la implementación predeterminada.  
  
 [in] `uArgMenuID`  
 El identificador de recurso de menú del menú emergente de argumentos.  
  
 [in] `uInitDirMenuID`  
 El identificador de recurso de menú del menú emergente de directorio inicial.  
  
### <a name="remarks"></a>Comentarios  
 No llame a este constructor. En su lugar, llame a [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) para habilitar herramientas de usuario y llamar a [CWinAppEx::GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager) para obtener un puntero a la `CUserToolsManager`. Para obtener más información, consulte [herramientas definidas por el usuario](../../mfc/user-defined-tools.md).  
  
##  <a name="a-namefindtoola--cusertoolsmanagerfindtool"></a><a name="findtool"></a>CUserToolsManager::FindTool  
 Devuelve el puntero a la [CUserTool clase](../../mfc/reference/cusertool-class.md) objeto que está asociado con un identificador de comando especificado.  
  
```  
CUserTool* FindTool(UINT uiCmdId) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdId`  
 Un identificador de comando de menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CUserTool clase](../../mfc/reference/cusertool-class.md) o `CUserTool`-objeto derivado si correcto; en caso contrario `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `FindTool` es correcta, el tipo devuelto es el mismo que el tipo de la `pToolRTC` parámetro [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).  
  
##  <a name="a-namegetargumentsmenuida--cusertoolsmanagergetargumentsmenuid"></a><a name="getargumentsmenuid"></a>CUserToolsManager::GetArgumentsMenuID  
 Devuelve el identificador de recursos que está asociado el **argumentos** menú en el **herramientas** ficha de la **personalizar** cuadro de diálogo.  
  
```  
UINT GetArgumentsMenuID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de un recurso de menú.  
  
### <a name="remarks"></a>Comentarios  
 El `uArgMenuID` parámetro de [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) especifica el identificador del recurso.  
  
##  <a name="a-namegetdefexta--cusertoolsmanagergetdefext"></a><a name="getdefext"></a>CUserToolsManager::GetDefExt  
 Devuelve la extensión predeterminada que el **abrir archivo** cuadro de diálogo ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) se utiliza en el **comando** en el **herramientas** ficha de la **personalizar** cuadro de diálogo.  
  
```  
const CString& GetDefExt() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la `CString` objeto que contiene la extensión.  
  
##  <a name="a-namegetfiltera--cusertoolsmanagergetfilter"></a><a name="getfilter"></a>CUserToolsManager::GetFilter  
 Devuelve el filtro de archivos que la **abrir archivo** cuadro de diálogo ( [CFileDialog (clase)](../../mfc/reference/cfiledialog-class.md)) se utiliza en el **comando** en el **herramientas** ficha de la **personalizar** cuadro de diálogo.  
  
```  
const CString& GetFilter() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la `CString` objeto que contiene el filtro.  
  
##  <a name="a-namegetinitialdirmenuida--cusertoolsmanagergetinitialdirmenuid"></a><a name="getinitialdirmenuid"></a>CUserToolsManager::GetInitialDirMenuID  
 Devuelve el identificador de recursos que está asociado el **directorio inicial** menú en el **herramientas** ficha de la **personalizar** cuadro de diálogo.  
  
```  
UINT GetInitialDirMenuID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de recurso de menú.  
  
### <a name="remarks"></a>Comentarios  
 El identificador devuelto se especifica en el `uInitDirMenuID` parámetro de [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).  
  
##  <a name="a-namegetmaxtoolsa--cusertoolsmanagergetmaxtools"></a><a name="getmaxtools"></a>CUserToolsManager::GetMaxTools  
 Devuelve el número máximo de las herramientas de usuario que se pueden asignar en la aplicación.  
  
```  
int GetMaxTools() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número máximo de las herramientas de usuario que se pueden asignar.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para recuperar el número máximo de herramientas que se pueden asignar en la aplicación. Este número es el número de identificadores en el intervalo de la `uiCmdFirst` a través de la `uiCmdLast` parámetros que se pasan a [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).  
  
##  <a name="a-namegettoolsentrycmda--cusertoolsmanagergettoolsentrycmd"></a><a name="gettoolsentrycmd"></a>CUserToolsManager::GetToolsEntryCmd  
 Devuelve el identificador de comando del marcador de posición de elemento de menú para herramientas de usuario.  
  
```  
UINT GetToolsEntryCmd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de comando del marcador de posición.  
  
### <a name="remarks"></a>Comentarios  
 Para habilitar las herramientas de usuario, se llama a [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools). El `uiCmdToolsDummy` parámetro especifica el identificador de comando del comando de entrada de herramientas. Este método devuelve el identificador de comando de entrada de herramientas. Siempre que ese identificador se utiliza en un menú, se reemplaza por la lista de herramientas de usuario cuando aparezca el menú.  
  
##  <a name="a-namegetusertoolsa--cusertoolsmanagergetusertools"></a><a name="getusertools"></a>CUserToolsManager::GetUserTools  
 Devuelve una referencia a la lista de herramientas de usuario.  
  
```  
const CObList& GetUserTools() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Const hacen referencia a un [clase CObList](../../mfc/reference/coblist-class.md) objeto que contiene una lista de herramientas de usuario.  
  
### <a name="remarks"></a>Comentarios  
 Llamada a este método para recuperar una lista de usuarios de las herramientas que el [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) objeto mantiene. Cada herramienta de usuario está representado por un objeto de tipo [CUserTool clase](../../mfc/reference/cusertool-class.md) o un tipo derivado de `CUserTool`. El tipo especificado por el `pToolRTC` parámetro al llamar a [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) para habilitar las herramientas de usuario.  
  
##  <a name="a-nameinvoketoola--cusertoolsmanagerinvoketool"></a><a name="invoketool"></a>CUserToolsManager::InvokeTool  
 Ejecuta una aplicación asociada con la herramienta de usuario que tiene un identificador de comando especificado.  
  
```  
BOOL InvokeTool(UINT uiCmdId);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdId`  
 El identificador de comando de menú asociado a la herramienta de usuario.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el comando asociado con la herramienta de usuario se ha ejecutado correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Llamada herramienta de este método para ejecutar una aplicación asociada con el usuario que tiene el identificador de comando especificado por `uiCmdId`.  
  
##  <a name="a-nameisusertoolcmda--cusertoolsmanagerisusertoolcmd"></a><a name="isusertoolcmd"></a>CUserToolsManager::IsUserToolCmd  
 Determina si un identificador de comando está asociado a una herramienta de usuario.  
  
```  
BOOL IsUserToolCmd(UINT uiCmdId) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdId`  
 Identificador de comando del elemento de menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si un identificador de comando especificado está asociado a una herramienta de usuario; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método comprueba si el identificador de comando especificado está en el intervalo de identificadores de comando. Especifique el intervalo al llamar a [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) para habilitar las herramientas de usuario.  
  
##  <a name="a-nameloadstatea--cusertoolsmanagerloadstate"></a><a name="loadstate"></a>CUserToolsManager::LoadState  
 Carga información acerca de las herramientas de usuario desde el registro de Windows.  
  
```  
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 La ruta de acceso de la clave del registro de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el estado se ha cargado correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método carga el estado de la `CUserToolsManager` objeto del registro de Windows.  
  
 Normalmente, no se llama directamente este método. [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate) llama como parte del proceso de inicialización del área de trabajo.  
  
##  <a name="a-namemovetooldowna--cusertoolsmanagermovetooldown"></a><a name="movetooldown"></a>CUserToolsManager::MoveToolDown  
 Baja la herramienta de usuario especificado en la lista de herramientas de usuario.  
  
```  
BOOL MoveToolDown(CUserTool* pTool);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pTool`  
 Especifica la herramienta de usuario para mover.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la herramienta de usuario se desplaza hacia abajo correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El método produce un error si la herramienta que el `pTool` especifica no está en la lista interna o si la herramienta es el última de la lista.  
  
##  <a name="a-namemovetoolupa--cusertoolsmanagermovetoolup"></a><a name="movetoolup"></a>CUserToolsManager::MoveToolUp  
 Sube la herramienta de usuario especificado en la lista de herramientas de usuario.  
  
```  
BOOL MoveToolUp(CUserTool* pTool);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pTool`  
 Especifica la herramienta de usuario para mover.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la herramienta de usuario se ha movido correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El método produce un error si la herramienta que el `pTool` parámetro especifica que no está en la lista interna o si la herramienta es el primer elemento de la herramienta en la lista.  
  
##  <a name="a-nameremovetoola--cusertoolsmanagerremovetool"></a><a name="removetool"></a>CUserToolsManager::RemoveTool  
 Quita la herramienta de usuario especificado de la aplicación.  
  
```  
BOOL RemoveTool(CUserTool* pTool);
```  
  
### <a name="parameters"></a>Parámetros  
 [in, out] `pTool`  
 Puntero a una herramienta de usuario que va a quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la herramienta se quita correctamente. En caso contrario, es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si la herramienta se quita correctamente, este método elimina `pTool`.  
  
##  <a name="a-namesavestatea--cusertoolsmanagersavestate"></a><a name="savestate"></a>CUserToolsManager::SaveState  
 Almacena información acerca de las herramientas de usuario en el registro de Windows.  
  
```  
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Ruta de acceso a la clave del registro de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el estado se guardó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El método almacena el estado actual de la `CUserToolsManager` objeto en el registro de Windows.  
  
 Normalmente, no es necesario llamar a este método directamente, [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate) llama de forma automática como parte del proceso de serialización de área de trabajo de la aplicación.  
  
##  <a name="a-namesetdefexta--cusertoolsmanagersetdefext"></a><a name="setdefext"></a>CUserToolsManager::SetDefExt  
 Especifica la extensión predeterminada que el **abrir archivo** cuadro de diálogo ( [CFileDialog (clase)](../../mfc/reference/cfiledialog-class.md)) se utiliza en el **comando** en el **herramientas** ficha de la **personalizar** cuadro de diálogo.  
  
```  
void SetDefExt(const CString& strDefExt);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strDefExt`  
 Una cadena de texto que contiene la extensión de nombre de archivo predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para especificar una extensión de nombre de archivo predeterminado en el **abrir archivo** cuadro de diálogo que se muestra cuando el usuario selecciona una aplicación para asociar a la herramienta de usuario. El valor predeterminado es "exe".  
  
##  <a name="a-namesetfiltera--cusertoolsmanagersetfilter"></a><a name="setfilter"></a>CUserToolsManager::SetFilter  
 Especifica el archivo de filtro que el **abrir archivo** cuadro de diálogo ( [clase CFileDialog](../../mfc/reference/cfiledialog-class.md)) usa en la **comando** en el **herramientas** ficha de la **personalizar** cuadro de diálogo.  
  
```  
void SetFilter(const CString& strFilter);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strFilter`  
 Especifica el filtro.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CWinAppEx](../../mfc/reference/cwinappex-class.md)   
 [Clase CUserTool](../../mfc/reference/cusertool-class.md)

