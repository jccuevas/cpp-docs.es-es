---
title: Clase CMFCToolTipInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBalloonTooltip
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBoldLabel
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bRoundedCorners
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bVislManagerTheme
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrBorder
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFill
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFillGradient
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrText
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nGradientAngle
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nMaxDescrWidth
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolTipInfo [MFC], m_bBalloonTooltip
- CMFCToolTipInfo [MFC], m_bBoldLabel
- CMFCToolTipInfo [MFC], m_bDrawDescription
- CMFCToolTipInfo [MFC], m_bDrawIcon
- CMFCToolTipInfo [MFC], m_bDrawSeparator
- CMFCToolTipInfo [MFC], m_bRoundedCorners
- CMFCToolTipInfo [MFC], m_bVislManagerTheme
- CMFCToolTipInfo [MFC], m_clrBorder
- CMFCToolTipInfo [MFC], m_clrFill
- CMFCToolTipInfo [MFC], m_clrFillGradient
- CMFCToolTipInfo [MFC], m_clrText
- CMFCToolTipInfo [MFC], m_nGradientAngle
- CMFCToolTipInfo [MFC], m_nMaxDescrWidth
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb5cb4020b851f3522842951030c8155ee68516f
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037550"
---
# <a name="cmfctooltipinfo-class"></a>Clase CMFCToolTipInfo
Almacena información sobre el aspecto visual de la información sobre herramientas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCToolTipInfo  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolTipInfo::operator =](#operator_eq)||  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolTipInfo::m_bBalloonTooltip](#m_bballoontooltip)|Variable booleana que indica si la información sobre herramientas tiene apariencia de globo.|  
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|Variable booleana que indica si las etiquetas de información sobre herramientas se muestran en negrita.|  
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|Variable booleana que indica si la información sobre herramientas contiene una descripción.|  
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|Variable booleana que indica si la información sobre herramientas contiene un icono.|  
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|Variable booleana que indica si se muestra un separador entre la etiqueta de información sobre herramientas y la descripción de la información sobre herramientas.|  
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|Variable booleana que indica si la información sobre herramientas tiene esquinas redondeadas.|  
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|Una variable booleana que indica si la apariencia de la información sobre herramientas debe controlarse mediante un administrador visual (vea [CMFCVisualManager clase](../../mfc/reference/cmfcvisualmanager-class.md)).|  
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|Color del borde de la información sobre herramientas.|  
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|Color del fondo de la información sobre herramientas.|  
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|Color del relleno de degradado en la información sobre herramientas.|  
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|Color del texto en la información sobre herramientas.|  
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|Ángulo del relleno de degradado en la información sobre herramientas.|  
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|Ancho máximo posible, en píxeles, de la descripción en la información sobre herramientas.|  
  
## <a name="remarks"></a>Comentarios  
 Use [CMFCToolTipCtrl clase](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, y [CTooltipManager clase](../../mfc/reference/ctooltipmanager-class.md) juntos para implementar información sobre herramientas personalizada en la aplicación. Para obtener un ejemplo de cómo usar estas clases de información sobre herramientas, vea el [CMFCToolTipCtrl clase](../../mfc/reference/cmfctooltipctrl-class.md) tema.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer los valores de las distintas variables de miembro en la clase `CMFCToolTipInfo`.  
  
 [!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtooltipctrl.h  
  
##  <a name="m_bballoontooltip"></a>  CMFCToolTipInfo::m_bBalloonTooltip  
 Especifica el estilo de presentación de todas las informaciones sobre herramientas.  
  
```  
BOOL m_bBalloonTooltip;  
```  
  
### <a name="remarks"></a>Comentarios  
 `TRUE` indica que la información sobre herramientas utiliza el estilo de globo, `FALSE` indica que la información sobre herramientas utiliza el estilo rectangular.  
  
##  <a name="m_bboldlabel"></a>  CMFCToolTipInfo::m_bBoldLabel  
 Especifica si la fuente del texto de información sobre herramientas aparece en negrita.  
  
```  
BOOL m_bBoldLabel;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este miembro del grupo de `TRUE` para mostrar el texto de información sobre herramientas con formato en negrita, o `FALSE` para mostrar las etiquetas de información sobre herramientas con una fuente no esté en negrita.  
  
##  <a name="m_bdrawdescription"></a>  CMFCToolTipInfo::m_bDrawDescription  
 Especifica si cada información sobre herramientas muestra texto de descripción.  
  
```  
BOOL m_bDrawDescription;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este miembro del grupo de `TRUE` para mostrar la descripción, o `FALSE` para ocultar la descripción. Puede especificar la descripción en una información sobre herramientas mediante una llamada a [CMFCToolTipCtrl::SetDescription](../../mfc/reference/cmfctooltipctrl-class.md#setdescription)  
  
##  <a name="m_bdrawicon"></a>  CMFCToolTipInfo::m_bDrawIcon  
 Especifica si todas las informaciones sobre herramientas mostrar iconos.  
  
```  
BOOL m_bDrawIcon;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este miembro del grupo de `TRUE` para mostrar un icono en cada información sobre herramientas, o `FALSE` para mostrar información sobre herramientas sin iconos.  
  
##  <a name="m_bdrawseparator"></a>  CMFCToolTipInfo::m_bDrawSeparator  
 Especifica si cada información sobre herramientas tiene un separador entre la etiqueta y su descripción.  
  
```  
BOOL m_bDrawSeparator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este miembro del grupo de `TRUE` para mostrar el separador entre la etiqueta de información sobre herramientas y la descripción, o `FALSE` para mostrar información sobre herramientas con ningún separador.  
  
##  <a name="m_broundedcorners"></a>  CMFCToolTipInfo::m_bRoundedCorners  
 Especifica si todas las informaciones sobre herramientas tenga esquinas redondeadas.  
  
```  
BOOL m_bRoundedCorners;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este miembro del grupo de `TRUE` para mostrar las esquinas redondeadas en información sobre herramientas, o `FALSE` para mostrar las esquinas rectangulares en información sobre herramientas.  
  
##  <a name="m_clrborder"></a>  CMFCToolTipInfo::m_clrBorder  
 Especifica el color de los bordes en todas las informaciones sobre herramientas.  
  
```  
COLORREF m_clrBorder;  
```  
  
##  <a name="m_clrfill"></a>  CMFCToolTipInfo::m_clrFill  
 Especifica el color de fondo de la información sobre herramientas.  
  
```  
COLORREF m_clrFill;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) es -1, el color de fondo de la información sobre herramientas es `m_clrFill`. En caso contrario, `m_clrFill` especifica el color del principio del degradado y `m_clrFillGradient` especifica el color del final del degradado. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) determina la dirección del degradado.  
  
##  <a name="m_clrfillgradient"></a>  CMFCToolTipInfo::m_clrFillGradient  
 Especifica el color final de un fondo degradado para la información sobre herramientas.  
  
```  
COLORREF m_clrFillGradient;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si `m_clrFillGradient` es -1, no hay ningún degradado. En caso contrario, se especifica el color inicial del degradado por [CMFCToolTipInfo::m_clrFill](#m_clrfill) y se especifica el color final del degradado por `m_clrFillGradient`. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) determina la dirección del degradado.  
  
##  <a name="m_clrtext"></a>  CMFCToolTipInfo::m_clrText  
 Especifica el color del texto de todas las informaciones sobre herramientas.  
  
```  
COLORREF m_clrText;  
```  
  
##  <a name="m_ngradientangle"></a>  CMFCToolTipInfo::m_nGradientAngle  
 Especifica el ángulo en el que se dibuja un degradado del fondo de la información sobre herramientas.  
  
```  
int m_nGradientAngle;  
```  
  
### <a name="remarks"></a>Comentarios  
 `m_nGradientAngle` Especifica el ángulo, en grados, que se desplaza el degradado en el fondo de informaciones sobre herramientas de horizontal. Si `m_nGradientAngle` es 0, se dibuja el degradado de izquierda a derecha. Si `m_nGradientAngle` es entre 1 y 360, degradado es girar a la derecha por el número de grados. Si `m_nGradientAngle` es -1, que es el valor predeterminado, se dibuja el degradado de arriba abajo. Esto es lo mismo que establecer `m_nGradientAngle` en 90.  
  
 [CMFCToolTipInfo::m_clrFill](#m_clrfill) `clrFill` especifica el color del principio del degradado y [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) `clrFillGradient` especifica el color del final del degradado. Si `m_clrFillGradient` es -1, no hay ningún degradado.  
  
##  <a name="m_nmaxdescrwidth"></a>  CMFCToolTipInfo::m_nMaxDescrWidth  
 Especifica el ancho máximo de la descripción que muestra en cada información sobre herramientas. Si el ancho de la descripción supera el valor especificado, se ajusta el texto.  
  
```  
int m_nMaxDescrWidth;  
```  
  
##  <a name="m_bvislmanagertheme"></a>  CMFCToolTipInfo::m_bVislManagerTheme  
 Especifica si el administrador visual de la aplicación controla el aspecto de todas las informaciones sobre herramientas.  
  
```  
BOOL m_bVislManagerTheme;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si `m_bVislManagerTheme` es `TRUE`, cada información sobre herramientas solicita un nuevo [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) desde el Administrador de la aplicación antes de que aparecen en la pantalla y utiliza los valores de ese objeto para determinar su apariencia visual. Los demás miembros de su [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) se omiten.  
  
##  <a name="operator_eq"></a>  CMFCToolTipInfo::operator =  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *src*  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)   
 [CMFCToolTipCtrl (clase)](../../mfc/reference/cmfctooltipctrl-class.md)
