---
title: Clase CMFCShellTreeCtrl
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
ms.openlocfilehash: 97136342049a54d45af893962025f01eda4366d4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504904"
---
# <a name="cmfcshelltreectrl-class"></a>Clase CMFCShellTreeCtrl

La `CMFCShellTreeCtrl` clase extiende la funcionalidad de la [clase CTreeCtrl](../../mfc/reference/ctreectrl-class.md) mostrando una jerarquía de elementos de Shell.

Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.
## <a name="syntax"></a>Sintaxis

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Habilita o deshabilita el menú contextual.|
|[CMFCShellTreeCtrl::GetFlags](#getflags)|Devuelve una combinación de marcas que se pasan a [IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Recupera la ruta de acceso a un elemento.|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|Devuelve un puntero al objeto de la [clase objeto cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) que se usa junto con `CMFCShellTreeCtrl` este objeto para crear una ventana similar a la del explorador.|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|La ventana primaria de esta ventana llama a esta función miembro cuando recibe un mensaje de notificación que se aplica a esta ventana. (Invalida [CWnd:: OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify)).|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl::Refresh](#refresh)|Actualiza y vuelve a dibujar el objeto actual `CMFCShellTreeCtrl` .|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Selecciona el elemento de control de árbol adecuado en función de una ruta de acceso de cadena o PIDL proporcionada.|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Establece marcas para filtrar el contexto de árbol (similar a las marcas `IShellFolder::EnumObjects`usadas por).|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Establece una relación entre el objeto `CMFCShellTreeCtrl` actual y un `CMFCShellListCtrl` objeto.|

## <a name="remarks"></a>Comentarios

Esta clase extiende la `CTreeCtrl` clase habilitando el programa para incluir elementos de Windows Shell en el árbol. Esta clase se puede asociar a `CMFCShellListCtrl` un objeto para crear una ventana completa del explorador. A continuación, al seleccionar un elemento en el árbol, se mostrará una lista de elementos del shell de Windows en la lista asociada.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxshelltreeCtrl. h

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo crear un objeto de la clase `CMFCShellTreeCtrl`. Este fragmento de código forma parte del [ejemplo de explorador](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

##  <a name="enableshellcontextmenu"></a>  CMFCShellTreeCtrl::EnableShellContextMenu

Habilita el menú contextual.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
de Valor booleano que especifica si se debe habilitar el menú contextual.

##  <a name="getflags"></a>  CMFCShellTreeCtrl::GetFlags

Devuelve el conjunto de marcadores para el objeto de la [clase CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>Valor devuelto

Valor DWORD que especifica la combinación de marcas establecidas actualmente.

### <a name="remarks"></a>Comentarios

Las marcas establecidas en `CMFCShellTreeCtrl` se envían al método [IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) cada vez que se actualiza el objeto. Puede cambiar las marcas con el método [CMFCShellTreeCtrl:: SetFlags](#setflags) .

##  <a name="getitempath"></a>  CMFCShellTreeCtrl::GetItemPath

Recupera la ruta de acceso de un elemento en el objeto de la [clase CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>Parámetros

*strPath*<br/>
enuncia Referencia a un parámetro de cadena. El método escribe la ruta de acceso del elemento en este parámetro.

*htreeItem*<br/>
de El método recupera la ruta de acceso de este elemento de control de árbol.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 en caso contrario.

### <a name="remarks"></a>Comentarios

Si se produce un error en este método, *strPath* contiene la cadena vacía.

Si no especifica *hTreeItem*, este método intenta obtener la cadena del elemento seleccionado actualmente. Si no se selecciona ningún elemento y *hTreeItem* es null, se produce un error en este método.

##  <a name="getrelatedlist"></a>  CMFCShellTreeCtrl::GetRelatedList

Devuelve un puntero al objeto de la [clase objeto cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) que está asociado a este objeto [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al `CMFCShellListCtrl` objeto que está asociado a este objeto de control de árbol.

### <a name="remarks"></a>Comentarios

Mediante el uso `CMFCShellListCtrl` de un objeto junto `CMFCShellTreeCtrl` con un objeto, puede crear una ventana similar a la del explorador. Use el método [CMFCShellTreeCtrl:: SetRelatedList](#setrelatedlist) para asociar las dos clases. Una vez asociados, el marco `CMFCShellListCtrl` `CMFCShellTreeCtrl` de trabajo actualiza automáticamente el objeto si se cambia la selección de.

##  <a name="onchildnotify"></a>  CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>Parámetros

de *mensaje* de<br/>
de *wParam*<br/>
de *lParam*<br/>
de *pLResult*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="ongetitemicon"></a>  CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>Parámetros

de *pItem*<br/>
de *bSelected*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="ongetitemtext"></a>  CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parámetros

de *pItem*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="refresh"></a>  CMFCShellTreeCtrl::Refresh

Actualiza y vuelve a dibujar el [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md).

```
void Refresh();
```

### <a name="remarks"></a>Comentarios

Llame a este método para actualizar la jerarquía de los elementos que se `CMFCShellTreeCtrl`muestran en.

##  <a name="selectpath"></a>  CMFCShellTreeCtrl::SelectPath

Selecciona un elemento de la [clase CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) basándose en la ruta de acceso proporcionada.

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>Parámetros

*lpszPath*<br/>
de Cadena que especifica la ruta de acceso de un elemento.

*lpidl*<br/>
de PIDL que especifica el elemento.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; E_FAIL en caso contrario.

##  <a name="setflags"></a>  CMFCShellTreeCtrl::SetFlags

Establece marcas para filtrar el contexto de árbol.

```
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
de Marcas que se van a establecer.

*bRefresh*<br/>
de Valor booleano que especifica si `CMFCShellTreeCtrl` se debe actualizar inmediatamente.

### <a name="remarks"></a>Comentarios

El `CMFCShellTreeCtrl` pasa todas las marcas de conjunto a [IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects). Para obtener más información sobre los valores de diferentes marcas, vea [IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).

##  <a name="setrelatedlist"></a>  CMFCShellTreeCtrl::SetRelatedList

Asocia un objeto [objeto cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) con un objeto [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>Parámetros

*pShellList*<br/>
de Un puntero a un `CMFCShellListCtrl` objeto.

### <a name="remarks"></a>Comentarios

Este método asocia un `CMFCShellListCtrl` con un `CMFCShellTreeCtrl`. Estos objetos se pueden mostrar como una ventana de tipo explorador: Si el usuario selecciona un objeto en `CMFCShellTreeCtrl`, los elementos asociados `CMFCShellListCtrl` en se actualizarán automáticamente.

Use el método [CMFCShellTreeCtrl:: GetRelatedList](#getrelatedlist) para recuperar el `CMFCShellListCtrl` asociado `CMFCShellTreeCtrl`a.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl (clase)](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl (clase)](../../mfc/reference/cmfcshelllistctrl-class.md)
