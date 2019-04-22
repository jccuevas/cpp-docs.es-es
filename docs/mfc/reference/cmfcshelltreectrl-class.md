---
title: CMFCShellTreeCtrl Class
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
ms.openlocfilehash: 1fc422c3aca3efe1fb177e7a3567530d70c27119
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58779760"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl Class

El `CMFCShellTreeCtrl` extiende la clase [CTreeCtrl (clase)](../../mfc/reference/ctreectrl-class.md) funcionalidad mostrando una jerarquía de elementos de Shell.

Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.
## <a name="syntax"></a>Sintaxis

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Habilita o deshabilita el menú contextual.|
|[CMFCShellTreeCtrl::GetFlags](#getflags)|Devuelve una combinación de marcas que se pasan a [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Recupera la ruta de acceso a un elemento.|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|Devuelve un puntero a la [CMFCShellListCtrl (clase)](../../mfc/reference/cmfcshelllistctrl-class.md) objeto que se usa junto con esto `CMFCShellTreeCtrl` objeto para crear una ventana similar al explorador.|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|Esta ventana primaria llama a esta función miembro cuando recibe un mensaje de notificación que se aplica a esta ventana. (Invalida [CWnd::OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl::Refresh](#refresh)|Actualiza y vuelve a dibujar actual `CMFCShellTreeCtrl` objeto.|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Selecciona el elemento de control de árbol apropiado en función de una ruta de acceso de cadena o PIDL proporcionado.|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Establece marcas para filtrar el contexto de árbol (similar a las marcas usadas por `IShellFolder::EnumObjects`).|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Establece una relación entre el representador actual `CMFCShellTreeCtrl` objeto y un `CMFCShellListCtrl` objeto.|

## <a name="remarks"></a>Comentarios

Esta clase extiende la `CTreeCtrl` clase habilitando el programa incluir elementos de Shell de Windows en el árbol. Esta clase se puede asociar un `CMFCShellListCtrl` objeto para crear una ventana del explorador completa. A continuación, seleccionar un elemento en el árbol mostrará una lista de elementos de Shell de Windows en la lista asociada.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>Requisitos

**Header:** afxshelltreeCtrl.h

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo crear un objeto de la clase `CMFCShellTreeCtrl`. Este fragmento de código forma parte de la [ejemplo Explorer](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

##  <a name="enableshellcontextmenu"></a>  CMFCShellTreeCtrl::EnableShellContextMenu

Permite el acceso directo.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
[in] Valor booleano que especifica si se habilita el menú contextual.

##  <a name="getflags"></a>  CMFCShellTreeCtrl::GetFlags

Devuelve las marcas establecidas para el [CMFCShellTreeCtrl (clase)](../../mfc/reference/cmfcshelltreectrl-class.md) objeto.

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>Valor devuelto

Establece un valor DWORD que especifica la combinación de marcas actualmente.

### <a name="remarks"></a>Comentarios

Las marcas establecidas el `CMFCShellTreeCtrl` se envían al método [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) cada vez que el objeto se actualiza. Puede cambiar los indicadores con el [CMFCShellTreeCtrl::SetFlags](#setflags) método.

##  <a name="getitempath"></a>  CMFCShellTreeCtrl::GetItemPath

Recupera la ruta de acceso de un elemento en el [CMFCShellTreeCtrl (clase)](../../mfc/reference/cmfcshelltreectrl-class.md) objeto.

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>Parámetros

*strPath*<br/>
[out] Una referencia a un parámetro de cadena. El método escribe la ruta de acceso del elemento a este parámetro.

*htreeItem*<br/>
[in] El método recupera la ruta de acceso para este elemento de control de árbol.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si este método produce un error, *strPath* contiene una cadena vacía.

Si no especifica *hTreeItem*, este método intenta obtener la cadena del elemento actualmente seleccionado. Si se selecciona ningún elemento y *hTreeItem* es NULL, este método produce un error.

##  <a name="getrelatedlist"></a>  CMFCShellTreeCtrl::GetRelatedList

Devuelve un puntero a la [CMFCShellListCtrl (clase)](../../mfc/reference/cmfcshelllistctrl-class.md) objeto que está asociado con este [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objeto.

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la `CMFCShellListCtrl` objeto que está asociado a este objeto de control de árbol.

### <a name="remarks"></a>Comentarios

Mediante el uso de un `CMFCShellListCtrl` objeto junto con un `CMFCShellTreeCtrl` de objeto, puede crear una ventana similar al explorador. Utilice el método [CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist) para asociar las dos clases. Una vez asociados, el marco de trabajo se actualiza automáticamente el `CMFCShellListCtrl` si la selección en el `CMFCShellTreeCtrl` los cambios.

##  <a name="onchildnotify"></a>  CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>Parámetros

[in] *message*<br/>
[in] *wParam*<br/>
[in] *lParam*<br/>
[in] *pLResult*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="ongetitemicon"></a>  CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>Parámetros

[in] *pItem*<br/>
[in] *bSelected*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="ongetitemtext"></a>  CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parámetros

[in] *pItem*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="refresh"></a>  CMFCShellTreeCtrl::Refresh

Actualiza y vuelve a dibujar el [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md).

```
void Refresh();
```

### <a name="remarks"></a>Comentarios

Llame a este método para actualizar la jerarquía de los elementos mostrados en la `CMFCShellTreeCtrl`.

##  <a name="selectpath"></a>  CMFCShellTreeCtrl::SelectPath

Selecciona un elemento en el [CMFCShellTreeCtrl (clase)](../../mfc/reference/cmfcshelltreectrl-class.md) basándose en la ruta de acceso proporcionada.

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>Parámetros

*lpszPath*<br/>
[in] Una cadena que especifica la ruta de acceso de un elemento.

*lpidl*<br/>
[in] Un PIDL que especifica el elemento

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; E_FAIL en caso contrario.

##  <a name="setflags"></a>  CMFCShellTreeCtrl::SetFlags

Establece marcas para filtrar el contexto del árbol.

```
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
[in] Para establecer las marcas.

*bRefresh*<br/>
[in] Un valor booleano que especifica si el `CMFCShellTreeCtrl` debe actualizarse inmediatamente.

### <a name="remarks"></a>Comentarios

El `CMFCShellTreeCtrl` pasadas todos establecer marcas para [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects). Para obtener más información acerca de los valores de los indicadores, vea [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).

##  <a name="setrelatedlist"></a>  CMFCShellTreeCtrl::SetRelatedList

Asocia un [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto con un [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objeto.

```
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>Parámetros

*pShellList*<br/>
[in] Un puntero a un `CMFCShellListCtrl` objeto.

### <a name="remarks"></a>Comentarios

Este método asocia un `CMFCShellListCtrl` con un `CMFCShellTreeCtrl`. Estos objetos pueden aparecer como una ventana similar al explorador: si el usuario selecciona un objeto en el `CMFCShellTreeCtrl`, el asociado los elementos de la `CMFCShellListCtrl` se actualizará automáticamente.

Utilice el método [CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist) para recuperar el `CMFCShellListCtrl` asociado con un `CMFCShellTreeCtrl`.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl (clase)](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl (clase)](../../mfc/reference/cmfcshelllistctrl-class.md)
