---
title: Clase CDockablePaneAdapter | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDockablePaneAdapter
dev_langs:
- C++
helpviewer_keywords:
- CDockablePaneAdapter class
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
caps.latest.revision: 22
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
ms.openlocfilehash: 05d34e3ec84db48e50328b99c38abf1ef73747b4
ms.lasthandoff: 02/24/2017

---
# <a name="cdockablepaneadapter-class"></a>Clase CDockablePaneAdapter
Proporciona compatibilidad para paneles derivados de `CWnd`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDockablePaneAdapter : public CDockablePane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|Devuelve la ventana ajustada.|  
|[CDockablePaneAdapter::LoadState](#loadstate)|(Invalida [CDockablePane::LoadState](http://msdn.microsoft.com/en-us/96110136-4f46-4764-8a76-3b4abaf77917).)|  
|[CDockablePaneAdapter::SaveState](#savestate)|(Invalida [CDockablePane::SaveState](http://msdn.microsoft.com/en-us/c5c24249-8d0d-46cb-96d9-9f5c6dc191db).)|  
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, el marco de trabajo crea los objetos de esta clase cuando se utiliza la [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) o [CMFCBaseTabCtrl::InsertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) métodos.  
  
 Si desea personalizar la `CDockablePaneAdapter` comportamiento, simplemente derivar una nueva clase y establezca la información de clase en tiempo de ejecución en una ventana con fichas mediante [CMFCBaseTabCtrl::SetDockingBarWrapperRTC](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxDockablePaneAdapter.h  
  
##  <a name="a-namegetwrappedwnda--cdockablepaneadaptergetwrappedwnd"></a><a name="getwrappedwnd"></a>CDockablePaneAdapter::GetWrappedWnd  
 Devuelve la ventana subyacente para el adaptador de un panel acoplable.  
  
```  
virtual CWnd* GetWrappedWnd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la ventana ajustada.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para obtener acceso a la ventana ajustada.  
  
##  <a name="a-nameloadstatea--cdockablepaneadapterloadstate"></a><a name="loadstate"></a>CDockablePaneAdapter::LoadState  
 Carga el estado del panel desde el registro.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 El nombre del perfil.  
  
 [in] `nIndex`  
 El índice del perfil.  
  
 [in] `uiID`  
 El identificador del panel.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesavestatea--cdockablepaneadaptersavestate"></a><a name="savestate"></a>CDockablePaneAdapter::SaveState  
 Guarda el estado del panel en el registro.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 El nombre del perfil.  
  
 [in] `nIndex`  
 El índice de perfil (el valor predeterminado es el identificador del control de la ventana).  
  
 [in] `uiID`  
 El identificador del panel.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetwrappedwnda--cdockablepaneadaptersetwrappedwnd"></a><a name="setwrappedwnd"></a>CDockablePaneAdapter::SetWrappedWnd  
 Establece la ventana subyacente para el adaptador de un panel acoplable.  
  
```  
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Puntero a la ventana para el adaptador de panel ajustar.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CDockablePane](../../mfc/reference/cdockablepane-class.md)

