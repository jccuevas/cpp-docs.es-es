---
title: CMFCColorDialog (clase)
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
ms.openlocfilehash: 1b9f57e46d5ac74dd52f7ddb7ebd90f8888891e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403742"
---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog (clase)

La `CMFCColorDialog` clase representa un cuadro de diálogo de selección de color.

## <a name="syntax"></a>Sintaxis

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|Construye un objeto `CMFCColorDialog`.|
|`CMFCColorDialog::~CMFCColorDialog`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCColorDialog::GetColor](#getcolor)|Devuelve el color seleccionado actual.|
|[CMFCColorDialog::GetPalette](#getpalette)|Devuelve la paleta de colores.|
|`CMFCColorDialog::PreTranslateMessage`|Traduce los mensajes de ventana antes de enviarlos a la [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funciones de Windows. Para obtener más información y la sintaxis, vea [CWnd:: PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Invalida `CDialogEx::PreTranslateMessage`).|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Deriva una paleta de la paleta del sistema.|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Establece el color seleccionado actual.|
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Establece el color más equivalente a un valor RGB especificado.|
|[CMFCColorDialog::SetPageOne](#setpageone)|Selecciona un valor RGB para la primera página de propiedades.|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Selecciona un valor RGB para la segunda página de propiedades.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Name|Descripción|
|----------|-----------------|
|`m_bIsMyPalette`|TRUE si el cuadro de diálogo de selección de color utiliza su propia paleta de colores, o FALSE si el cuadro de diálogo utiliza una paleta que se especifica en el `CMFCColorDialog` constructor.|
|`m_bPickerMode`|TRUE cuando el usuario está seleccionando un color en el cuadro de diálogo de selección; en caso contrario, FALSE.|
|`m_btnColorSelect`|El botón de color seleccionado por el usuario.|
|`m_CurrentColor`|El color seleccionado actualmente.|
|`m_hcurPicker`|El cursor que se utiliza para elegir un color.|
|`m_NewColor`|Color seleccionado potencial, que se puede activar permanentemente o se puede revertir al color original.|
|`m_pColourSheetOne`|Un puntero a la primera página de propiedades de la hoja de propiedades de la selección de color.|
|`m_pColourSheetTwo`|Un puntero a la segunda página de propiedades de la hoja de propiedades de la selección de color.|
|`m_pPalette`|La paleta lógica actual.|
|`m_pPropSheet`|Un puntero a la hoja de propiedades para el cuadro de diálogo de selección de color.|
|`m_wndColors`|Un objeto de control de selector de color.|
|`m_wndStaticPlaceHolder`|Un control estático que es un marcador de posición para la hoja de propiedades de selector de color.|

## <a name="remarks"></a>Comentarios

El cuadro de diálogo de selección de color se muestra como una hoja de propiedades con dos páginas. En la primera página, seleccione un color estándar desde la paleta del sistema; en la segunda página, seleccione un color personalizado.

Puede construir un `CMFCColorDialog` en la pila de objetos y, a continuación, llame a `DoModal`, pasando el color inicial como un parámetro a la `CMFCColorDialog` constructor. El cuadro de diálogo de selección de color, a continuación, crea varias [CMFCColorPickerCtrl (clase)](../../mfc/reference/cmfccolorpickerctrl-class.md) objetos para procesar cada paleta de colores.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo configurar un cuadro de diálogo color mediante distintos métodos en el `CMFCColorDialog` clase. El ejemplo muestra cómo establecer el actual y los nuevos colores del cuadro de diálogo y cómo se establecen los componentes rojos, verde y azules de un color seleccionado en las páginas de dos propiedades del cuadro de diálogo color. Este ejemplo forma parte de la [ejemplo de controles nuevos](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcolordialog.h

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
[in] La selección de color predeterminado. Si se especifica ningún valor, el valor predeterminado es RGB(0,0,0) (negro).

*dwFlags*<br/>
[in] Reservado.

*pParentWnd*<br/>
[in] Un puntero a la ventana de principal o propietaria del cuadro de diálogo.

*hPal*<br/>
[in] Identificador de una paleta de colores.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getcolor"></a>  CMFCColorDialog::GetColor

Recupera el color que el usuario selecciona en el cuadro de diálogo color.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un [COLORREF](/windows/desktop/gdi/colorref) valor que contiene la información de RGB del color seleccionado en el cuadro de diálogo color.

### <a name="remarks"></a>Comentarios

Llame a esta función después de llamar a la `DoModal` método.

##  <a name="getpalette"></a>  CMFCColorDialog::GetPalette

Recupera la paleta de colores que está disponible en el cuadro de diálogo color actual.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la `CPalette` objeto que se especificó en el `CMFCColorDialog` constructor.

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
[in] Un valor de color RGB

### <a name="remarks"></a>Comentarios

##  <a name="setnewcolor"></a>  CMFCColorDialog::SetNewColor

Establece el color actual en el color de la paleta actual que es más similar.

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>Parámetros

*rgb*<br/>
[in] Un [COLORREF](/windows/desktop/gdi/colorref) que especifica un color RGB.

### <a name="remarks"></a>Comentarios

##  <a name="setpageone"></a>  CMFCColorDialog::SetPageOne

Especifica explícitamente los componentes rojos, verde y azules de un color seleccionado en la primera página de propiedades de un cuadro de diálogo color.

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parámetros

*R*<br/>
[in] Especifica el componente rojo del valor RGB.

*G*<br/>
[in] Especifica el componente verde del valor RGB.

*B*<br/>
[in] Especifica el componente azul del valor RGB.

### <a name="remarks"></a>Comentarios

##  <a name="setpagetwo"></a>  CMFCColorDialog::SetPageTwo

Especifica explícitamente los componentes rojos, verde y azules de un color seleccionado en la segunda página de propiedades de un cuadro de diálogo color.

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parámetros

*R*<br/>
[in] Especifica un componente rojo del valor RGB

*G*<br/>
[in] Especifica un componente verde de un valor RGB

*B*<br/>
[in] Especifica un componente azul de un valor RGB

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorPickerCtrl (clase)](../../mfc/reference/cmfccolorpickerctrl-class.md)
