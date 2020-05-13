---
title: Clase CUserToolsManager
ms.date: 11/04/2016
f1_keywords:
- CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CreateNewTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::FindTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetArgumentsMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetFilter
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetInitialDirMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetMaxTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetToolsEntryCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetUserTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::InvokeTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::IsUserToolCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::LoadState
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolDown
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolUp
- AFXUSERTOOLSMANAGER/CUserToolsManager::RemoveTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::SaveState
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetFilter
helpviewer_keywords:
- CUserToolsManager [MFC], CUserToolsManager
- CUserToolsManager [MFC], CreateNewTool
- CUserToolsManager [MFC], FindTool
- CUserToolsManager [MFC], GetArgumentsMenuID
- CUserToolsManager [MFC], GetDefExt
- CUserToolsManager [MFC], GetFilter
- CUserToolsManager [MFC], GetInitialDirMenuID
- CUserToolsManager [MFC], GetMaxTools
- CUserToolsManager [MFC], GetToolsEntryCmd
- CUserToolsManager [MFC], GetUserTools
- CUserToolsManager [MFC], InvokeTool
- CUserToolsManager [MFC], IsUserToolCmd
- CUserToolsManager [MFC], LoadState
- CUserToolsManager [MFC], MoveToolDown
- CUserToolsManager [MFC], MoveToolUp
- CUserToolsManager [MFC], RemoveTool
- CUserToolsManager [MFC], SaveState
- CUserToolsManager [MFC], SetDefExt
- CUserToolsManager [MFC], SetFilter
ms.assetid: bdfa37ae-efca-4616-abb5-9d0dcd2d335b
ms.openlocfilehash: 1e9be5d7cb81f2769b98d9baeae786873f5fa73d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751985"
---
# <a name="cusertoolsmanager-class"></a>Clase CUserToolsManager

Mantiene la colección de [CUserTool Clase](../../mfc/reference/cusertool-class.md) objetos en una aplicación. Una herramienta de usuario es un elemento de menú que ejecuta una aplicación externa. El objeto `CUserToolsManager` permite al usuario o al programador agregar nuevas herramientas de usuario a la aplicación. Admite la ejecución de los comandos asociados a las herramientas de usuario y también guarda información sobre las herramientas de usuario en el Registro de Windows.

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
|[CUserToolsManager::FindTool](#findtool)|Devuelve el puntero `CMFCUserTool` al objeto asociado a un identificador de comando especificado.|
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|Devuelve el identificador de recurso asociado al menú **Argumentos** de la ficha **Herramientas** del cuadro de diálogo **Personalizar.**|
|[CUserToolsManager::GetDefExt](#getdefext)|Devuelve la extensión predeterminada que utiliza el cuadro de diálogo **Abrir archivo** ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) en el campo **Comando** de la ficha **Herramientas** del cuadro de diálogo **Personalizar.**|
|[CUserToolsManager::GetFilter](#getfilter)|Devuelve el filtro de archivos que utiliza el cuadro de diálogo **Abrir archivo** ( [Clase CFileDialog](../../mfc/reference/cfiledialog-class.md)) en el campo **Comando** de la ficha **Herramientas** del cuadro de diálogo **Personalizar.**|
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|Devuelve el identificador de recurso asociado al menú **Directorio inicial** de la ficha **Herramientas** del cuadro de diálogo **Personalizar.**|
|[CUserToolsManager::GetMaxTools](#getmaxtools)|Devuelve el número máximo de herramientas de usuario que se pueden asignar en la aplicación.|
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|Devuelve el identificador de comando del marcador de posición del elemento de menú para las herramientas de usuario.|
|[CUserToolsManager::GetUserTools](#getusertools)|Devuelve una referencia a la lista de herramientas de usuario.|
|[CUserToolsManager::InvokeTool](#invoketool)|Ejecuta una aplicación asociada a la herramienta de usuario que tiene un identificador de comando especificado.|
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|Determina si un identificador de comando está asociado a una herramienta de usuario.|
|[CUserToolsManager::LoadState](#loadstate)|Carga información sobre las herramientas de usuario desde el registro de Windows.|
|[CUserToolsManager::MoveToolDown](#movetooldown)|Mueve la herramienta de usuario especificada hacia abajo en la lista de herramientas de usuario.|
|[CUserToolsManager::MoveToolUp](#movetoolup)|Mueve la herramienta de usuario especificada hacia arriba en la lista de herramientas de usuario.|
|[CUserToolsManager::RemoveTool](#removetool)|Quita la herramienta de usuario especificada de la aplicación.|
|[CUserToolsManager::SaveState](#savestate)|Almacena información sobre las herramientas de usuario en el registro de Windows.|
|[CUserToolsManager::SetDefExt](#setdefext)|Especifica la extensión predeterminada que utiliza el cuadro de diálogo **Abrir archivo** ( [Clase CFileDialog](../../mfc/reference/cfiledialog-class.md)) en el campo **Comando** de la ficha **Herramientas** del cuadro de diálogo **Personalizar.**|
|[CUserToolsManager::SetFilter](#setfilter)|Especifica el filtro de archivo que utiliza el cuadro de diálogo **Abrir archivo** ( [Clase CFileDialog](../../mfc/reference/cfiledialog-class.md)) en el campo **Comando** de la ficha **Herramientas** del cuadro de diálogo **Personalizar.**|

## <a name="remarks"></a>Observaciones

Para incorporar herramientas de usuario en la aplicación, debe:

1. Reserve un elemento de menú y un identificador de comando asociado para una entrada de menú de herramientas de usuario.

2. Reserve un identificador de comando secuencial para cada herramienta de usuario que un usuario pueda definir en la aplicación.

3. Llame al método [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) y proporcione los siguientes parámetros: ID de comando de menú, primer identificador de comando de herramienta de usuario y último identificador de comando de herramienta de usuario.

Solo debe haber `CUserToolsManager` un objeto global por aplicación.

Para obtener un ejemplo de herramientas de usuario, vea el VisualStudioDemo proyecto de ejemplo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CUserToolsManager` cómo recuperar una referencia a un objeto y cómo crear nuevas herramientas de usuario. Este fragmento de código forma parte del [ejemplo de demostración](../../overview/visual-cpp-samples.md)de Visual Studio.

[!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CUserToolsManager`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxusertoolsmanager.h

## <a name="cusertoolsmanagercreatenewtool"></a><a name="createnewtool"></a>CUserToolsManager::CreateNewTool

Crea una nueva herramienta de usuario.

```
CUserTool* CreateNewTool();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la herramienta de usuario recién creada, o NULL si el número de herramientas de usuario ha superado el máximo. El tipo devuelto es el mismo que `CWinAppEx::EnableUserTools` el tipo al que se pasa como el parámetro *pToolRTC.*

### <a name="remarks"></a>Observaciones

Este método busca el primer identificador de comando de menú disponible en el intervalo que se proporciona en la llamada a [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) y asigna a la herramienta de usuario este identificador.

Se produce un error en el método si el número de herramientas ha alcanzado el máximo. Esto ocurre cuando todos los ID de comando dentro del rango se asignan a las herramientas de usuario. Puede recuperar el número máximo de herramientas llamando a [CUserToolsManager::GetMaxTools](#getmaxtools). Puede obtener acceso a la lista de herramientas mediante una llamada a la [CUserToolsManager::GetUserTools](#getusertools) método.

## <a name="cusertoolsmanagercusertoolsmanager"></a><a name="cusertoolsmanager"></a>CUserToolsManager::CUserToolsManager

Construye un objeto `CUserToolsManager`. Cada aplicación debe tener como máximo un administrador de herramientas de usuario.

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

*uiCmdToolsDummy*<br/>
[en] Entero sin signo que el marco de trabajo utiliza como marcador de posición para el identificador de comando del menú de herramientas de usuario.

*uiCmdFirst*<br/>
[en] El identificador de comando para el primer comando de herramienta de usuario.

*uiCmdLast*<br/>
[en] El identificador de comando para el último comando de la herramienta de usuario.

*pToolRTC*<br/>
[en] La clase que [CUserToolsManager::CreateNewTool](#createnewtool) crea. Mediante el uso de esta clase, puede usar un tipo derivado de [CUserTool clase](../../mfc/reference/cusertool-class.md) en lugar de la implementación predeterminada.

*uArgMenuID*<br/>
[en] El identificador de recurso de menú del menú emergente de argumentos.

*uInitDirMenuID*<br/>
[en] El ID de recurso de menú del menú emergente del directorio inicial.

### <a name="remarks"></a>Observaciones

No llame a este constructor. En su lugar, llame a [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) para habilitar las herramientas de usuario y `CUserToolsManager`llame a [CWinAppEx::GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager) para obtener un puntero a la . Para obtener más información, consulte [Herramientas definidas por el usuario](../../mfc/user-defined-tools.md).

## <a name="cusertoolsmanagerfindtool"></a><a name="findtool"></a>CUserToolsManager::FindTool

Devuelve el puntero a la [CUserTool clase](../../mfc/reference/cusertool-class.md) objeto que está asociado a un identificador de comando especificado.

```
CUserTool* FindTool(UINT uiCmdId) const;
```

### <a name="parameters"></a>Parámetros

*uiCmdId*<br/>
[en] Identificador de comando de menú.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CUserTool clase](../../mfc/reference/cusertool-class.md) o `CUserTool`-objeto derivado si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Cuando `FindTool` se realiza correctamente, el tipo devuelto es el mismo que el tipo del parámetro *pToolRTC* a [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergetargumentsmenuid"></a><a name="getargumentsmenuid"></a>CUserToolsManager::GetArgumentsMenuID

Devuelve el identificador de recurso asociado al menú **Argumentos** de la ficha **Herramientas** del cuadro de diálogo **Personalizar.**

```
UINT GetArgumentsMenuID() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador de un recurso de menú.

### <a name="remarks"></a>Observaciones

El *uArgMenuID* parámetro de [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) especifica el identificador del recurso.

## <a name="cusertoolsmanagergetdefext"></a><a name="getdefext"></a>CUserToolsManager::GetDefExt

Devuelve la extensión predeterminada que utiliza el cuadro de diálogo **Abrir archivo** ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) en el campo **Comando** de la ficha **Herramientas** del cuadro de diálogo **Personalizar.**

```
const CString& GetDefExt() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia `CString` al objeto que contiene la extensión.

## <a name="cusertoolsmanagergetfilter"></a><a name="getfilter"></a>CUserToolsManager::GetFilter

Devuelve el filtro de archivos que utiliza el cuadro de diálogo **Abrir archivo** ( [Clase CFileDialog](../../mfc/reference/cfiledialog-class.md)) en el campo **Comando** de la ficha **Herramientas** del cuadro de diálogo **Personalizar.**

```
const CString& GetFilter() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia `CString` al objeto que contiene el filtro.

## <a name="cusertoolsmanagergetinitialdirmenuid"></a><a name="getinitialdirmenuid"></a>CUserToolsManager::GetInitialDirMenuID

Devuelve el identificador de recurso asociado al menú **Directorio inicial** de la ficha **Herramientas** del cuadro de diálogo **Personalizar.**

```
UINT GetInitialDirMenuID() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador de recursos de menú.

### <a name="remarks"></a>Observaciones

El identificador devuelto se especifica en el parámetro *uInitDirMenuID* de [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergetmaxtools"></a><a name="getmaxtools"></a>CUserToolsManager::GetMaxTools

Devuelve el número máximo de herramientas de usuario que se pueden asignar en la aplicación.

```
int GetMaxTools() const;
```

### <a name="return-value"></a>Valor devuelto

El número máximo de herramientas de usuario que se pueden asignar.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar el número máximo de herramientas que se pueden asignar en la aplicación. Este número es el número de ID en el intervalo desde *uiCmdFirst* hasta los parámetros *uiCmdLast* que se pasan a [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergettoolsentrycmd"></a><a name="gettoolsentrycmd"></a>CUserToolsManager::GetToolsEntryCmd

Devuelve el identificador de comando del marcador de posición del elemento de menú para las herramientas de usuario.

```
UINT GetToolsEntryCmd() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador de comando del marcador de posición.

### <a name="remarks"></a>Observaciones

Para habilitar las herramientas de usuario, llame a [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools). El parámetro *uiCmdToolsDummy* especifica el identificador de comando del comando tools entry. Este método devuelve el identificador de comando de entrada de herramientas. Dondequiera que se utilice ese ID en un menú, se sustituye por la lista de herramientas de usuario cuando aparece el menú.

## <a name="cusertoolsmanagergetusertools"></a><a name="getusertools"></a>CUserToolsManager::GetUserTools

Devuelve una referencia a la lista de herramientas de usuario.

```
const CObList& GetUserTools() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia const a un [CObList clase](../../mfc/reference/coblist-class.md) objeto que contiene una lista de herramientas de usuario.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar una lista de herramientas de usuario que el [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) objeto mantiene. Cada herramienta de usuario está representada por un objeto de tipo `CUserTool` [CUserTool Class](../../mfc/reference/cusertool-class.md) o un tipo derivado de . El tipo se especifica mediante el *pToolRTC* parámetro cuando se llama a [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) para habilitar las herramientas de usuario.

## <a name="cusertoolsmanagerinvoketool"></a><a name="invoketool"></a>CUserToolsManager::InvokeTool

Ejecuta una aplicación asociada a la herramienta de usuario que tiene un identificador de comando especificado.

```
BOOL InvokeTool(UINT uiCmdId);
```

### <a name="parameters"></a>Parámetros

*uiCmdId*<br/>
[en] El ID de comando de menú asociado a la herramienta de usuario.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el comando asociado a la herramienta de usuario se ejecutó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Llame a este método para ejecutar una aplicación asociada a la herramienta de usuario que tiene el identificador de comando especificado por *uiCmdId*.

## <a name="cusertoolsmanagerisusertoolcmd"></a><a name="isusertoolcmd"></a>CUserToolsManager::IsUserToolCmd

Determina si un identificador de comando está asociado a una herramienta de usuario.

```
BOOL IsUserToolCmd(UINT uiCmdId) const;
```

### <a name="parameters"></a>Parámetros

*uiCmdId*<br/>
[en] Un identificador de comando del elemento de menú.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si un identificador de comando determinado está asociado a una herramienta de usuario; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método comprueba si el ID de comando dado está en el intervalo de ID de comando. Especifique el intervalo cuando se llama a [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) para habilitar las herramientas de usuario.

## <a name="cusertoolsmanagerloadstate"></a><a name="loadstate"></a>CUserToolsManager::LoadState

Carga información sobre las herramientas de usuario desde el registro de Windows.

```
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
[en] La ruta de acceso de la clave del Registro de Windows.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el estado se cargó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método carga el `CUserToolsManager` estado del objeto desde el registro de Windows.

Normalmente, no se llama a este método directamente. [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate) lo llama como parte del proceso de inicialización del área de trabajo.

## <a name="cusertoolsmanagermovetooldown"></a><a name="movetooldown"></a>CUserToolsManager::MoveToolDown

Mueve la herramienta de usuario especificada hacia abajo en la lista de herramientas de usuario.

```
BOOL MoveToolDown(CUserTool* pTool);
```

### <a name="parameters"></a>Parámetros

*pTool*<br/>
[en] Especifica la herramienta de usuario que se va a mover.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la herramienta de usuario se movió hacia abajo correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El método falla si la herramienta que la *pTool* especifica no está en la lista interna o si la herramienta es la última de la lista.

## <a name="cusertoolsmanagermovetoolup"></a><a name="movetoolup"></a>CUserToolsManager::MoveToolUp

Mueve la herramienta de usuario especificada hacia arriba en la lista de herramientas de usuario.

```
BOOL MoveToolUp(CUserTool* pTool);
```

### <a name="parameters"></a>Parámetros

*pTool*<br/>
[en] Especifica la herramienta de usuario que se va a mover.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la herramienta de usuario se ha movido hacia arriba correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El método falla si la herramienta que especifica el parámetro *pTool* no está en la lista interna o si la herramienta es el primer elemento de herramienta de la lista.

## <a name="cusertoolsmanagerremovetool"></a><a name="removetool"></a>CUserToolsManager::RemoveTool

Quita la herramienta de usuario especificada de la aplicación.

```
BOOL RemoveTool(CUserTool* pTool);
```

### <a name="parameters"></a>Parámetros

*pTool*<br/>
[adentro, fuera] Puntero a una herramienta de usuario que se va a quitar.

### <a name="return-value"></a>Valor devuelto

TRUESi la herramienta se ha quitado correctamente. De lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si la herramienta se elimina correctamente, este método elimina *pTool*.

## <a name="cusertoolsmanagersavestate"></a><a name="savestate"></a>CUserToolsManager::SaveState

Almacena información sobre las herramientas de usuario en el registro de Windows.

```
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
[en] Una ruta de acceso a la clave del Registro de Windows.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el estado se guardó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El método almacena el `CUserToolsManager` estado actual del objeto en el registro de Windows.

Normalmente, no es necesario llamar a este método directamente, [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate) lo llama automáticamente como parte del proceso de serialización del área de trabajo de la aplicación.

## <a name="cusertoolsmanagersetdefext"></a><a name="setdefext"></a>CUserToolsManager::SetDefExt

Especifica la extensión predeterminada que utiliza el cuadro de diálogo **Abrir archivo** ( [Clase CFileDialog](../../mfc/reference/cfiledialog-class.md)) en el campo **Comando** de la ficha **Herramientas** del cuadro de diálogo **Personalizar.**

```cpp
void SetDefExt(const CString& strDefExt);
```

### <a name="parameters"></a>Parámetros

*strDefExt*<br/>
[en] Cadena de texto que contiene la extensión de nombre de archivo predeterminada.

### <a name="remarks"></a>Observaciones

Llame a este método para especificar una extensión de nombre de archivo predeterminada en el cuadro de diálogo **Abrir archivo,** que se muestra cuando el usuario selecciona una aplicación para asociar con la herramienta de usuario. El valor predeterminado es "exe".

## <a name="cusertoolsmanagersetfilter"></a><a name="setfilter"></a>CUserToolsManager::SetFilter

Especifica el filtro de archivo que utiliza el cuadro de diálogo **Abrir archivo** ( [Clase CFileDialog](../../mfc/reference/cfiledialog-class.md)) en el campo **Comando** de la ficha **Herramientas** del cuadro de diálogo **Personalizar.**

```cpp
void SetFilter(const CString& strFilter);
```

### <a name="parameters"></a>Parámetros

*strFilter*<br/>
[en] Especifica el filtro.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[CUserTool (clase)](../../mfc/reference/cusertool-class.md)
