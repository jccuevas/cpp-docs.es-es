---
title: CColorDialog (clase)
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
ms.openlocfilehash: bc9bc76b328359d4c8ec7796de7dfaa7d3a9cf2c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207730"
---
# <a name="ccolordialog-class"></a>CColorDialog (clase)

Permite incorporar un cuadro de diálogo de selección de color en la aplicación.

## <a name="syntax"></a>Sintaxis

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CColorDialog::CColorDialog](#ccolordialog)|Construye un objeto `CColorDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CColorDialog::DoModal](#domodal)|Muestra un cuadro de diálogo color y permite al usuario realizar una selección.|
|[CColorDialog::GetColor](#getcolor)|Devuelve un `COLORREF` estructura que contiene los valores del color seleccionado.|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Recupera los colores personalizados creados por el usuario.|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Fuerza la selección de color actual en el color especificado.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CColorDialog::OnColorOK](#oncolorok)|Reemplace este valor para validar el color especificado en el cuadro de diálogo.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CColorDialog::m_cc](#m_cc)|Una estructura que se utiliza para personalizar la configuración del cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

Un `CColorDialog` objeto es un cuadro de diálogo con una lista de colores que se definen para el sistema de presentación. El usuario puede seleccionar o crear un color determinado en la lista, que es, a continuación, informar a la aplicación cuando se cierra el cuadro de diálogo.

Para construir un `CColorDialog` de objeto, utilice el constructor proporcionado o derivar una clase nueva y usar su propio constructor personalizado.

Una vez que se ha construido el cuadro de diálogo, puede establecer o modificar los valores de la [m_cc](#m_cc) estructura para inicializar los valores de los controles del cuadro de diálogo. El *m_cc* estructura es de tipo [CHOOSECOLOR](/windows/desktop/api/commdlg/ns-commdlg-tagchoosecolora).

Después de inicializar los controles del cuadro de diálogo, llame a la `DoModal` la función miembro para mostrar el cuadro de diálogo y permitir al usuario seleccionar un color. `DoModal` Devuelve la selección del usuario del botón de Aceptar (IDOK) o Cancelar (IDCANCEL) del cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede usar uno de `CColorDialog`de las funciones miembro para recuperar la información de entrada por el usuario.

Puede usar el Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) función para determinar si se produjo un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error.

`CColorDialog` se basa en el COMMDLG. Archivo DLL que se incluye con las versiones 3.1 y posteriores de Windows.

Para personalizar el cuadro de diálogo, derive una clase de `CColorDialog`, proporcione una plantilla de cuadro de diálogo personalizado y agregar un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Los mensajes no procesados se deben pasar a la clase base.

Personalización de la función de enlace no es necesario.

> [!NOTE]
>  En algunas instalaciones la `CColorDialog` objeto no se mostrará con un fondo gris si ha utilizado el marco de trabajo que para hacer otras `CDialog` gris de objetos.

Para obtener más información sobre el uso de `CColorDialog`, consulte [clases de cuadro de diálogo comunes](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

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
La selección de color predeterminado. Si se especifica ningún valor, el valor predeterminado es RGB(0,0,0) (negro).

*dwFlags*<br/>
Un conjunto de marcadores que personalizan la función y la apariencia del cuadro de diálogo. Para obtener más información, consulte el [CHOOSECOLOR](/windows/desktop/api/commdlg/ns-commdlg-tagchoosecolora) estructura en el SDK de Windows.

*pParentWnd*<br/>
Un puntero a la ventana de principal o propietaria del cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

##  <a name="domodal"></a>  CColorDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo color común de Windows y permitir al usuario seleccionar un color.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL. Si se devuelve IDCANCEL, llame a la Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) función para determinar si se produjo un error.

IDOK e IDCANCEL son las constantes que indican si el usuario seleccionó el botón Aceptar o Cancelar.

### <a name="remarks"></a>Comentarios

Si desea inicializar las distintas opciones del cuadro de diálogo color estableciendo los miembros de la [m_cc](#m_cc) estructura, debe hacerlo antes de llamar a `DoModal` pero después de que se construye el objeto de cuadro de diálogo.

Después de llamar a `DoModal`, se puede llamar a otra funciones miembro para recuperar la configuración o la entrada de información por el usuario en el cuadro de diálogo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CColorDialog::CColorDialog](#ccolordialog).

##  <a name="getcolor"></a>  CColorDialog::GetColor

Llame a esta función después de llamar a `DoModal` para recuperar la información sobre el color seleccionados por el usuario.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un [COLORREF](/windows/desktop/gdi/colorref) valor que contiene la información de RGB del color seleccionado en el cuadro de diálogo color.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

##  <a name="getsavedcustomcolors"></a>  CColorDialog::GetSavedCustomColors

`CColorDialog` objetos de permiten que el usuario, además de elegir los colores, para definir un máximo de 16 colores personalizados.

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a una matriz de 16 valores de color RGB que almacena los colores personalizados creados por el usuario.

### <a name="remarks"></a>Comentarios

El `GetSavedCustomColors` función miembro proporciona acceso a estos colores. Estos colores se pueden recuperar después [DoModal](#domodal) devuelve IDOK.

Cada uno de los 16 valores RGB en la matriz devuelta se inicializa en RGB(255,255,255) (blanco). Los colores personalizados elegidos por el usuario se guardan solo entre las invocaciones de cuadro de diálogo dentro de la aplicación. Si desea guardar estos colores entre las distintas invocaciones de la aplicación, debe guardarlos en alguna otra manera, como en el código de inicialización (. Archivo INI).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

##  <a name="m_cc"></a>  CColorDialog::m_cc

Una estructura de tipo [CHOOSECOLOR](/windows/desktop/api/commdlg/ns-commdlg-tagchoosecolora), cuyos miembros almacenan las características y los valores del cuadro de diálogo.

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>Comentarios

Después de crear un `CColorDialog` objeto, puede usar *m_cc* para establecer varios aspectos del cuadro de diálogo antes de llamar a la [DoModal](#domodal) función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

##  <a name="oncolorok"></a>  CColorDialog::OnColorOK

Reemplace este valor para validar el color especificado en el cuadro de diálogo.

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si no se debe descartar el cuadro de diálogo; en caso contrario, 0 para aceptar el color que se ha especificado.

### <a name="remarks"></a>Comentarios

Reemplace esta función sólo si desea proporcionar validación personalizada del color que el usuario selecciona en el cuadro de diálogo color.

El usuario puede seleccionar un color mediante uno de los dos métodos siguientes:

- Al hacer clic en un color en la paleta de colores. Los valores RGB del color seleccionado, a continuación, se reflejan en los cuadros de edición RGB correspondientes.

- Cuadros de edición de introducir valores en el RGB

Reemplazar `OnColorOK` permite rechazar un color que el usuario escribe en un cuadro de diálogo común de color por cualquier motivo específico de la aplicación.

Normalmente, no es necesario utilizar esta función porque el marco de trabajo proporciona validación predeterminada de colores y muestra un cuadro de mensaje si se ha especificado un color no válido.

Puede llamar a [SetCurrentColor](#setcurrentcolor) desde `OnColorOK` para forzar una selección de color. Una vez `OnColorOK` se ha desencadenado (es decir, el usuario hace clic **Aceptar** para aceptar el cambio de color), puede llamar a [GetColor](#getcolor) para obtener el valor RGB del nuevo color.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

##  <a name="setcurrentcolor"></a>  CColorDialog::SetCurrentColor

Llame a esta función después de llamar a `DoModal` para forzar la selección de color actual en el valor de color especificado en *clr*.

```
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>Parámetros

*clr*<br/>
Un valor de color RGB.

### <a name="remarks"></a>Comentarios

Esta función se llama desde dentro de un controlador de mensajes o `OnColorOK`. El cuadro de diálogo actualizará automáticamente la selección del usuario en función del valor de la *clr* parámetro.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CColorDialog::OnColorOK](#oncolorok).

## <a name="see-also"></a>Vea también

[Ejemplo MDI de MFC](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog (clase)](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
