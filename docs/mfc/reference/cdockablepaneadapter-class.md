---
title: CDockablePaneAdapter (clase) | Microsoft Docs
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
ms.openlocfilehash: 71d89020869db10b45688dbaae71f38711d2667c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676368"
---
# <a name="cdockablepaneadapter-class"></a>CDockablePaneAdapter (clase)
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
|[CDockablePaneAdapter::LoadState](#loadstate)|(Invalida [CDockablePane:: Loadstate](cdockablepane-class.md#loadstate).)|  
|[CDockablePaneAdapter::SaveState](#savestate)|(Invalida [CDockablePane:: SaveState](cdockablepane-class.md).)|  
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, el marco de trabajo crea una instancia de objetos de esta clase cuando se usa el [cmfcbasetabctrl:: addTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) o [cmfcbasetabctrl:: insertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) métodos.  
  
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
 [in] *lpszProfileName*  
 El nombre del perfil.  
  
 [in] *nIndex*  
 El índice del perfil.  
  
 [in] *uiID*  
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
 [in] *lpszProfileName*  
 El nombre del perfil.  
  
 [in] *nIndex*  
 El índice de perfil (el valor predeterminado es el identificador de control de la ventana).  
  
 [in] *uiID*  
 El identificador del panel.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setwrappedwnd"></a>  CDockablePaneAdapter::SetWrappedWnd  
 Establece la ventana subyacente para el adaptador de panel acoplable.  
  
```  
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *conquistado*  
 Un puntero a la ventana para ajustar el adaptador de panel.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CDockablePane (clase)](../../mfc/reference/cdockablepane-class.md)
