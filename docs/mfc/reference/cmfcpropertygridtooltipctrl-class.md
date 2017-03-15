---
title: Clase CMFCPropertyGridToolTipCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyGridToolTipCtrl::PreTranslateMessage
- ~CMFCPropertyGridToolTipCtrl
- PreTranslateMessage
- CMFCPropertyGridToolTipCtrl.~CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl.PreTranslateMessage
- CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl class
- CMFCPropertyGridToolTipCtrl class, destructor
- PreTranslateMessage method
- ~CMFCPropertyGridToolTipCtrl destructor
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
caps.latest.revision: 24
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
ms.openlocfilehash: e5290706799dcd253205ac74dad72cd7783d19dd
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcpropertygridtooltipctrl-class"></a>Clase CMFCPropertyGridToolTipCtrl
Implementa una información sobre herramientas que controlan la [CMFCPropertyGridCtrl clase](../../mfc/reference/cmfcpropertygridctrl-class.md) usa para mostrar información sobre herramientas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCPropertyGridToolTipCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|Construye un objeto `CMFCPropertyGridToolTipCtrl`.|  
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|[CMFCPropertyGridToolTipCtrl::Create](#create)|Crea una ventana para el control de información sobre herramientas.|  
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Desactiva y oculta el control de información sobre herramientas.|  
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Devuelve las coordenadas de la última posición del control de información sobre herramientas.|  
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|Oculta el control de información sobre herramientas.|  
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Utilizado por la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir los mensajes de ventana antes de que se envíen a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows. (Invalida [CWnd:: PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Establece el espaciado entre el texto y el borde de la ventana de información sobre herramientas.|  
|[CMFCPropertyGridToolTipCtrl::Track](#track)|Muestra el control de información sobre herramientas.|  
  
## <a name="remarks"></a>Comentarios  
 Se muestra información sobre herramientas cuando se sitúa el puntero sobre un nombre de propiedad. El [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) clase muestra una información sobre herramientas para que sea fácilmente legible por el usuario. Normalmente, la posición de una información sobre herramientas se determina por la posición del puntero. Mediante esta clase, la información sobre herramientas aparece sobre el nombre de propiedad y es similar a la extensión de propiedad natural, para que sea totalmente visible el nombre de propiedad.  
  
 MFC automáticamente crea este control y se utiliza en el [CMFCPropertyGridCtrl clase](../../mfc/reference/cmfcpropertygridctrl-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCPropertyGridToolTipCtrl` clase y cómo mostrar el control de información sobre herramientas.  
  
 [!code-cpp[23 de NVC_MFC_RibbonApp #](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpropertygridtooltipctrl.h  
  
##  <a name="a-namecmfcpropertygridtooltipctrla--cmfcpropertygridtooltipctrlcmfcpropertygridtooltipctrl"></a><a name="cmfcpropertygridtooltipctrl"></a>CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl  
 Construye un objeto `CMFCPropertyGridToolTipCtrl`.  
  
```  
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```  
  
##  <a name="a-namecreatea--cmfcpropertygridtooltipctrlcreate"></a><a name="create"></a>CMFCPropertyGridToolTipCtrl::Create  
 Crea una ventana para el control de información sobre herramientas.  
  
```  
BOOL Create(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndParent`  
 Puntero a la ventana primaria.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la ventana se creó correctamente; de lo contrario, FALSE.  
  
##  <a name="a-namedeactivatea--cmfcpropertygridtooltipctrldeactivate"></a><a name="deactivate"></a>CMFCPropertyGridToolTipCtrl::Deactivate  
 Desactiva y oculta el control de información sobre herramientas.  
  
```  
void Deactivate();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método establece la última posición y texto a los valores vacíos, para que las futuras llamadas a [CMFCPropertyGridToolTipCtrl::Track](#track) mostrar la información sobre herramientas.  
  
##  <a name="a-namegetlastrecta--cmfcpropertygridtooltipctrlgetlastrect"></a><a name="getlastrect"></a>CMFCPropertyGridToolTipCtrl::GetLastRect  
 Devuelve las coordenadas de la última posición del control de información sobre herramientas.  
  
```  
void GetLastRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rect`  
 Contiene la última posición del control de información sobre herramientas.  
  
##  <a name="a-namehidea--cmfcpropertygridtooltipctrlhide"></a><a name="hide"></a>CMFCPropertyGridToolTipCtrl::Hide  
 Oculta el control de información sobre herramientas.  
  
```  
void Hide();
```  
  
##  <a name="a-namesettextmargina--cmfcpropertygridtooltipctrlsettextmargin"></a><a name="settextmargin"></a>CMFCPropertyGridToolTipCtrl::SetTextMargin  
 Establece el espaciado entre el texto y el borde de la ventana de información sobre herramientas.  
  
```  
void SetTextMargin(int nTextMargin);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nTextMargin`  
 Especifica el espaciado entre el texto de información sobre herramientas del control y el borde de la ventana de información sobre herramientas. El valor predeterminado es 10 píxeles.  
  
##  <a name="a-nametracka--cmfcpropertygridtooltipctrltrack"></a><a name="track"></a>CMFCPropertyGridToolTipCtrl::Track  
 Muestra el control de información sobre herramientas.  
  
```  
void Track(
    CRect rect,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rect`  
 Especifica la posición y el tamaño del control de información sobre herramientas.  
  
 [in] `strText`  
 Especifica el texto que se mostrará en la información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Este método muestra el control de información sobre herramientas en la posición y el tamaño especificado por `rect`. Si la posición, el tamaño y el texto no han cambiado desde la última vez que se llama a este método, este método tiene ningún efecto.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)

