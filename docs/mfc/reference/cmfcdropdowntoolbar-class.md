---
title: Clase CMFCDropDownToolBar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownToolBar class
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
caps.latest.revision: 37
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
ms.openlocfilehash: ba643d67b12ba22bcf9fb54d32f3c329fa2c65a0
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcdropdowntoolbar-class"></a>Clase de CMFCDropDownToolBar
Una barra de herramientas que aparece cuando el usuario presiona y mantiene presionado un botón de la barra de herramientas de nivel superior.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCDropDownToolBar : public CMFCToolBar  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Invalida `CPane::AllowShowOnPaneMenu`).|  
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(Invalida [CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|  
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(Invalida [CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|  
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||  
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||  
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(Invalida `CMFCToolBar::OnSendCommand`).|  
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(Invalida [CMFCToolBar::OnUpdateCmdUI](http://msdn.microsoft.com/en-us/571a38ab-2a56-4968-9796-273516126f80).)|  
  
### <a name="remarks"></a>Comentarios  
 Un `CMFCDropDownToolBar` objeto combina la apariencia visual de una barra de herramientas con el comportamiento de un menú emergente. Cuando un usuario presiona y mantiene presionado un botón de barra de herramientas desplegable (consulte [CMFCDropDownToolbarButton clase](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)), aparece una barra de herramientas de la lista desplegable y el usuario puede seleccionar un botón de la barra de herramientas desplegable desplazándose a él y soltar el botón del mouse. Después de que el usuario selecciona un botón en la barra de herramientas de la lista desplegable, ese botón se muestra como el botón actual en la barra de herramientas de nivel superior.  
  
 No se puede personalizar o acoplar una barra de herramientas de la lista desplegable, y no tiene un estado.  
  
 La siguiente ilustración muestra un `CMFCDropDownToolBar` objeto:  
  
 ![Ejemplo de CMFCDropDownToolbar](../../mfc/reference/media/cmfcdropdown.png "cmfcdropdown")  
  
 Crear un `CMFCDropDownToolBar` objeto del mismo modo que se crea una barra de herramientas normal (vea [CMFCToolBar clase](../../mfc/reference/cmfctoolbar-class.md)).  
  
 Para insertar la barra de herramientas desplegable en una barra de herramientas primario:  
  
 1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas.  
  
 2. Crear un `CMFCDropDownToolBarButton` objeto que contiene la barra de herramientas de la lista desplegable (para obtener más información, consulte [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).  
  
 3. Reemplace el botón ficticio con el `CMFCDropDownToolBarButton` objeto utilizando [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
 Para obtener más información acerca de los botones de barra de herramientas, consulte [Tutorial: poner controles en barras de herramientas de](../../mfc/walkthrough-putting-controls-on-toolbars.md). Para obtener un ejemplo de una barra de herramientas de la lista desplegable, consulte el proyecto de ejemplo VisualStudioDemo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `Create` método en la `CMFCDropDownToolBar` clase. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#29;](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo Nº&30;](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdropdowntoolbar.h  
  
##  <a name="allowshowonpanemenu"></a>CMFCDropDownToolBar::AllowShowOnPaneMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="loadbitmap"></a>CMFCDropDownToolBar::LoadBitmap  
 Carga las imágenes de la barra de herramientas desde los recursos de la aplicación.  
  
```  
virtual BOOL LoadBitmap(
    UINT uiResID,  
    UINT uiColdResID=0,  
    UINT uiMenuResID=0,  
    BOOL bLocked=FALSE,  
    UINT uiDisabledResID=0,  
    UINT uiMenuDisabledResID=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiResID`  
 El identificador de recurso del mapa de bits que hace referencia a las imágenes de barra de herramientas activa.  
  
 [in] `uiColdResID`  
 El identificador de recurso del mapa de bits que hace referencia a las imágenes de barra de herramientas inactiva.  
  
 [in] `uiMenuResID`  
 El identificador de recurso del mapa de bits que hace referencia a las imágenes de menú regular.  
  
 [in] `bLocked`  
 `TRUE`Para bloquear la barra de herramientas; de lo contrario, `FALSE`.  
  
 [in] `uiDisabledResID`  
 El identificador de recurso del mapa de bits que hace referencia a las imágenes de barra de herramientas deshabilitada.  
  
 [in] `uiMenuDisabledResID`  
 El identificador de recurso del mapa de bits que hace referencia a las imágenes de menú deshabilitado.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) método llama a este método para cargar las imágenes que están asociadas a la barra de herramientas. Invalide este método para realizar la carga personalizada de recursos de imagen.  
  
 Llame al método `LoadBitmapEx` para cargar imágenes adicionales después de crear la barra de herramientas.  
  
##  <a name="loadtoolbar"></a>CMFCDropDownToolBar::LoadToolBar  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL LoadToolBar(
    UINT uiResID,  
    UINT uiColdResID = 0,  
    UINT uiMenuResID = 0,
    BOOL = FALSE,  
    UINT uiDisabledResID = 0,  
    UINT uiMenuDisabledResID = 0,  
    UINT uiHotResID = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiResID`  
 [in] `uiColdResID`  
 [in] `uiMenuResID`  
 [in] `BOOL`  
 [in] `uiDisabledResID`  
 [in] `uiMenuDisabledResID`  
 [in] `uiHotResID`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onlbuttonup"></a>CMFCDropDownToolBar::OnLButtonUp  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
afx_msg void OnLButtonUp(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nFlags`  
 [in] `point`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onmousemove"></a>CMFCDropDownToolBar::OnMouseMove  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
afx_msg void OnMouseMove(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nFlags`  
 [in] `point`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onsendcommand"></a>CMFCDropDownToolBar::OnSendCommand  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onupdatecmdui"></a>CMFCDropDownToolBar::OnUpdateCmdUI  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pTarget`  
 [in] `bDisableIfNoHndler`  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBar::Create](../../mfc/reference/cmfctoolbar-class.md#create)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Clase CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)   
 [Tutorial: Poner controles en barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)




