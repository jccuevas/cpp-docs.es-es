---
title: Clase CMouseManager
ms.date: 11/04/2016
f1_keywords:
- CMouseManager
- AFXMOUSEMANAGER/CMouseManager
- AFXMOUSEMANAGER/CMouseManager::AddView
- AFXMOUSEMANAGER/CMouseManager::GetViewDblClickCommand
- AFXMOUSEMANAGER/CMouseManager::GetViewIconId
- AFXMOUSEMANAGER/CMouseManager::GetViewIdByName
- AFXMOUSEMANAGER/CMouseManager::GetViewNames
- AFXMOUSEMANAGER/CMouseManager::LoadState
- AFXMOUSEMANAGER/CMouseManager::SaveState
- AFXMOUSEMANAGER/CMouseManager::SetCommandForDblClk
helpviewer_keywords:
- CMouseManager [MFC], AddView
- CMouseManager [MFC], GetViewDblClickCommand
- CMouseManager [MFC], GetViewIconId
- CMouseManager [MFC], GetViewIdByName
- CMouseManager [MFC], GetViewNames
- CMouseManager [MFC], LoadState
- CMouseManager [MFC], SaveState
- CMouseManager [MFC], SetCommandForDblClk
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
ms.openlocfilehash: d05a2e186f001a69310e99cec013193a4d1bff3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319719"
---
# <a name="cmousemanager-class"></a>Clase CMouseManager

Permite a un usuario asociar diferentes comandos con un objeto [CView](../../mfc/reference/cview-class.md) determinado cuando el usuario hace doble clic dentro de esa vista.

## <a name="syntax"></a>Sintaxis

```
class CMouseManager : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMouseManager::AddView](#addview)|Agrega un `CView` objeto al cuadro de diálogo **Personalización.** El cuadro de diálogo **Personalización** permite al usuario asociar un doble clic con un comando para cada una de las vistas enumeradas.|
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|Devuelve el comando que se ejecuta cuando el usuario hace doble clic dentro de la vista proporcionada.|
|[CMouseManager::GetViewIconId](#getviewiconid)|Devuelve el icono asociado con el identificador de vista proporcionado.|
|[CMouseManager::GetViewIdByName](#getviewidbyname)|Devuelve el identificador de vista asociado con el nombre de vista proporcionado.|
|[CMouseManager::GetViewNames](#getviewnames)|Recupera una lista de todos los nombres de vista agregados.|
|[CMouseManager::LoadState](#loadstate)|Carga `CMouseManager` el estado desde el registro de Windows.|
|[CMouseManager::SaveState](#savestate)|Escribe el `CMouseManager` estado en el registro de Windows.|
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|Asocia el comando proporcionado y la vista proporcionada.|

## <a name="remarks"></a>Observaciones

La `CMouseManager` clase mantiene una `CView` colección de objetos. Cada vista se identifica por un nombre y por un identificador. Estas vistas se muestran en el cuadro de diálogo **Personalización.** El usuario puede cambiar el comando asociado a cualquier vista a través del cuadro de diálogo **Personalización.** El comando asociado se ejecuta cuando el usuario hace doble clic en esa vista. Para admitir esto desde una perspectiva de codificación, debe procesar el mensaje WM_LBUTTONDBLCLK y llamar a `CView` la [función CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick) en el código de ese objeto..

No debe crear `CMouseManager` un objeto manualmente. Se creará mediante el marco de la aplicación. También se destruirá automáticamente cuando el usuario salga de la aplicación. Para obtener un puntero al administrador del mouse de la aplicación, llame a [CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMouseManager`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmousemanager.h

## <a name="cmousemanageraddview"></a><a name="addview"></a>CMouseManager::AddView

Registra un [CView](../../mfc/reference/cview-class.md) objeto con el [CMouseManager clase](../../mfc/reference/cmousemanager-class.md) para admitir el comportamiento personalizado del mouse.

```
BOOL AddView(
    int iViewId,
    UINT uiViewNameResId,
    UINT uiIconId = 0);

BOOL AddView(
    int iId,
    LPCTSTR lpszViewName,
    UINT uiIconId = 0);
```

### <a name="parameters"></a>Parámetros

*iViewId*<br/>
[en] Un ID de vista.

*uiViewNameResId*<br/>
[en] Identificador de cadena de recursos que hace referencia al nombre de la vista.

*uiIconId*<br/>
[en] Un identificador de icono de vista.

*Iid*<br/>
[en] Un ID de vista.

*lpszViewName*<br/>
[en] Un nombre de vista.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Para admitir el comportamiento personalizado del mouse, `CMouseManager` se debe registrar una vista con el objeto. Cualquier objeto derivado `CView` de la clase se puede registrar con el administrador del mouse. La cadena y el icono asociados a una vista se muestran en la ficha **Ratón** del cuadro de diálogo **Personalizar.**

Es responsabilidad del programador crear y mantener identificadores de vista como *iViewId* e *iId*.

Para obtener más información sobre cómo proporcionar un comportamiento personalizado del mouse, vea [Personalización de teclado y mouse](../../mfc/keyboard-and-mouse-customization.md).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMouseManager` cómo recuperar `CWinAppEx::GetMouseManager` un puntero `AddView` a `CMouseManager` un objeto mediante el método y el método de la clase. Este fragmento de código forma parte del [ejemplo de colección de](../../overview/visual-cpp-samples.md)estado.

[!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]

## <a name="cmousemanagergetviewdblclickcommand"></a><a name="getviewdblclickcommand"></a>CMouseManager::GetViewDblClickCommand

Devuelve el comando que se ejecuta cuando el usuario hace doble clic dentro de la vista proporcionada.

```
UINT GetViewDblClickCommand(int iId) const;
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] El identificador de vista.

### <a name="return-value"></a>Valor devuelto

El identificador de comando si la vista está asociada a un comando; de lo contrario 0.

## <a name="cmousemanagergetviewiconid"></a><a name="getviewiconid"></a>CMouseManager::GetViewIconId

Recupera el icono asociado a un identificador de vista.

```
UINT GetViewIconId(int iViewId) const;
```

### <a name="parameters"></a>Parámetros

*iViewId*<br/>
[en] El identificador de vista.

### <a name="return-value"></a>Valor devuelto

Un identificador de recurso de icono si se realiza correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método producirá un error si la vista no se registra primero mediante [CMouseManager::AddView](#addview).

## <a name="cmousemanagergetviewidbyname"></a><a name="getviewidbyname"></a>CMouseManager::GetViewIdByName

Recupera el identificador de vista asociado a un nombre de vista.

```
int GetViewIdByName(LPCTSTR lpszName) const;
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
[en] El nombre de la vista.

### <a name="return-value"></a>Valor devuelto

Un identificador de vista si se realiza correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método busca en vistas registradas mediante [CMouseManager::AddView](#addview).

## <a name="cmousemanagergetviewnames"></a><a name="getviewnames"></a>CMouseManager::GetViewNames

Recupera una lista de todos los nombres de vista registrados.

```
void GetViewNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parámetros

*listOfNames*<br/>
[fuera] Una referencia `CStringList` al objeto.

### <a name="remarks"></a>Observaciones

Este método rellena `listOfNames` el parámetro con los nombres de todas las vistas registradas mediante [CMouseManager::AddView](#addview).

## <a name="cmousemanagerloadstate"></a><a name="loadstate"></a>CMouseManager::LoadState

Carga el estado de la [clase CMouseManager](../../mfc/reference/cmousemanager-class.md) desde el registro.

```
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
[en] Una ruta de acceso de una clave del Registro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La información de estado cargada desde el registro incluye las vistas registradas, los identificadores de vista y los comandos asociados. Si el parámetro *lpszProfileName* es NULL, esta función carga los `CMouseManager` datos desde la ubicación predeterminada del Registro controlada por la clase [CWinAppEx](../../mfc/reference/cwinappex-class.md).

En la mayoría de los casos, no es necesario llamar a esta función directamente. Se llama como parte del proceso de inicialización del espacio de trabajo. Para obtener más información sobre el proceso de inicialización del área de trabajo, vea [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate).

## <a name="cmousemanagersavestate"></a><a name="savestate"></a>CMouseManager::SaveState

Escribe el estado de la [clase CMouseManager](../../mfc/reference/cmousemanager-class.md) en el registro.

```
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
[en] Una ruta de acceso de una clave del Registro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La información de estado escrita en el registro incluye todas las vistas registradas, identificadores de vista y los comandos asociados. Si el parámetro *lpszProfileName* es NULL, `CMouseManager` esta función escribe los datos en la ubicación predeterminada del Registro controlada por la [clase CWinAppEx](../../mfc/reference/cwinappex-class.md).

En la mayoría de los casos, no es necesario llamar a esta función directamente. Se llama como parte del proceso de serialización del área de trabajo. Para obtener más información sobre el proceso de serialización del área de trabajo, vea [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).

## <a name="cmousemanagersetcommandfordblclk"></a><a name="setcommandfordblclk"></a>CMouseManager::SetCommandForDblClk

Asocia un comando personalizado con una vista que se registra por primera vez con el administrador del mouse.

```
void SetCommandForDblClk(
    int iViewId,
    UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*iViewId*<br/>
[en] El identificador de vista.

*uiCmd*<br/>
[in] El identificador de comando.

### <a name="remarks"></a>Observaciones

Para asociar un comando personalizado a una vista, primero debe registrar la vista mediante [CMouseManager::AddView](#addview). El `AddView` método requiere un identificador de vista como parámetro de entrada. Una vez que registre una `CMouseManager::SetCommandForDblClk` vista, puede llamar con el `AddView`mismo parámetro de entrada de identificador de vista que proporcionó a . A partir de entonces, cuando el usuario hace doble clic en el mouse en la vista registrada, la aplicación ejecutará el comando indicado por *uiCmd.* Para admitir el comportamiento personalizado del mouse, también tendrá que personalizar la vista registrada con el administrador del mouse. Para obtener más información sobre el comportamiento personalizado del mouse, vea [Personalización de teclado y mouse](../keyboard-and-mouse-customization.md).

Si *uiCmd* se establece en 0, la vista especificada ya no está asociada a un comando.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[Personalización de teclado y ratón](../../mfc/keyboard-and-mouse-customization.md)
