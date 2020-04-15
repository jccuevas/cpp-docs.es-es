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
ms.openlocfilehash: ab8d934ca0c40c7073f2fc6d88549eb8db595b3f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352237"
---
# <a name="ccolordialog-class"></a>CColorDialog (clase)

Le permite incorporar un cuadro de diálogo de selección de color en la aplicación.

## <a name="syntax"></a>Sintaxis

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CColorDialog::CColorDialog](#ccolordialog)|Construye un objeto `CColorDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CColorDialog::DoModal](#domodal)|Muestra un cuadro de diálogo de color y permite al usuario realizar una selección.|
|[CColorDialog::GetColor](#getcolor)|Devuelve `COLORREF` una estructura que contiene los valores del color seleccionado.|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Recupera colores personalizados creados por el usuario.|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Fuerza la selección de color actual al color especificado.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CColorDialog::OnColorOK](#oncolorok)|Reemplazar para validar el color introducido en el cuadro de diálogo.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CColorDialog::m_cc](#m_cc)|Estructura utilizada para personalizar la configuración del cuadro de diálogo.|

## <a name="remarks"></a>Observaciones

Un `CColorDialog` objeto es un cuadro de diálogo con una lista de colores definidos para el sistema de visualización. El usuario puede seleccionar o crear un color determinado de la lista, que luego se notifica a la aplicación cuando se cierra el cuadro de diálogo.

Para construir `CColorDialog` un objeto, utilice el constructor proporcionado o derive una nueva clase y use su propio constructor personalizado.

Una vez construido el cuadro de diálogo, puede establecer o modificar cualquier valor de la [estructura m_cc](#m_cc) para inicializar los valores de los controles del cuadro de diálogo. La estructura *m_cc* es de tipo [CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1).

Después de inicializar los controles del `DoModal` cuadro de diálogo, llame a la función miembro para mostrar el cuadro de diálogo y permitir al usuario seleccionar un color. `DoModal`devuelve la selección del usuario del botón Aceptar (IDOK) o Cancelar (IDCANCEL) del cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede `CColorDialog`usar una de las funciones miembro de 's para recuperar la información introducida por el usuario.

Puede usar la función [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows para determinar si se ha producido un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error.

`CColorDialog`depende del COMMDLG. DLL que se incluye con las versiones 3.1 y posteriores de Windows.

Para personalizar el cuadro de `CColorDialog`diálogo, derive una clase de , proporcione una plantilla de cuadro de diálogo personalizada y agregue un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Los mensajes sin procesar deben pasarse a la clase base.

No es necesario personalizar la función de gancho.

> [!NOTE]
> En algunas `CColorDialog` instalaciones, el objeto no se mostrará con `CDialog` un fondo gris si ha utilizado el marco de trabajo para hacer que otros objetos sean grises.

Para obtener más `CColorDialog`información sobre el uso de , consulte [Clases de cuadro de diálogo comunes](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

## <a name="ccolordialogccolordialog"></a><a name="ccolordialog"></a>CColorDialog::CColorDialog

Construye un objeto `CColorDialog`.

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*clrInit*<br/>
La selección de color predeterminada. Si no se especifica ningún valor, el valor predeterminado es RGB(0,0,0) (negro).

*dwFlags*<br/>
Conjunto de indicadores que personalizan la función y la apariencia del cuadro de diálogo. Para obtener más información, vea la estructura [CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1) en el Windows SDK.

*pParentWnd*<br/>
Puntero a la ventana principal o propietaria del cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

## <a name="ccolordialogdomodal"></a><a name="domodal"></a>CColorDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo de color común de Windows y permitir al usuario seleccionar un color.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL. Si se devuelve IDCANCEL, llame a la función [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows para determinar si se ha producido un error.

IDOK e IDCANCEL son constantes que indican si el usuario ha seleccionado el botón Aceptar o Cancelar.

### <a name="remarks"></a>Observaciones

Si desea inicializar las distintas opciones de cuadro de diálogo de color estableciendo miembros de la [estructura m_cc,](#m_cc) debe hacerlo antes de llamar, `DoModal` pero después de que se construye el objeto de cuadro de diálogo.

Después `DoModal`de llamar a , puede llamar a otras funciones miembro para recuperar la configuración o la información introducida por el usuario en el cuadro de diálogo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CColorDialog::CColorDialog](#ccolordialog).

## <a name="ccolordialoggetcolor"></a><a name="getcolor"></a>CColorDialog::GetColor

Llame a esta `DoModal` función después de llamar para recuperar la información sobre el color seleccionado por el usuario.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor [COLORREF](/windows/win32/gdi/colorref) que contiene la información RGB del color seleccionado en el cuadro de diálogo de color.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

## <a name="ccolordialoggetsavedcustomcolors"></a><a name="getsavedcustomcolors"></a>CColorDialog::GetSavedCustomColors

`CColorDialog`los objetos permiten al usuario, además de elegir colores, definir hasta 16 colores personalizados.

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una matriz de 16 valores de color RGB que almacena colores personalizados creados por el usuario.

### <a name="remarks"></a>Observaciones

La `GetSavedCustomColors` función miembro proporciona acceso a estos colores. Estos colores se pueden recuperar después de [DoModal](#domodal) devuelve IDOK.

Cada uno de los 16 valores RGB de la matriz devuelta se inicializa en RGB(255,255,255) (blanco). Los colores personalizados elegidos por el usuario se guardan solo entre invocaciones de cuadro de diálogo dentro de la aplicación. Si desea guardar estos colores entre invocaciones de la aplicación, debe guardarlos de alguna otra manera, como en una inicialización (. INI).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

## <a name="ccolordialogm_cc"></a><a name="m_cc"></a>CColorDialog::m_cc

Estructura de tipo [CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1), cuyos miembros almacenan las características y los valores del cuadro de diálogo.

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>Observaciones

Después de `CColorDialog` construir un objeto, puede usar *m_cc* para establecer varios aspectos del cuadro de diálogo antes de llamar a la [DoModal](#domodal) función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

## <a name="ccolordialogoncolorok"></a><a name="oncolorok"></a>CColorDialog::OnColorOK

Reemplazar para validar el color introducido en el cuadro de diálogo.

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si no se debe descartar el cuadro de diálogo; de lo contrario 0 para aceptar el color que se introdujo.

### <a name="remarks"></a>Observaciones

Reemplace esta función solo si desea proporcionar una validación personalizada del color que el usuario selecciona en el cuadro de diálogo de color.

El usuario puede seleccionar un color por uno de los dos métodos siguientes:

- Haga clic en un color de la paleta de colores. Los valores RGB del color seleccionado se reflejan en los cuadros de edición RGB adecuados.

- Introducir valores en los cuadros de edición RGB

La `OnColorOK` invalidación le permite rechazar un color que el usuario introduce en un cuadro de diálogo de color común por cualquier motivo específico de la aplicación.

Normalmente, no es necesario utilizar esta función porque el marco de trabajo proporciona la validación predeterminada de colores y muestra un cuadro de mensaje si se especifica un color no válido.

Puede llamar a [SetCurrentColor](#setcurrentcolor) desde dentro `OnColorOK` para forzar una selección de color. Una `OnColorOK` vez que se ha desencadenado (es decir, el usuario hace clic en **Aceptar** para aceptar el cambio de color), puede llamar a [GetColor](#getcolor) para obtener el valor RGB del nuevo color.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

## <a name="ccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CColorDialog::SetCurrentColor

Llame a esta `DoModal` función después de llamar para forzar la selección de color actual al valor de color especificado en *clr*.

```
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>Parámetros

*Clr*<br/>
Un valor de color RGB.

### <a name="remarks"></a>Observaciones

Se llama a esta función `OnColorOK`desde un controlador de mensajes o . El cuadro de diálogo actualizará automáticamente la selección del usuario en función del valor del parámetro *clr.*

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CColorDialog::OnColorOK](#oncolorok).

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[Clase CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
