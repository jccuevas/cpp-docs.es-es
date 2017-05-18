---
title: Clase CMFCVisualManagerWindows7 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::OnFillMenuImageRect
dev_langs:
- C++
helpviewer_keywords:
- CMFCVisualManagerWindows7 class
ms.assetid: e8d87df1-0c09-4b58-8ade-4e911f796e42
caps.latest.revision: 21
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 236223fe371973fb4e009d2fcb242f2ed6e90963
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcvisualmanagerwindows7-class"></a>Clase CMFCVisualManagerWindows7
El `CMFCVisualManagerWindows7` proporciona a una aplicación el aspecto de un [!INCLUDE[win7](../../build/includes/win7_md.md)] aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCVisualManagerWindows7 : public CMFCVisualManagerWindows;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCVisualManagerWindows7::CMFCVisualManagerWindows7](#cmfcvisualmanagerwindows7)|Constructor predeterminado.|  
|[CMFCVisualManagerWindows7:: ~ CMFCVisualManagerWindows7](#cmfcvisualmanagerwindows7__~cmfcvisualmanagerwindows7)|Destructor predeterminado.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCVisualManagerWindows7::CleanStyle`|Borra el estilo visual actual y restablece el estilo visual predeterminado.|  
|`CMFCVisualManagerWindows7::CleanUp`|Borra todos los objetos en la interfaz de usuario y restablece los menús.|  
|`CMFCVisualManagerWindows7::DrawNcBtn`|Dibuja un botón en el área no cliente, en el marco. Los usos de framework este método para dibujar minimizar, maximizar, cierre y restaurar los botones en la esquina superior derecha del marco de ventana. No se llama a este método cuando el programa utiliza un tema no son Aero.|  
|`CMFCVisualManagerWindows7::DrawNcText`|Dibuja el texto en el área no cliente en el marco. El marco de trabajo utiliza este método para dibujar el título de la aplicación en la barra de título en la parte superior de la ventana de marco.|  
|`CMFCVisualManagerWindows7::DrawSeparator`|Dibuja un separador en el [CMFCToolBar clase](../../mfc/reference/cmfctoolbar-class.md).|  
|`CMFCVisualManagerWindows7::GetRibbonBar`|Recupera el [CMFCRibbonBar clase](../../mfc/reference/cmfcribbonbar-class.md) asociado a la interfaz de usuario.|  
|[CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor](#getribboneditbackgroundcolor)|Obtiene un color de fondo del cuadro de edición de cinta de opciones.|  
|`CMFCVisualManagerWindows7::GetRibbonPopupBorderSize`|Reemplaza [CMFCVisualManager::GetRibbonPopupBorderSize](../../mfc/reference/cmfcvisualmanager-class.md#getribbonpopupbordersize)|  
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarChevronOffset`|Reemplaza [CMFCVisualManager::GetRibbonQuickAccessToolBarChevronOffset](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarchevronoffset)|  
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarRightMargin`|Reemplaza [CMFCVisualManager::GetRibbonQuickAccessToolBarRightMargin](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarrightmargin)|  
|`CMFCVisualManagerWindows7::IsHighlightWholeMenuItem`|Reemplaza [CMFCVisualManagerWindows::IsHighlightWholeMenuItem](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ishighlightwholemenuitem)|  
|`CMFCVisualManagerWindows7::IsOwnerDrawMenuCheck`|Reemplaza [CMFCVisualManager::IsOwnerDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#isownerdrawmenucheck)|  
|`CMFCVisualManagerWindows7::IsRibbonPresent`|Determina si un `CMFCRibbonBar` está presente y es visible.|  
|`CMFCVisualManagerWindows7::OnDrawButtonBorder`|Reemplaza [CMFCVisualManagerWindows::OnDrawButtonBorder](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawbuttonborder)|  
|`CMFCVisualManagerWindows7::OnDrawCheckBoxEx`|Reemplaza [CMFCVisualManagerWindows::OnDrawCheckBoxEx](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcheckboxex)|  
|`CMFCVisualManagerWindows7::OnDrawComboDropButton`|Reemplaza [CMFCVisualManagerWindows::OnDrawComboDropButton](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcombodropbutton)|  
|`CMFCVisualManagerWindows7::OnDrawDefaultRibbonImage`|Reemplaza [CMFCVisualManager::OnDrawDefaultRibbonImage](../../mfc/reference/cmfcvisualmanager-class.md#ondrawdefaultribbonimage)|  
|`CMFCVisualManagerWindows7::OnDrawMenuBorder`|Reemplaza [CMFCVisualManagerWindows::OnDrawMenuBorder](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawmenuborder)|  
|`CMFCVisualManagerWindows7::OnDrawMenuCheck`|Reemplaza [CMFCVisualManager::OnDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenucheck)|  
|`CMFCVisualManagerWindows7::OnDrawMenuLabel`|Reemplaza [CMFCVisualManager::OnDrawMenuLabel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenulabel)|  
|`CMFCVisualManagerWindows7::OnDrawRadioButton`|Invalidaciones`CMFCVisualManager::OnDrawRadioButton`|  
|`CMFCVisualManagerWindows7::OnDrawRibbonApplicationButton`|Reemplaza [CMFCVisualManager::OnDrawRibbonApplicationButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonapplicationbutton)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonButtonBorder`|Reemplaza [CMFCVisualManager::OnDrawRibbonButtonBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonbuttonborder)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCaption`|Reemplaza [CMFCVisualManager::OnDrawRibbonCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaption)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCaptionButton`|Reemplaza [CMFCVisualManager::OnDrawRibbonCaptionButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaptionbutton)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCategory`|Reemplaza [CMFCVisualManager::OnDrawRibbonCategory](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategory)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCategoryTab`|Reemplaza [CMFCVisualManager::OnDrawRibbonCategoryTab](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategorytab)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonDefaultPaneButton`|Reemplaza [CMFCVisualManager::OnDrawRibbonDefaultPaneButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbondefaultpanebutton)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonGalleryButton`|Reemplaza [CMFCVisualManager::OnDrawRibbonGalleryButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbongallerybutton)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonLaunchButton`|Invalidaciones`CMFCVisualManager::OnDrawRibbonLaunchButton`|  
|`CMFCVisualManagerWindows7::OnDrawRibbonMenuCheckFrame`|Reemplaza [CMFCVisualManager::OnDrawRibbonMenuCheckFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonmenucheckframe)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonPanel`|Reemplaza [CMFCVisualManager::OnDrawRibbonPanel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanel)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonPanelCaption`|Reemplaza [CMFCVisualManager::OnDrawRibbonPanelCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanelcaption)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonProgressBar`|Reemplaza [CMFCVisualManager::OnDrawRibbonProgressBar](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonprogressbar)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonRecentFilesFrame`|Reemplaza [CMFCVisualManager::OnDrawRibbonRecentFilesFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonrecentfilesframe)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderChannel`|Reemplaza [CMFCVisualManager::OnDrawRibbonSliderChannel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderchannel)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderThumb`|Reemplaza [CMFCVisualManager::OnDrawRibbonSliderThumb](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderthumb)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderZoomButton`|Reemplaza [CMFCVisualManager::OnDrawRibbonSliderZoomButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderzoombutton)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonStatusBarPane`|Reemplaza [CMFCVisualManager::OnDrawRibbonStatusBarPane](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonstatusbarpane)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonTabsFrame`|Reemplaza [CMFCVisualManager::OnDrawRibbonTabsFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbontabsframe)|  
|`CMFCVisualManagerWindows7::OnDrawStatusBarSizeBox`|Reemplaza [CMFCVisualManagerWindows::OnDrawStatusBarSizeBox](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawstatusbarsizebox)|  
|`CMFCVisualManagerWindows7::OnFillBarBackground`|Reemplaza [CMFCVisualManagerWindows::OnFillBarBackground](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbarbackground)|  
|`CMFCVisualManagerWindows7::OnFillButtonInterior`|Reemplaza [CMFCVisualManagerWindows::OnFillButtonInterior](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbuttoninterior)|  
|[CMFCVisualManagerWindows7::OnFillMenuImageRect](#onfillmenuimagerect)|El marco de trabajo llama a este método cuando se llena el área de imágenes de elementos de menú.|  
|`CMFCVisualManagerWindows7::OnFillRibbonButton`|Reemplaza [CMFCVisualManager::OnFillRibbonButton](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonbutton)|  
|`CMFCVisualManagerWindows7::OnFillRibbonQuickAccessToolBarPopup`|Reemplaza [CMFCVisualManager::OnFillRibbonQuickAccessToolBarPopup](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonquickaccesstoolbarpopup)|  
|`CMFCVisualManagerWindows7::OnHighlightMenuItem`|Reemplaza [CMFCVisualManagerWindows::OnHighlightMenuItem](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onhighlightmenuitem)|  
|`CMFCVisualManagerWindows7::OnNcActivate`|Reemplaza [CMFCVisualManager::OnNcActivate](../../mfc/reference/cmfcvisualmanager-class.md#onncactivate)|  
|`CMFCVisualManagerWindows7::OnNcPaint`|Reemplaza [CMFCVisualManager::OnNcPaint](../../mfc/reference/cmfcvisualmanager-class.md#onncpaint)|  
|`CMFCVisualManagerWindows7::OnUpdateSystemColors`|Reemplaza [CMFCVisualManagerWindows::OnUpdateSystemColors](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onupdatesystemcolors)|  
|`CMFCVisualManagerWindows7::SetResourceHandle`|Establece el identificador de recursos que describe los atributos del administrador visual.|  
|`CMFCVisualManagerWindows7::SetStyle`|Establece la combinación de colores de la `CMFCVisualManagerWindows7` interfaz gráfica de usuario.|  
  
## <a name="remarks"></a>Comentarios  
 Utilice la `CMFCVisualManagerWindows7` clase para cambiar la apariencia de la aplicación para imitar el valor predeterminado es [!INCLUDE[win7](../../build/includes/win7_md.md)] aplicación. Esta clase no puede ser válida si la aplicación se ejecuta en una versión de Windows anterior a [!INCLUDE[win7](../../build/includes/win7_md.md)]. En ese caso, la aplicación utiliza el administrador visual predeterminado definido en [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md).  
  
 El CMFCVisualManagerWindows7 hereda varios métodos de la [CMFCVisualManagerWindows clase](../../mfc/reference/cmfcvisualmanagerwindows-class.md) y `CMFCVisualManager` (clase). Los métodos enumerados en la sección anterior son nuevos para la `CMFCVisualManagerWindows7` clase.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)  
  
 `CMFCVisualManagerWindows7`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxvisualmanagerwindows7.h  
  
##  <a name="_dtorcmfcvisualmanagerwindows7"></a>CMFCVisualManagerWindows7:: ~ CMFCVisualManagerWindows7  
 Destructor predeterminado.  
  
```  
virtual ~CMFCVisualManagerWindows7();
```  
  
##  <a name="cmfcvisualmanagerwindows7"></a>CMFCVisualManagerWindows7::CMFCVisualManagerWindows7  
 Constructor predeterminado.  
  
```  
CMFCVisualManagerWindows7();
```  
  
##  <a name="getribboneditbackgroundcolor"></a>CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor  
 Obtiene el color de fondo de un cuadro de edición de la cinta de opciones.  
  
```  
virtual COLORREF GetRibbonEditBackgroundColor (
    CMFCRibbonRichEditCtrl* pEdit,  
    BOOL bIsHighlighted,  
    BOOL bIsPaneHighlighted,  
    BOOL bIsDisabled);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pEdit`  
 Un puntero al control de edición. Este valor no puede ser `NULL`.  
  
 [out] `bIsHighlighted`  
 Devuelve si se resalta el cuadro de la cinta de opciones.  
  
 [out] `bIsPaneHighlighted`  
 Devuelve `TRUE` si la cinta de opciones del panel que contiene `pEdit` se resalta.  
  
 [out] `bIsDisabled`  
 Devuelve si `pEdit` está deshabilitado.  
  
### <a name="return-value"></a>Valor devuelto  
 El color de fondo del cuadro de edición `pEdit`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onfillmenuimagerect"></a>CMFCVisualManagerWindows7::OnFillMenuImageRect  
 El marco de trabajo llama a este método cuando se llena el área alrededor de la imagen de un elemento de menú.  
  
```  
virtual void OnFillMenuImageRect(
    CDC* pDC,  
    CMFCToolBarButton* pButton,  
    CRect rect,  
    CMFCVisualManager::AFX_BUTTON_STATE state);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Un puntero al contexto de dispositivo de un botón de menú.  
  
 [in] `pButton`  
 Un puntero a un `CMFCToolBarButton`. El marco de trabajo rellena el fondo para este botón.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del área de imagen del botón de menú.  
  
 [in] `state`  
 El estado del botón.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)   
 [Clase CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)

