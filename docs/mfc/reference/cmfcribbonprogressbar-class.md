---
title: Clase CMFCRibbonProgressBar | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMax
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMin
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRegularSize
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::IsInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::OnDraw
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetRange
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonProgressBar [MFC], CMFCRibbonProgressBar
- CMFCRibbonProgressBar [MFC], GetPos
- CMFCRibbonProgressBar [MFC], GetRangeMax
- CMFCRibbonProgressBar [MFC], GetRangeMin
- CMFCRibbonProgressBar [MFC], GetRegularSize
- CMFCRibbonProgressBar [MFC], IsInfiniteMode
- CMFCRibbonProgressBar [MFC], OnDraw
- CMFCRibbonProgressBar [MFC], SetInfiniteMode
- CMFCRibbonProgressBar [MFC], SetPos
- CMFCRibbonProgressBar [MFC], SetRange
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b9d0d1ab9722b14caddc3935d820301ae229f5a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369341"
---
# <a name="cmfcribbonprogressbar-class"></a>Clase CMFCRibbonProgressBar
Implementa un control que indica visualmente el progreso de una operación larga.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](#cmfcribbonprogressbar)|Construye e inicializa un objeto `CMFCRibbonProgressBar`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::GetPos](#getpos)|Devuelve el progreso actual.|  
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|Devuelve el valor máximo del intervalo actual.|  
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|Devuelve el valor mínimo del intervalo actual.|  
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|Devuelve el tamaño normal del elemento de la cinta. (Invalida [cmfcribbonbaseelement:: Getregularsize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|  
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|Especifica si la barra de progreso está funcionando en modo de infinito.|  
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|Llamado por el marco de trabajo para dibujar el elemento de la cinta. (Invalida [cmfcribbonbaseelement:: OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|  
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|Establece la barra de progreso para operar en modo infinito.|  
|[CMFCRibbonProgressBar::SetPos](#setpos)|Establece el progreso actual.|  
|[CMFCRibbonProgressBar::SetRange](#setrange)|Establece los valores mínimos y máximo.|  
  
## <a name="remarks"></a>Comentarios  
 Un `CMFCRibbonProgressBar` puede funcionar en dos modos: normales e infinito. En modo normal, la barra de progreso se rellena de izquierda a derecha y se detiene cuando alcanza el valor máximo. En el modo infinito, la barra de progreso se rellena repetidamente desde el valor mínimo para el valor máximo. Puede usar el modo de infinito para indicar que una operación está en curso, pero que la hora de finalización es desconocida.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CMFCRibbonProgressBar` clase. En el ejemplo se muestra cómo establecer la barra de progreso para operar en modo infinito (donde la hora de finalización de una operación es desconocida), Establece los valores mínimos y máximo de la barra de progreso y establece la posición actual de la barra de progreso. Este fragmento de código forma parte de la [ejemplo de demostración de MS Office 2007](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxRibbonProgressBar.h  
  
##  <a name="cmfcribbonprogressbar"></a>  CMFCRibbonProgressBar::CMFCRibbonProgressBar  
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
  
##  <a name="getpos"></a>  CMFCRibbonProgressBar::GetPos  
 Devuelve la posición actual de la barra de progreso.  
  
```  
int GetPos () const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que representa la posición actual de la barra de progreso.  
  
### <a name="remarks"></a>Comentarios  
 El intervalo que se va a establecer debe estar dentro del intervalo especificado por el [CMFCRibbonProgressBar::SetRange](#setrange) método.  
  
##  <a name="getrangemax"></a>  CMFCRibbonProgressBar::GetRangeMax  
 Devuelve el actual de la barra de progreso del valor máximo.  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor máximo del intervalo actual.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getrangemin"></a>  CMFCRibbonProgressBar::GetRangeMin  
 Devuelve el actual de la barra de progreso del valor mínimo del intervalo.  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor mínimo del intervalo actual.  
  
##  <a name="getregularsize"></a>  CMFCRibbonProgressBar::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isinfinitemode"></a>  CMFCRibbonProgressBar::IsInfiniteMode  
 Especifica si la barra de progreso está funcionando en modo de infinito.  
  
```  
BOOL IsInfiniteMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si la barra de progreso está en modo infinito; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 En el modo infinito, la barra de progreso rellena repetidamente desde el valor mínimo para el valor máximo. Puede usar el modo de infinito para indicar que una operación está en curso, pero que la hora de finalización es desconocida.  
  
##  <a name="ondraw"></a>  CMFCRibbonProgressBar::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setinfinitemode"></a>  CMFCRibbonProgressBar::SetInfiniteMode  
 Establece la barra de progreso para operar en modo infinito.  
  
```  
void SetInfiniteMode(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
 `TRUE` para especificar que la barra de progreso está en modo de infinito; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Por lo general, si la barra de progreso está en modo de infinito, se indica al usuario que está en curso una operación, pero que la hora de finalización es desconocida. Por lo tanto, la barra de progreso rellena repetidamente desde el valor mínimo para el valor máximo.  
  
##  <a name="setpos"></a>  CMFCRibbonProgressBar::SetPos  
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
  
##  <a name="setrange"></a>  CMFCRibbonProgressBar::SetRange  
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
 Utilice este método para definir el intervalo de la barra de progreso estableciendo valores mínimo y máximo.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)
