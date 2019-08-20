---
title: Clase CColorDialog
ms.date: 11/04/2016
f1_keywords:
- CColorDialog
- AFXDLGS/CColorDialog
- AFXDLGS/CColorDialog::CColorDialog
- AFXDLGS/CColorDialog::DoModal
- AFXDLGS/CColorDialog::GetColor
- AFXDLGS/CColorDialog::GetSavedCustomColors
- AFXDLGS/CColorDialog::SetCurrentColor
- AFXDLGS/CColorDialog::OnColorOK
- AFXDLGS/CColorDialog::m_cc
helpviewer_keywords:
- CColorDialog [MFC], CColorDialog
- CColorDialog [MFC], DoModal
- CColorDialog [MFC], GetColor
- CColorDialog [MFC], GetSavedCustomColors
- CColorDialog [MFC], SetCurrentColor
- CColorDialog [MFC], OnColorOK
- CColorDialog [MFC], m_cc
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
ms.openlocfilehash: 3031b1e5870dd7f59af7adf48a6a77aaccdf53fc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507200"
---
# <a name="ccolordialog-class"></a>Clase CColorDialog

Permite incorporar un cuadro de diálogo de selección de color en la aplicación.

## <a name="syntax"></a>Sintaxis

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CColorDialog::CColorDialog](#ccolordialog)|Construye un objeto `CColorDialog`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CColorDialog::DoModal](#domodal)|Muestra un cuadro de diálogo de color y permite al usuario realizar una selección.|
|[CColorDialog::GetColor](#getcolor)|Devuelve una `COLORREF` estructura que contiene los valores del color seleccionado.|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Recupera los colores personalizados creados por el usuario.|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Fuerza la selección del color actual al color especificado.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CColorDialog::OnColorOK](#oncolorok)|Invalide para validar el color especificado en el cuadro de diálogo.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CColorDialog::m_cc](#m_cc)|Estructura utilizada para personalizar la configuración del cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

Un `CColorDialog` objeto es un cuadro de diálogo con una lista de colores definidos para el sistema de pantalla. El usuario puede seleccionar o crear un color determinado en la lista, que se devolverá a la aplicación cuando se cierre el cuadro de diálogo.

Para construir un `CColorDialog` objeto, use el constructor proporcionado o derive una nueva clase y use su propio constructor personalizado.

Una vez que se ha construido el cuadro de diálogo, puede establecer o modificar los valores de la estructura [m_cc](#m_cc) para inicializar los valores de los controles del cuadro de diálogo. La estructura *m_cc* es de tipo [las choosecolor](/windows/win32/api/commdlg/ns-commdlg-choosecolorw).

Después de inicializar los controles del cuadro de diálogo `DoModal` , llame a la función miembro para mostrar el cuadro de diálogo y permitir que el usuario seleccione un color. `DoModal`Devuelve la selección del usuario del botón Aceptar (IDOK) o cancelar (IDCANCEL) del cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede usar una de las `CColorDialog`funciones miembro de para recuperar la información introducida por el usuario.

Puede usar la función [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows para determinar si se ha producido un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error.

`CColorDialog`se basa en el COMMDLG. Archivo DLL que se incluye con las versiones 3,1 y posteriores de Windows.

Para personalizar el cuadro de diálogo, derive una clase `CColorDialog`de, proporcione una plantilla de cuadro de diálogo personalizada y agregue un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Los mensajes no procesados se deben pasar a la clase base.

No es necesaria la personalización de la función de enlace.

> [!NOTE]
>  En algunas instalaciones, `CColorDialog` el objeto no se mostrará con un fondo gris si ha usado el marco para que otros `CDialog` objetos estén atenuados.

Para obtener más información sobre `CColorDialog`el uso de, vea [clases de cuadro de diálogo comunes](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs. h

##  <a name="ccolordialog"></a>  CColorDialog::CColorDialog

Construye un objeto `CColorDialog`.

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*clrInit*<br/>
Selección de color predeterminada. Si no se especifica ningún valor, el valor predeterminado es RGB (0,0) (negro).

*dwFlags*<br/>
Un conjunto de marcas que personalizan la función y la apariencia del cuadro de diálogo. Para obtener más información, vea la estructura [las choosecolor.](/windows/win32/api/commdlg/ns-commdlg-choosecolorw) en el Windows SDK.

*pParentWnd*<br/>
Puntero a la ventana primaria o propietaria del cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

##  <a name="domodal"></a>  CColorDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo de color común de Windows y permitir que el usuario seleccione un color.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL. Si se devuelve IDCANCEL, llame a la función [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows para determinar si se ha producido un error.

IDOK y IDCANCEL son constantes que indican si el usuario seleccionó el botón Aceptar o cancelar.

### <a name="remarks"></a>Comentarios

Si desea inicializar las diversas opciones del cuadro de diálogo de color estableciendo los miembros de la estructura [m_cc](#m_cc) , debe hacerlo antes de llamar `DoModal` a pero después de que se construya el objeto de cuadro de diálogo.

Después de `DoModal`llamar a, puede llamar a otras funciones miembro para recuperar la información de configuración o la entrada del usuario en el cuadro de diálogo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CColorDialog:: CColorDialog](#ccolordialog).

##  <a name="getcolor"></a>  CColorDialog::GetColor

Llame a esta función después `DoModal` de llamar a para recuperar la información sobre el color seleccionado por el usuario.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de [COLORREF](/windows/win32/gdi/colorref) que contiene la información de RGB para el color seleccionado en el cuadro de diálogo de color.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

##  <a name="getsavedcustomcolors"></a>  CColorDialog::GetSavedCustomColors

`CColorDialog`los objetos permiten al usuario, además de elegir los colores, definir hasta 16 colores personalizados.

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una matriz de 16 valores de color RGB que almacena los colores personalizados creados por el usuario.

### <a name="remarks"></a>Comentarios

La `GetSavedCustomColors` función miembro proporciona acceso a estos colores. Estos colores se pueden recuperar después de que [DoModal](#domodal) devuelva IDOK.

Cada uno de los 16 valores RGB de la matriz devuelta se inicializa en RGB (255255255) (blanco). Los colores personalizados elegidos por el usuario solo se guardan entre las invocaciones del cuadro de diálogo dentro de la aplicación. Si desea guardar estos colores entre las invocaciones de la aplicación, debe guardarlos de otra manera, por ejemplo, en una inicialización (. INI).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

##  <a name="m_cc"></a>  CColorDialog::m_cc

Estructura de tipo [las choosecolor.](/windows/win32/api/commdlg/ns-commdlg-choosecolorw), cuyos miembros almacenan las características y los valores del cuadro de diálogo.

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>Comentarios

Después de construir un `CColorDialog` objeto, puede usar *m_cc* para establecer distintos aspectos del cuadro de diálogo antes de llamar a la función miembro [DoModal](#domodal) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

##  <a name="oncolorok"></a>  CColorDialog::OnColorOK

Invalide para validar el color especificado en el cuadro de diálogo.

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el cuadro de diálogo no se debe descartar; de lo contrario, 0 para aceptar el color que se especificó.

### <a name="remarks"></a>Comentarios

Invalide esta función solo si desea proporcionar una validación personalizada del color que el usuario selecciona en el cuadro de diálogo color.

El usuario puede seleccionar un color mediante uno de los dos métodos siguientes:

- Hacer clic en un color de la paleta de colores. Los valores RGB del color seleccionado se reflejan en los cuadros de edición RGB correspondientes.

- Escribir valores en los cuadros de edición RGB

La invalidación `OnColorOK` le permite rechazar un color que el usuario escribe en un cuadro de diálogo de color común para cualquier motivo específico de la aplicación.

Normalmente, no es necesario usar esta función porque el marco de trabajo proporciona la validación predeterminada de los colores y muestra un cuadro de mensaje si se escribe un color no válido.

Puede llamar a [SetCurrentColor](#setcurrentcolor) desde dentro `OnColorOK` de para forzar una selección de color. Una `OnColorOK` vez que se ha desencadenado (es decir, el usuario hace clic en **Aceptar** para aceptar el cambio de color), puede llamar a [GetColor](#getcolor) para obtener el valor RGB del nuevo color.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

##  <a name="setcurrentcolor"></a>  CColorDialog::SetCurrentColor

Llame a esta función después `DoModal` de llamar a para forzar la selección de color actual al valor de color especificado en *CLR*.

```
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>Parámetros

*clr*<br/>
Valor de color RGB.

### <a name="remarks"></a>Comentarios

Esta función se llama desde dentro de un controlador de `OnColorOK`mensajes o. El cuadro de diálogo actualizará automáticamente la selección del usuario en función del valor del parámetro *CLR* .

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CColorDialog:: OnColorOK](#oncolorok).

## <a name="see-also"></a>Vea también

[Ejemplo de MDI de MFC](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog (clase)](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
