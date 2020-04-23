---
title: CMFCShellTreeCtrl Clase
ms.date: 11/04/2016
f1_keywords:
- CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::EnableShellContextMenu
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetItemPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetRelatedList
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnChildNotify
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemIcon
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemText
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::Refresh
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SelectPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetRelatedList
helpviewer_keywords:
- CMFCShellTreeCtrl [MFC], EnableShellContextMenu
- CMFCShellTreeCtrl [MFC], GetFlags
- CMFCShellTreeCtrl [MFC], GetItemPath
- CMFCShellTreeCtrl [MFC], GetRelatedList
- CMFCShellTreeCtrl [MFC], OnChildNotify
- CMFCShellTreeCtrl [MFC], OnGetItemIcon
- CMFCShellTreeCtrl [MFC], OnGetItemText
- CMFCShellTreeCtrl [MFC], Refresh
- CMFCShellTreeCtrl [MFC], SelectPath
- CMFCShellTreeCtrl [MFC], SetFlags
- CMFCShellTreeCtrl [MFC], SetRelatedList
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
ms.openlocfilehash: c6f5856e92c2aca1d23ee6a37b99ea9700ea6db0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753447"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl Clase

La `CMFCShellTreeCtrl` clase extiende la funcionalidad de la [clase CTreeCtrl](../../mfc/reference/ctreectrl-class.md) mostrando una jerarquía de elementos de Shell.

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Habilita o deshabilita el menú contextual.|
|[CMFCShellTreeCtrl::GetFlags](#getflags)|Devuelve una combinación de marcas que se pasan a [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Recupera la ruta de acceso a un elemento.|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|Devuelve un puntero a la [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) clase `CMFCShellTreeCtrl` objeto que se usa junto con este objeto para crear una ventana similar al Explorador.|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|Esta función miembro es llamada por la ventana primaria de esta ventana cuando recibe un mensaje de notificación que se aplica a esta ventana. (Reemplaza [CWnd::OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl::Refresh](#refresh)|Actualiza y vuelve a `CMFCShellTreeCtrl` pintar el objeto actual.|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Selecciona el elemento de control de árbol adecuado en función de un PIDL o ruta de acceso de cadena proporcionado.|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Establece marcas para filtrar el contexto de `IShellFolder::EnumObjects`árbol (similar a las marcas utilizadas por ).|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Establece una relación `CMFCShellTreeCtrl` entre el `CMFCShellListCtrl` objeto actual y un objeto.|

## <a name="remarks"></a>Observaciones

Esta clase amplía `CTreeCtrl` la clase habilitando el programa para incluir elementos de Shell de Windows en el árbol. Esta clase se puede `CMFCShellListCtrl` asociar a un objeto para crear una ventana completa del Explorador. A continuación, al seleccionar un elemento en el árbol se mostrará una lista de elementos de Windows Shell en la lista asociada.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxshelltreeCtrl.h

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo crear un objeto de la clase `CMFCShellTreeCtrl`. Este fragmento de código forma parte del [ejemplo Explorer](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

## <a name="cmfcshelltreectrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellTreeCtrl::EnableShellContextMenu

Habilita el menú contextual.

```cpp
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] Un valor booleano que especifica si se debe habilitar el menú contextual.

## <a name="cmfcshelltreectrlgetflags"></a><a name="getflags"></a>CMFCShellTreeCtrl::GetFlags

Devuelve las marcas establecidas para el [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objeto de clase.

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor DWORD que especifica la combinación de indicadores establecidos actualmente.

### <a name="remarks"></a>Observaciones

Las marcas establecidas en el `CMFCShellTreeCtrl` se envían al método [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) cada vez que se actualiza el objeto. Puede cambiar las marcas con el [CMFCShellTreeCtrl::SetFlags](#setflags) método.

## <a name="cmfcshelltreectrlgetitempath"></a><a name="getitempath"></a>CMFCShellTreeCtrl::GetItemPath

Recupera la ruta de acceso de un elemento en el [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) clase objeto.

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>Parámetros

*strPath*<br/>
[fuera] Una referencia a un parámetro de cadena. El método escribe la ruta de acceso del elemento en este parámetro.

*htreeItem*<br/>
[en] El método recupera la ruta de acceso para este elemento de control de árbol.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 en caso contrario.

### <a name="remarks"></a>Observaciones

Si se produce un error en este método, *strPath* contiene la cadena vacía.

Si no especifica *hTreeItem*, este método intenta obtener la cadena para el elemento seleccionado actualmente. Si no se selecciona ningún elemento y *hTreeItem* es NULL, se produce un error en este método.

## <a name="cmfcshelltreectrlgetrelatedlist"></a><a name="getrelatedlist"></a>CMFCShellTreeCtrl::GetRelatedList

Devuelve un puntero a la [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto que está asociado a este [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objeto.

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al `CMFCShellListCtrl` objeto asociado a este objeto de control de árbol.

### <a name="remarks"></a>Observaciones

Mediante el `CMFCShellListCtrl` uso de `CMFCShellTreeCtrl` un objeto junto con un objeto, puede crear una ventana similar al Explorador. Utilice el método [CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist) para asociar las dos clases. Una vez asociados, el `CMFCShellListCtrl` marco de trabajo `CMFCShellTreeCtrl` actualiza automáticamente la selección if en los cambios.

## <a name="cmfcshelltreectrlonchildnotify"></a><a name="onchildnotify"></a>CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>Parámetros

[en] *mensaje*<br/>
[en] *wParam*<br/>
[en] *lParam*<br/>
[en] *pLResult*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcshelltreectrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>Parámetros

[en] *pItem*<br/>
[en] *bSeleccionado*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcshelltreectrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parámetros

[en] *pItem*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcshelltreectrlrefresh"></a><a name="refresh"></a>CMFCShellTreeCtrl::Refresh

Actualiza y vuelve a pintar [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md).

```cpp
void Refresh();
```

### <a name="remarks"></a>Observaciones

Llame a este método para actualizar la `CMFCShellTreeCtrl`jerarquía de los elementos que se muestran en el archivo .

## <a name="cmfcshelltreectrlselectpath"></a><a name="selectpath"></a>CMFCShellTreeCtrl::SelectPath

Selecciona un elemento de la [CMFCShellTreeCtrl clase](../../mfc/reference/cmfcshelltreectrl-class.md) basada en la ruta de acceso proporcionada.

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>Parámetros

*lpszPath*<br/>
[en] Cadena que especifica la ruta de acceso de un elemento.

*lpidl*<br/>
[en] Un PIDL que especifica el elemento

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; E_FAIL de lo contrario.

## <a name="cmfcshelltreectrlsetflags"></a><a name="setflags"></a>CMFCShellTreeCtrl::SetFlags

Establece marcas para filtrar el contexto de árbol.

```cpp
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
[en] Las banderas que se han establecido.

*bRefresh*<br/>
[en] Un valor booleano `CMFCShellTreeCtrl` que especifica si se debe actualizar inmediatamente.

### <a name="remarks"></a>Observaciones

El `CMFCShellTreeCtrl` pasa todos los indicadores set a [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects). Para obtener más información acerca de los valores de diferentes marcas, vea [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).

## <a name="cmfcshelltreectrlsetrelatedlist"></a><a name="setrelatedlist"></a>CMFCShellTreeCtrl::SetRelatedList

Asocia un [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto con un [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objeto.

```cpp
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>Parámetros

*pShellList*<br/>
[en] Un puntero `CMFCShellListCtrl` a un objeto.

### <a name="remarks"></a>Observaciones

Este método `CMFCShellListCtrl` asocia `CMFCShellTreeCtrl`un archivo . Estos objetos se pueden mostrar como una ventana similar al Explorador: si el usuario selecciona un objeto en el `CMFCShellTreeCtrl`, los elementos asociados en el `CMFCShellListCtrl` se actualizarán automáticamente.

Utilice el método [CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist) para recuperar el `CMFCShellListCtrl` asociado a un `CMFCShellTreeCtrl`archivo .

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl (clase)](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl (clase)](../../mfc/reference/cmfcshelllistctrl-class.md)
