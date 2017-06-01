---
title: Clase CMFCShellTreeCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCShellTreeCtrl class
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
caps.latest.revision: 30
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: cf9c7c3577646895546c443c975a92431194d3f4
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcshelltreectrl-class"></a>Clase CMFCShellTreeCtrl
El `CMFCShellTreeCtrl` amplía la clase [CTreeCtrl (clase)](../../mfc/reference/ctreectrl-class.md) funcionalidad mostrando una jerarquía de elementos de Shell.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCShellTreeCtrl : public CTreeCtrl  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Habilita o deshabilita el menú contextual.|  
|[CMFCShellTreeCtrl::GetFlags](#getflags)|Devuelve una combinación de indicadores que se pasan a [IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066).|  
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Recupera la ruta de acceso a un elemento.|  
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|Devuelve un puntero a la [CMFCShellListCtrl clase](../../mfc/reference/cmfcshelllistctrl-class.md) objeto que se utiliza junto con este `CMFCShellTreeCtrl` objeto para crear una ventana similar al explorador.|  
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|Se llama a esta función miembro por esta ventana primaria cuando recibe un mensaje de notificación que se aplica a esta ventana. (Invalida [CWnd::OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|  
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||  
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||  
|[CMFCShellTreeCtrl::Refresh](#refresh)|Actualiza y vuelve a dibujar actual `CMFCShellTreeCtrl` objeto.|  
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Selecciona el elemento de control de árbol apropiado según un PIDL proporcionado o ruta de acceso de cadena.|  
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Establece los indicadores para filtrar el contexto de árbol (similar a los marcadores utilizados por `IShellFolder::EnumObjects`).|  
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Establece una relación entre la corriente `CMFCShellTreeCtrl` objeto y un `CMFCShellListCtrl` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase extiende la `CTreeCtrl` clase habilitando el programa incluir elementos de Shell de Windows en el árbol. Esta clase puede asociarse con un `CMFCShellListCtrl` objeto para crear una ventana del explorador completa. A continuación, seleccionar un elemento en el árbol mostrará una lista de elementos de Shell de Windows en la lista asociada.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CTreeCtrl](../../mfc/reference/ctreectrl-class.md)  
  
 `CMFCShellTreeCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxshelltreeCtrl.h  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo crear un objeto de la clase `CMFCShellTreeCtrl`. Este fragmento de código forma parte de la [ejemplo Explorer](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_Explorer Nº&4;](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer&#5;](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]  
  
##  <a name="enableshellcontextmenu"></a>CMFCShellTreeCtrl::EnableShellContextMenu  
 Permite el acceso directo.  
  
```  
void EnableShellContextMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 Valor booleano que especifica si se habilita el menú contextual.  
  
##  <a name="getflags"></a>CMFCShellTreeCtrl::GetFlags  
 Devuelve los marcadores establecidos para la [CMFCShellTreeCtrl clase](../../mfc/reference/cmfcshelltreectrl-class.md) objeto.  
  
```  
DWORD GetFlags() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `DWORD` establece el valor que especifica la combinación de indicadores actualmente.  
  
### <a name="remarks"></a>Comentarios  
 Las marcas establecidas el `CMFCShellTreeCtrl` se envían al método [IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066) cada vez que se actualiza el objeto. Puede cambiar las marcas con el [CMFCShellTreeCtrl::SetFlags](#setflags) método.  
  
##  <a name="getitempath"></a>CMFCShellTreeCtrl::GetItemPath  
 Recupera la ruta de acceso de un elemento en el [CMFCShellTreeCtrl clase](../../mfc/reference/cmfcshelltreectrl-class.md) objeto.  
  
```  
BOOL GetItemPath(
    CString& strPath,  
    HTREEITEM htreeItem = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `strPath`  
 Una referencia a un parámetro de cadena. El método escribe la ruta de acceso del elemento a este parámetro.  
  
 [in] `htreeItem`  
 El método recupera la ruta de acceso para este elemento de control de árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error en este método, `strPath` contiene la cadena vacía.  
  
 Si no se especifica `hTreeItem`, este método intenta obtener la cadena del elemento actualmente seleccionado. Si se selecciona ningún elemento y `hTreeItem` es `NULL`, este método produce un error.  
  
##  <a name="getrelatedlist"></a>CMFCShellTreeCtrl::GetRelatedList  
 Devuelve un puntero a la [CMFCShellListCtrl clase](../../mfc/reference/cmfcshelllistctrl-class.md) objeto asociado con este [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objeto.  
  
```  
CMFCShellListCtrl* GetRelatedList() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `CMFCShellListCtrl` objeto que está asociado a este objeto de control de árbol.  
  
### <a name="remarks"></a>Comentarios  
 Mediante el uso de un `CMFCShellListCtrl` objeto junto con un `CMFCShellTreeCtrl` de objeto, puede crear una ventana similar al explorador. Utilice el método [CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist) para asociar las dos clases. Una vez que están asociadas, el marco de trabajo actualiza automáticamente el `CMFCShellListCtrl` si la selección en el `CMFCShellTreeCtrl` cambios.  
  
##  <a name="onchildnotify"></a>CMFCShellTreeCtrl::OnChildNotify  

  
```  
virtual BOOL OnChildNotify(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam,  
    LRESULT* pLResult);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `message`  
 [in] `wParam`  
 [in] `lParam`  
 [in] `pLResult`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ongetitemicon"></a>CMFCShellTreeCtrl::OnGetItemIcon  

  
```  
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pItem`  
 [in] `bSelected`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ongetitemtext"></a>CMFCShellTreeCtrl::OnGetItemText  

  
```  
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pItem`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="refresh"></a>CMFCShellTreeCtrl::Refresh  
 Actualiza y vuelve a dibujar el [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md).  
  
```  
void Refresh();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para actualizar la jerarquía de los elementos mostrados en la `CMFCShellTreeCtrl`.  
  
##  <a name="selectpath"></a>CMFCShellTreeCtrl::SelectPath  
 Selecciona un elemento en el [CMFCShellTreeCtrl clase](../../mfc/reference/cmfcshelltreectrl-class.md) basándose en la ruta de acceso proporcionada.  
  
```  
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszPath`  
 Cadena que especifica la ruta de acceso de un elemento.  
  
 [in] `lpidl`  
 Un PIDL que especifica el elemento  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`Si es correcto; `E_FAIL` en caso contrario.  
  
##  <a name="setflags"></a>CMFCShellTreeCtrl::SetFlags  
 Establece los indicadores para filtrar el contexto del árbol.  
  
```  
void SetFlags(
    DWORD dwFlags,  
    BOOL bRefresh = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwFlags`  
 Marcas que se van a establecer.  
  
 [in] `bRefresh`  
 Un valor booleano que especifica si el `CMFCShellTreeCtrl` debe actualizarse inmediatamente.  
  
### <a name="remarks"></a>Comentarios  
 El `CMFCShellTreeCtrl` pasa todos establecen marcadores en [IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066). Para obtener más información acerca de los valores de indicadores, consulte [IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066).  
  
##  <a name="setrelatedlist"></a>CMFCShellTreeCtrl::SetRelatedList  
 Asocia un [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objeto con un [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objeto.  
  
```  
void SetRelatedList(CMFCShellListCtrl* pShellList);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pShellList`  
 Un puntero a un `CMFCShellListCtrl` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Este método asocia un `CMFCShellListCtrl` con un `CMFCShellTreeCtrl`. Estos objetos se muestran como una ventana de explorador: si el usuario selecciona un objeto en el `CMFCShellTreeCtrl`, el asociado elementos en el `CMFCShellListCtrl` se actualizará automáticamente.  
  
 Utilice el método [CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist) para recuperar la `CMFCShellListCtrl` asociado con un `CMFCShellTreeCtrl`.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CTreeCtrl (clase)](../../mfc/reference/ctreectrl-class.md)   
 [Clase CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)

