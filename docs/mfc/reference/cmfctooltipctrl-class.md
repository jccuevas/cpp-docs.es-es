---
title: Clase CMFCToolTipCtrl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetIconSize
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetParams
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawBorder
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawLabel
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnFillBackground
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetFixedWidth
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetHotRibbonButton
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetLocation
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetParams
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolTipCtrl [MFC], GetIconSize
- CMFCToolTipCtrl [MFC], GetParams
- CMFCToolTipCtrl [MFC], OnDrawBorder
- CMFCToolTipCtrl [MFC], OnDrawDescription
- CMFCToolTipCtrl [MFC], OnDrawIcon
- CMFCToolTipCtrl [MFC], OnDrawLabel
- CMFCToolTipCtrl [MFC], OnDrawSeparator
- CMFCToolTipCtrl [MFC], OnFillBackground
- CMFCToolTipCtrl [MFC], SetDescription
- CMFCToolTipCtrl [MFC], SetFixedWidth
- CMFCToolTipCtrl [MFC], SetHotRibbonButton
- CMFCToolTipCtrl [MFC], SetLocation
- CMFCToolTipCtrl [MFC], SetParams
ms.assetid: 9fbfcfb1-a8ab-417f-ae29-9a9ca85ee58f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74efac50304554af3224b8b707b29a31248143f6
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37042074"
---
# <a name="cmfctooltipctrl-class"></a>Clase CMFCToolTipCtrl
Implementación extendida de información sobre herramientas basada en [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md). Una información sobre herramientas basada en la clase `CMFCToolTipCtrl` puede mostrar un icono, una etiqueta y una descripción. Puede personalizar su apariencia visual mediante un relleno de degradado, colores de texto y bordes personalizados, texto en negrita, esquinas redondeadas o un estilo de globo.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCToolTipCtrl : public CToolTipCtrl  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|Constructor predeterminado.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolTipCtrl::GetIconSize](#geticonsize)|Devuelve el tamaño de un icono en una información sobre herramientas.|  
|[CMFCToolTipCtrl::GetParams](#getparams)|Devuelve la configuración de visualización en una información sobre herramientas.|  
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|Dibuja el borde de una información sobre herramientas.|  
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||  
|[CMFCToolTipCtrl::OnDrawIcon](#ondrawicon)|Muestra un icono en una información sobre herramientas.|  
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|Dibuja la etiqueta de una información sobre herramientas o calcula el tamaño de la etiqueta.|  
|[CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)|Dibuja el separador entre la etiqueta y la descripción en una información sobre herramientas.|  
|[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)|Rellena el fondo de la información sobre herramientas.|  
|[CMFCToolTipCtrl::SetDescription](#setdescription)|Establece la descripción que se mostrará en la información sobre herramientas.|  
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||  
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||  
|[CMFCToolTipCtrl::SetLocation](#setlocation)||  
|[CMFCToolTipCtrl::SetParams](#setparams)|Especifica la apariencia visual de una información sobre herramientas con un objeto `CMFCToolTipInfo`.|  
  
## <a name="remarks"></a>Comentarios  
 Use `CMFCToolTipCtrl`, `CMFCToolTipInfo`, y [CTooltipManager clase](../../mfc/reference/ctooltipmanager-class.md) objetos juntos para implementar información sobre herramientas personalizada en la aplicación.  
  
 Por ejemplo, para usar informaciones sobre herramientas con estilo de globo, siga estos pasos:  
  
 1. Use la [CWinAppEx Class](../../mfc/reference/cwinappex-class.md) método para inicializar el Administrador de información sobre herramientas en la aplicación.  
  
 2. Cree una estructura `CMFCToolTipInfo` para especificar el estilo visual que desee:  
  
```  
CMFCToolTipInfo params;  
    params.m_bBoldLabel = FALSE;  
    params.m_bDrawDescription = FALSE;  
    params.m_bDrawIcon = FALSE;  
    params.m_bRoundedCorners = TRUE;  
    params.m_bDrawSeparator = FALSE;  
    if (m_bCustomColors)  
 {  
    params.m_clrFill = RGB (255,
    255,
    255);

    params.m_clrFillGradient = RGB (228,
    228,
    240);

    params.m_clrText = RGB (61,
    83,
    80);

    params.m_clrBorder = RGB (144,
    149,
    168);

 }  
```  
3. Use la [ctooltipmanager:: Settooltipparams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams) método para establecer el estilo visual de todas las informaciones sobre herramientas en la aplicación mediante el uso de los estilos definidos en el `CMFCToolTipInfo` objeto:  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);
```  
También puede derivar una clase nueva de `CMFCToolTipCtrl` para controlar la representación y el comportamiento de la información sobre herramientas. Para especificar una nueva clase de control de información sobre herramientas, use el método `CTooltipManager::SetTooltipParams`:  
  
```  
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMyToolTipCtrl))  
```  
Para restaurar la clase de control predeterminada de información sobre herramientas y restablecer la apariencia de esta información a su estado predeterminado, especifique NULL en los parámetros de información sobre herramientas y de información de clase en tiempo de ejecución de `SetTooltipParams`:  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    NULL,
    NULL);
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto `CMFCToolTipCtrl`, se establece la descripción que se muestra en la información sobre herramientas y se establece también el ancho del control de esta información.  
  
 [!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)  
  
 [CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtooltipctrl.h  
  
##  <a name="cmfctooltipctrl"></a>  CMFCToolTipCtrl::CMFCToolTipCtrl  

  
```  
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pParams*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="geticonsize"></a>  CMFCToolTipCtrl::GetIconSize  
 Devuelve el tamaño de un icono en una información sobre herramientas.  
  
```  
virtual CSize GetIconSize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño del icono, en píxeles.  
  
##  <a name="getparams"></a>  CMFCToolTipCtrl::GetParams  
 Devuelve la configuración de visualización en una información sobre herramientas.  
  
```  
const CMFCToolTipInfo& GetParams() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La configuración actual de visualización de información sobre herramientas, que se almacena en un [CMFCToolTipInfo clase](../../mfc/reference/cmfctooltipinfo-class.md) objeto.  
  
##  <a name="ondrawborder"></a>  CMFCToolTipCtrl::OnDrawBorder  
 Dibuja el borde de una información sobre herramientas.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rect,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
 [in] *rect*  
 El rectángulo delimitador de la información sobre herramientas.  
  
 [in] *clrLine*  
 Color del borde.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para personalizar la apariencia del borde de información sobre herramientas.  
  
##  <a name="ondrawdescription"></a>  CMFCToolTipCtrl::OnDrawDescription  

  
```  
virtual CSize OnDrawDescription(
    CDC* pDC,  
    CRect rect,  
    BOOL bCalcOnly);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 [in] *rect*  
 [in] *bCalcOnly*  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondrawicon"></a>  CMFCToolTipCtrl::OnDrawIcon  
 Muestra un icono en una información sobre herramientas.  
  
```  
virtual BOOL OnDrawIcon(
    CDC* pDC,  
    CRect rectImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
 [in] *rectImage*  
 Coordenadas del icono.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si se dibuja el icono. En caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para mostrar un icono personalizado. También debe invalidar [CMFCToolTipCtrl::GetIconSize](#geticonsize) para habilitar la información sobre herramientas calcular correctamente el diseño de texto y una descripción.  
  
##  <a name="ondrawlabel"></a>  CMFCToolTipCtrl::OnDrawLabel  
 Dibuja la etiqueta de una información sobre herramientas o calcula el tamaño de la etiqueta.  
  
```  
virtual CSize OnDrawLabel(
    CDC* pDC,  
    CRect rect,  
    BOOL bCalcOnly);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
 [in] *rect*  
 Rectángulo delimitador del área de etiqueta.  
  
 [in] *bCalcOnly*  
 Si `TRUE`, no se dibujará la etiqueta.  
  
### <a name="return-value"></a>Valor devuelto  
 Tamaño de la etiqueta, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada si desea personalizar la apariencia de la etiqueta de información sobre herramientas.  
  
##  <a name="ondrawseparator"></a>  CMFCToolTipCtrl::OnDrawSeparator  
 Dibuja el separador entre la etiqueta y la descripción en una información sobre herramientas.  
  
```  
virtual void OnDrawSeparator(
    CDC* pDC,  
    int x1,  
    int x2,  
    int y);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
 [in] *x1*  
 Coordenada horizontal del extremo izquierdo del separador.  
  
 [in] *x2*  
 Coordenada horizontal del extremo derecho del separador.  
  
 [in] *Y*  
 Coordenada vertical del separador.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada dibuja una línea desde el punto (x1, y) en el punto (x2, y).  
  
 Invalide este método en una clase derivada para personalizar la apariencia del separador.  
  
##  <a name="onfillbackground"></a>  CMFCToolTipCtrl::OnFillBackground  
 Rellena el fondo de la información sobre herramientas.  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    CRect rect,  
    COLORREF& clrText,  
    COLORREF& clrLine);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
 [in] *rect*  
 Especifica el rectángulo delimitador del área que desea rellenar.  
  
 [in] *clrText*  
 Color de primer plano de información sobre herramientas.  
  
 [in] *clrLine*  
 Color de los bordes y la línea de delimitador entre etiqueta y una descripción.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada rellena el rectángulo especificado por *rect* con el color o el patrón especificado por la llamada más reciente a [CMFCToolTipCtrl::SetParams](#setparams).  
  
 Invalide este método en una clase derivada si desea personalizar la apariencia de la información sobre herramientas.  
  
##  <a name="setdescription"></a>  CMFCToolTipCtrl::SetDescription  
 Establece la descripción que se mostrará en la información sobre herramientas.  
  
```  
virtual void SetDescription(const CString strDesrciption);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *strDesrciption*  
 Texto de descripción.  
  
### <a name="remarks"></a>Comentarios  
 El texto de descripción se muestra en la información sobre herramientas en el separador.  
  
##  <a name="setfixedwidth"></a>  CMFCToolTipCtrl::SetFixedWidth  

  
```  
void SetFixedWidth(
    int nWidthRegular,  
    int nWidthLargeImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nWidthRegular*  
 [in] *nWidthLargeImage*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="sethotribbonbutton"></a>  CMFCToolTipCtrl::SetHotRibbonButton  

  
```  
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pRibbonButton*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setlocation"></a>  CMFCToolTipCtrl::SetLocation  

  
```  
void SetLocation(CPoint pt);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pt*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setparams"></a>  CMFCToolTipCtrl::SetParams  
 Especifica el aspecto visual de una información sobre herramientas mediante el uso de un [CMFCToolTipInfo clase](../../mfc/reference/cmfctooltipinfo-class.md) objeto.  
  
```  
void SetParams(CMFCToolTipInfo* pParams);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pParams*  
 Puntero a un [CMFCToolTipInfo clase](../../mfc/reference/cmfctooltipinfo-class.md) objeto que contiene los parámetros de visualización.  
  
### <a name="remarks"></a>Comentarios  
 Cada vez que se muestra la información sobre herramientas, se dibuja utilizando los colores y estilos visual que *pParams* especifica. El valor de *pParams* se almacena en el miembro protegido `m_Params`, que se puede acceder mediante una clase derivada que invalide [CMFCToolTipCtrl::OnDrawBorder](#ondrawborder), [CMFCToolTipCtrl: : OnDrawIcon](#ondrawicon), [CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel), [CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator), o [CMFCToolTipCtrl::OnFillBackground](#onfillbackground)para mantener el aspecto especificado.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CToolTipCtrl (clase)](../../mfc/reference/ctooltipctrl-class.md)   
 [Clase CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)   
 [Clase CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)   
 [CWinAppEx (clase)](../../mfc/reference/cwinappex-class.md)
