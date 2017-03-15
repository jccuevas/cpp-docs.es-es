---
title: Clase CTabView | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTabView
dev_langs:
- C++
helpviewer_keywords:
- CTabView class
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
caps.latest.revision: 32
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 20f5745c3784e771d6ec95f7d4dc363142c687f8
ms.lasthandoff: 02/24/2017

---
# <a name="ctabview-class"></a>Clase CTabView
El `CTabView` clase simplifica el uso de la clase de control de ficha ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) en aplicaciones que utilizan la arquitectura documento/vista de MFC.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CTabbedView : public CView  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CTabView::AddView](#addview)|Agrega una nueva vista para el control de ficha.|  
|[CTabView::FindTab](#findtab)|Devuelve el índice de la vista especificada en el control de ficha.|  
|[CTabView::GetActiveView](#getactiveview)|Devuelve un puntero a la vista activa|  
|[CTabView::GetTabControl](#gettabcontrol)|Devuelve una referencia al control asociado a la vista.|  
|[CTabView::RemoveView](#removeview)|Quita la vista del control de ficha.|  
|[CTabView::SetActiveView](#setactiveview)|Una vista activa.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CTabView::IsScrollBar](#isscrollbar)|Lo llama el marco de trabajo al crear una vista de ficha para determinar si la vista de ficha tiene una barra de desplazamiento horizontal compartida.|  
|[CTabView::OnActivateView](#onactivateview)|Llamado por el marco de trabajo cuando se realiza la vista de la ficha activo o inactivo.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase facilita la colocación de una vista con pestañas en una aplicación de documento/vista. `CTabView`es un `CView`-clase derivada que contiene incrustado `CMFCTabCtrl` objeto. `CTabView`administra todos los mensajes necesarios para admitir la `CMFCTabCtrl` objeto. Simplemente hay que derivar una clase de `CTabView` y conectarlo a la aplicación, agregue `CView`-clases derivadas usando la `AddView` método. El control de ficha mostrará esas vistas como fichas.  
  
 Por ejemplo, podría tener un documento que se puede representar de maneras diferentes: como una hoja de cálculo, un gráfico, un formulario editable y así sucesivamente. Puede crear vistas individuales dibujando los datos según sea necesario, insertarlos en la `CTabView`-objeto derivado y tenerlos fichas sin programación adicional.  
  
 [Ejemplo de TabbedView: Aplicación de vista de MFC con pestañas](../../visual-cpp-samples.md) muestra el uso de `CTabView`.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `CTabView` se utiliza en el ejemplo de TabbedView.  
  
 [!code-cpp[1 NVC_MFC_TabbedView](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxTabView.h  
  
##  <a name="a-nameaddviewa--ctabviewaddview"></a><a name="addview"></a>CTabView::AddView  
 Agrega una vista para el control de ficha.  
  
```  
int AddView(
    CRuntimeClass* pViewClass,  
    const CString& strViewLabel,  
    int iIndex=-1,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pViewClass`  
 Un puntero a una clase en tiempo de ejecución de la vista insertada.  
  
 [in] `strViewLabel`  
 Especifica el texto de la ficha.  
  
 [in] `iIndex`  
 Especifica la posición de base cero donde se inserta la vista. Si la posición es -1 en la nueva ficha se inserta al final.  
  
 [in] `pContext`  
 Un puntero a la `CCreateContext` de la vista.  
  
### <a name="return-value"></a>Valor devuelto  
 Un índice de la vista, si este método se realiza correctamente. En caso contrario, es -1.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para agregar una vista para el control de ficha que se incrusta en un marco.  
  
##  <a name="a-namefindtaba--ctabviewfindtab"></a><a name="findtab"></a>CTabView::FindTab  
 Devuelve el índice de la vista especificada en el control de ficha.  
  
```  
int FindTab(HWND hWndView) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hWndView`  
 El identificador de la vista.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de la vista si se encuentra; en caso contrario, es -1.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar el índice de una vista que tiene el identificador especificado.  
  
##  <a name="a-namegetactiveviewa--ctabviewgetactiveview"></a><a name="getactiveview"></a>CTabView::GetActiveView  
 Devuelve un puntero a la vista activa.  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero válido a la vista activa, o `NULL` si no hay ninguna vista activa.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettabcontrola--ctabviewgettabcontrol"></a><a name="gettabcontrol"></a>CTabView::GetTabControl  
 Devuelve una referencia al control asociado a la vista.  
  
```  
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al control asociado a la vista.  
  
##  <a name="a-nameisscrollbara--ctabviewisscrollbar"></a><a name="isscrollbar"></a>CTabView::IsScrollBar  
 Lo llama el marco de trabajo al crear una vista de ficha para determinar si la vista de ficha tiene una barra de desplazamiento horizontal compartida.  
  
```  
virtual BOOL IsScrollBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la vista de ficha debe crearse junto con una barra de desplazamiento compartido. En caso contrario, es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando un `CTabView` se crea el objeto.  
  
 Invalidar el `IsScrollBar` método en un `CTabView`-derivado de la clase y devolver `TRUE` si desea crear una vista que tiene una barra de desplazamiento horizontal compartida.  
  
##  <a name="a-nameonactivateviewa--ctabviewonactivateview"></a><a name="onactivateview"></a>CTabView::OnActivateView  
 Llamado por el marco de trabajo cuando se realiza la vista de la ficha activo o inactivo.  
  
```  
virtual void OnActivateView(CView* view);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `view`  
 Puntero a la vista.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no hace nada. Invalide este método en un `CTabView`-clase derivada para procesar esta notificación.  
  
##  <a name="a-nameremoveviewa--ctabviewremoveview"></a><a name="removeview"></a>CTabView::RemoveView  
 Quita la vista del control de ficha.  
  
```  
BOOL RemoveView(int iTabNum);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTabNum`  
 El índice de la vista para quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de la vista quita si este método se realiza correctamente. De lo contrario, devuelve-1.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetactiveviewa--ctabviewsetactiveview"></a><a name="setactiveview"></a>CTabView::SetActiveView  
 Una vista activa.  
  
```  
BOOL SetActiveView(int iTabNum);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTabNum`  
 Índice de base cero de la vista de ficha.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la vista especificada se realizó activa, `FALSE` si el índice de la vista no es válido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)

