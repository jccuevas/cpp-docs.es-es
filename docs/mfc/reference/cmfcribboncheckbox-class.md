---
title: Clase CMFCRibbonCheckBox | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 444d42c7273e64a07966592b315660b92ddf8ee0
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37042061"
---
# <a name="cmfcribboncheckbox-class"></a>Clase CMFCRibbonCheckBox
La clase `CMFCRibbonCheckBox` implementa una casilla que se puede agregar a un menú emergente, a la barra de herramientas de acceso rápido o al panel de cinta de opciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonCheckBox : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(Invalida [cmfcribbonbutton:: Getcompactsize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|  
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(Invalida [cmfcribbonbutton:: Getintermediatesize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|  
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(Invalida [cmfcribbonbutton:: Getregularsize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|  
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Invalida `CMFCRibbonButton::IsDrawTooltipImage`).|  
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(Invalida [cmfcribbonbutton:: OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|  
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Invalida [cmfcribbonbaseelement:: Ondrawmenuimage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|  
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(Invalida `CMFCRibbonButton::OnDrawOnList`).|  
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(Invalida [cmfcribbonbutton:: Setaccdata](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|  
  
## <a name="remarks"></a>Comentarios  
 Para usar un elemento `CMFCRibbonCheckBox` en su aplicación, agregue el siguiente constructor al código:  
  
```  
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)  
```  
donde *nID* es el identificador de comando de casilla de verificación y *lpszText* es la etiqueta de texto de la casilla de verificación.  
  
 Puede agregar una casilla a un panel de cinta de opciones mediante [cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxribboncheckbox.h  
  
##  <a name="cmfcribboncheckbox"></a>  CMFCRibbonCheckBox::CMFCRibbonCheckBox  
 Constructor de un objeto de casilla de verificación de la cinta de opciones  
  
```  
CMFCRibbonCheckBox(
    UINT nID,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nID*  
 Especifica el identificador del comando.  
  
 [in] *lpszText*  
 Especifica la etiqueta de texto.  
  
### <a name="return-value"></a>Valor devuelto  
 Construye un objeto de casilla de verificación de la cinta de opciones.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCRibbonCheckBox` clase.  
  
 [!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]  
  
##  <a name="getcompactsize"></a>  CMFCRibbonCheckBox::GetCompactSize  
 Cuando se reemplaza, obtiene el tamaño compacto de la casilla de verificación.  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a la `CDC` asociado con la casilla de verificación.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `CSize` objeto que contiene el tamaño compacto de la casilla de verificación.  
  
### <a name="remarks"></a>Comentarios  
 Si no se reemplaza, devuelve el tamaño de la casilla de verificación intermedio.  
  
##  <a name="getintermediatesize"></a>  CMFCRibbonCheckBox::GetIntermediateSize  
 Obtiene el tamaño de la casilla de verificación intermedio.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a la `CDC` asociados con esta casilla de verificación.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CSize` objeto que contiene el tamaño de la casilla de verificación intermedio.  
  
### <a name="remarks"></a>Comentarios  
 Si no se reemplaza, calcula el tamaño intermedio como el tamaño de la casilla de verificación predeterminado ( `AFX_CHECK_BOX_DEFAULT_SIZE`) más el tamaño del texto, además de los márgenes.  
  
##  <a name="getregularsize"></a>  CMFCRibbonCheckBox::GetRegularSize  
 Obtiene el tamaño normal de la casilla de verificación.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a la `CDC` objeto asociado con esta casilla de verificación.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `CSize` objeto que contiene el tamaño normal de la casilla de verificación.  
  
### <a name="remarks"></a>Comentarios  
 Si no se reemplaza, devuelve el tamaño de la casilla de verificación intermedio.  
  
##  <a name="isdrawtooltipimage"></a>  CMFCRibbonCheckBox::IsDrawTooltipImage  
 Indica si hay una imagen de información sobre herramientas asociada a la casilla de verificación.  
  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si hay una imagen de información sobre herramientas asociada a la casilla de verificación, o `FALSE` si no es así.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondraw"></a>  CMFCRibbonCheckBox::OnDraw  
 Lo llama el marco de trabajo para dibujar la casilla de verificación Usar un contexto de dispositivo especificado.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a la `CDC` en el que se va a dibujar la casilla de verificación.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondrawmenuimage"></a>  CMFCRibbonCheckBox::OnDrawMenuImage  
 Lo llama el marco de trabajo para dibujar una imagen del menú de la casilla.  
  
```  
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *CDC**  
 Puntero a la `CDC` asociado con la casilla de verificación.  
  
 [in] *CRect*  
 Un `CRect` objeto que especifica el rectángulo en el que se va a dibujar la imagen del menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si se dibuja la imagen, o `FALSE` si no es así.  
  
### <a name="remarks"></a>Comentarios  
 Si no se reemplaza, devuelve `FALSE`.  
  
##  <a name="ondrawonlist"></a>  CMFCRibbonCheckBox::OnDrawOnList  
 Lo llama el marco de trabajo para dibujar la casilla de verificación en un cuadro de lista de comandos.  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero al contexto de dispositivo en el que se va a dibujar la casilla de verificación.  
  
 [in] *strText*  
 El texto para mostrar.  
  
 [in] *nTextOffset*  
 La distancia, en píxeles, del lado izquierdo del cuadro de lista para el texto de presentación.  
  
 [in] *rect*  
 El rectángulo de presentación de la casilla.  
  
 [in] *bIsSelected*  
 `TRUE` Si se selecciona la casilla de verificación, o `FALSE` si no es así.  
  
 [in] *bHighlighted*  
 `TRUE` Si la casilla de verificación está resaltado, o `FALSE` si no es así.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setaccdata"></a>  CMFCRibbonCheckBox::SetACCData  
 Establece los datos de accesibilidad de la casilla.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parámetros  
 *pParent*  
 La ventana primaria de la casilla de verificación.  
  
 *data*  
 Los datos de accesibilidad de la casilla.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método establece los datos de accesibilidad para la casilla de verificación y siempre devuelve `TRUE`. Invalide este método para establecer los datos de accesibilidad y devolver un valor que indique éxito o error.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel (clase)](../../mfc/reference/cmfcribbonpanel-class.md)
