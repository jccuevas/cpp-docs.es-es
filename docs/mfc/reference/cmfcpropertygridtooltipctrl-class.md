---
title: CMFCPropertyGridToolTipCtrl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 574da3d370a403aa74ba8c438b7c175bee19f198
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211970"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl (clase)
Implementa una información sobre herramientas que controlan el [CMFCPropertyGridCtrl (clase)](../../mfc/reference/cmfcpropertygridctrl-class.md) usa para mostrar información sobre herramientas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCPropertyGridToolTipCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|Construye un objeto `CMFCPropertyGridToolTipCtrl`.|  
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCPropertyGridToolTipCtrl::Create](#create)|Crea una ventana para el control tooltip.|  
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Desactiva y oculta el control tooltip.|  
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Devuelve las coordenadas de la última posición del control tooltip.|  
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|Oculta el control tooltip.|  
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Utilizado por la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir los mensajes de ventana antes de enviarlos a la [TranslateMessage](https://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](https://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows. (Invalida [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)).|  
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Establece el espaciado entre el texto de información sobre herramientas y el borde de la ventana de información sobre herramientas.|  
|[CMFCPropertyGridToolTipCtrl::Track](#track)|Muestra el control de información sobre herramientas.|  
  
## <a name="remarks"></a>Comentarios  
 Información sobre herramientas se muestra cuando el puntero se sitúa sobre un nombre de propiedad. El [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) clase muestra una información sobre herramientas para que resulte fácil de leer el usuario. Normalmente, la posición de una información sobre herramientas viene determinada por la posición del puntero. Mediante el uso de esta clase, la información sobre herramientas aparece sobre el nombre de propiedad y es similar a la extensión natural de propiedad, por lo que el nombre de propiedad está totalmente visible.  
  
 MFC automáticamente crea este control y se utiliza en el [CMFCPropertyGridCtrl (clase)](../../mfc/reference/cmfcpropertygridctrl-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCPropertyGridToolTipCtrl` clase y cómo mostrar el control tooltip.  
  
 [!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpropertygridtooltipctrl.h  
  
##  <a name="cmfcpropertygridtooltipctrl"></a>  CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl  
 Construye un objeto `CMFCPropertyGridToolTipCtrl`.  
  
```  
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```  
  
##  <a name="create"></a>  CMFCPropertyGridToolTipCtrl::Create  
 Crea una ventana para el control tooltip.  
  
```  
BOOL Create(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pWndParent*  
 Un puntero a la ventana primaria.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la ventana se ha creado correctamente; en caso contrario, FALSE.  
  
##  <a name="deactivate"></a>  CMFCPropertyGridToolTipCtrl::Deactivate  
 Desactiva y oculta el control tooltip.  
  
```  
void Deactivate();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método establece la última posición y texto a los valores vacíos, para que las llamadas futuras a [CMFCPropertyGridToolTipCtrl::Track](#track) mostrar la información sobre herramientas.  
  
##  <a name="getlastrect"></a>  CMFCPropertyGridToolTipCtrl::GetLastRect  
 Devuelve las coordenadas de la última posición del control tooltip.  
  
```  
void GetLastRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] *rect*  
 Contiene la última posición del control tooltip.  
  
##  <a name="hide"></a>  CMFCPropertyGridToolTipCtrl::Hide  
 Oculta el control tooltip.  
  
```  
void Hide();
```  
  
##  <a name="settextmargin"></a>  CMFCPropertyGridToolTipCtrl::SetTextMargin  
 Establece el espaciado entre el texto de información sobre herramientas y el borde de la ventana de información sobre herramientas.  
  
```  
void SetTextMargin(int nTextMargin);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nTextMargin*  
 Especifica el espaciado entre el texto del control de información sobre herramientas y el borde de la ventana de información sobre herramientas. El valor predeterminado es 10 píxeles.  
  
##  <a name="track"></a>  CMFCPropertyGridToolTipCtrl::Track  
 Muestra el control de información sobre herramientas.  
  
```  
void Track(
    CRect rect,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *rect*  
 Especifica la posición y el tamaño del control tooltip.  
  
 [in] *strText*  
 Especifica el texto que se mostrará en la información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Este método muestra el control de información sobre herramientas en la posición y el tamaño especificado por *rect*. Si la posición, el tamaño y el texto no han cambiado desde la última vez que se llamó a este método, este método tiene ningún efecto.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)
