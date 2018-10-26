---
title: CMouseManager (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d430ab70818dafb883e405b082f60c86689853cb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081045"
---
# <a name="cmousemanager-class"></a>CMouseManager (clase)

Permite que un usuario asociar diferentes comandos a un determinado [CView](../../mfc/reference/cview-class.md) objeto cuando el usuario hace doble clic dentro de esa vista.

## <a name="syntax"></a>Sintaxis

```
class CMouseManager : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMouseManager::AddView](#addview)|Agrega un `CView` de objeto para el **personalización** cuadro de diálogo. El **personalización** cuadro de diálogo permite al usuario asociar un doble clic con un comando para cada una de las vistas de lista.|
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|Devuelve el comando que se ejecuta cuando el usuario hace doble clic dentro de la vista proporcionada.|
|[CMouseManager::GetViewIconId](#getviewiconid)|Devuelve el icono asociado al identificador de vista proporcionado.|
|[CMouseManager::GetViewIdByName](#getviewidbyname)|Devuelve el identificador de vista asociado con el nombre de vista proporcionado.|
|[CMouseManager::GetViewNames](#getviewnames)|Recupera una lista de todos los nombres de vista se ha agregado.|
|[CMouseManager::LoadState](#loadstate)|Carga el `CMouseManager` estado desde el registro de Windows.|
|[CMouseManager::SaveState](#savestate)|Escribe el `CMouseManager` estado en el registro de Windows.|
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|Asocia el comando proporcionado y la vista proporcionada.|

## <a name="remarks"></a>Comentarios

El `CMouseManager` clase mantiene una colección de `CView` objetos. Cada vista se identifica mediante un nombre y con un identificador. Estas vistas se muestran en el **personalización** cuadro de diálogo. El usuario puede cambiar el comando que está asociado con cualquier vista a través de la **personalización** cuadro de diálogo. El comando asociado se ejecuta cuando el usuario hace doble clic en esa vista. Para admitir esto desde una perspectiva de programación, debe procesar el mensaje de WM_LBUTTONDBLCLK y llamar a la [CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick) función en el código para que `CView` objeto...

No debería crear un `CMouseManager` objeto manualmente. Se creará el marco de trabajo de la aplicación. También se destruirá automáticamente cuando el usuario sale de la aplicación. Para obtener un puntero al administrador del mouse para la aplicación, llame a [CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMouseManager`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmousemanager.h

##  <a name="addview"></a>  CMouseManager::AddView

Registra un [CView](../../mfc/reference/cview-class.md) objeto con el [CMouseManager (clase)](../../mfc/reference/cmousemanager-class.md) para admitir el comportamiento personalizado del mouse.

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
[in] Un identificador de la vista.

*uiViewNameResId*<br/>
[in] Un identificador de cadena de recurso que se hace referencia al nombre de vista.

*uiIconId*<br/>
[in] Un identificador de icono de vista.

*iId*<br/>
[in] Un identificador de la vista.

*lpszViewName*<br/>
[in] Un nombre de vista.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Con el fin de admitir el comportamiento personalizado del mouse, una vista debe estar registrada en el `CMouseManager` objeto. Cualquier objeto derivado de la `CView` clase se puede registrar con el administrador del mouse. La cadena y el icono asociado a una vista se muestran en el **Mouse** pestaña de la **personalizar** cuadro de diálogo.

Es responsabilidad del programador para crear y mantener los identificadores de vista como *iViewId* y *iId*.

Para obtener más información acerca de cómo proporcionar un comportamiento personalizado del mouse, consulte [personalización del teclado y Mouse](../../mfc/keyboard-and-mouse-customization.md).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo recuperar un puntero a un `CMouseManager` objeto utilizando el `CWinAppEx::GetMouseManager` método y el `AddView` método en el `CMouseManager` clase. Este fragmento de código forma parte de la [ejemplo de la colección de estados](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]

##  <a name="getviewdblclickcommand"></a>  CMouseManager::GetViewDblClickCommand

Devuelve el comando que se ejecuta cuando el usuario hace doble clic dentro de la vista proporcionada.

```
UINT GetViewDblClickCommand(int iId) const;
```

### <a name="parameters"></a>Parámetros

*iId*<br/>
[in] El identificador de la vista.

### <a name="return-value"></a>Valor devuelto

El identificador de comando si la vista está asociada con un comando; en caso contrario, es 0.

##  <a name="getviewiconid"></a>  CMouseManager::GetViewIconId

Recupera el icono asociado con un identificador de la vista.

```
UINT GetViewIconId(int iViewId) const;
```

### <a name="parameters"></a>Parámetros

*iViewId*<br/>
[in] El identificador de la vista.

### <a name="return-value"></a>Valor devuelto

Un identificador de recurso de icono, si se realiza correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método se producirá un error si la vista no se registra primero mediante el uso de [CMouseManager::AddView](#addview).

##  <a name="getviewidbyname"></a>  CMouseManager::GetViewIdByName

Recupera el identificador de vista asociado con un nombre de vista.

```
int GetViewIdByName(LPCTSTR lpszName) const;
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
[in] El nombre de vista.

### <a name="return-value"></a>Valor devuelto

Un identificador de la vista si se realiza correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método busca a través de vistas registradas mediante [CMouseManager::AddView](#addview).

##  <a name="getviewnames"></a>  CMouseManager::GetViewNames

Recupera una lista de todos los nombres de vista registrados.

```
void GetViewNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parámetros

*listOfNames*<br/>
[out] Una referencia a `CStringList` objeto.

### <a name="remarks"></a>Comentarios

Este método rellena el parámetro `listOfNames` con los nombres de todas las vistas registrados mediante [CMouseManager::AddView](#addview).

##  <a name="loadstate"></a>  CMouseManager::LoadState

Carga el estado de la [CMouseManager (clase)](../../mfc/reference/cmousemanager-class.md) del registro.

```
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
[in] Una ruta de acceso de una clave del registro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

La información de estado que se carga desde el registro incluye las vistas registradas, los identificadores de vista y los comandos asociados. Si el parámetro *lpszProfileName* es NULL, esta función se carga el `CMouseManager` datos desde la ubicación del registro predeterminada controlada por el [CWinAppEx (clase)](../../mfc/reference/cwinappex-class.md).

En la mayoría de los casos, no es necesario llamar directamente a esta función. Se llama como parte del proceso de inicialización del área de trabajo. Para obtener más información sobre el proceso de inicialización del área de trabajo, consulte [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate).

##  <a name="savestate"></a>  CMouseManager::SaveState

Escribe el estado de la [CMouseManager (clase)](../../mfc/reference/cmousemanager-class.md) en el registro.

```
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
[in] Una ruta de acceso de una clave del registro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

La información de estado que se escriben en el registro incluye todas las instancias registradas vistas, los identificadores de vista y los comandos asociados. Si el parámetro *lpszProfileName* es NULL, esta función escribe el `CMouseManager` datos a la ubicación del registro predeterminada controlada por el [CWinAppEx (clase)](../../mfc/reference/cwinappex-class.md).

En la mayoría de los casos, no es necesario llamar directamente a esta función. Se llama como parte del proceso de serialización del área de trabajo. Para obtener más información sobre el proceso de serialización del área de trabajo, consulte [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).

##  <a name="setcommandfordblclk"></a>  CMouseManager::SetCommandForDblClk

Asocia un comando personalizado a una vista que se registra primero con el administrador del mouse.

```
void SetCommandForDblClk(
    int iViewId,
    UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*iViewId*<br/>
[in] El identificador de la vista.

*uiCmd*<br/>
[in] Identificador de comando.

### <a name="remarks"></a>Comentarios

Con el fin de asociar un comando personalizado a una vista, primero debe registrar la vista mediante [CMouseManager::AddView](#addview). El `AddView` método requiere un identificador de la vista como un parámetro de entrada. Una vez que registra una vista, puede llamar a `CMouseManager::SetCommandForDblClk` con la misma vista identificador parámetro de entrada que ha proporcionado a `AddView`. A partir de entonces, cuando el usuario hace doble clic del mouse (ratón) en la vista registrada, la aplicación ejecutará el comando indicado por *uiCmd.* Para admitir el comportamiento personalizado del mouse, también deberá personalizar la vista registrada con el administrador del mouse. Para obtener más información sobre el comportamiento personalizado del mouse, consulte [personalización del teclado y Mouse](../keyboard-and-mouse-customization.md).

Si *uiCmd* se establece en 0, ya no está asociada a un comando de la vista especificada.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx (clase)](../../mfc/reference/cwinappex-class.md)<br/>
[Personalización del teclado y del mouse](../../mfc/keyboard-and-mouse-customization.md)

