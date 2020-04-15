---
title: CMFCRibbonStatusBarPane (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: 554b9fe364c6a213e038416a605c17cdd4f8e7d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368793"
---
# <a name="cmfcribbonstatusbarpane-class"></a>CMFCRibbonStatusBarPane (clase)

La `CMFCRibbonStatusBarPane` clase implementa un elemento de la cinta de opciones que puede agregar a una barra de estado de la cinta de opciones.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonStatusBarPane : public CMFCRibbonButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|Construye e inicializa un objeto `CMFCRibbonStatusBarPane`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|Devuelve la cadena que define la cadena de texto más larga que se puede mostrar en el panel sin truncamiento.|
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|Devuelve la configuración actual de la alineación del texto.|
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|Determina si la animación está en curso.|
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|Determina si el panel se encuentra en el área extendida de la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(Reemplaza [CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder).)|
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(Reemplaza [CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground).)|
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|Define la cadena de texto más larga que se puede mostrar en el panel sin truncamiento.|
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|Asigna al panel una lista de imágenes que se puede utilizar para la animación.|
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|Establece la alineación del texto.|
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|Inicia la animación asignada al panel.|
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|Detiene la animación asignada al panel. .|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|Llamado por el marco de trabajo cuando se detiene la animación asignada al panel.|

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCRibbonStatusBarPane`. En el ejemplo se `CMFCRibbonStatusBarPane` muestra cómo construir un objeto, establecer la alineación de texto de la etiqueta del panel de la barra de estado, definir el texto más largo que se puede mostrar en el panel de la barra de estado sin truncamiento, adjuntar al panel de la barra de estado una lista de imágenes que se puede utilizar para la animación e iniciar la animación.

[!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribbonstatusbarpane.h

## <a name="cmfcribbonstatusbarpanecmfcribbonstatusbarpane"></a><a name="cmfcribbonstatusbarpane"></a>CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane

Construya un objeto de panel en la barra de estado.

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

*nCmdID*<br/>
[en] Especifica el identificador de comando del panel.

*lpszText*<br/>
[en] Especifica la cadena de texto que se mostrará en el panel.

*bIsStatic*<br/>
[en] Si es TRUE, el panel de estado no se puede resaltar ni seleccionar haciendo clic en él.

*hIcon*<br/>
[en] Especifica un identificador de un icono que se mostrará en el panel.

*lpszAlmostLargeText*<br/>
[en] Especifica la cadena de texto más larga que puede mostrar el panel.

*hBmpAnimationList*<br/>
[en] Especifica un identificador de una lista de imágenes que se utiliza para la animación.

*cxAnimation*<br/>
[en] Especifica el ancho, en píxeles, del icono de la lista de imágenes que se utiliza para la animación.

*clrTrnsp*<br/>
[en] Especifica el color transparente de las imágenes de la lista de imágenes que se utilizan para la animación.

*uiAnimationListResID*<br/>
[en] Especifica un identificador de recurso de una lista de imágenes que se utiliza para la animación.

## <a name="cmfcribbonstatusbarpanegetalmostlargetext"></a><a name="getalmostlargetext"></a>CMFCRibbonStatusBarPane::GetAlmostLargeText

Obtiene la cadena de texto más larga que puede mostrar el panel de la barra de estado.

```
LPCTSTR GetAlmostLargeText() const;
```

### <a name="return-value"></a>Valor devuelto

La cadena de texto más larga que puede mostrar el panel de la barra de estado.

## <a name="cmfcribbonstatusbarpanegettextalign"></a><a name="gettextalign"></a>CMFCRibbonStatusBarPane::GetTextAlign

Obtiene la configuración actual de la alineación de texto de la etiqueta del panel de la barra de estado.

```
int GetTextAlign() const;
```

### <a name="return-value"></a>Valor devuelto

Alineación de texto actual que puede ser una de las siguientes:

- TA_LEFT

- TA_CENTER

- TA_RIGHT.

## <a name="cmfcribbonstatusbarpaneisanimation"></a><a name="isanimation"></a>CMFCRibbonStatusBarPane::IsAnimation

Determina si la animación está en curso.

```
BOOL IsAnimation() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi la animación está en curso; FALSE en caso contrario.

## <a name="cmfcribbonstatusbarpaneisextended"></a><a name="isextended"></a>CMFCRibbonStatusBarPane::IsExtended

Determine si el panel se encuentra en el área extendida de la barra de estado de la cinta de opciones.

```
BOOL IsExtended() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el panel está en el área extendida de la barra de estado. FALSE en caso contrario.

## <a name="cmfcribbonstatusbarpaneondrawborder"></a><a name="ondrawborder"></a>CMFCRibbonStatusBarPane::OnDrawBorder

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
virtual void OnDrawBorder(CDC*);
```

### <a name="parameters"></a>Parámetros

[en] *CDC&#42;*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonstatusbarpaneonfillbackground"></a><a name="onfillbackground"></a>CMFCRibbonStatusBarPane::OnFillBackground

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
virtual COLORREF OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonstatusbarpaneonfinishanimation"></a><a name="onfinishanimation"></a>CMFCRibbonStatusBarPane::OnFinishAnimation

Framework llama a este método cuando finaliza la animación asignada al panel.

```
virtual void OnFinishAnimation();
```

### <a name="remarks"></a>Observaciones

`StopAnimation`método llama `OnFinishAnimation` al método, que puede usar para limpiar los datos cuando finaliza la animación.

## <a name="cmfcribbonstatusbarpanesetalmostlargetext"></a><a name="setalmostlargetext"></a>CMFCRibbonStatusBarPane::SetAlmostLargeText

Defina el texto más largo que se puede mostrar en el panel de la barra de estado sin truncamiento.

```
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```

### <a name="parameters"></a>Parámetros

*lpszAlmostLargeText*<br/>
[en] Especifica la cadena más larga que se puede mostrar en el panel de la barra de estado sin truncamiento.

### <a name="remarks"></a>Observaciones

La biblioteca calcula el tamaño del texto que *lpszAlmostLargeText* especifica y cambia el tamaño del panel en consecuencia. El texto se truncará si sigue sin encajar en el panel.

## <a name="cmfcribbonstatusbarpanesetanimationlist"></a><a name="setanimationlist"></a>CMFCRibbonStatusBarPane::SetAnimationList

Adjunta al panel de la barra de estado una lista de imágenes que se puede utilizar para la animación.

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

*hBmpAnimationList*<br/>
[en] Especifica un identificador de una lista de imágenes.

*cxAnimation*<br/>
[en] Especifica el ancho, en píxeles, del marco de la lista de imágenes.

*clrTransp*<br/>
[en] Especifica el color transparente de la lista de imágenes.

*uiAnimationListResID*<br/>
[en] Especifica el identificador de recurso de la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

TRUESi la lista de imágenes se adjunta correctamente al panel de la barra de estado; FALSE en caso contrario.

## <a name="cmfcribbonstatusbarpanesettextalign"></a><a name="settextalign"></a>CMFCRibbonStatusBarPane::SetTextAlign

Establece la alineación de texto de la etiqueta del panel de la barra de estado.

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Parámetros

*nAlinear*<br/>
[en] Especifica la alineación del texto.

### <a name="remarks"></a>Observaciones

*nAlign* puede tener uno de los siguientes valores:

- TA_LEFT: alineación izquierda

- TA_CENTER: alineación central

- TA_RIGHT: alineación derecha

## <a name="cmfcribbonstatusbarpanestartanimation"></a><a name="startanimation"></a>CMFCRibbonStatusBarPane::StartAnimation

Inicia la animación que se asigna al panel.

```
void StartAnimation(
    UINT nFrameDelay=500,
    UINT nDuration=-1);
```

### <a name="parameters"></a>Parámetros

*nFrameDelay*<br/>
[en] Especifica la velocidad de fotogramas de la animación, en milisegundos.

*nDuración*<br/>
[en] Especifica cuánto tiempo se reproducirá la animación, en milisegundos. Utilice -1 para un bucle infinito.

### <a name="remarks"></a>Observaciones

Debe especificar un identificador para una `StartAnimation` lista `SetAnimationList`de imágenes antes de llamar mediante .

## <a name="cmfcribbonstatusbarpanestopanimation"></a><a name="stopanimation"></a>CMFCRibbonStatusBarPane::StopAnimation

Detiene la animación que asignó al panel de la barra de estado.

```
void StopAnimation();
```

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton (clase)](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonStatusBar (clase)](../../mfc/reference/cmfcribbonstatusbar-class.md)
