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
ms.openlocfilehash: 1d4bd31d5095f572ee80f0357a2d7526482f1caa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752543"
---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog (clase)

La `CMFCColorDialog` clase representa un cuadro de diálogo de selección de color.

## <a name="syntax"></a>Sintaxis

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|Construye un objeto `CMFCColorDialog`.|
|`CMFCColorDialog::~CMFCColorDialog`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCColorDialog::GetColor](#getcolor)|Devuelve el color seleccionado actual.|
|[CMFCColorDialog::GetPalette](#getpalette)|Devuelve la paleta del color.|
|`CMFCColorDialog::PreTranslateMessage`|Traduce los mensajes de ventana antes de que se distribuyan a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Para obtener sintaxis y más información, vea [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Invalida `CDialogEx::PreTranslateMessage`).|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Deriva una paleta de la paleta del sistema.|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Establece el color seleccionado actual.|
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Establece el color más equivalente a un valor RGB especificado.|
|[CMFCColorDialog::SetPageOne](#setpageone)|Selecciona un valor RGB para la primera página de propiedades.|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Selecciona un valor RGB para la segunda página de propiedades.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|`m_bIsMyPalette`|TRUESi el cuadro de diálogo de selección de color utiliza su propia paleta de `CMFCColorDialog` colores, o FALSE si el cuadro de diálogo utiliza una paleta especificada en el constructor.|
|`m_bPickerMode`|TRUEMientras el usuario está seleccionando un color en el cuadro de diálogo de selección; de lo contrario, FALSE.|
|`m_btnColorSelect`|El botón de color que el usuario ha seleccionado.|
|`m_CurrentColor`|El color seleccionado actualmente.|
|`m_hcurPicker`|El cursor que se utiliza para elegir un color.|
|`m_NewColor`|El color seleccionado prospectivo, que se puede seleccionar o revertir permanentemente al color original.|
|`m_pColourSheetOne`|Puntero a la primera página de propiedades de la hoja de propiedades de selección de color.|
|`m_pColourSheetTwo`|Puntero a la segunda página de propiedades de la hoja de propiedades de selección de color.|
|`m_pPalette`|La paleta lógica actual.|
|`m_pPropSheet`|Puntero a la hoja de propiedades del cuadro de diálogo de selección de color.|
|`m_wndColors`|Un objeto de control de selector de color.|
|`m_wndStaticPlaceHolder`|Un control estático que es un marcador de posición para la hoja de propiedades del selector de color.|

## <a name="remarks"></a>Observaciones

El cuadro de diálogo de selección de color se muestra como una hoja de propiedades con dos páginas. En la primera página, seleccione un color estándar de la paleta del sistema; en la segunda página, seleccione un color personalizado.

Puede construir `CMFCColorDialog` un objeto en la `DoModal`pila y, a continuación, `CMFCColorDialog` llamar a , pasando el color inicial como parámetro al constructor. A continuación, el cuadro de diálogo de selección de color crea varios [CMFCColorPickerCtrl clase](../../mfc/reference/cmfccolorpickerctrl-class.md) objetos para controlar cada paleta de colores.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo configurar un `CMFCColorDialog` cuadro de diálogo de color mediante varios métodos en la clase. En el ejemplo se muestra cómo establecer los colores actualy los nuevos del cuadro de diálogo, y cómo establecer los componentes rojo, verde y azul de un color seleccionado en las dos páginas de propiedades del cuadro de diálogo de color. Este ejemplo forma parte del [ejemplo Nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcolordialog.h

## <a name="cmfccolordialogcmfccolordialog"></a><a name="cmfccolordialog"></a>CMFCColorDialog::CMFCColorDialog

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
[en] La selección de color predeterminada. Si no se especifica ningún valor, el valor predeterminado es RGB(0,0,0) (negro).

*dwFlags*<br/>
[in] Reservado.

*pParentWnd*<br/>
[en] Puntero a la ventana principal o propietaria del cuadro de diálogo.

*hPal*<br/>
[en] Un identificador de una paleta de colores.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfccolordialoggetcolor"></a><a name="getcolor"></a>CMFCColorDialog::GetColor

Recupera el color que el usuario selecciona en el cuadro de diálogo de color.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor [COLORREF](/windows/win32/gdi/colorref) que contiene la información RGB del color seleccionado en el cuadro de diálogo de color.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar al `DoModal` método.

## <a name="cmfccolordialoggetpalette"></a><a name="getpalette"></a>CMFCColorDialog::GetPalette

Recupera la paleta de colores que está disponible en el cuadro de diálogo de color actual.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al `CPalette` objeto especificado en el `CMFCColorDialog` constructor.

### <a name="remarks"></a>Observaciones

La paleta de colores especifica los colores que el usuario puede elegir.

## <a name="cmfccolordialogrebuildpalette"></a><a name="rebuildpalette"></a>CMFCColorDialog::RebuildPalette

Deriva una paleta de la paleta del sistema.

```cpp
void RebuildPalette();
```

## <a name="cmfccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor

Establece el color actual del cuadro de diálogo.

```cpp
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>Parámetros

*Rgb*<br/>
[en] Un valor de color RGB

### <a name="remarks"></a>Observaciones

## <a name="cmfccolordialogsetnewcolor"></a><a name="setnewcolor"></a>CMFCColorDialog::SetNewColor

Establece el color actual en el color de la paleta actual que sea más similar.

```cpp
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>Parámetros

*Rgb*<br/>
[en] [ColorREF](/windows/win32/gdi/colorref) que especifica un color RGB.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolordialogsetpageone"></a><a name="setpageone"></a>CMFCColorDialog::SetPageOne

Especifica explícitamente los componentes rojo, verde y azul de un color seleccionado en la primera página de propiedades de un cuadro de diálogo de color.

```cpp
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parámetros

*R*<br/>
[en] Especifica el componente rojo del valor RGB.

*G*<br/>
[en] Especifica el componente verde del valor RGB.

*B*<br/>
[en] Especifica el componente azul del valor RGB.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolordialogsetpagetwo"></a><a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo

Especifica explícitamente los componentes rojo, verde y azul de un color seleccionado en la segunda página de propiedades de un cuadro de diálogo de color.

```cpp
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parámetros

*R*<br/>
[en] Especifica un componente rojo del valor RGB

*G*<br/>
[en] Especifica un componente verde de un valor RGB

*B*<br/>
[en] Especifica un componente azul de un valor RGB

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorPickerCtrl (clase)](../../mfc/reference/cmfccolorpickerctrl-class.md)
