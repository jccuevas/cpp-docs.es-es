---
title: Clase CMFCRibbonEdit | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CanBeStretched
- AFXRIBBONEDIT/CMFCRibbonEdit::CopyFrom
- AFXRIBBONEDIT/CMFCRibbonEdit::CreateEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::DestroyCtrl
- AFXRIBBONEDIT/CMFCRibbonEdit::DropDownList
- AFXRIBBONEDIT/CMFCRibbonEdit::EnableSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::GetCompactSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::GetIntermediateSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::GetWidth
- AFXRIBBONEDIT/CMFCRibbonEdit::HasCompactMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasFocus
- AFXRIBBONEDIT/CMFCRibbonEdit::HasLargeMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::IsHighlighted
- AFXRIBBONEDIT/CMFCRibbonEdit::OnAfterChangeRect
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDraw
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawLabelAndImage
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawOnList
- AFXRIBBONEDIT/CMFCRibbonEdit::OnEnable
- AFXRIBBONEDIT/CMFCRibbonEdit::OnHighlight
- AFXRIBBONEDIT/CMFCRibbonEdit::OnKey
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonDown
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonUp
- AFXRIBBONEDIT/CMFCRibbonEdit::OnRTLChanged
- AFXRIBBONEDIT/CMFCRibbonEdit::OnShow
- AFXRIBBONEDIT/CMFCRibbonEdit::Redraw
- AFXRIBBONEDIT/CMFCRibbonEdit::SetACCData
- AFXRIBBONEDIT/CMFCRibbonEdit::SetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::SetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::SetWidth
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CanBeStretched
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CopyFrom
- CMFCRibbonEdit [MFC], CreateEdit
- CMFCRibbonEdit [MFC], DestroyCtrl
- CMFCRibbonEdit [MFC], DropDownList
- CMFCRibbonEdit [MFC], EnableSpinButtons
- CMFCRibbonEdit [MFC], GetCompactSize
- CMFCRibbonEdit [MFC], GetEditText
- CMFCRibbonEdit [MFC], GetIntermediateSize
- CMFCRibbonEdit [MFC], GetTextAlign
- CMFCRibbonEdit [MFC], GetWidth
- CMFCRibbonEdit [MFC], HasCompactMode
- CMFCRibbonEdit [MFC], HasFocus
- CMFCRibbonEdit [MFC], HasLargeMode
- CMFCRibbonEdit [MFC], HasSpinButtons
- CMFCRibbonEdit [MFC], IsHighlighted
- CMFCRibbonEdit [MFC], OnAfterChangeRect
- CMFCRibbonEdit [MFC], OnDraw
- CMFCRibbonEdit [MFC], OnDrawLabelAndImage
- CMFCRibbonEdit [MFC], OnDrawOnList
- CMFCRibbonEdit [MFC], OnEnable
- CMFCRibbonEdit [MFC], OnHighlight
- CMFCRibbonEdit [MFC], OnKey
- CMFCRibbonEdit [MFC], OnLButtonDown
- CMFCRibbonEdit [MFC], OnLButtonUp
- CMFCRibbonEdit [MFC], OnRTLChanged
- CMFCRibbonEdit [MFC], OnShow
- CMFCRibbonEdit [MFC], Redraw
- CMFCRibbonEdit [MFC], SetACCData
- CMFCRibbonEdit [MFC], SetEditText
- CMFCRibbonEdit [MFC], SetTextAlign
- CMFCRibbonEdit [MFC], SetWidth
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 43a497b3eeec48c22d688f4974efcb3d2f511446
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonedit-class"></a>Clase CMFCRibbonEdit
Implementa un control de edición que se encuentra en una barra de cinta de opciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonEdit : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Construye un objeto `CMFCRibbonEdit`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Indica si el alto de la `CMFCRibbonEdit` control puede aumentar verticalmente el alto de una fila de la cinta de opciones.|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Construye un objeto `CMFCRibbonEdit`.|  
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Copia el estado del elemento especificado `CMFCRibbonEdit` objeto al actual `CMFCRibbonEdit` objeto.|  
|[CMFCRibbonEdit::CreateEdit](#createedit)|Crea un nuevo cuadro de texto para el `CMFCRibbonEdit` objeto.|  
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|Destruye el objeto `CMFCRibbonEdit`.|  
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Quita un cuadro de lista desplegable.|  
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Habilita y configura el intervalo de botón de número para el cuadro de texto.|  
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Recupera el tamaño compacto de la `CFMCRibbonEdit` objeto.|  
|[CMFCRibbonEdit::GetEditText](#getedittext)|Recupera el texto en el cuadro de texto.|  
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Recupera el tamaño intermedio de la `CMFCRibbonEdit` objeto.|  
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|Recupera la alineación del texto en el cuadro de texto.|  
|[CMFCRibbonEdit::GetWidth](#getwidth)|Recupera el ancho, en píxeles, de la `CMFCRibbonEdit` control.|  
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Indica si la pantalla de cambio de tamaño para el `CMFCRibbonEdit` control puede ser compact.|  
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Indica si el `CMFCRIbbonEdit` control tiene el foco.|  
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Indica si la pantalla de cambio de tamaño para el `CMFCRibbonEdit` control puede ser grande.|  
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Indica si el cuadro de texto tiene un botón de número.|  
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|Indica si el `CMFCRibbonEdit` control aparece resaltado.|  
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Lo llama el marco cuando las dimensiones del rectángulo de presentación para el `CMFCRibbonEdit` controlar los cambios.|  
|[CMFCRibbonEdit::OnDraw](#ondraw)|Lo llama el marco para dibujar el `CMFCRibbonEdit` control.|  
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Lo llama el marco para dibujar la etiqueta y la imagen para el `CMFCRibbonEdit` control.|  
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|Lo llama el marco para dibujar el `CMFCRibbonEdit` control en un cuadro de lista de comandos.|  
|[CMFCRibbonEdit::OnEnable](#onenable)|Lo llama el marco para habilitar o deshabilitar la `CMFCRibbonEdit` control.|  
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|Lo llama el marco de trabajo cuando el puntero entra o sale de los límites de la `CMFCRibbonEdit` control.|  
|[CMFCRibbonEdit::OnKey](#onkey)|Lo llama el marco cuando el usuario presiona keytip y `CMFCRibbonEdit` control tiene el foco.|  
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Lo llama el marco para actualizar la `CMFCRibbonEdit` controlar cuando el usuario presiona el botón primario del mouse en el control.|  
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Lo llama el marco cuando el usuario suelta el botón primario del mouse.|  
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Lo llama el marco para actualizar la `CMFCRibbonEdit` controlar cuando cambia el diseño de la dirección.|  
|[CMFCRibbonEdit::OnShow](#onshow)|Lo llama el marco para mostrar u ocultar el `CMFCRibbonEdit` control.|  
|[CMFCRibbonEdit::Redraw](#redraw)|Actualiza la presentación de la `CMFCRibbonEdit` control.|  
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Establece los datos de accesibilidad para el `CMFCRibbonEdit` objeto.|  
|[CMFCRibbonEdit::SetEditText](#setedittext)|Establece el texto en el cuadro de texto.|  
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Establece la alineación del texto del cuadro de texto.|  
|[CMFCRibbonEdit::SetWidth](#setwidth)|Establece el ancho del cuadro de texto para el `CMFCRibbonEdit` control.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un `CMFCRibbonEdit` objeto, mostrar botones de número situado junto al control de edición y establecer el texto del control de edición. Este fragmento de código forma parte de la [ejemplo de demostración de MS Office 2007](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxRibbonEdit.h  
  
##  <a name="canbestretched"></a>CMFCRibbonEdit::CanBeStretched  
 Indica si el alto de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control puede aumentar verticalmente el alto de una fila de la cinta de opciones.  
  
```  
virtual BOOL CanBeStretched();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="cmfcribbonedit"></a>CMFCRibbonEdit::CMFCRibbonEdit  
 Construye un [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.  
  
```  
CMFCRibbonEdit(
    UINT nID,  
    int nWidth,  
    LPCTSTR lpszLabel = NULL,  
    int nImage = -1);

CMFCRibbonEdit();
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 Comando identificador para el `CMFCRibbonEdit` control.  
  
 [in] `nWidth`  
 El ancho, en píxeles, del cuadro de texto para el `CMFCRibbonEdit` control.  
  
 [in] `lpszLabel`  
 La etiqueta para el `CMFCRibbonEdit` control.  
  
 [in] `nImage`  
 Índice de la imagen pequeña que se utilizará para el `CMFCRibbonEdit` control. La colección de imágenes pequeñas se mantiene por la categoría de cinta de opciones del elemento primario.  
  
### <a name="remarks"></a>Comentarios  
 El `CMFCRibbonEdit` control no usa una imagen grande.  
  
##  <a name="copyfrom"></a>CMFCRibbonEdit::CopyFrom  
 Copia el estado del elemento especificado [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto al actual [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `src`  
 Objeto `CMFCRibbonEdit` de origen.  
  
### <a name="remarks"></a>Comentarios  
 El `src` parámetro debe ser de tipo `CMFCRibbonEdit`.  
  
##  <a name="createedit"></a>CMFCRibbonEdit::CreateEdit  
 Crea un nuevo cuadro de texto para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.  
  
```  
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndParent`  
 Un puntero a la ventana primaria de la `CMFCRibbonEdit` objeto.  
  
 [in] `dwEditStyle`  
 Especifica el estilo del cuadro de texto. Puede combinar los estilos de ventana que aparece en la sección de comentarios con la [estilos de control de edición](http://msdn.microsoft.com/library/windows/desktop/bb775464) que se describen en el SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al nuevo cuadro de texto si el método se realizó correctamente; en caso contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para crear un cuadro de texto personalizado.  
  
 Puede aplicar la siguiente [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) al cuadro de texto:  
  
- **WS_CHILD**  
  
- **WS_VISIBLE**  
  
- **WS_DISABLED**  
  
- **WS_GROUP**  
  
- **WS_TABSTOP**  
  
##  <a name="destroyctrl"></a>CMFCRibbonEdit::DestroyCtrl  
 Destruye el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.  
  
```  
virtual void DestroyCtrl();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="dropdownlist"></a>CMFCRibbonEdit::DropDownList  
 Quita un cuadro de lista desplegable.  
  
```  
virtual void DropDownList();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método no hace nada. Invalide este método para un cuadro de lista desplegable.  
  
##  <a name="enablespinbuttons"></a>CMFCRibbonEdit::EnableSpinButtons  
 Habilita y configura el intervalo de botón de número para el cuadro de texto.  
  
```  
void EnableSpinButtons(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nMin`  
 El valor mínimo del botón de número.  
  
 [in] `nMax`  
 El valor máximo del botón de número.  
  
### <a name="remarks"></a>Comentarios  
 Botones Mostrar un arriba y flecha abajo y permiten a los usuarios desplazarse por un conjunto fijo de valores.  
  
##  <a name="getcompactsize"></a>CMFCRibbonEdit::GetCompactSize  
 Recupera el tamaño compacto de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo para la `CMFCRibbonEdit` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño compacto de la `CMFCRibbonEdit` objeto.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getedittext"></a>CMFCRibbonEdit::GetEditText  
 Recupera el texto en el cuadro de texto.  
  
```  
CString GetEditText() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El texto en el cuadro de texto.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getintermediatesize"></a>CMFCRibbonEdit::GetIntermediateSize  
 Recupera el tamaño intermedio de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo para la `CMFCRibbonEdit` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño intermedio de la `CMFCRibbonEdit` objeto.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gettextalign"></a>CMFCRibbonEdit::GetTextAlign  
 Recupera la alineación del texto en el cuadro de texto.  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor enumerado de alineación de texto. Vea la sección Comentarios para los valores posibles.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto es uno de los estilos de control de edición siguientes:  
  
- **ES_LEFT** para alineación a la izquierda  
  
- **ES_CENTER** para centrar  
  
- **ES_RIGHT** para alineación a la derecha  
  
 Para obtener más información acerca de estos estilos, consulte [Editar estilos de Control](http://msdn.microsoft.com/library/windows/desktop/bb775464).  
  
##  <a name="getwidth"></a>CMFCRibbonEdit::GetWidth  
 Recupera el ancho, en píxeles, de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.  
  
```  
int GetWidth(BOOL bInFloatyMode = FALSE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bInFloatyMode`  
 `TRUE`Si el `CMFCRibbonEdit` control está en modo de punto flotante; en caso contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho, en píxeles, de la `CMFCRibbonEdit` control.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="hascompactmode"></a>CMFCRibbonEdit::HasCompactMode  
 Indica si la pantalla de cambio de tamaño para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control puede ser compact.  
  
```  
virtual BOOL HasCompactMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método devuelve siempre `TRUE`. Invalide este método para indicar si el tamaño de presentación puede ser compact.  
  
##  <a name="hasfocus"></a>CMFCRibbonEdit::HasFocus  
 Indica si la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control tiene el foco.  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el `CMFCRibbonEdit` control tiene el foco; en caso contrario `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="haslargemode"></a>CMFCRibbonEdit::HasLargeMode  
 Indica si la pantalla de cambio de tamaño para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control puede ser grande.  
  
```  
virtual BOOL HasLargeMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método devuelve siempre `FALSE`. Invalide este método para indicar si el tamaño de presentación puede ser grande.  
  
##  <a name="hasspinbuttons"></a>CMFCRibbonEdit::HasSpinButtons  
 Indica si el cuadro de texto tiene un botón de número.  
  
```  
virtual BOOL HasSpinButtons() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el cuadro de texto tiene un botón de número; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ishighlighted"></a>CMFCRibbonEdit::IsHighlighted  
 Indica si la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control aparece resaltado.  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el `CMFCRibbonEdit` control está resaltado; en caso contrario `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onafterchangerect"></a>CMFCRibbonEdit::OnAfterChangeRect  
 Lo llama el marco cuando las dimensiones del rectángulo de presentación para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controlar el cambio.  
  
```  
virtual void OnAfterChangeRect(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo para el `CMFCRibbonEdit` control.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondraw"></a>CMFCRibbonEdit::OnDraw  
 Lo llama el marco para dibujar el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo para el `CMFCRibbonEdit` control.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondrawlabelandimage"></a>CMFCRibbonEdit::OnDrawLabelAndImage  
 Lo llama el marco para dibujar la etiqueta y la imagen para la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.  
  
```  
virtual void OnDrawLabelAndImage(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo para el `CMFCRibbonEdit` control.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondrawonlist"></a>CMFCRibbonEdit::OnDrawOnList  
 Lo llama el marco para dibujar el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control en un cuadro de lista de comandos.  
  
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
 Puntero a un contexto de dispositivo para el `CMFCRibbonEdit` control.  
  
 [in] `strText`  
 El texto de presentación [](../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit clase").  
  
 [in] `nTextOffset`  
 Distancia, en píxeles, del lado izquierdo del cuadro de lista para el texto de presentación.  
  
 [in] `rect`  
 El rectángulo de presentación para el `CMFCRibbonEdit` control.  
  
 [in] `bIsSelected`  
 Este parámetro no se utiliza.  
  
 [in] `bHighlighted`  
 Este parámetro no se utiliza.  
  
### <a name="remarks"></a>Comentarios  
 El cuadro de lista de comandos muestra los controles de cinta de opciones para permitir a los usuarios personalizar la barra de herramientas de acceso rápido.  
  
##  <a name="onenable"></a>CMFCRibbonEdit::OnEnable  
 Lo llama el marco para habilitar o deshabilitar la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.  
  
```  
virtual void OnEnable(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar el control; `FALSE` para deshabilitar el control.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onhighlight"></a>CMFCRibbonEdit::OnHighlight  
 Lo llama el marco de trabajo cuando el puntero entra o sale de los límites de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.  
  
```  
virtual void OnHighlight(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bHighlight`  
 `TRUE`Si el puntero está en los límites de la `CMFCRibbonEdit` control; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onkey"></a>CMFCRibbonEdit::OnKey  
 Lo llama el marco cuando el usuario presiona keytip y [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control tiene el foco.  
  
```  
virtual BOOL OnKey(BOOL bIsMenuKey);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bIsMenuKey`  
 `TRUE`Si la keytip muestra un menú emergente; en caso contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si se controló el evento; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onlbuttondown"></a>CMFCRibbonEdit::OnLButtonDown  
 Lo llama el marco para actualizar la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controlar cuando el usuario presiona el botón primario del mouse en el control.  
  
```  
virtual void OnLButtonDown(CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Este parámetro no se utiliza.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onlbuttonup"></a>CMFCRibbonEdit::OnLButtonUp  
 Lo llama el marco cuando el usuario suelta el botón primario del mouse.  
  
```  
virtual void OnLButtonUp(CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Este parámetro no se utiliza.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onrtlchanged"></a>CMFCRibbonEdit::OnRTLChanged  
 Lo llama el marco para actualizar la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controlar cuando cambia el diseño de la dirección.  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bIsRTL`  
 `TRUE`Si el diseño es de derecha a izquierda; `FALSE` si el diseño es de izquierda a derecha.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onshow"></a>CMFCRibbonEdit::OnShow  
 Lo llama el marco para mostrar u ocultar la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShow`  
 `TRUE`para mostrar el control; `FALSE` para ocultar el control.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="redraw"></a>CMFCRibbonEdit::Redraw  
 Actualiza la presentación de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.  
  
```  
virtual void Redraw();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método vuelve a dibujar el rectángulo de presentación para el `CMFCRibbonEdit` objeto llamando indirectamente [CWnd::RedrawWindow](http://msdn.microsoft.com/library/windows/desktop/dd162911) con el `RDW_INVALIDATE`, `RDW_ERASE`, y `RDW_UPDATENOW` conjunto.  
  
##  <a name="setaccdata"></a>CMFCRibbonEdit::SetACCData  
 Establece los datos de accesibilidad para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParent`  
 Puntero a la ventana primaria para el `CMFCRibbonEdit` objeto.  
  
 `data`  
 Los datos de accesibilidad para el `CMFCRibbonEdit` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setedittext"></a>CMFCRibbonEdit::SetEditText  
 Establece el texto en el cuadro de texto.  
  
```  
void SetEditText(CString strText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strText`  
 El texto del cuadro de texto.  
  
##  <a name="settextalign"></a>CMFCRibbonEdit::SetTextAlign  
 Establece la alineación del texto del cuadro de texto.  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nAlign`  
 Un valor enumerado de alineación de texto. Vea la sección Comentarios para los valores posibles.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro `nAlign` es uno de la siguiente modificación estilos de control:  
  
- **ES_LEFT** para alineación a la izquierda  
  
- **ES_CENTER** para centrar  
  
- **ES_RIGHT** para alineación a la derecha  
  
 Para obtener más información acerca de estos estilos, consulte [Editar estilos de Control](http://msdn.microsoft.com/library/windows/desktop/bb775464).  
  
##  <a name="setwidth"></a>CMFCRibbonEdit::SetWidth  
 Establece el ancho del cuadro de texto para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.  
  
```  
void SetWidth(
    int nWidth,  
    BOOL bInFloatyMode = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nWidth`  
 El ancho, en píxeles, del cuadro de texto.  
  
 `bInFloatyMode`  
 `TRUE`Para establecer el ancho para el modo de punto flotante; `FALSE` para establecer el ancho del modo normal.  
  
### <a name="remarks"></a>Comentarios  
 El `CMFCRibbonEdit` control tiene dos anchos según su modo de presentación: flotante modo y el modo normal.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)