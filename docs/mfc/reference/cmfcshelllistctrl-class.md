---
title: CMFCShellListCtrl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 939adc0507eee61be432ba8e8f582cfc53005aa0
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37854000"
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl (clase)
La `CMFCShellListCtrl` clase proporciona funcionalidad de control de lista de Windows y la expande incluyendo la capacidad para mostrar una lista de elementos de shell.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCShellListCtrl : public CMFCListCtrl  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|Muestra una lista de elementos que se encuentran en una carpeta proporcionada.|  
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|Muestra una lista de elementos que se encuentran en la carpeta que es el elemento primario de la carpeta que se muestra actualmente.|  
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Habilita o deshabilita el menú contextual.|  
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Recupera la ruta de acceso de la carpeta actual.|  
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Recupera el nombre de la carpeta actual.|  
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Devuelve el PIDL del elemento de control de lista actual.|  
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Devuelve un puntero a la carpeta de Shell actual.|  
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Devuelve la ruta de acceso textual de un elemento.|  
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Devuelve los tipos de elemento de Shell que se muestran en el control de lista.|  
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|Comprueba si la carpeta actualmente seleccionada es la carpeta del escritorio.|  
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|El marco llama a este método cuando compara dos elementos. (Invalida [CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|  
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|Se llama cuando el marco de trabajo recupera la fecha del archivo muestra el control de lista.|  
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|Se llama cuando el marco de trabajo convierte el tamaño del archivo de un control de lista.|  
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|Se llama cuando el marco de trabajo recupera el icono de un elemento de control de lista.|  
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Se llama cuando el marco de trabajo convierte el texto de un elemento de control de lista.|  
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Lo llama el marco de trabajo cuando lo establece los nombres de las columnas.|  
|[CMFCShellListCtrl::Refresh](#refresh)|Se actualiza y vuelve a dibujar el control de lista.|  
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Establece el tipo de elementos mostrados por el control de lista.|  
  
## <a name="remarks"></a>Comentarios  
 El `CMFCShellListCtrl` clase extiende la funcionalidad de la [CMFCListCtrl (clase)](../../mfc/reference/cmfclistctrl-class.md) habilitando el programa enumerar los elementos de shell de Windows. El formato de presentación que se usa es similar de una vista de lista para una ventana del explorador.  
  
 Un [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objeto se puede asociar un `CMFCShellListCtrl` objeto para crear una ventana del explorador completa. A continuación, seleccionar un elemento en el `CMFCShellTreeCtrl` provocará la `CMFCShellListCtrl` objeto para mostrar el contenido del elemento seleccionado.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo crear un objeto de la `CMFCShellListCtrl` clase y cómo mostrar la carpeta principal de la carpeta que se muestra actualmente. Este fragmento de código forma parte de la [ejemplo Explorer](../../visual-cpp-samples.md).  
  
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
  
##  <a name="displayfolder"></a>  CMFCShellListCtrl::DisplayFolder  
 Muestra una lista de elementos que se encuentran en la carpeta proporcionada.  
  
```  
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lpszPath*  
 Una cadena que contiene la ruta de acceso de una carpeta.  
  
 [in] *lpItemInfo*  
 Un puntero a un `LPAFX_SHELLITEMINFO` estructura que describe una carpeta para mostrar.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; E_FAIL en caso contrario.  
  
##  <a name="displayparentfolder"></a>  CMFCShellListCtrl::DisplayParentFolder  
 Las actualizaciones de la [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto para mostrar la carpeta principal de la carpeta que se muestra actualmente.  
  
```  
virtual HRESULT DisplayParentFolder();
```  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; E_FAIL en caso contrario.  
  
##  <a name="enableshellcontextmenu"></a>  CMFCShellListCtrl::EnableShellContextMenu  
 Permite el acceso directo.  
  
```  
void EnableShellContextMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bHabilitar el*  
 Un valor booleano que especifica si el marco de trabajo permite el acceso directo.  
  
##  <a name="getcurrentfolder"></a>  CMFCShellListCtrl::GetCurrentFolder  
 Recupera la ruta de acceso de la carpeta actualmente seleccionada en el [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto.  
  
```  
BOOL GetCurrentFolder(CString& strPath) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] *strPath*  
 Una referencia a un parámetro de cadena donde el método escribe la ruta de acceso.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se realiza correctamente; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método produce un error si no hay ninguna carpeta seleccionada en el `CMFCShellListCtrl`.  
  
##  <a name="getcurrentfoldername"></a>  CMFCShellListCtrl::GetCurrentFolderName  
 Recupera el nombre de la carpeta actualmente seleccionada en el [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto.  
  
```  
BOOL GetCurrentFolderName(CString& strName) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] *strName*  
 Una referencia a un parámetro de cadena donde el método escribe el nombre.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se realiza correctamente; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método produce un error si no hay ninguna carpeta seleccionada en el `CMFCShellListCtrl`.  
  
##  <a name="getcurrentitemidlist"></a>  CMFCShellListCtrl::GetCurrentItemIdList  
 Devuelve el PIDL del elemento actualmente seleccionado.  
  
```  
LPITEMIDLIST GetCurrentItemIdList() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 PIDL del elemento actual.  
  
##  <a name="getcurrentshellfolder"></a>  CMFCShellListCtrl::GetCurrentShellFolder  
 Obtiene un puntero al elemento seleccionado actualmente en el [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto.  
  
```  
const IShellFolder* GetCurrentShellFolder() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [IShellFolder interfaz](http://msdn.microsoft.com/library/windows/desktop/bb775075) para el objeto seleccionado.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve NULL si no hay ningún objeto está seleccionado actualmente.  
  
##  <a name="getitempath"></a>  CMFCShellListCtrl::GetItemPath  
 Recupera la ruta de acceso para un elemento.  
  
```  
BOOL GetItemPath(
    CString& strPath,  
    int iItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] *strPath*  
 Una referencia a una cadena que recibe la ruta de acceso.  
  
 [in] *iItem*  
 El índice del elemento de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se realiza correctamente; FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 El índice proporcionado por *iItem* se basa en los elementos mostrados actualmente por el [CMFCShellListCtrl (clase)](../../mfc/reference/cmfcshelllistctrl-class.md) objeto.  
  
##  <a name="getitemtypes"></a>  CMFCShellListCtrl::GetItemTypes  
 Devuelve el tipo de elementos mostrados por la [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto.  
  
```  
SHCONTF GetItemTypes() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [SHCONTF](http://msdn.microsoft.com/library/windows/desktop/bb762539) valor que contiene el tipo de elementos que aparecen en la `CMFCShellListCtrl`.  
  
### <a name="remarks"></a>Comentarios  
 Para establecer el tipo de elementos que aparecen en un `CMFCShellListCtrl`, llame a [CMFCShellListCtrl::SetItemTypes](#setitemtypes).  
  
##  <a name="isdesktop"></a>  CMFCShellListCtrl::IsDesktop  
 Determina si la carpeta que se muestra en el [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto es la carpeta del escritorio.  
  
```  
BOOL IsDesktop() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es TRUE si la carpeta que se muestra es la carpeta del escritorio; FALSE en caso contrario.  
  
##  <a name="oncompareitems"></a>  CMFCShellListCtrl::OnCompareItems  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int OnCompareItems(
    LPARAM lParam1,  
    LPARAM lParam2,  
    int iColumn);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lParam1*  
 [in] *lParam2*  
 [in] *iColumn*  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onformatfiledate"></a>  CMFCShellListCtrl::OnFormatFileDate  
 El marco llama a este método cuando debe convertir la fecha asociada a un objeto en una cadena.  
  
```  
virtual void OnFormatFileDate(
    const CTime& tmFile,  
    CString& str);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *tmFile*  
 La fecha asociada a un archivo.  
  
 [out] *str*  
 Una cadena que contiene la fecha con formato de archivo.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un [CMFCShellListCtrl (clase)](../../mfc/reference/cmfcshelllistctrl-class.md) objeto muestra la fecha asociada a un archivo, que debe convertir esa fecha en un formato de cadena. El `CMFCShellListCtrl` usa este método para realizar esa conversión. De forma predeterminada, este método usa la configuración regional para dar formato a la fecha en una cadena.  
  
##  <a name="onformatfilesize"></a>  CMFCShellListCtrl::OnFormatFileSize  
 El marco llama a este método cuando convierte el tamaño de un objeto en una cadena.  
  
```  
virtual void OnFormatFileSize(
    long lFileSize,  
    CString& str);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lFileSize*  
 El tamaño del archivo que se mostrará el marco de trabajo.  
  
 [out] *str*  
 Una cadena que contiene el tamaño de archivo con formato.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un [CMFCShellListCtrl (clase)](../../mfc/reference/cmfcshelllistctrl-class.md) debe mostrar el tamaño de un archivo de objeto, debe convertir el tamaño del archivo en un formato de cadena. El `CMFCShellListCtrl` usa este método para realizar esa conversión. De forma predeterminada, este método convierte el tamaño del archivo de bytes en kilobytes y, a continuación, utiliza la configuración regional para dar formato el tamaño en cadena.  
  
##  <a name="ongetitemicon"></a>  CMFCShellListCtrl::OnGetItemIcon  
 El marco llama a este método para recuperar el icono asociado a un elemento de lista de shell.  
  
```  
virtual int OnGetItemIcon(
    int iItem,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *iItem*  
 El índice del elemento.  
  
 [in] *pItem*  
 Un parámetro LPAFX_SHELLITEMINFO que describe el elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de la imagen del icono si es correcto; -1 si se produce un error en la función.  
  
### <a name="remarks"></a>Comentarios  
 El índice de imagen del icono se basa en la lista de imágenes del sistema.  
  
 De forma predeterminada, este método se basa en el *pItem* parámetro. El valor de *iItem* no se utiliza en la implementación predeterminada. Puede usar *iItem* para implementar un comportamiento personalizado.  
  
##  <a name="ongetitemtext"></a>  CMFCShellListCtrl::OnGetItemText  
 El marco llama a este método cuando debe recuperar el texto de un elemento de shell.  
  
```  
virtual CString OnGetItemText(
    int iItem,  
    int iColumn,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *iItem*  
 El índice del elemento.  
  
 [in] *iColumn*  
 La columna de interés.  
  
 [in] *pItem*  
 Un parámetro LPAFX_SHELLITEMINFO que describe el elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene el texto asociado al elemento.  
  
### <a name="remarks"></a>Comentarios  
 Cada elemento de la `CMFCShellListCtrl` objeto puede tener el texto en una o varias columnas. Cuando el marco llama a este método, especifica la columna que está interesado. Si se llama a esta función manualmente, también debe especificar la columna que le interesen.  
  
 De forma predeterminada, este método se basa en el *pItem* parámetro para determinar el elemento al proceso. El valor de *iItem* no se utiliza en la implementación predeterminada.  
  
##  <a name="onsetcolumns"></a>  CMFCShellListCtrl::OnSetColumns  
 El marco llama a este método cuando establece los nombres de las columnas.  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el marco de trabajo crea cuatro columnas en un `CMFCShellListCtrl` objeto. Los nombres de estas columnas son **nombre**, **tamaño**, **tipo**, y **Modified**. Puede invalidar este método para personalizar el número de columnas y sus nombres.  
  
##  <a name="refresh"></a>  CMFCShellListCtrl::Refresh  
 Actualiza y vuelve a dibujar el [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto.  
  
```  
virtual HRESULT Refresh();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK` Si se realiza correctamente; en caso contrario, un valor de error.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para actualizar la lista de elementos mostrados por la `CMFCShellListCtrl` objeto.  
  
##  <a name="setitemtypes"></a>  CMFCShellListCtrl::SetItemTypes  
 Establece el tipo de elementos que aparecen en la [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto.  
  
```  
void SetItemTypes(SHCONTF nTypes);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nTypes*  
 Una lista de elementos de tipos que el `CMFCShellListCtrl` objeto admite.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de la lista de tipos de elemento, vea [SHCONTF](http://msdn.microsoft.com/library/windows/desktop/bb762539).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl (clase)](../../mfc/reference/cmfclistctrl-class.md)   
 [CMFCShellTreeCtrl (clase)](../../mfc/reference/cmfcshelltreectrl-class.md)
