---
title: Clase CMFCColorDialog
ms.date: 11/04/2016
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
helpviewer_keywords:
- CMFCColorDialog [MFC], CMFCColorDialog
- CMFCColorDialog [MFC], GetColor
- CMFCColorDialog [MFC], GetPalette
- CMFCColorDialog [MFC], RebuildPalette
- CMFCColorDialog [MFC], SetCurrentColor
- CMFCColorDialog [MFC], SetNewColor
- CMFCColorDialog [MFC], SetPageOne
- CMFCColorDialog [MFC], SetPageTwo
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
ms.openlocfilehash: 9e018c122cded09e5366c3b349525fa7cc004897
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505339"
---
# <a name="cmfccolordialog-class"></a>Clase CMFCColorDialog

La `CMFCColorDialog` clase representa un cuadro de diálogo de selección de color.

## <a name="syntax"></a>Sintaxis

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|Construye un objeto `CMFCColorDialog`.|
|`CMFCColorDialog::~CMFCColorDialog`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCColorDialog::GetColor](#getcolor)|Devuelve el color seleccionado actualmente.|
|[CMFCColorDialog::GetPalette](#getpalette)|Devuelve la paleta del color.|
|`CMFCColorDialog::PreTranslateMessage`|Traduce los mensajes de ventana antes de que se envíen a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . Para ver la sintaxis y obtener más información, vea [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Invalida `CDialogEx::PreTranslateMessage`).|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Deriva una paleta de la paleta del sistema.|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Establece el color seleccionado actualmente.|
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Establece el color más equivalente a un valor RGB especificado.|
|[CMFCColorDialog::SetPageOne](#setpageone)|Selecciona un valor RGB para la primera página de propiedades.|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Selecciona un valor RGB para la segunda página de propiedades.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`m_bIsMyPalette`|True si el cuadro de diálogo de selección de color utiliza su propia paleta de colores, o false si el cuadro de diálogo usa una paleta `CMFCColorDialog` especificada en el constructor.|
|`m_bPickerMode`|TRUE mientras el usuario selecciona un color en el cuadro de diálogo de selección; en caso contrario, FALSE.|
|`m_btnColorSelect`|Botón de color seleccionado por el usuario.|
|`m_CurrentColor`|El color seleccionado actualmente.|
|`m_hcurPicker`|Cursor que se usa para seleccionar un color.|
|`m_NewColor`|El color seleccionado, que se puede seleccionar o revertir permanentemente al color original.|
|`m_pColourSheetOne`|Puntero a la primera página de propiedades de la hoja de propiedades de selección de color.|
|`m_pColourSheetTwo`|Puntero a la segunda página de propiedades de la hoja de propiedades de selección de color.|
|`m_pPalette`|Paleta lógica actual.|
|`m_pPropSheet`|Un puntero a la hoja de propiedades para el cuadro de diálogo de selección de color.|
|`m_wndColors`|Objeto de control selector de colores.|
|`m_wndStaticPlaceHolder`|Control estático que es un marcador de posición para la hoja de propiedades del selector de colores.|

## <a name="remarks"></a>Comentarios

El cuadro de diálogo Selección de color se muestra como una hoja de propiedades con dos páginas. En la primera página, seleccione un color estándar de la paleta del sistema. en la segunda página, seleccione un color personalizado.

Puede construir un `CMFCColorDialog` objeto en la pila y, a continuación `DoModal`, llamar a, pasando el color inicial `CMFCColorDialog` como parámetro al constructor. A continuación, el cuadro de diálogo Selección de colores crea varios objetos de la [clase CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md) para controlar cada paleta de colores.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo configurar un cuadro de diálogo de color mediante el `CMFCColorDialog` uso de varios métodos en la clase. En el ejemplo se muestra cómo establecer los colores actuales y nuevos del cuadro de diálogo, y cómo establecer los componentes rojo, verde y azul de un color seleccionado en las dos páginas de propiedades del cuadro de diálogo color. Este ejemplo forma parte del [ejemplo de nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcolordialog. h

##  <a name="cmfccolordialog"></a>  CMFCColorDialog::CMFCColorDialog

Construye un objeto `CMFCColorDialog`.

```
CMFCColorDialog(
    COLORREF clrInit=0,
    DWORD dwFlags=0,
    CWnd* pParentWnd=NULL,
    HPALETTE hPal=NULL);
```

### <a name="parameters"></a>Parámetros

*clrInit*<br/>
de Selección de color predeterminada. Si no se especifica ningún valor, el valor predeterminado es RGB (0,0) (negro).

*dwFlags*<br/>
[in] Reservado.

*pParentWnd*<br/>
de Puntero a la ventana primaria o propietaria del cuadro de diálogo.

*hPal*<br/>
de Identificador de una paleta de colores.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getcolor"></a>  CMFCColorDialog::GetColor

Recupera el color que el usuario selecciona en el cuadro de diálogo de color.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de [COLORREF](/windows/win32/gdi/colorref) que contiene la información de RGB para el color seleccionado en el cuadro de diálogo de color.

### <a name="remarks"></a>Comentarios

Llame a esta función después de llamar `DoModal` al método.

##  <a name="getpalette"></a>  CMFCColorDialog::GetPalette

Recupera la paleta de colores que está disponible en el cuadro de diálogo de color actual.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al `CPalette` objeto que se especificó en el `CMFCColorDialog` constructor.

### <a name="remarks"></a>Comentarios

La paleta de colores especifica los colores que el usuario puede elegir.

##  <a name="rebuildpalette"></a>  CMFCColorDialog::RebuildPalette

Deriva una paleta de la paleta del sistema.

```
void RebuildPalette();
```

##  <a name="setcurrentcolor"></a>  CMFCColorDialog::SetCurrentColor

Establece el color actual del cuadro de diálogo.

```
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>Parámetros

*rgb*<br/>
de Un valor de color RGB

### <a name="remarks"></a>Comentarios

##  <a name="setnewcolor"></a>  CMFCColorDialog::SetNewColor

Establece el color actual en el color de la paleta actual que es más similar.

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>Parámetros

*rgb*<br/>
de [COLORREF](/windows/win32/gdi/colorref) que especifica un color RGB.

### <a name="remarks"></a>Comentarios

##  <a name="setpageone"></a>  CMFCColorDialog::SetPageOne

Especifica explícitamente los componentes rojo, verde y azul de un color seleccionado en la primera página de propiedades de un cuadro de diálogo de color.

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parámetros

*R*<br/>
de Especifica el componente rojo del valor RGB.

*G*<br/>
de Especifica el componente verde del valor RGB.

*B*<br/>
de Especifica el componente azul del valor RGB.

### <a name="remarks"></a>Comentarios

##  <a name="setpagetwo"></a>  CMFCColorDialog::SetPageTwo

Especifica explícitamente los componentes rojo, verde y azul de un color seleccionado en la segunda página de propiedades de un cuadro de diálogo de color.

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parámetros

*R*<br/>
de Especifica un componente rojo del valor RGB.

*G*<br/>
de Especifica un componente verde de un valor RGB.

*B*<br/>
de Especifica un componente azul de un valor RGB.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorPickerCtrl (clase)](../../mfc/reference/cmfccolorpickerctrl-class.md)
