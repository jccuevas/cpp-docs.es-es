---
title: Clase CDockablePaneAdapter | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::GetWrappedWnd
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::LoadState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SaveState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SetWrappedWnd
dev_langs:
- C++
helpviewer_keywords:
- CDockablePaneAdapter [MFC], GetWrappedWnd
- CDockablePaneAdapter [MFC], LoadState
- CDockablePaneAdapter [MFC], SaveState
- CDockablePaneAdapter [MFC], SetWrappedWnd
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea3a2cb6c3d9a454c33654254fb751bfc8679696
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cdockablepaneadapter-class"></a>Clase CDockablePaneAdapter
Proporciona compatibilidad para paneles derivados de `CWnd`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDockablePaneAdapter : public CDockablePane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|Devuelve la ventana ajustada.|  
|[CDockablePaneAdapter::LoadState](#loadstate)|(Invalida [CDockablePane:: Loadstate](http://msdn.microsoft.com/en-us/96110136-4f46-4764-8a76-3b4abaf77917).)|  
|[CDockablePaneAdapter::SaveState](#savestate)|(Invalida [CDockablePane:: SaveState](http://msdn.microsoft.com/en-us/c5c24249-8d0d-46cb-96d9-9f5c6dc191db).)|  
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||  
  
## <a name="remarks"></a>Comentarios  
 Por lo general, el marco de trabajo crea los objetos de esta clase cuando se utiliza el [cmfcbasetabctrl:: addTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) o [cmfcbasetabctrl:: insertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) métodos.  
  
 Si desea personalizar la `CDockablePaneAdapter` comportamiento, simplemente derivar una nueva clase y establezca la información de clase en tiempo de ejecución en una ventana con fichas mediante [cmfcbasetabctrl:: Setdockingbarwrapperrtc](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxDockablePaneAdapter.h  
  
##  <a name="getwrappedwnd"></a>  CDockablePaneAdapter::GetWrappedWnd  
 Devuelve la ventana subyacente para el adaptador de panel acoplable.  
  
```  
virtual CWnd* GetWrappedWnd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la ventana ajustada.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para tener acceso a la ventana ajustada.  
  
##  <a name="loadstate"></a>  CDockablePaneAdapter::LoadState  
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
 El índice de perfil.  
  
 [in] `uiID`  
 El identificador del panel.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="savestate"></a>  CDockablePaneAdapter::SaveState  
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
  
##  <a name="setwrappedwnd"></a>  CDockablePaneAdapter::SetWrappedWnd  
 Establece la ventana subyacente para el adaptador de panel acoplable.  
  
```  
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Un puntero a la ventana para el adaptador de panel que va a contener.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CDockablePane (clase)](../../mfc/reference/cdockablepane-class.md)
