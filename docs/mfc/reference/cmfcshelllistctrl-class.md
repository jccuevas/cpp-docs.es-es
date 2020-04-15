---
title: CMFCShellListCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayParentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::EnableShellContextMenu
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolderName
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentItemIdList
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentShellFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemPath
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemTypes
- AFXSHELLLISTCTRL/CMFCShellListCtrl::IsDesktop
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnCompareItems
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileDate
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileSize
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemIcon
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemText
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnSetColumns
- AFXSHELLLISTCTRL/CMFCShellListCtrl::Refresh
- AFXSHELLLISTCTRL/CMFCShellListCtrl::SetItemTypes
helpviewer_keywords:
- CMFCShellListCtrl [MFC], DisplayFolder
- CMFCShellListCtrl [MFC], DisplayParentFolder
- CMFCShellListCtrl [MFC], EnableShellContextMenu
- CMFCShellListCtrl [MFC], GetCurrentFolder
- CMFCShellListCtrl [MFC], GetCurrentFolderName
- CMFCShellListCtrl [MFC], GetCurrentItemIdList
- CMFCShellListCtrl [MFC], GetCurrentShellFolder
- CMFCShellListCtrl [MFC], GetItemPath
- CMFCShellListCtrl [MFC], GetItemTypes
- CMFCShellListCtrl [MFC], IsDesktop
- CMFCShellListCtrl [MFC], OnCompareItems
- CMFCShellListCtrl [MFC], OnFormatFileDate
- CMFCShellListCtrl [MFC], OnFormatFileSize
- CMFCShellListCtrl [MFC], OnGetItemIcon
- CMFCShellListCtrl [MFC], OnGetItemText
- CMFCShellListCtrl [MFC], OnSetColumns
- CMFCShellListCtrl [MFC], Refresh
- CMFCShellListCtrl [MFC], SetItemTypes
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
ms.openlocfilehash: d5c987e1d7dbe053a0cff093d1a9113f762cee26
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368778"
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl (clase)

La `CMFCShellListCtrl` clase proporciona funcionalidad de control de lista de Windows y la expande mediante la inclusión de la capacidad de mostrar una lista de elementos de shell.

## <a name="syntax"></a>Sintaxis

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|Muestra una lista de elementos contenidos en una carpeta proporcionada.|
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|Muestra una lista de elementos que se encuentran en la carpeta que es el elemento primario de la carpeta que se muestra actualmente.|
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Habilita o deshabilita el menú contextual.|
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Recupera la ruta de acceso de la carpeta actual.|
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Recupera el nombre de la carpeta actual.|
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Devuelve el PIDL del elemento de control de lista actual.|
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Devuelve un puntero a la carpeta Shell actual.|
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Devuelve la ruta de acceso textual de un elemento.|
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Devuelve los tipos de elemento Shell que muestra el control de lista.|
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|Comprueba si la carpeta seleccionada actualmente es la carpeta de escritorio.|
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|El marco de trabajo llama a este método cuando compara dos elementos. (Reemplaza [CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|Se llama cuando el marco de trabajo recupera la fecha de archivo que muestra el control de lista.|
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|Se llama cuando el marco de trabajo convierte el tamaño de archivo de un control de lista.|
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|Se llama cuando el marco de trabajo recupera el icono de un elemento de control de lista.|
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Se llama cuando el marco de trabajo convierte el texto de un elemento de control de lista.|
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Llamado por el marco de trabajo cuando establece los nombres de las columnas.|
|[CMFCShellListCtrl::Refresh](#refresh)|Actualiza y vuelve a pintar el control de lista.|
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Establece el tipo de elementos mostrados por el control de lista.|

## <a name="remarks"></a>Observaciones

La `CMFCShellListCtrl` clase extiende la funcionalidad de la [CMFCListCtrl clase](../../mfc/reference/cmfclistctrl-class.md) habilitando el programa para enumerar los elementos de shell de Windows. El formato de visualización que se utiliza es similar al de una vista de lista para una ventana del Explorador.

Un [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objeto se `CMFCShellListCtrl` puede asociar a un objeto para crear una ventana completa del Explorador. A continuación, si `CMFCShellTreeCtrl` selecciona un `CMFCShellListCtrl` elemento en el, el objeto mostrará la lista del contenido del elemento seleccionado.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCShellListCtrl` cómo crear un objeto de la clase y cómo mostrar la carpeta primaria de la carpeta que se muestra actualmente. Este fragmento de código forma parte del [ejemplo Explorer](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

`CMFCShellListCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxshelllistCtrl.h

## <a name="cmfcshelllistctrldisplayfolder"></a><a name="displayfolder"></a>CMFCShellListCtrl::DisplayFolder

Muestra una lista de elementos contenidos en la carpeta proporcionada.

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>Parámetros

*lpszPath*<br/>
[en] Cadena que contiene la ruta de acceso de una carpeta.

*lpItemInfo*<br/>
[en] Puntero a `LPAFX_SHELLITEMINFO` una estructura que describe una carpeta que se va a mostrar.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; E_FAIL de lo contrario.

## <a name="cmfcshelllistctrldisplayparentfolder"></a><a name="displayparentfolder"></a>CMFCShellListCtrl::DisplayParentFolder

Actualiza el [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto para mostrar la carpeta primaria de la carpeta que se muestra actualmente.

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; E_FAIL de lo contrario.

## <a name="cmfcshelllistctrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellListCtrl::EnableShellContextMenu

Habilita el menú contextual.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] Un valor booleano que especifica si el marco de trabajo habilita el menú contextual.

## <a name="cmfcshelllistctrlgetcurrentfolder"></a><a name="getcurrentfolder"></a>CMFCShellListCtrl::GetCurrentFolder

Recupera la ruta de acceso de la carpeta seleccionada actualmente en el [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto.

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>Parámetros

*strPath*<br/>
[fuera] Una referencia a un parámetro de cadena donde el método escribe la ruta de acceso.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 en caso contrario.

### <a name="remarks"></a>Observaciones

Este método falla si no hay `CMFCShellListCtrl`ninguna carpeta seleccionada en el archivo .

## <a name="cmfcshelllistctrlgetcurrentfoldername"></a><a name="getcurrentfoldername"></a>CMFCShellListCtrl::GetCurrentFolderName

Recupera el nombre de la carpeta seleccionada actualmente en el [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto.

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>Parámetros

*strName*<br/>
[fuera] Una referencia a un parámetro de cadena donde el método escribe el nombre.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 en caso contrario.

### <a name="remarks"></a>Observaciones

Este método falla si no hay `CMFCShellListCtrl`ninguna carpeta seleccionada en el archivo .

## <a name="cmfcshelllistctrlgetcurrentitemidlist"></a><a name="getcurrentitemidlist"></a>CMFCShellListCtrl::GetCurrentItemIdList

Devuelve el PIDL del elemento seleccionado actualmente.

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>Valor devuelto

El PIDL del elemento actual.

## <a name="cmfcshelllistctrlgetcurrentshellfolder"></a><a name="getcurrentshellfolder"></a>CMFCShellListCtrl::GetCurrentShellFolder

Obtiene un puntero al elemento seleccionado actualmente en el [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto.

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la [interfaz IShellFolder](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder) para el objeto seleccionado.

### <a name="remarks"></a>Observaciones

Este método devuelve NULL si no hay ningún objeto seleccionado actualmente.

## <a name="cmfcshelllistctrlgetitempath"></a><a name="getitempath"></a>CMFCShellListCtrl::GetItemPath

Recupera la ruta de acceso de un elemento.

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>Parámetros

*strPath*<br/>
[fuera] Una referencia a una cadena que recibe la ruta de acceso.

*iItem*<br/>
[en] El índice del elemento de lista.

### <a name="return-value"></a>Valor devuelto

TRUESi se realiza correctamente; FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

El índice proporcionado por *iItem* se basa en los elementos que muestra actualmente el [CMFCShellListCtrl clase](../../mfc/reference/cmfcshelllistctrl-class.md) objeto.

## <a name="cmfcshelllistctrlgetitemtypes"></a><a name="getitemtypes"></a>CMFCShellListCtrl::GetItemTypes

Devuelve el tipo de elementos mostrados por el [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto.

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf) que contiene el `CMFCShellListCtrl`tipo de elementos enumerados en el archivo .

### <a name="remarks"></a>Observaciones

Para establecer el tipo de `CMFCShellListCtrl`elementos enumerados en un archivo , llame a [CMFCShellListCtrl::SetItemTypes](#setitemtypes).

## <a name="cmfcshelllistctrlisdesktop"></a><a name="isdesktop"></a>CMFCShellListCtrl::IsDesktop

Determina si la carpeta que se muestra en el [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto es la carpeta de escritorio.

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi la carpeta mostrada es la carpeta de escritorio; FALSE en caso contrario.

## <a name="cmfcshelllistctrloncompareitems"></a><a name="oncompareitems"></a>CMFCShellListCtrl::OnCompareItems

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parámetros

[en] *lParam1*<br/>
[en] *lParam2*<br/>
[en] *iColumn*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcshelllistctrlonformatfiledate"></a><a name="onformatfiledate"></a>CMFCShellListCtrl::OnFormatFileDate

El marco de trabajo llama a este método cuando debe convertir la fecha asociada a un objeto en una cadena.

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>Parámetros

*tmFile*<br/>
[en] La fecha asociada a un archivo.

*Str*<br/>
[fuera] Cadena que contiene la fecha del archivo con formato.

### <a name="remarks"></a>Observaciones

Cuando un [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) clase objeto muestra la fecha asociada a un archivo, debe convertir esa fecha a un formato de cadena. El `CMFCShellListCtrl` utiliza este método para realizar esa conversión. De forma predeterminada, este método utiliza la configuración regional actual para dar formato a la fecha en una cadena.

## <a name="cmfcshelllistctrlonformatfilesize"></a><a name="onformatfilesize"></a>CMFCShellListCtrl::OnFormatFileSize

El marco de trabajo llama a este método cuando convierte el tamaño de un objeto en una cadena.

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>Parámetros

*lFileSize*<br/>
[en] El tamaño del archivo que mostrará el marco de trabajo.

*Str*<br/>
[fuera] Cadena que contiene el tamaño de archivo con formato.

### <a name="remarks"></a>Observaciones

Cuando un [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) clase objeto necesita mostrar el tamaño de un archivo, debe convertir el tamaño de archivo en un formato de cadena. El `CMFCShellListCtrl` utiliza este método para realizar esa conversión. De forma predeterminada, este método convierte el tamaño del archivo de bytes a kilobytes y, a continuación, usa la configuración regional actual para dar formato al tamaño en cadena.

## <a name="cmfcshelllistctrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShellListCtrl::OnGetItemIcon

El marco de trabajo llama a este método para recuperar el icono asociado a un elemento de lista de shell.

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parámetros

*iItem*<br/>
[en] El índice de elementos.

*pItem*<br/>
[en] Un parámetro LPAFX_SHELLITEMINFO que describe el elemento.

### <a name="return-value"></a>Valor devuelto

El índice de la imagen del icono si se realiza correctamente; -1 si la función falla.

### <a name="remarks"></a>Observaciones

El índice de imagen de icono se basa en la lista de imágenes del sistema.

De forma predeterminada, este método se basa en el *pItem* parámetro. El valor de *iItem* no se utiliza en la implementación predeterminada. Puede usar *iItem* para implementar un comportamiento personalizado.

## <a name="cmfcshelllistctrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShellListCtrl::OnGetItemText

El marco de trabajo llama a este método cuando debe recuperar el texto de un elemento de shell.

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parámetros

*iItem*<br/>
[en] El índice de elementos.

*iColumn*<br/>
[en] La columna de interés.

*pItem*<br/>
[en] Un parámetro LPAFX_SHELLITEMINFO que describe el elemento.

### <a name="return-value"></a>Valor devuelto

A `CString` que contiene el texto asociado al elemento.

### <a name="remarks"></a>Observaciones

Cada elemento `CMFCShellListCtrl` del objeto puede tener texto en una o más columnas. Cuando el marco de trabajo llama a este método, especifica la columna que le interesa. Si llama a esta función manualmente, también debe especificar la columna que le interesa.

De forma predeterminada, este método se basa en el *pItem* parámetro para determinar qué elemento para procesar. El valor de *iItem* no se utiliza en la implementación predeterminada.

## <a name="cmfcshelllistctrlonsetcolumns"></a><a name="onsetcolumns"></a>CMFCShellListCtrl::OnSetColumns

El marco de trabajo llama a este método cuando establece los nombres de las columnas.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, el marco `CMFCShellListCtrl` de trabajo crea cuatro columnas en un objeto. Los nombres de estas columnas son **Nombre**, **Tamaño**, **Tipo**y **Modificado**. Puede invalidar este método para personalizar el número de columnas y sus nombres.

## <a name="cmfcshelllistctrlrefresh"></a><a name="refresh"></a>CMFCShellListCtrl::Refresh

Actualiza y vuelve a pintar el [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto.

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>Valor devuelto

`S_OK`si tiene éxito; de lo contrario un valor de error.

### <a name="remarks"></a>Observaciones

Llame a este método para actualizar la `CMFCShellListCtrl` lista de elementos mostrados por el objeto.

## <a name="cmfcshelllistctrlsetitemtypes"></a><a name="setitemtypes"></a>CMFCShellListCtrl::SetItemTypes

Establece el tipo de elementos que se enumeran en el [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto.

```
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>Parámetros

*nTipos*<br/>
[en] Una lista de tipos `CMFCShellListCtrl` de elementos que admite el objeto.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de la lista de tipos de elementos, vea [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf).

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)<br/>
[CMFCShellTreeCtrl Clase](../../mfc/reference/cmfcshelltreectrl-class.md)
