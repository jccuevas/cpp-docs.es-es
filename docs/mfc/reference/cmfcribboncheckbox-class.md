---
title: Clase CMFCRibbonCheckBox | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonCheckBox
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCheckBox class
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
caps.latest.revision: 30
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
ms.openlocfilehash: 9efe04a8e79835b8e51b7045cb86ab2dba68b675
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribboncheckbox-class"></a>Clase CMFCRibbonCheckBox
La clase `CMFCRibbonCheckBox` implementa una casilla que se puede agregar a un menú emergente, a la barra de herramientas de acceso rápido o al panel de cinta de opciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonCheckBox : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(Invalida [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|  
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(Invalida [CMFCRibbonButton::GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|  
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(Invalida [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|  
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Invalida `CMFCRibbonButton::IsDrawTooltipImage`).|  
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(Invalida [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|  
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Invalida [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|  
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(Invalida `CMFCRibbonButton::OnDrawOnList`).|  
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(Invalida [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|  
  
## <a name="remarks"></a>Comentarios  
 Para usar un elemento `CMFCRibbonCheckBox` en su aplicación, agregue el siguiente constructor al código:  
  
```  
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)  
```  
`nID` es el identificador de comando de la casilla y `lpszText` la etiqueta de texto de la casilla.  
  
 Puede agregar una casilla de verificación a un panel de cinta de opciones mediante [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxribboncheckbox.h  
  
##  <a name="a-namecmfcribboncheckboxa--cmfcribboncheckboxcmfcribboncheckbox"></a><a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonCheckBox  
 Constructor de un objeto de casilla de verificación de la cinta de opciones  
  
```  
CMFCRibbonCheckBox(
    UINT nID,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 Especifica el identificador del comando.  
  
 [in] `lpszText`  
 Especifica la etiqueta de texto.  
  
### <a name="return-value"></a>Valor devuelto  
 Construye un objeto de casilla de verificación de la cinta de opciones.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCRibbonCheckBox` clase.  
  
 [!code-cpp[NVC_MFC_RibbonApp&#17;](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]  
  
##  <a name="a-namegetcompactsizea--cmfcribboncheckboxgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonCheckBox::GetCompactSize  
 Cuando se reemplaza, obtiene el tamaño de la casilla de verificación compact.  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a la `CDC` asociado a la casilla de verificación.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `CSize` objeto que contiene el tamaño de la casilla de verificación compact.  
  
### <a name="remarks"></a>Comentarios  
 Si no se reemplaza, devuelve el tamaño de la casilla de verificación intermedio.  
  
##  <a name="a-namegetintermediatesizea--cmfcribboncheckboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonCheckBox::GetIntermediateSize  
 Obtiene el tamaño de la casilla de verificación intermedio.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a la `CDC` asociado con esta casilla de verificación.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CSize` objeto que contiene el tamaño de la casilla de verificación intermedio.  
  
### <a name="remarks"></a>Comentarios  
 Si no se reemplaza, calcula el tamaño intermedio como el tamaño de la casilla de verificación predeterminado ( `AFX_CHECK_BOX_DEFAULT_SIZE`) más el tamaño del texto, más los márgenes.  
  
##  <a name="a-namegetregularsizea--cmfcribboncheckboxgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonCheckBox::GetRegularSize  
 Obtiene el tamaño de la casilla de verificación normal.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a la `CDC` objeto asociado con esta casilla de verificación.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `CSize` objeto que contiene el tamaño de la casilla de verificación normal.  
  
### <a name="remarks"></a>Comentarios  
 Si no se reemplaza, devuelve el tamaño de la casilla de verificación intermedio.  
  
##  <a name="a-nameisdrawtooltipimagea--cmfcribboncheckboxisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage  
 Indica si hay una imagen de información sobre herramientas asociada a la casilla de verificación.  
  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si hay una imagen de información sobre herramientas asociada a la casilla de verificación, o `FALSE` si no es así.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawa--cmfcribboncheckboxondraw"></a><a name="ondraw"></a>CMFCRibbonCheckBox::OnDraw  
 Llamado por el marco para dibujar la casilla de verificación Usar un contexto de dispositivo especificado.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a la `CDC` en el que se va a dibujar la casilla de verificación.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawmenuimagea--cmfcribboncheckboxondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMFCRibbonCheckBox::OnDrawMenuImage  
 Llamado por el marco para dibujar una imagen del menú de la casilla de verificación.  
  
```  
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CDC*`  
 Puntero a la `CDC` asociado a la casilla de verificación.  
  
 [in] `CRect`  
 Un `CRect` objeto que especifica el rectángulo en el que se va a dibujar la imagen del menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si se dibuja la imagen, o `FALSE` si no es así.  
  
### <a name="remarks"></a>Comentarios  
 Si no se reemplaza, devuelve `FALSE`.  
  
##  <a name="a-nameondrawonlista--cmfcribboncheckboxondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawOnList  
 Llamado por el marco para dibujar la casilla de verificación en un cuadro de lista de comandos.  
  
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
 [in] `pDC`  
 Puntero al contexto de dispositivo en el que se va a dibujar la casilla de verificación.  
  
 [in] `strText`  
 El texto para mostrar.  
  
 [in] `nTextOffset`  
 La distancia, en píxeles, del lado izquierdo del cuadro de lista para el texto para mostrar.  
  
 [in] `rect`  
 El rectángulo de presentación de la casilla de verificación.  
  
 [in] `bIsSelected`  
 `TRUE`Si está activada la casilla de verificación, o `FALSE` si no es así.  
  
 [in] `bHighlighted`  
 `TRUE`Si la casilla de verificación está resaltado, o `FALSE` si no es así.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetaccdataa--cmfcribboncheckboxsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonCheckBox::SetACCData  
 Establece los datos de la accesibilidad de la casilla de verificación.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParent`  
 La ventana primaria de la casilla de verificación.  
  
 `data`  
 Los datos de la accesibilidad de la casilla de verificación.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método establece los datos de la accesibilidad de la casilla de verificación y siempre devuelve `TRUE`. Invalide este método para establecer los datos de accesibilidad y devolver un valor que indique éxito o error.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

