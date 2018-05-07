---
title: Clase CMFCRibbonStatusBarPane | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsExtended
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnDrawBorder
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFillBackground
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAnimationList
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StartAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StopAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFinishAnimation
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonStatusBarPane [MFC], CMFCRibbonStatusBarPane
- CMFCRibbonStatusBarPane [MFC], GetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], GetTextAlign
- CMFCRibbonStatusBarPane [MFC], IsAnimation
- CMFCRibbonStatusBarPane [MFC], IsExtended
- CMFCRibbonStatusBarPane [MFC], OnDrawBorder
- CMFCRibbonStatusBarPane [MFC], OnFillBackground
- CMFCRibbonStatusBarPane [MFC], SetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], SetAnimationList
- CMFCRibbonStatusBarPane [MFC], SetTextAlign
- CMFCRibbonStatusBarPane [MFC], StartAnimation
- CMFCRibbonStatusBarPane [MFC], StopAnimation
- CMFCRibbonStatusBarPane [MFC], OnFinishAnimation
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df9109ef4613a2fb905fc5bef525f3553155417b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcribbonstatusbarpane-class"></a>Clase CMFCRibbonStatusBarPane
La `CMFCRibbonStatusBarPane` clase implementa un elemento de la cinta de opciones que puede agregar a una barra de estado de la cinta de opciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonStatusBarPane : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|Construye e inicializa un objeto `CMFCRibbonStatusBarPane`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|Devuelve la cadena que define la cadena de texto más larga que puede mostrarse en el panel sin truncamiento.|  
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|Devuelve el valor actual de la alineación del texto.|  
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|Determina si la animación está en curso.|  
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|Determina si el panel se encuentra en el área extendida de la barra de estado de la cinta de opciones.|  
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(Invalida [CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder).)|  
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(Invalida [CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground).)|  
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|Define la cadena de texto más larga que puede mostrarse en el panel sin truncamiento.|  
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|Asigna al panel de una lista de imágenes que se puede usar para ver la animación.|  
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|Establece la alineación del texto.|  
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|Inicia la animación que se asigna al panel.|  
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|Detiene la animación que se asigna al panel. .|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|Llamado por el marco de trabajo cuando se detiene la animación que se asigna al panel.|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCRibbonStatusBarPane`. En el ejemplo se muestra cómo construir un `CMFCRibbonStatusBarPane` de objeto, establecer la alineación del texto de la etiqueta del panel de barra de estado, definir el texto más largo que puede mostrarse en el panel de la barra de estado sin truncamiento, adjuntar en el panel de la barra de estado de una lista de imágenes que puede usarse para un animación e inicie la animación.  
  
 [!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxribbonstatusbarpane.h  
  
##  <a name="cmfcribbonstatusbarpane"></a>  CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane  
 Construir un objeto de panel en la barra de estado.  
  
```  
CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    BOOL bIsStatic=FALSE,  
    HICON hIcon=NULL,  
    LPCTSTR lpszAlmostLargeText=NULL);

CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    HBITMAP hBmpAnimationList,  
    int cxAnimation=16,  
    COLORREF clrTrnsp=RGB(192,192 1,192) 1,  
    HICON hIcon=NULL,  
    BOOL bIsStatic=FALSE);

CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    UINT uiAnimationListResID,  
    int cxAnimation=16,  
    COLORREF clrTrnsp=RGB(192, 192 1, 192) 1,  
    HICON hIcon=NULL,  
    BOOL bIsStatic=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nCmdID`  
 Especifica el identificador de comando del panel.  
  
 [in] `lpszText`  
 Especifica la cadena de texto que se mostrará en el panel.  
  
 [in] `bIsStatic`  
 Si `TRUE`, el panel de estado no puede ser resaltado o seleccionado haciendo clic en él.  
  
 [in] `hIcon`  
 Especifica un identificador de un icono que se mostrará en el panel.  
  
 [in] `lpszAlmostLargeText`  
 Especifica la cadena de texto más larga que puede mostrarse en el panel.  
  
 [in] `hBmpAnimationList`  
 Especifica un identificador de una lista de imágenes que se usa para ver la animación.  
  
 [in] `cxAnimation`  
 Especifica el ancho, en píxeles, del icono en la lista de imágenes que se usa para ver la animación.  
  
 [in] `clrTrnsp`  
 Especifica el color transparente de las imágenes en la lista de imágenes que se usan para la animación.  
  
 [in] `uiAnimationListResID`  
 Especifica un identificador de recurso de una lista de imágenes que se usa para ver la animación.  
  
##  <a name="getalmostlargetext"></a>  CMFCRibbonStatusBarPane::GetAlmostLargeText  
 Obtiene la cadena de texto más larga que puede mostrar el panel de la barra de estado.  
  
```  
LPCTSTR GetAlmostLargeText() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La cadena de texto más larga que puede mostrar el panel de la barra de estado.  
  
##  <a name="gettextalign"></a>  CMFCRibbonStatusBarPane::GetTextAlign  
 Obtiene el valor actual de la alineación del texto de la etiqueta del panel de barra de estado.  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La alineación del texto actual que puede ser uno de los siguientes:  
  
-   TA_LEFT  
  
-   TA_CENTER  
  
-   TA_RIGHT.  
  
##  <a name="isanimation"></a>  CMFCRibbonStatusBarPane::IsAnimation  
 Determina si la animación está en curso.  
  
```  
BOOL IsAnimation() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si la animación está en curso; `FALSE` en caso contrario.  
  
##  <a name="isextended"></a>  CMFCRibbonStatusBarPane::IsExtended  
 Determinar si el panel se encuentra en el área extendida de la barra de estado de la cinta de opciones.  
  
```  
BOOL IsExtended() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si el panel se encuentra en el área extendida de la barra de estado. En caso contrario, es `FALSE`.  
  
##  <a name="ondrawborder"></a>  CMFCRibbonStatusBarPane::OnDrawBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawBorder(CDC*);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CDC*`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onfillbackground"></a>  CMFCRibbonStatusBarPane::OnFillBackground  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onfinishanimation"></a>  CMFCRibbonStatusBarPane::OnFinishAnimation  
 Marco de trabajo llama a este método cuando finaliza la animación que se asigna al panel.  
  
```  
virtual void OnFinishAnimation();
```  
  
### <a name="remarks"></a>Comentarios  
 `StopAnimation` llamadas al método el `OnFinishAnimation` método, que puede utilizar para limpiar los datos cuando finaliza la animación.  
  
##  <a name="setalmostlargetext"></a>  CMFCRibbonStatusBarPane::SetAlmostLargeText  
 Definir el texto más largo que puede mostrarse en el panel de la barra de estado sin truncamiento.  
  
```  
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszAlmostLargeText`  
 Especifica la cadena más larga que se pueden mostrar en el panel de la barra de estado sin truncamiento.  
  
### <a name="remarks"></a>Comentarios  
 La biblioteca calcula el tamaño del texto que `lpszAlmostLargeText` especifica y cambia el tamaño del panel en consecuencia. El texto se truncará si todavía no se ajusta en el panel.  
  
##  <a name="setanimationlist"></a>  CMFCRibbonStatusBarPane::SetAnimationList  
 En el panel de la barra de estado se asocia una lista de imágenes que se puede usar para ver la animación.  
  
```  
void SetAnimationList(
    HBITMAP hBmpAnimationList,  
    int cxAnimation=16,  
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);

BOOL SetAnimationList(
    UINT uiAnimationListResID,  
    int cxAnimation=16,  
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hBmpAnimationList`  
 Especifica un identificador de una lista de imágenes.  
  
 [in] `cxAnimation`  
 Especifica el ancho, en píxeles, del marco en la lista de imágenes.  
  
 [in] `clrTransp`  
 Especifica el color transparente de la lista de imágenes.  
  
 [in] `uiAnimationListResID`  
 Especifica el identificador de recurso de la lista de imágenes.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si la lista de imágenes está conectada correctamente al panel de la barra de estado; `FALSE` en caso contrario.  
  
##  <a name="settextalign"></a>  CMFCRibbonStatusBarPane::SetTextAlign  
 Establece la alineación del texto de la etiqueta del panel de barra de estado.  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nAlign`  
 Especifica la alineación del texto.  
  
### <a name="remarks"></a>Comentarios  
 `nAlign` Puede tener uno de los siguientes valores:  
  
- `TA_LEFT`: la alineación izquierda  
  
- `TA_CENTER:` Alineación central  
  
- `TA_RIGHT:` Alineación a la derecha  
  
##  <a name="startanimation"></a>  CMFCRibbonStatusBarPane::StartAnimation  
 Inicia la animación que se asigna al panel.  
  
```  
void StartAnimation(
    UINT nFrameDelay=500,  
    UINT nDuration=-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nFrameDelay`  
 Especifica la velocidad de fotogramas de animación, en milisegundos.  
  
 [in] `nDuration`  
 Especifica cuánto tiempo debe reproducir la animación, en milisegundos. Utilice -1 para un bucle infinito.  
  
### <a name="remarks"></a>Comentarios  
 Debe especificar un identificador de una lista de imágenes antes de llamar a `StartAnimation` utilizando `SetAnimationList`.  
  
##  <a name="stopanimation"></a>  CMFCRibbonStatusBarPane::StopAnimation  
 Detiene la animación que asignó en el panel de la barra de estado.  
  
```  
void StopAnimation();
```  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonStatusBar (clase)](../../mfc/reference/cmfcribbonstatusbar-class.md)
