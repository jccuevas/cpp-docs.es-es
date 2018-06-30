---
title: Clase CTabView | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTabView
- AFXTABVIEW/CTabView
- AFXTABVIEW/CTabView::AddView
- AFXTABVIEW/CTabView::FindTab
- AFXTABVIEW/CTabView::GetActiveView
- AFXTABVIEW/CTabView::GetTabControl
- AFXTABVIEW/CTabView::RemoveView
- AFXTABVIEW/CTabView::SetActiveView
- AFXTABVIEW/CTabView::IsScrollBar
- AFXTABVIEW/CTabView::OnActivateView
dev_langs:
- C++
helpviewer_keywords:
- CTabView [MFC], AddView
- CTabView [MFC], FindTab
- CTabView [MFC], GetActiveView
- CTabView [MFC], GetTabControl
- CTabView [MFC], RemoveView
- CTabView [MFC], SetActiveView
- CTabView [MFC], IsScrollBar
- CTabView [MFC], OnActivateView
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d64d503c4bad0d452be174064e2932ed100d7de
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121762"
---
# <a name="ctabview-class"></a>Clase CTabView
El `CTabView` clase simplifica el uso de la clase de control de pestaña ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) en las aplicaciones que utilizan la arquitectura documento/vista de MFC.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CTabbedView : public CView  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTabView::AddView](#addview)|Agrega una nueva vista para el control de ficha.|  
|[CTabView::FindTab](#findtab)|Devuelve el índice de la vista especificada en el control de ficha.|  
|[CTabView::GetActiveView](#getactiveview)|Devuelve un puntero a la vista activa|  
|[CTabView::GetTabControl](#gettabcontrol)|Devuelve una referencia al control de ficha asociado a la vista.|  
|[CTabView::RemoveView](#removeview)|Quita la vista de control de pestaña.|  
|[CTabView::SetActiveView](#setactiveview)|Activa una vista.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTabView::IsScrollBar](#isscrollbar)|Lo llama el marco al crear una vista de ficha para determinar si la vista de ficha tiene una barra de desplazamiento horizontal compartida.|  
|[CTabView::OnActivateView](#onactivateview)|Lo llama el marco cuando se realiza la vista de la pestaña activa o inactiva.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase resulta muy sencillo colocar una vista con pestañas en una aplicación de documento/vista. `CTabView` es un `CView`-clase derivada que contiene un incrustado `CMFCTabCtrl` objeto. `CTabView` administra todos los mensajes necesarios para admitir la `CMFCTabCtrl` objeto. Simplemente derive una clase de `CTabView` y conectarlo a la aplicación, a continuación, agregue `CView`-derivar clases mediante el `AddView` método. El control de pestaña mostrará esas vistas como fichas.  
  
 Por ejemplo, podría tener un documento que se puede representar de maneras diferentes: como una hoja de cálculo, un gráfico, un formulario editable y así sucesivamente. Puede crear vistas individuales dibujar los datos según sea necesario, insertarlos en la `CTabView`-objeto derivado de y concentrarlos por pestañas sin ninguna codificación adicional.  
  
 [Ejemplo de TabbedView: Aplicación de vista de MFC con fichas](../../visual-cpp-samples.md) muestra el uso de `CTabView`.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo se muestra cómo `CTabView` se utiliza en el ejemplo de TabbedView.  
  
 [!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxTabView.h  
  
##  <a name="addview"></a>  CTabView::AddView  
 Agrega una vista para el control de ficha.  
  
```  
int AddView(
    CRuntimeClass* pViewClass,  
    const CString& strViewLabel,  
    int iIndex=-1,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pViewClass*  
 Un puntero a una clase en tiempo de ejecución de la vista insertada.  
  
 [in] *strViewLabel*  
 Especifica el texto de la ficha.  
  
 [in] *iÍndice*  
 Especifica la posición de base cero donde se inserta la vista. Si la posición es -1 se inserta la nueva pestaña al final.  
  
 [in] *pContext*  
 Un puntero a la `CCreateContext` de la vista.  
  
### <a name="return-value"></a>Valor devuelto  
 Un índice de la vista, si este método se realiza correctamente. En caso contrario, devuelve -1.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para agregar una vista para el control de ficha que se incrusta en un marco.  
  
##  <a name="findtab"></a>  CTabView::FindTab  
 Devuelve el índice de la vista especificada en el control de ficha.  
  
```  
int FindTab(HWND hWndView) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *hWndView*  
 El identificador de la vista.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de la vista si se encuentra; en caso contrario, devuelve -1.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar el índice de una vista que tiene el identificador especificado.  
  
##  <a name="getactiveview"></a>  CTabView::GetActiveView  
 Devuelve un puntero a la vista activa.  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero válido a la vista activa, o NULL si no hay ninguna vista activa.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gettabcontrol"></a>  CTabView::GetTabControl  
 Devuelve una referencia al control de ficha asociado a la vista.  
  
```  
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al control de ficha asociado a la vista.  
  
##  <a name="isscrollbar"></a>  CTabView::IsScrollBar  
 Lo llama el marco al crear una vista de ficha para determinar si la vista de ficha tiene una barra de desplazamiento horizontal compartida.  
  
```  
virtual BOOL IsScrollBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es TRUE si la vista de ficha debe crearse junto con una barra de desplazamiento compartido. En caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando un *CTabView* se crea el objeto.  
  
 Invalidar el *IsScrollBar* método en un *CTabView*-clase derivada y devuelve TRUE si desea crear una vista que tiene una barra de desplazamiento horizontal compartida.  
  
##  <a name="onactivateview"></a>  CTabView::OnActivateView  
 Lo llama el marco cuando se realiza la vista de la pestaña activa o inactiva.  
  
```  
virtual void OnActivateView(CView* view);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *vista*  
 Un puntero a la vista.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no hace nada. Invalide este método en un `CTabView`-clase derivada para procesar esta notificación.  
  
##  <a name="removeview"></a>  CTabView::RemoveView  
 Quita la vista de control de pestaña.  
  
```  
BOOL RemoveView(int iTabNum);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *iTabNum*  
 El índice de la vista para quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de la vista quita si este método se realiza correctamente. En caso contrario,-1.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setactiveview"></a>  CTabView::SetActiveView  
 Activa una vista.  
  
```  
BOOL SetActiveView(int iTabNum);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *iTabNum*  
 Índice de base cero de la vista de ficha.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la vista especificada se realizó activa, FALSE si el índice de la vista no es válido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)
