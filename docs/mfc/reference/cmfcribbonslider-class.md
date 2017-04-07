---
title: Clase CMFCRibbonSlider | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMax
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMin
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRegularSize
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetZoomIncrement
- AFXRIBBONSLIDER/CMFCRibbonSlider::HasZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::OnDraw
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetRange
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomIncrement
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonSlider class
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
caps.latest.revision: 43
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
ms.openlocfilehash: 9f05ae7d0f3e1775a3321928867471749e11e679
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonslider-class"></a>Clase CMFCRibbonSlider
La `CMFCRibbonSlider` clase implementa un control deslizante que puede agregar a una barra de cinta de opciones o la barra de estado de la cinta de opciones. El control deslizante de la cinta es similar a los controles deslizantes del zoom que aparecen en las aplicaciones de Office 2007.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonSlider : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|Crea e inicializa un control deslizante de cinta de opciones.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonSlider::GetPos](#getpos)|Devuelve la posición actual del control deslizante.|  
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|Devuelve el valor máximo del control deslizante.|  
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|Devuelve el valor mínimo del control deslizante.|  
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|Devuelve el tamaño normal del elemento de la cinta. (Invalida [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|  
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|Devuelve el tamaño del incremento para el control deslizante del zoom.|  
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|Especifica si el control deslizante tiene botones de zoom.|  
|[CMFCRibbonSlider::OnDraw](#ondraw)|Llamado por el marco de trabajo para dibujar el elemento de la cinta. (Invalida [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|  
|[CMFCRibbonSlider::SetPos](#setpos)|Establece la posición actual del control deslizante.|  
|[CMFCRibbonSlider::SetRange](#setrange)|Especifica el intervalo del control deslizante estableciendo los valores mínimos y máximo.|  
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|Muestra u oculta los botones de zoom.|  
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|Establece el tamaño del incremento para el control deslizante del zoom.|  
  
## <a name="remarks"></a>Comentarios  
 Puede usar el `SetRange` método para configurar el intervalo de incrementos de zoom para el control deslizante. Puede establecer la posición actual del control deslizante mediante el `SetPos` método.  
  
 Puede mostrar botones de zoom circular en los lados izquierdo y derecho del control deslizante mediante el `SetZoomButtons` método. De forma predeterminada, el control deslizante es horizontal, el botón de zoom izquierdo muestra un signo menos y el botón de zoom derecho muestra un signo más.  
  
 El `SetZoomIncrement` método define el incremento que se debe sumar o restar desde la posición actual cuando un usuario hace clic en los botones de zoom.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CMFCRibbonSlider` clase para establecer las propiedades del control deslizante. En el ejemplo se muestra cómo construir un `CMFCRibbonSlider` objeto, mostrar botones de zoom, establecer la posición actual del control deslizante y establecer el intervalo de valores para el control deslizante.  
  
 [!code-cpp[NVC_MFC_RibbonApp&#12;](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxribbonslider.h  
  
##  <a name="cmfcribbonslider"></a>CMFCRibbonSlider::CMFCRibbonSlider  
 Crear un control deslizante de la cinta de opciones.  
  
```  
CMFCRibbonSlider(
    UINT nID,  
    int nWidth=100);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 Id. de control deslizante  
  
 [in]. `nWidth`  
 Ancho del control deslizante en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Crea un control deslizante de cinta que está `nWidth` píxeles de ancho en la categoría del panel donde se agrega el control deslizante. De forma predeterminada, el control deslizante es horizontal.  
  
##  <a name="getpos"></a>CMFCRibbonSlider::GetPos  
 Devuelve la posición actual del control deslizante.  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La posición actual del control deslizante, que es una posición relativa al principio del control deslizante.  
  
##  <a name="getrangemax"></a>CMFCRibbonSlider::GetRangeMax  
 Obtiene el incremento máximo del control deslizante que puede viajar el control deslizante en el control deslizante.  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El incremento máximo del control deslizante que puede viajar el control deslizante en el control deslizante.  
  
##  <a name="getrangemin"></a>CMFCRibbonSlider::GetRangeMin  
 Devuelve el incremento mínimo que el control deslizante puede viajar en el control deslizante.  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El incremento mínimo que el control deslizante puede viajar en el control deslizante.  
  
##  <a name="getregularsize"></a>CMFCRibbonSlider::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getzoomincrement"></a>CMFCRibbonSlider::GetZoomIncrement  
 Obtener el incremento de zoom del control deslizante.  
  
```  
int GetZoomIncrement() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El incremento de zoom del control deslizante.  
  
##  <a name="haszoombuttons"></a>CMFCRibbonSlider::HasZoomButtons  
 Especifica si el control deslizante tiene botones de zoom.  
  
```  
BOOL HasZoomButtons() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el control deslizante tiene botones de zoom. `FALSE` en caso contrario.  
  
##  <a name="ondraw"></a>CMFCRibbonSlider::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setpos"></a>CMFCRibbonSlider::SetPos  
 Establecer la posición actual del control deslizante.  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nPos`  
 Especifica la posición para establecer para el control deslizante. La posición es relativa al principio del control deslizante.  
  
 [in] `bRedraw`  
 Si `TRUE`, se volverá a dibujar el control deslizante.  
  
##  <a name="setrange"></a>CMFCRibbonSlider::SetRange  
 Establecer el intervalo de valores para el control deslizante.  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nMin`  
 Especifica el valor mínimo del control deslizante.  
  
 [in] `nMax`  
 Especifica el valor máximo del control deslizante.  
  
### <a name="remarks"></a>Comentarios  
 Especifica el intervalo de valores para el control deslizante estableciendo los valores mínimo y máximos.  
  
##  <a name="setzoombuttons"></a>CMFCRibbonSlider::SetZoomButtons  
 Mostrar u ocultar los botones de zoom.  
  
```  
void SetZoomButtons(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in]. `bSet`  
 `TRUE`para mostrar los botones de zoom; `FALSE` para ocultarlas.  
  
##  <a name="setzoomincrement"></a>CMFCRibbonSlider::SetZoomIncrement  
 Establecer el incremento de zoom del control deslizante.  
  
```  
void SetZoomIncrement(int nZoomIncrement);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nZoomIncrement`  
 Especifica el incremento de zoom del control deslizante.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

