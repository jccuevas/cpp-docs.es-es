---
title: Clase CMFCRibbonProgressBar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonProgressBar
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonProgressBar class
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
caps.latest.revision: 26
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
ms.openlocfilehash: 51efd8c4ac84dffe1384b7d664197b4bdebad110
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonprogressbar-class"></a>Clase CMFCRibbonProgressBar
Implementa un control que indica visualmente el progreso de una operación larga.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](#cmfcribbonprogressbar)|Construye e inicializa un objeto `CMFCRibbonProgressBar`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::GetPos](#getpos)|Devuelve el progreso actual.|  
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|Devuelve el valor máximo del intervalo actual.|  
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|Devuelve el valor mínimo del intervalo actual.|  
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|Devuelve el tamaño normal del elemento de la cinta. (Invalida [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|  
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|Especifica si la barra de progreso está funcionando en modo de infinito.|  
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|Llamado por el marco de trabajo para dibujar el elemento de la cinta. (Invalida [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|  
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|Establece la barra de progreso para funcionar en modo infinito.|  
|[CMFCRibbonProgressBar::SetPos](#setpos)|Establece el progreso actual.|  
|[CMFCRibbonProgressBar::SetRange](#setrange)|Establece los valores mínimos y máximo.|  
  
## <a name="remarks"></a>Comentarios  
 Un `CMFCRibbonProgressBar` puede funcionar en dos modos: normal e infinito. En el modo normal, la barra de progreso se rellena de izquierda a derecha y se detiene cuando alcanza el valor máximo. En el modo infinito, la barra de progreso se rellena repetidamente desde el valor mínimo para el valor máximo. Puede usar el modo de infinito para indicar que una operación está en curso, pero que la hora de finalización es desconocida.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CMFCRibbonProgressBar` clase. En el ejemplo se muestra cómo establecer la barra de progreso para funcionar en modo infinito (donde la hora de finalización de una operación es desconocida), establezca los valores mínimos y máximo de la barra de progreso y establecer la posición actual de la barra de progreso. Este fragmento de código forma parte de la [ejemplo de demostración de Microsoft Office 2007](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo&#11;](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxRibbonProgressBar.h  
  
##  <a name="a-namecmfcribbonprogressbara--cmfcribbonprogressbarcmfcribbonprogressbar"></a><a name="cmfcribbonprogressbar"></a>CMFCRibbonProgressBar::CMFCRibbonProgressBar  
 Construye e inicializa un [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md) objeto.  
  
```  
CMFCRibbonProgressBar();

 
CMFCRibbonProgressBar(
    UINT nID,  
    int nWidth = 90,  
    int nHeight = 22);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 Especifica el identificador de comando de la barra de progreso de la cinta de opciones.  
  
 [in] `nWidth`  
 Especifica el ancho, en píxeles, de la barra de progreso de la cinta de opciones.  
  
 [in] `nHeight`  
 Especifica el alto, en píxeles, de la barra de progreso de la cinta de opciones.  
  
##  <a name="a-namegetposa--cmfcribbonprogressbargetpos"></a><a name="getpos"></a>CMFCRibbonProgressBar::GetPos  
 Devuelve la posición actual de la barra de progreso.  
  
```  
int GetPos () const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que representa la posición actual de la barra de progreso.  
  
### <a name="remarks"></a>Comentarios  
 El intervalo que se va a establecer debe estar dentro del intervalo especificado por el [CMFCRibbonProgressBar::SetRange](#setrange) método.  
  
##  <a name="a-namegetrangemaxa--cmfcribbonprogressbargetrangemax"></a><a name="getrangemax"></a>CMFCRibbonProgressBar::GetRangeMax  
 Devuelve el actual de la barra de progreso del valor máximo.  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor máximo del intervalo actual.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetrangemina--cmfcribbonprogressbargetrangemin"></a><a name="getrangemin"></a>CMFCRibbonProgressBar::GetRangeMin  
 Devuelve el actual de la barra de progreso del valor mínimo del intervalo.  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor mínimo del intervalo actual.  
  
##  <a name="a-namegetregularsizea--cmfcribbonprogressbargetregularsize"></a><a name="getregularsize"></a>CMFCRibbonProgressBar::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisinfinitemodea--cmfcribbonprogressbarisinfinitemode"></a><a name="isinfinitemode"></a>CMFCRibbonProgressBar::IsInfiniteMode  
 Especifica si la barra de progreso está funcionando en modo de infinito.  
  
```  
BOOL IsInfiniteMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la barra de progreso está en modo infinito; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 En el modo infinito, la barra de progreso rellena repetidamente desde el valor mínimo para el valor máximo. Puede usar el modo de infinito para indicar que una operación está en curso, pero que la hora de finalización es desconocida.  
  
##  <a name="a-nameondrawa--cmfcribbonprogressbarondraw"></a><a name="ondraw"></a>CMFCRibbonProgressBar::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetinfinitemodea--cmfcribbonprogressbarsetinfinitemode"></a><a name="setinfinitemode"></a>CMFCRibbonProgressBar::SetInfiniteMode  
 Establece la barra de progreso para funcionar en modo infinito.  
  
```  
void SetInfiniteMode(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
 `TRUE`para especificar que la barra de progreso está en modo de infinito; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, si la barra de progreso está en modo infinito, se indica al usuario que está en curso una operación, pero que la hora de finalización es desconocida. Por lo tanto, la barra de progreso rellena repetidamente desde el valor mínimo para el valor máximo.  
  
##  <a name="a-namesetposa--cmfcribbonprogressbarsetpos"></a><a name="setpos"></a>CMFCRibbonProgressBar::SetPos  
 Establece la posición actual de la barra de progreso.  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nPos`  
 Especifica la posición a la que se establece la barra de progreso.  
  
 [in] `bRedraw`  
 Especifica si debe volver a dibujar la barra de progreso.  
  
### <a name="remarks"></a>Comentarios  
 El intervalo que se va a establecer debe estar dentro del intervalo especificado por el [CMFCRibbonProgressBar::SetRange](#setrange) método.  
  
##  <a name="a-namesetrangea--cmfcribbonprogressbarsetrange"></a><a name="setrange"></a>CMFCRibbonProgressBar::SetRange  
 Establece los valores mínimos y máximo de la barra de progreso.  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nMin`  
 Especifica el valor mínimo del intervalo.  
  
 [in] `nMax`  
 Especifica el valor máximo del intervalo.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para definir el intervalo de la barra de progreso estableciendo los valores mínimo y máximo.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [Clase CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)

