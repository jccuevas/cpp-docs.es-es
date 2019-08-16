---
title: Clase objeto cmfcshelllistctrl
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
ms.openlocfilehash: 02d4883c6b5445515d891c5e76ccf10b6bb35bba
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504919"
---
# <a name="cmfcshelllistctrl-class"></a>Clase objeto cmfcshelllistctrl

La `CMFCShellListCtrl` clase proporciona la funcionalidad de control de lista de Windows y la expande mediante la inclusión de la capacidad de mostrar una lista de elementos de Shell.

## <a name="syntax"></a>Sintaxis

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|Muestra una lista de elementos contenidos en una carpeta proporcionada.|
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|Muestra una lista de elementos contenidos en la carpeta primaria de la carpeta que se muestra actualmente.|
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Habilita o deshabilita el menú contextual.|
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Recupera la ruta de acceso de la carpeta actual.|
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Recupera el nombre de la carpeta actual.|
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Devuelve el PIDL del elemento de control de lista actual.|
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Devuelve un puntero a la carpeta de Shell actual.|
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Devuelve la ruta de acceso textual de un elemento.|
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Devuelve los tipos de elemento de Shell que se muestran en el control de lista.|
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|Comprueba si la carpeta seleccionada actualmente es la carpeta del escritorio.|
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|El marco de trabajo llama a este método cuando compara dos elementos. (Invalida [CMFCListCtrl:: OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems)).|
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|Se llama cuando el marco de trabajo recupera la fecha de archivo que muestra el control de lista.|
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|Se llama cuando el marco de trabajo convierte el tamaño de archivo de un control de lista.|
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|Se llama cuando el marco de trabajo recupera el icono de un elemento de control de lista.|
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Se llama cuando el marco de trabajo convierte el texto de un elemento de control de lista.|
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Lo llama el marco de trabajo cuando establece los nombres de las columnas.|
|[CMFCShellListCtrl::Refresh](#refresh)|Actualiza y vuelve a dibujar el control de lista.|
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Establece el tipo de elementos mostrados por el control de lista.|

## <a name="remarks"></a>Comentarios

La `CMFCShellListCtrl` clase extiende la funcionalidad de la [clase CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) al permitir que el programa Enumere los elementos de Windows Shell. El formato de presentación que se usa es similar al de una vista de lista para una ventana del explorador.

Un objeto [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) se puede asociar a `CMFCShellListCtrl` un objeto para crear una ventana completa del explorador. A continuación, si selecciona un elemento `CMFCShellTreeCtrl` en el, `CMFCShellListCtrl` el objeto mostrará el contenido del elemento seleccionado.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo crear un objeto de `CMFCShellListCtrl` la clase y cómo mostrar la carpeta primaria de la carpeta que se muestra actualmente. Este fragmento de código forma parte del [ejemplo de explorador](../../overview/visual-cpp-samples.md).

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

**Encabezado:** afxshelllistCtrl. h

##  <a name="displayfolder"></a>  CMFCShellListCtrl::DisplayFolder

Muestra una lista de elementos contenidos en la carpeta proporcionada.

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>Parámetros

*lpszPath*<br/>
de Cadena que contiene la ruta de acceso de una carpeta.

*lpItemInfo*<br/>
de Puntero a una `LPAFX_SHELLITEMINFO` estructura que describe la carpeta que se va a mostrar.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; E_FAIL en caso contrario.

##  <a name="displayparentfolder"></a>  CMFCShellListCtrl::DisplayParentFolder

Actualiza el objeto [objeto cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) para mostrar la carpeta primaria de la carpeta que se muestra actualmente.

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; E_FAIL en caso contrario.

##  <a name="enableshellcontextmenu"></a>  CMFCShellListCtrl::EnableShellContextMenu

Habilita el menú contextual.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
de Un valor booleano que especifica si el marco de trabajo habilita el menú contextual.

##  <a name="getcurrentfolder"></a>  CMFCShellListCtrl::GetCurrentFolder

Recupera la ruta de acceso de la carpeta actualmente seleccionada en el objeto [objeto cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>Parámetros

*strPath*<br/>
enuncia Referencia a un parámetro de cadena donde el método escribe la ruta de acceso.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 en caso contrario.

### <a name="remarks"></a>Comentarios

Este método produce un error si no hay ninguna carpeta seleccionada `CMFCShellListCtrl`en.

##  <a name="getcurrentfoldername"></a>  CMFCShellListCtrl::GetCurrentFolderName

Recupera el nombre de la carpeta actualmente seleccionada en el objeto [objeto cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>Parámetros

*strName*<br/>
enuncia Referencia a un parámetro de cadena donde el método escribe el nombre.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 en caso contrario.

### <a name="remarks"></a>Comentarios

Este método produce un error si no hay ninguna carpeta seleccionada `CMFCShellListCtrl`en.

##  <a name="getcurrentitemidlist"></a>  CMFCShellListCtrl::GetCurrentItemIdList

Devuelve el PIDL del elemento actualmente seleccionado.

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>Valor devuelto

PIDL del elemento actual.

##  <a name="getcurrentshellfolder"></a>  CMFCShellListCtrl::GetCurrentShellFolder

Obtiene un puntero al elemento actualmente seleccionado en el objeto [objeto cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la [interfaz IShellFolder](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder) para el objeto seleccionado.

### <a name="remarks"></a>Comentarios

Este método devuelve NULL si no hay ningún objeto seleccionado actualmente.

##  <a name="getitempath"></a>  CMFCShellListCtrl::GetItemPath

Recupera la ruta de acceso de un elemento.

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>Parámetros

*strPath*<br/>
enuncia Referencia a una cadena que recibe la ruta de acceso.

*iItem*<br/>
de Índice del elemento de lista.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; De lo contrario, FALSE.

### <a name="remarks"></a>Comentarios

El índice proporcionado por *iItem* se basa en los elementos mostrados actualmente por el objeto de la [clase objeto cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

##  <a name="getitemtypes"></a>  CMFCShellListCtrl::GetItemTypes

Devuelve el tipo de elementos que muestra el objeto [objeto cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf) que contiene el tipo de elementos enumerados en `CMFCShellListCtrl`.

### <a name="remarks"></a>Comentarios

Para establecer el tipo de elementos enumerados en `CMFCShellListCtrl`, llame a [objeto cmfcshelllistctrl:: SetItemTypes](#setitemtypes).

##  <a name="isdesktop"></a>  CMFCShellListCtrl::IsDesktop

Determina si la carpeta que se muestra en el objeto [objeto cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) es la carpeta del escritorio.

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si la carpeta mostrada es la carpeta de escritorio; De lo contrario, FALSE.

##  <a name="oncompareitems"></a>  CMFCShellListCtrl::OnCompareItems

Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parámetros

de *lParam1*<br/>
de *lParam2*<br/>
de *iColumn*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="onformatfiledate"></a>  CMFCShellListCtrl::OnFormatFileDate

El marco de trabajo llama a este método cuando debe convertir la fecha asociada a un objeto en una cadena.

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>Parámetros

*tmFile*<br/>
de Fecha asociada a un archivo.

*str*<br/>
enuncia Cadena que contiene la fecha de archivo con formato.

### <a name="remarks"></a>Comentarios

Cuando un objeto de [clase objeto cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) muestra la fecha asociada a un archivo, debe convertir esa fecha en un formato de cadena. `CMFCShellListCtrl` Utiliza este método para hacer esa conversión. De forma predeterminada, este método usa la configuración regional actual para dar formato a la fecha en una cadena.

##  <a name="onformatfilesize"></a>  CMFCShellListCtrl::OnFormatFileSize

El marco de trabajo llama a este método cuando convierte el tamaño de un objeto en una cadena.

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>Parámetros

*lFileSize*<br/>
de Tamaño del archivo que mostrará el marco de trabajo.

*str*<br/>
enuncia Cadena que contiene el tamaño de archivo con formato.

### <a name="remarks"></a>Comentarios

Cuando un objeto de [clase objeto cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) necesita mostrar el tamaño de un archivo, debe convertir el tamaño de archivo en un formato de cadena. `CMFCShellListCtrl` Utiliza este método para hacer esa conversión. De forma predeterminada, este método convierte el tamaño del archivo de bytes a kilobytes y, a continuación, usa la configuración regional actual para dar formato al tamaño en una cadena.

##  <a name="ongetitemicon"></a>  CMFCShellListCtrl::OnGetItemIcon

El marco de trabajo llama a este método para recuperar el icono asociado a un elemento de lista de Shell.

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parámetros

*iItem*<br/>
de Índice del elemento.

*pItem*<br/>
de Un parámetro LPAFX_SHELLITEMINFO que describe el elemento.

### <a name="return-value"></a>Valor devuelto

Índice de la imagen de icono si se realiza correctamente; -1 si se produce un error en la función.

### <a name="remarks"></a>Comentarios

El índice de la imagen de icono se basa en la lista de imágenes del sistema.

De forma predeterminada, este método se basa en el parámetro *pItem* . El valor de *iItem* no se utiliza en la implementación predeterminada. Puede usar *iItem* para implementar el comportamiento personalizado.

##  <a name="ongetitemtext"></a>  CMFCShellListCtrl::OnGetItemText

El marco de trabajo llama a este método cuando debe recuperar el texto de un elemento de Shell.

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parámetros

*iItem*<br/>
de Índice del elemento.

*iColumn*<br/>
de Columna de interés.

*pItem*<br/>
de Un parámetro LPAFX_SHELLITEMINFO que describe el elemento.

### <a name="return-value"></a>Valor devuelto

`CString` Que contiene el texto asociado al elemento.

### <a name="remarks"></a>Comentarios

Cada elemento `CMFCShellListCtrl` del objeto puede tener texto en una o varias columnas. Cuando el marco de trabajo llama a este método, especifica la columna en la que está interesado. Si llama a esta función manualmente, también debe especificar la columna que le interese.

De forma predeterminada, este método se basa en el parámetro *pItem* para determinar qué elemento se va a procesar. El valor de *iItem* no se utiliza en la implementación predeterminada.

##  <a name="onsetcolumns"></a>  CMFCShellListCtrl::OnSetColumns

El marco de trabajo llama a este método cuando establece los nombres de las columnas.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, el marco de trabajo crea cuatro `CMFCShellListCtrl` columnas en un objeto. Los nombres de estas columnas son **nombre**, **tamaño**, **tipo**y **modificado**. Puede invalidar este método para personalizar el número de columnas y sus nombres.

##  <a name="refresh"></a>  CMFCShellListCtrl::Refresh

Actualiza y vuelve a dibujar el objeto [objeto cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>Valor devuelto

`S_OK`Si es correcto; de lo contrario, un valor de error.

### <a name="remarks"></a>Comentarios

Llame a este método para actualizar la lista de elementos que muestra `CMFCShellListCtrl` el objeto.

##  <a name="setitemtypes"></a>  CMFCShellListCtrl::SetItemTypes

Establece el tipo de elementos que se enumeran en el objeto [objeto cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>Parámetros

*nTypes*<br/>
de Una lista de tipos de elemento que `CMFCShellListCtrl` admite el objeto.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre la lista de tipos de elemento, vea [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl (clase)](../../mfc/reference/cmfclistctrl-class.md)<br/>
[CMFCShellTreeCtrl (clase)](../../mfc/reference/cmfcshelltreectrl-class.md)
