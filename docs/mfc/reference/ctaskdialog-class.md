---
title: CTaskDialog Class
ms.date: 11/19/2018
f1_keywords:
- CTaskDialog
- AFXTASKDIALOG/CTaskDialog
- AFXTASKDIALOG/CTaskDialog::CTaskDialog
- AFXTASKDIALOG/CTaskDialog::AddCommandControl
- AFXTASKDIALOG/CTaskDialog::AddRadioButton
- AFXTASKDIALOG/CTaskDialog::ClickCommandControl
- AFXTASKDIALOG/CTaskDialog::ClickRadioButton
- AFXTASKDIALOG/CTaskDialog::DoModal
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonCount
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonFlag
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonId
- AFXTASKDIALOG/CTaskDialog::GetOptions
- AFXTASKDIALOG/CTaskDialog::GetSelectedCommandControlID
- AFXTASKDIALOG/CTaskDialog::GetSelectedRadioButtonID
- AFXTASKDIALOG/CTaskDialog::GetVerificationCheckboxState
- AFXTASKDIALOG/CTaskDialog::IsCommandControlEnabled
- AFXTASKDIALOG/CTaskDialog::IsRadioButtonEnabled
- AFXTASKDIALOG/CTaskDialog::IsSupported
- AFXTASKDIALOG/CTaskDialog::LoadCommandControls
- AFXTASKDIALOG/CTaskDialog::LoadRadioButtons
- AFXTASKDIALOG/CTaskDialog::NavigateTo
- AFXTASKDIALOG/CTaskDialog::OnCommandControlClick
- AFXTASKDIALOG/CTaskDialog::OnCreate
- AFXTASKDIALOG/CTaskDialog::OnDestroy
- AFXTASKDIALOG/CTaskDialog::OnExpandButtonClick
- AFXTASKDIALOG/CTaskDialog::OnHelp
- AFXTASKDIALOG/CTaskDialog::OnHyperlinkClick
- AFXTASKDIALOG/CTaskDialog::OnInit
- AFXTASKDIALOG/CTaskDialog::OnNavigatePage
- AFXTASKDIALOG/CTaskDialog::OnRadioButtonClick
- AFXTASKDIALOG/CTaskDialog::OnTimer
- AFXTASKDIALOG/CTaskDialog::OnVerificationCheckboxClick
- AFXTASKDIALOG/CTaskDialog::RemoveAllCommandControls
- AFXTASKDIALOG/CTaskDialog::RemoveAllRadioButtons
- AFXTASKDIALOG/CTaskDialog::SetCommandControlOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtons
- AFXTASKDIALOG/CTaskDialog::SetContent
- AFXTASKDIALOG/CTaskDialog::SetDefaultCommandControl
- AFXTASKDIALOG/CTaskDialog::SetDefaultRadioButton
- AFXTASKDIALOG/CTaskDialog::SetDialogWidth
- AFXTASKDIALOG/CTaskDialog::SetExpansionArea
- AFXTASKDIALOG/CTaskDialog::SetFooterIcon
- AFXTASKDIALOG/CTaskDialog::SetFooterText
- AFXTASKDIALOG/CTaskDialog::SetMainIcon
- AFXTASKDIALOG/CTaskDialog::SetMainInstruction
- AFXTASKDIALOG/CTaskDialog::SetOptions
- AFXTASKDIALOG/CTaskDialog::SetProgressBarMarquee
- AFXTASKDIALOG/CTaskDialog::SetProgressBarPosition
- AFXTASKDIALOG/CTaskDialog::SetProgressBarRange
- AFXTASKDIALOG/CTaskDialog::SetProgressBarState
- AFXTASKDIALOG/CTaskDialog::SetRadioButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckbox
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckboxText
- AFXTASKDIALOG/CTaskDialog::SetWindowTitle
- AFXTASKDIALOG/CTaskDialog::ShowDialog
- AFXTASKDIALOG/CTaskDialog::TaskDialogCallback
helpviewer_keywords:
- CTaskDialog [MFC], CTaskDialog
- CTaskDialog [MFC], AddCommandControl
- CTaskDialog [MFC], AddRadioButton
- CTaskDialog [MFC], ClickCommandControl
- CTaskDialog [MFC], ClickRadioButton
- CTaskDialog [MFC], DoModal
- CTaskDialog [MFC], GetCommonButtonCount
- CTaskDialog [MFC], GetCommonButtonFlag
- CTaskDialog [MFC], GetCommonButtonId
- CTaskDialog [MFC], GetOptions
- CTaskDialog [MFC], GetSelectedCommandControlID
- CTaskDialog [MFC], GetSelectedRadioButtonID
- CTaskDialog [MFC], GetVerificationCheckboxState
- CTaskDialog [MFC], IsCommandControlEnabled
- CTaskDialog [MFC], IsRadioButtonEnabled
- CTaskDialog [MFC], IsSupported
- CTaskDialog [MFC], LoadCommandControls
- CTaskDialog [MFC], LoadRadioButtons
- CTaskDialog [MFC], NavigateTo
- CTaskDialog [MFC], OnCommandControlClick
- CTaskDialog [MFC], OnCreate
- CTaskDialog [MFC], OnDestroy
- CTaskDialog [MFC], OnExpandButtonClick
- CTaskDialog [MFC], OnHelp
- CTaskDialog [MFC], OnHyperlinkClick
- CTaskDialog [MFC], OnInit
- CTaskDialog [MFC], OnNavigatePage
- CTaskDialog [MFC], OnRadioButtonClick
- CTaskDialog [MFC], OnTimer
- CTaskDialog [MFC], OnVerificationCheckboxClick
- CTaskDialog [MFC], RemoveAllCommandControls
- CTaskDialog [MFC], RemoveAllRadioButtons
- CTaskDialog [MFC], SetCommandControlOptions
- CTaskDialog [MFC], SetCommonButtonOptions
- CTaskDialog [MFC], SetCommonButtons
- CTaskDialog [MFC], SetContent
- CTaskDialog [MFC], SetDefaultCommandControl
- CTaskDialog [MFC], SetDefaultRadioButton
- CTaskDialog [MFC], SetDialogWidth
- CTaskDialog [MFC], SetExpansionArea
- CTaskDialog [MFC], SetFooterIcon
- CTaskDialog [MFC], SetFooterText
- CTaskDialog [MFC], SetMainIcon
- CTaskDialog [MFC], SetMainInstruction
- CTaskDialog [MFC], SetOptions
- CTaskDialog [MFC], SetProgressBarMarquee
- CTaskDialog [MFC], SetProgressBarPosition
- CTaskDialog [MFC], SetProgressBarRange
- CTaskDialog [MFC], SetProgressBarState
- CTaskDialog [MFC], SetRadioButtonOptions
- CTaskDialog [MFC], SetVerificationCheckbox
- CTaskDialog [MFC], SetVerificationCheckboxText
- CTaskDialog [MFC], SetWindowTitle
- CTaskDialog [MFC], ShowDialog
- CTaskDialog [MFC], TaskDialogCallback
ms.assetid: 1991ec98-ae56-4483-958b-233809c8c559
ms.openlocfilehash: e2f77a2eda4397ed368e477165e876f9b8fbf936
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502343"
---
# <a name="ctaskdialog-class"></a>CTaskDialog Class

Un cuadro de diálogo emergente que funciona como un cuadro de mensaje pero que puede mostrar información adicional al usuario. `CTaskDialog` también incluye funcionalidad para recopilar información del usuario.

## <a name="syntax"></a>Sintaxis

```
class CTaskDialog : public CObject
```

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|||
|-|-|
|[CTaskDialog::CTaskDialog](#ctaskdialog)|Construye un objeto `CTaskDialog`.|

### <a name="methods"></a>Métodos

|||
|-|-|
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|Agrega un control de botón de comando `CTaskDialog`a.|
|[CTaskDialog::AddRadioButton](#addradiobutton)|Agrega un botón de radio a `CTaskDialog`la.|
|[CTaskDialog::ClickCommandControl](#clickcommandcontrol)|Hace clic en un control de botón de comando o en un botón común mediante programación.|
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|Hace clic en un botón de radio mediante programación.|
|[CTaskDialog::DoModal](#domodal)|Muestra el `CTaskDialog`.|
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|Recupera el número de botones comunes disponibles.|
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|Convierte un botón estándar de Windows en el tipo de botón común asociado a `CTaskDialog` la clase.|
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|Convierte uno de los tipos de botón comunes asociados a la `CTaskDialog` clase en un botón estándar de Windows.|
|[CTaskDialog::GetOptions](#getoptions)|Devuelve las marcas de opción para `CTaskDialog`este.|
|[CTaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|Devuelve el control de botón de comando seleccionado.|
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|Devuelve el botón de radio seleccionado.|
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|Recupera el estado de la casilla de verificación.|
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|Determina si está habilitado un control de botón de comando o un botón común.|
|[CTaskDialog::IsRadioButtonEnabled](#isradiobuttonenabled)|Determina si está habilitado un botón de radio.|
|[CTaskDialog::IsSupported](#issupported)|Determina si el equipo que ejecuta la aplicación admite `CTaskDialog`.|
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|Agrega controles de botón de comando mediante el uso de datos de la tabla de cadenas.|
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|Agrega botones de radio mediante los datos de la tabla de cadenas.|
|[CTaskDialog::NavigateTo](#navigateto)|Transfiere el foco a otro `CTaskDialog`.|
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|El marco de trabajo llama a este método cuando el usuario hace clic en un control de botón de comando.|
|[CTaskDialog::OnCreate](#oncreate)|El marco de trabajo llama a este método después `CTaskDialog`de crear el.|
|[CTaskDialog::OnDestroy](#ondestroy)|El marco de trabajo llama a este método inmediatamente antes de `CTaskDialog`que destruya el.|
|[CTaskDialog::OnExpandButtonClick](#onexpandbuttonclick)|El marco de trabajo llama a este método cuando el usuario hace clic en el botón de expansión.|
|[CTaskDialog::OnHelp](#onhelp)|El marco de trabajo llama a este método cuando el usuario solicita ayuda.|
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|El marco de trabajo llama a este método cuando el usuario hace clic en un hipervínculo.|
|[CTaskDialog::OnInit](#oninit)|El marco de trabajo llama a este `CTaskDialog` método cuando se inicializa.|
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|El marco de trabajo llama a este método cuando el usuario mueve el foco con respecto a `CTaskDialog`los controles de.|
|[CTaskDialog::OnRadioButtonClick](#onradiobuttonclick)|El marco de trabajo llama a este método cuando el usuario selecciona un control de botón de radio.|
|[CTaskDialog::OnTimer](#ontimer)|El marco de trabajo llama a este método cuando el temporizador expira.|
|[CTaskDialog::OnVerificationCheckboxClick](#onverificationcheckboxclick)|El marco de trabajo llama a este método cuando el usuario hace clic en la casilla de verificación.|
|[CTaskDialog::RemoveAllCommandControls](#removeallcommandcontrols)|Quita todos los controles de comando de `CTaskDialog`.|
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|Quita todos los botones de radio de `CTaskDialog`.|
|[CTaskDialog::SetCommandControlOptions](#setcommandcontroloptions)|Actualiza un control de botón de comando `CTaskDialog`en.|
|[CTaskDialog::SetCommonButtonOptions](#setcommonbuttonoptions)|Actualiza un subconjunto de botones comunes que se van a habilitar y requiere elevación de UAC.|
|[CTaskDialog::SetCommonButtons](#setcommonbuttons)|Agrega botones comunes al `CTaskDialog`.|
|[CTaskDialog::SetContent](#setcontent)|Actualiza el contenido de `CTaskDialog`.|
|[CTaskDialog::SetDefaultCommandControl](#setdefaultcommandcontrol)|Especifica el control de botón de comando predeterminado.|
|[CTaskDialog::SetDefaultRadioButton](#setdefaultradiobutton)|Especifica el botón de radio predeterminado.|
|[CTaskDialog::SetDialogWidth](#setdialogwidth)|Ajusta el ancho de `CTaskDialog`.|
|[CTaskDialog::SetExpansionArea](#setexpansionarea)|Actualiza el área de expansión de `CTaskDialog`.|
|[CTaskDialog::SetFooterIcon](#setfootericon)|Actualiza el icono de pie de página `CTaskDialog`del.|
|[CTaskDialog::SetFooterText](#setfootertext)|Actualiza el texto en el pie de página de `CTaskDialog`.|
|[CTaskDialog::SetMainIcon](#setmainicon)|Actualiza el icono principal de `CTaskDialog`.|
|[CTaskDialog::SetMainInstruction](#setmaininstruction)|Actualiza la instrucción principal del `CTaskDialog`.|
|[CTaskDialog::SetOptions](#setoptions)|Configura las opciones para `CTaskDialog`.|
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|Configura una barra de Marquesina para el `CTaskDialog` y lo agrega al cuadro de diálogo.|
|[CTaskDialog::SetProgressBarPosition](#setprogressbarposition)|Ajusta la posición de la barra de progreso.|
|[CTaskDialog::SetProgressBarRange](#setprogressbarrange)|Ajusta el intervalo de la barra de progreso.|
|[CTaskDialog::SetProgressBarState](#setprogressbarstate)|Establece el estado de la barra de progreso y lo muestra en `CTaskDialog`.|
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|Habilita o deshabilita un botón de radio.|
|[CTaskDialog::SetVerificationCheckbox](#setverificationcheckbox)|Establece el estado activado de la casilla de verificación.|
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|Establece el texto del lado derecho de la casilla de verificación.|
|[CTaskDialog::SetWindowTitle](#setwindowtitle)|Establece el título del `CTaskDialog`.|
|[CTaskDialog::ShowDialog](#showdialog)|Crea y muestra un `CTaskDialog`.|
|[CTaskDialog::TaskDialogCallback](#taskdialogcallback)|El marco de trabajo llama a este en respuesta a varios mensajes de Windows.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|`m_aButtons`|Matriz de controles de botón de comando para `CTaskDialog`.|
|`m_aRadioButtons`|Matriz de controles de botón de radio para `CTaskDialog`.|
|`m_bVerified`|`TRUE`indica que la casilla de verificación está activada; `FALSE` indica que no lo es.|
|`m_footerIcon`|Icono del pie de página de `CTaskDialog`.|
|`m_hWnd`|Identificador de la ventana de `CTaskDialog`.|
|`m_mainIcon`|Icono principal de `CTaskDialog`.|
|`m_nButtonDisabled`|Máscara que indica cuál de los botones comunes están deshabilitados.|
|`m_nButtonElevation`|Máscara que indica cuál de los botones comunes requiere elevación de UAC.|
|`m_nButtonId`|IDENTIFICADOR del control de botón de comando seleccionado.|
|`m_nCommonButton`|Máscara que indica qué botones comunes se muestran en `CTaskDialog`.|
|`m_nDefaultCommandControl`|Identificador del control de botón de comando que se selecciona cuando `CTaskDialog` se muestra.|
|`m_nDefaultRadioButton`|Identificador del control de botón de radio que se selecciona cuando `CTaskDialog` se muestra.|
|`m_nFlags`|Máscara que indica las opciones de `CTaskDialog`.|
|`m_nProgressPos`|La posición actual de la barra de progreso.  Dicho valor debe encontrarse entre `m_nProgressRangeMin` y `m_nProgressRangeMax`.|
|`m_nProgressRangeMax`|Valor máximo de la barra de progreso.|
|`m_nProgressRangeMin`|Valor mínimo de la barra de progreso.|
|`m_nProgressState`|Estado de la barra de progreso. Para obtener más información, vea [clase CTaskDialog:: SetProgressBarState](#setprogressbarstate).|
|`m_nRadioId`|IDENTIFICADOR del control de botón de radio seleccionado.|
|`m_nWidth`|Ancho del control `CTaskDialog`, en píxeles.|
|`m_strCollapse`|La cadena `CTaskDialog` que se muestra a la derecha del cuadro de expansión cuando se oculta la información expandida.|
|`m_strContent`|Cadena de contenido de `CTaskDialog`.|
|`m_strExpand`|La cadena `CTaskDialog` que se muestra a la derecha del cuadro de expansión cuando se muestra la información expandida.|
|`m_strFooter`|Pie de página de `CTaskDialog`.|
|`m_strInformation`|La información expandida para `CTaskDialog`.|
|`m_strMainInstruction`|Instrucción principal del `CTaskDialog`.|
|`m_strTitle`|Título del `CTaskDialog`.|
|`m_strVerification`|Cadena que `CTaskDialog` muestra a la derecha de la casilla de verificación.|

## <a name="remarks"></a>Comentarios

La `CTaskDialog` clase reemplaza el cuadro de mensaje de Windows estándar y tiene una funcionalidad adicional, como nuevos controles para recopilar información del usuario. Esta clase está en la biblioteca MFC en Visual Studio 2010 y versiones posteriores. `CTaskDialog` Está disponible a partir de Windows Vista. Las versiones anteriores de Windows no pueden `CTaskDialog` mostrar el objeto. Use `CTaskDialog::IsSupported` para determinar en tiempo de ejecución si el usuario actual puede mostrar el cuadro de diálogo de tarea. Todavía se admite el cuadro de mensaje de Windows estándar.

Solo `CTaskDialog` está disponible al compilar la aplicación mediante la biblioteca Unicode.

`CTaskDialog` Tiene dos constructores diferentes. Un constructor le permite especificar dos botones de comando y un máximo de seis controles de botón normales. Puede agregar más botones de comando después de crear el `CTaskDialog`. El segundo constructor no es compatible con los botones de comando, pero puede Agregar un número ilimitado de controles de botón normales. Para obtener más información sobre los constructores, vea [clase CTaskDialog:: clase CTaskDialog](#ctaskdialog).

La siguiente imagen muestra un ejemplo `CTaskDialog` para ilustrar la ubicación de algunos de los controles.

![Ejemplo de clase CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "Ejemplo de clase CTaskDialog") <br/>
Ejemplo de clase CTaskDialog

## <a name="requirements"></a>Requisitos

**Sistema operativo mínimo requerido:** Windows Vista

**Encabezado:** afxtaskdialog. h

##  <a name="addcommandcontrol"></a>  CTaskDialog::AddCommandControl

Agrega un nuevo control de botón de comando `CTaskDialog`a.

```
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
de El número de identificación del control de comandos.

*strCaption*<br/>
de Cadena que `CTaskDialog` muestra al usuario. Utilice esta cadena para explicar el propósito del comando.

*bEnabled*<br/>
de Un parámetro booleano que indica si el nuevo botón está habilitado o deshabilitado.

*bRequiresElevation*<br/>
de Un parámetro booleano que indica si un comando requiere elevación.

### <a name="remarks"></a>Comentarios

`CTaskDialog Class` Puede mostrar un número ilimitado de controles de botón de comando. Sin embargo, si `CTaskDialog` muestra un control de botón de comando, puede mostrar un máximo de seis botones. Si no `CTaskDialog` tiene controles de botón de comando, puede mostrar un número ilimitado de botones.

Cuando el usuario selecciona un control de botón de comando `CTaskDialog` , se cierra. Si la aplicación muestra el cuadro de diálogo mediante [clase CTaskDialog::D omodal](#domodal), `DoModal` devuelve el *nCommandControlID* del control de botón de comando seleccionado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="addradiobutton"></a>  CTaskDialog::AddRadioButton

Agrega un botón de radio a `CTaskDialog`la.

```
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
de Número de identificación del botón de radio.

*strCaption*<br/>
de La cadena que `CTaskDialog` muestra junto al botón de radio.

*bEnabled*<br/>
de Un parámetro booleano que indica si está habilitado el botón de radio.

### <a name="remarks"></a>Comentarios

Los botones de radio de la [clase clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md) permiten recopilar información del usuario. Use la función [clase CTaskDialog:: GetSelectedRadioButtonID](#getselectedradiobuttonid) para determinar qué botón de radio está seleccionado.

No requiere que los parámetros nRadioButtonID sean únicos para cada botón de radio. `CTaskDialog` Sin embargo, puede experimentar un comportamiento inesperado si no usa un identificador distinto para cada botón de radio.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="clickcommandcontrol"></a>  CTaskDialog::ClickCommandControl

Hace clic en un control de botón de comando o en un botón común mediante programación.

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
de IDENTIFICADOR de comando del control en el que se va a hacer clic.

### <a name="remarks"></a>Comentarios

Este método genera el mensaje de Windows TDM_CLICK_BUTTON.

##  <a name="clickradiobutton"></a>  CTaskDialog::ClickRadioButton

Hace clic en un botón de radio mediante programación.

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
de IDENTIFICADOR del botón de radio en el que se va a hacer clic.

### <a name="remarks"></a>Comentarios

Este método genera el mensaje de Windows TDM_CLICK_RADIO_BUTTON.

##  <a name="ctaskdialog"></a>  CTaskDialog::CTaskDialog

Crea una instancia de la [clase clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

```
CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nCommonButtons = TDCBF_OK_BUTTON | TDCBF_CANCEL_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));

CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>Parámetros

*strContent*<br/>
de Cadena que se va a usar para el contenido `CTaskDialog`de.

*strMainInstruction*<br/>
de Instrucción principal del `CTaskDialog`.

*strTitle*<br/>
de Título del `CTaskDialog`.

*nCommonButtons*<br/>
de Máscara de los botones comunes que se van a agregar `CTaskDialog`a.

*nTaskDialogOptions*<br/>
de Conjunto de opciones que se va a usar `CTaskDialog`para.

*strFooter*<br/>
de Cadena que se va a usar como pie de página.

*nIDCommandControlsFirst*<br/>
de IDENTIFICADOR de cadena del primer comando.

*nIDCommandControlsLast*<br/>
de IDENTIFICADOR de cadena del último comando.

### <a name="remarks"></a>Comentarios

Hay dos maneras de agregar un `CTaskDialog` a la aplicación. La primera forma es usar uno de los constructores para crear `CTaskDialog` y mostrarlo mediante [clase CTaskDialog::D omodal](#domodal). La segunda manera es usar la función estática [clase CTaskDialog:: ShowDialog](#showdialog), que permite mostrar un `CTaskDialog` sin crear explícitamente un `CTaskDialog` objeto.

El segundo constructor crea controles de botón de comando mediante datos del archivo de recursos de la aplicación. La tabla de cadenas del archivo de recursos tiene varias cadenas con identificadores de cadena asociados. Este método agrega un control de botón de comando para cada entrada válida de la tabla de cadenas entre *nIDCommandControlsFirst* y *nCommandControlsLast*, ambos incluidos. Para estos controles de botón de comando, la cadena de la tabla de cadenas es el título del control y el identificador de cadena es el identificador del control.

Vea [clase CTaskDialog:: SetOptions](#setoptions) para obtener una lista de opciones válidas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="domodal"></a>  CTaskDialog::DoModal

Muestra el `CTaskDialog` y lo convierte en modal.

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parámetros

*hParent*<br/>
de Ventana primaria para el `CTaskDialog`objeto.

### <a name="return-value"></a>Valor devuelto

Entero que corresponde a la selección realizada por el usuario.

### <a name="remarks"></a>Comentarios

Muestra esta instancia de [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md). A continuación, la aplicación espera a que el usuario cierre el cuadro de diálogo.

Se cierra cuando el usuario selecciona un botón común, un control de vínculo de comando o cierra `CTaskDialog`. `CTaskDialog` El valor devuelto es el identificador que indica cómo el usuario cerró el cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="getcommonbuttoncount"></a>  CTaskDialog::GetCommonButtonCount

Recupera el número de botones comunes.

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de botones comunes disponibles.

### <a name="remarks"></a>Comentarios

Los botones comunes son los botones predeterminados que se proporcionan a [clase CTaskDialog:: clase CTaskDialog](#ctaskdialog). La [clase clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md) muestra los botones situados en la parte inferior del cuadro de diálogo.

La lista enumerada de botones se proporciona en CommCtrl. h.

##  <a name="getcommonbuttonflag"></a>  CTaskDialog::GetCommonButtonFlag

Convierte un botón estándar de Windows en el tipo de botón común asociado a la [clase clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>Parámetros

*nButtonId*<br/>
de Valor del botón estándar de Windows.

### <a name="return-value"></a>Valor devuelto

Valor del botón común correspondiente `CTaskDialog` . Si no hay ningún botón común correspondiente, este método devuelve 0.

##  <a name="getcommonbuttonid"></a>  CTaskDialog::GetCommonButtonId

Convierte uno de los tipos de botón comunes asociados a la [clase clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md) en un botón estándar de Windows.

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>Parámetros

*nFlag*<br/>
de El tipo de botón común asociado a `CTaskDialog` la clase.

### <a name="return-value"></a>Valor devuelto

Valor del botón estándar de Windows correspondiente. Si no hay ningún botón de Windows correspondiente, el método devuelve 0.

##  <a name="getoptions"></a>  CTaskDialog::GetOptions

Devuelve las marcas de opción para `CTaskDialog`este.

```
int GetOptions() const;
```

### <a name="return-value"></a>Valor devuelto

Marcas para `CTaskDialog`.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre las opciones disponibles para la [clase clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md), vea [clase CTaskDialog:: SetOptions](#setoptions).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="getselectedcommandcontrolid"></a>  CTaskDialog::GetSelectedCommandControlID

Devuelve el control de botón de comando seleccionado.

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>Valor devuelto

IDENTIFICADOR del control de botón de comando seleccionado actualmente.

### <a name="remarks"></a>Comentarios

No es necesario utilizar este método para recuperar el identificador del botón de comando que el usuario seleccionó. Este identificador se devuelve por [clase CTaskDialog::D omodal](#domodal) o [clase CTaskDialog:: ShowDialog](#showdialog).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="getselectedradiobuttonid"></a>  CTaskDialog::GetSelectedRadioButtonID

Devuelve el botón de radio seleccionado.

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>Valor devuelto

IDENTIFICADOR del botón de radio seleccionado.

### <a name="remarks"></a>Comentarios

Puede usar este método después de que el usuario cierre el cuadro de diálogo para recuperar el botón de radio seleccionado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="getverificationcheckboxstate"></a>  CTaskDialog::GetVerificationCheckboxState

Recupera el estado de la casilla de verificación.

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si la casilla está activada, FALSE en caso contrario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="iscommandcontrolenabled"></a>  CTaskDialog::IsCommandControlEnabled

Determina si está habilitado un control de botón o botón de comando.

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
de IDENTIFICADOR del botón o control de botón de comando que se va a probar.

### <a name="return-value"></a>Valor devuelto

TRUE si el control está habilitado, FALSE si no lo está.

### <a name="remarks"></a>Comentarios

Puede usar este método para determinar la disponibilidad de ambos controles de botón de comando y de los botones comunes `CTaskDialog` de la clase *.

Si *nCommandControlID* no es un identificador válido para un botón común `CTaskDialog` o un control de botón de comando, este método produce una excepción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="isradiobuttonenabled"></a>  CTaskDialog::IsRadioButtonEnabled

Determina si está habilitado un botón de radio.

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
de IDENTIFICADOR del botón de radio que se va a probar.

### <a name="return-value"></a>Valor devuelto

TRUE si el botón de radio está habilitado, FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Si *nRadioButtonID* no es un identificador válido para un botón de radio, este método produce una excepción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="issupported"></a>  CTaskDialog::IsSupported

Determina si el equipo que ejecuta la aplicación admite `CTaskDialog`.

```
static BOOL IsSupported();
```

### <a name="return-value"></a>Valor devuelto

TRUE si el equipo admite el `CTaskDialog`; De lo contrario, FALSE.

### <a name="remarks"></a>Comentarios

Utilice esta función para determinar en tiempo de ejecución si el equipo que ejecuta la aplicación admite `CTaskDialog` la clase. Si el equipo no admite `CTaskDialog`, debe proporcionar otro método para comunicar información al usuario. La aplicación se bloqueará si intenta usar un `CTaskDialog` en un equipo que no admita la `CTaskDialog` clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

##  <a name="loadcommandcontrols"></a>  CTaskDialog::LoadCommandControls

Agrega controles de botón de comando mediante el uso de datos de la tabla de cadenas.

```
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>Parámetros

*nIDCommandControlsFirst*<br/>
de IDENTIFICADOR de cadena del primer comando.

*nIDCommandControlsLast*<br/>
de IDENTIFICADOR de cadena del último comando.

### <a name="remarks"></a>Comentarios

Este método crea controles de botón de comando mediante datos del archivo de recursos de la aplicación. La tabla de cadenas del archivo de recursos tiene varias cadenas con identificadores de cadena asociados. Los nuevos controles de botón de comando agregados mediante este método usan la cadena para el título del control y el identificador de cadena para el identificador del control. El intervalo de cadenas seleccionado lo proporcionan *nIDCommandControlsFirst* y *nCommandControlsLast*, ambos incluidos. Si hay una entrada vacía en el intervalo, el método no agrega un control de botón de comando para dicha entrada.

De forma predeterminada, los nuevos controles de botón de comando están habilitados y no requieren elevación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="loadradiobuttons"></a>  CTaskDialog::LoadRadioButtons

Agrega controles de botón de radio mediante los datos de la tabla de cadenas.

```
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>Parámetros

*nIDRadioButtonsFirst*<br/>
de IDENTIFICADOR de cadena del primer botón de radio.

*nIDRadioButtonsLast*<br/>
de IDENTIFICADOR de cadena del último botón de radio.

### <a name="remarks"></a>Comentarios

Este método crea botones de radio mediante el uso de datos del archivo de recursos de la aplicación. La tabla de cadenas del archivo de recursos tiene varias cadenas con identificadores de cadena asociados. Los nuevos botones de radio agregados mediante este método usan la cadena para el título del botón de radio y el identificador de cadena para el identificador del botón de radio. El intervalo de cadenas seleccionado lo proporcionan *nIDRadioButtonsFirst* y *nRadioButtonsLast*, ambos incluidos. Si hay una entrada vacía en el intervalo, el método no agrega un botón de radio para dicha entrada.

De forma predeterminada, se habilitan los nuevos botones de radio.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="navigateto"></a>  CTaskDialog::NavigateTo

Transfiere el foco a otro `CTaskDialog`.

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>Parámetros

*oTaskDialog*<br/>
de `CTaskDialog` Que recibe el foco.

### <a name="remarks"></a>Comentarios

Este método oculta el actual `CTaskDialog` cuando muestra el *oTaskDialog*. El *oTaskDialog* se muestra en la misma ubicación que el actual `CTaskDialog`.

##  <a name="oncommandcontrolclick"></a>  CTaskDialog::OnCommandControlClick

El marco de trabajo llama a este método cuando el usuario hace clic en un control de botón de comando.

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
de IDENTIFICADOR del control de botón de comando que el usuario seleccionó.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar el comportamiento personalizado.

##  <a name="oncreate"></a>  CTaskDialog::OnCreate

El marco de trabajo llama a este método después `CTaskDialog`de crear el.

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar el comportamiento personalizado.

##  <a name="ondestroy"></a>  CTaskDialog::OnDestroy

El marco de trabajo llama a este método inmediatamente antes de `CTaskDialog`que destruya el.

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar el comportamiento personalizado.

##  <a name="onexpandbuttonclick"></a>  CTaskDialog::OnExpandButtonClick

El marco de trabajo llama a este método cuando el usuario hace clic en el botón de expansión.

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>Parámetros

*bExpanded*<br/>
de Un valor distinto de cero indica que se muestra la información adicional; 0 indica que la información adicional está oculta.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar el comportamiento personalizado.

##  <a name="onhelp"></a>  CTaskDialog::OnHelp

El marco de trabajo llama a este método cuando el usuario solicita ayuda.

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar el comportamiento personalizado.

##  <a name="onhyperlinkclick"></a>  CTaskDialog::OnHyperlinkClick

El marco de trabajo llama a este método cuando el usuario hace clic en un hipervínculo.

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>Parámetros

*strHref*<br/>
de Cadena que representa el hipervínculo.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Este método llama a [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) antes de devolver S_OK.

Invalide este método en una clase derivada para implementar el comportamiento personalizado.

##  <a name="oninit"></a>  CTaskDialog::OnInit

El marco de trabajo llama a este `CTaskDialog` método cuando se inicializa.

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar el comportamiento personalizado.

##  <a name="onnavigatepage"></a>  CTaskDialog::OnNavigatePage

El marco de trabajo llama a este método en respuesta al método [clase CTaskDialog:: navigato](#navigateto) .

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar el comportamiento personalizado.

##  <a name="onradiobuttonclick"></a>  CTaskDialog::OnRadioButtonClick

El marco de trabajo llama a este método cuando el usuario selecciona un control de botón de radio.

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
de IDENTIFICADOR del control de botón de radio en el que el usuario hizo clic.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar el comportamiento personalizado.

##  <a name="ontimer"></a>  CTaskDialog::OnTimer

El marco de trabajo llama a este método cuando el temporizador expira.

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>Parámetros

*lTime*<br/>
de Tiempo en milisegundos desde que `CTaskDialog` se creó o se restableció el temporizador.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar el comportamiento personalizado.

##  <a name="onverificationcheckboxclick"></a>  CTaskDialog::OnVerificationCheckboxClick

El marco de trabajo llama a este método cuando el usuario hace clic en la casilla de verificación.

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>Parámetros

*bChecked*<br/>
de TRUE indica que la casilla de verificación está activada. FALSE indica que no lo es.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar el comportamiento personalizado.

##  <a name="removeallcommandcontrols"></a>  CTaskDialog::RemoveAllCommandControls

Quita todos los controles de botón de comando `CTaskDialog`de.

```
void RemoveAllCommandControls();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="removeallradiobuttons"></a>  CTaskDialog::RemoveAllRadioButtons

Quita todos los botones de radio de `CTaskDialog`.

```
void RemoveAllRadioButtons();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setcommandcontroloptions"></a>  CTaskDialog::SetCommandControlOptions

Actualiza un control de botón de comando `CTaskDialog`en.

```
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
de IDENTIFICADOR del control de comando que se va a actualizar.

*bEnabled*<br/>
de Un parámetro booleano que indica si el control de botón de comando especificado está habilitado o deshabilitado.

*bRequiresElevation*<br/>
de Un parámetro booleano que indica si el control de botón de comando especificado requiere elevación.

### <a name="remarks"></a>Comentarios

Utilice este método para cambiar si un control de botón de comando está habilitado o requiere elevación una vez que se `CTaskDialog` ha agregado a la clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setcommonbuttonoptions"></a>  CTaskDialog::SetCommonButtonOptions

Actualiza un subconjunto de botones comunes que se van a habilitar y requiere elevación de UAC.

```
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parámetros

*nDisabledButtonMask*<br/>
de Máscara para los botones comunes que se van a deshabilitar.

*nElevationButtonMask*<br/>
de Máscara para los botones comunes que requieren elevación.

### <a name="remarks"></a>Comentarios

Puede establecer los botones comunes disponibles para una instancia de la [clase clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md) mediante el constructor [clase CTaskDialog:: clase CTaskDialog](#ctaskdialog) y el método [clase CTaskDialog:: SetCommonButtons](#setcommonbuttons). `CTaskDialog::SetCommonButtonOptions`no admite la adición de nuevos botones comunes.

Si utiliza este método para deshabilitar o elevar un botón común que no está disponible para esto `CTaskDialog`, este método produce una excepción mediante la macro [sure](diagnostic-services.md#ensure) .

Este método habilita cualquier botón que esté disponible para `CTaskDialog` , pero que no esté en *nDisabledButtonMask*, incluso si estaba deshabilitado anteriormente. Este método trata la elevación de manera similar: registra botones comunes que no requieren elevación si el botón común está disponible pero no se incluye en *nElevationButtonMask*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcommonbuttons"></a>  CTaskDialog::SetCommonButtons

Agrega botones comunes al `CTaskDialog`.

```
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parámetros

*nButtonMask*<br/>
de Máscara de los botones que se van a agregar `CTaskDialog`a.

*nDisabledButtonMask*<br/>
de Máscara de los botones que se van a deshabilitar.

*nElevationButtonMask*<br/>
de Máscara de los botones que requieren elevación.

### <a name="remarks"></a>Comentarios

No se puede llamar a este método después de crear la ventana de presentación `CTaskDialog` de esta instancia de la clase. Si lo hace, este método produce una excepción.

Los botones indicados por *nButtonMask* invalidan los botones comunes agregados previamente a `CTaskDialog`. Solo están disponibles los botones indicados en *nButtonMask* .

Si *nDisabledButtonMask* o *nElevationButtonMask* contienen un botón que no está en *nButtonMask*, este método produce una excepción mediante la macro de [sure](diagnostic-services.md#ensure) .

De forma predeterminada, todos los botones comunes están habilitados y no requieren elevación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcontent"></a>  CTaskDialog::SetContent

Actualiza el contenido de `CTaskDialog`.

```
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>Parámetros

*strContent*<br/>
de Cadena que se va a mostrar al usuario.

### <a name="remarks"></a>Comentarios

El contenido de la `CTaskDialog` clase es el texto que se muestra al usuario en la sección principal del cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setdefaultcommandcontrol"></a>  CTaskDialog::SetDefaultCommandControl

Especifica el control de botón de comando predeterminado.

```
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
de IDENTIFICADOR del control de botón de comando que va a ser el valor predeterminado.

### <a name="remarks"></a>Comentarios

El control de botón de comando predeterminado es el control que se selecciona `CTaskDialog` cuando se muestra por primera vez al usuario.

Este método produce una excepción si no puede encontrar el control de botón de comando especificado por *nCommandControlID*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setdefaultradiobutton"></a>  CTaskDialog::SetDefaultRadioButton

Especifica el botón de radio predeterminado.

```
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
de IDENTIFICADOR del botón de radio que será el valor predeterminado.

### <a name="remarks"></a>Comentarios

El botón de radio predeterminado es el botón que se selecciona cuando `CTaskDialog` se muestra por primera vez al usuario.

Este método produce una excepción si no encuentra el botón de radio especificado por *nRadioButtonID*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setdialogwidth"></a>  CTaskDialog::SetDialogWidth

Ajusta el ancho de `CTaskDialog`.

```
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>Parámetros

*nWidth*<br/>
de Ancho del cuadro de diálogo, en píxeles.

### <a name="remarks"></a>Comentarios

El parámetro *nWidth* debe ser mayor o igual que 0. De lo contrario, este método produce una excepción.

Si *nWidth* se establece en 0, este método establece el cuadro de diálogo en el tamaño predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setexpansionarea"></a>  CTaskDialog::SetExpansionArea

Actualiza el área de expansión de `CTaskDialog`.

```
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>Parámetros

*strExpandedInformation*<br/>
de Cadena que `CTaskDialog` muestra en el cuerpo principal del cuadro de diálogo cuando el usuario hace clic en el botón de expansión.

*strCollapsedLabel*<br/>
de La cadena que `CTaskDialog` muestra junto al botón de expansión cuando se contrae el área expandida.

*strExpandedLabel*<br/>
de La cadena que `CTaskDialog` muestra junto al botón de expansión cuando se muestra el área expandida.

### <a name="remarks"></a>Comentarios

El área de expansión de `CTaskDialog` la clase le permite proporcionar información adicional al usuario. El área de expansión está en la parte principal de `CTaskDialog`, que se encuentra inmediatamente debajo del título y la cadena de contenido.

Cuando se muestra por primera vez, no se muestra la información expandida y `strCollapsedLabel` se coloca junto al botón de expansión. `CTaskDialog` Cuando el usuario hace clic en el botón de expansión `CTaskDialog` , muestra *strExpandedInformation* y cambia la etiqueta a *strExpandedLabel*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootericon"></a>  CTaskDialog::SetFooterIcon

Actualiza el icono de pie de página `CTaskDialog`de.

```
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>Parámetros

*hFooterIcon*<br/>
de Nuevo icono de `CTaskDialog`.

*lpszFooterIcon*<br/>
de Nuevo icono de `CTaskDialog`.

### <a name="remarks"></a>Comentarios

El icono de pie de página se muestra en la parte inferior de la [clase clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Puede tener texto de pie de página asociado. Puede cambiar el texto del pie de página con [clase CTaskDialog:: SetFooterText](#setfootertext).

Este método produce una excepción con la macro [sure](diagnostic-services.md#ensure) si `CTaskDialog` se muestra o el parámetro de entrada es NULL.

Un `CTaskDialog` solo puede `HICON` aceptar o `LPCWSTR` como un icono de pie de página. Esto se configura estableciendo la opción TDF_USE_HICON_FOOTER en el constructor o [clase CTaskDialog:: SetOptions](#setoptions). De forma predeterminada, `CTaskDialog` está configurado para usar `LPCWSTR` como tipo de entrada para el icono de pie de página. Este método genera una excepción si se intenta establecer el icono con el tipo inadecuado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootertext"></a>  CTaskDialog::SetFooterText

Actualiza el texto en el pie de página de `CTaskDialog`.

```
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>Parámetros

*strFooterText*<br/>
de Nuevo texto del pie de página.

### <a name="remarks"></a>Comentarios

El icono de pie de página aparece junto al texto del pie de página en la `CTaskDialog`parte inferior del. Puede cambiar el icono de pie de página con [clase CTaskDialog:: SetFooterIcon](#setfootericon).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmainicon"></a>  CTaskDialog::SetMainIcon

Actualiza el icono principal de `CTaskDialog`.

```
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>Parámetros

*hMainIcon*<br/>
de Icono nuevo.

*lpszMainIcon*<br/>
de Icono nuevo.

### <a name="remarks"></a>Comentarios

Este método produce una excepción con la macro [sure](diagnostic-services.md#ensure) si `CTaskDialog` se muestra o el parámetro de entrada es NULL.

Un `CTaskDialog` solo puede `HICON` aceptar o `LPCWSTR` como un icono principal. Para configurarlo, establezca la opción TDF_USE_HICON_MAIN en el constructor o en el método [clase CTaskDialog:: SetOptions](#setoptions) . De forma predeterminada, `CTaskDialog` está configurado para usar `LPCWSTR` como tipo de entrada para el icono principal. Este método genera una excepción si se intenta establecer el icono con el tipo inadecuado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmaininstruction"></a>  CTaskDialog::SetMainInstruction

Actualiza la instrucción principal del `CTaskDialog`.

```
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>Parámetros

*strInstructions*<br/>
de La nueva instrucción principal.

### <a name="remarks"></a>Comentarios

La instrucción principal de la `CTaskDialog` clase es el texto que se muestra al usuario en una fuente Negrita grande. Se encuentra en el cuadro de diálogo situado debajo de la barra de título.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setoptions"></a>  CTaskDialog::SetOptions

Configura las opciones para `CTaskDialog`.

```
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>Parámetros

*nOptionFlag*<br/>
de Conjunto de marcas que se va a usar `CTaskDialog`para.

### <a name="remarks"></a>Comentarios

Este método borra todas las opciones `CTaskDialog`actuales del. Para conservar las opciones actuales, debe recuperarlas primero con [clase CTaskDialog:: GetOptions](#getoptions) y combinarlas con las opciones que desea establecer.

En la tabla siguiente se enumeran todas las opciones válidas.

|||
|-|-|
|TDF_ENABLE_HYPERLINKS|Habilita los `CTaskDialog`hipervínculos en.|
|TDF_USE_HICON_MAIN|Configura el `CTaskDialog` para `HICON` utilizar para el icono principal. La alternativa es usar `LPCWSTR`.|
|TDF_USE_HICON_FOOTER|Configura el `CTaskDialog` para `HICON` utilizar para el icono de pie de página. La alternativa es usar `LPCWSTR`.|
|TDF_ALLOW_DIALOG_CANCELLATION|Permite al usuario cerrar `CTaskDialog` con el teclado o con el icono de la esquina superior derecha del cuadro de diálogo, incluso si el botón **Cancelar** no está habilitado. Si no se establece esta marca y el botón **Cancelar** no está habilitado, el usuario no puede cerrar el cuadro de diálogo con Alt + F4, la tecla escape o el botón cerrar de la barra de título.|
|TDF_USE_COMMAND_LINKS|Configura `CTaskDialog` para usar los controles de botón de comando.|
|TDF_USE_COMMAND_LINKS_NO_ICON|Configura `CTaskDialog` para usar los controles de botón de comando sin mostrar un icono junto al control. TDF_USE_COMMAND_LINKS invalida TDF_USE_COMMAND_LINKS_NO_ICON.|
|TDF_EXPAND_FOOTER_AREA|Indica que el área de expansión está expandida actualmente.|
|TDF_EXPANDED_BY_DEFAULT|Determina si el área de expansión se expande de forma predeterminada.|
|TDF_VERIFICATION_FLAG_CHECKED|Indica que la casilla de verificación está seleccionada actualmente.|
|TDF_SHOW_PROGRESS_BAR|Configura `CTaskDialog` para mostrar una barra de progreso.|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|Configura la barra de progreso para que sea una barra de progreso de marquesina. Si habilita esta opción, debe establecer TDF_SHOW_PROGRESS_BAR para que tenga el comportamiento esperado.|
|TDF_CALLBACK_TIMER|Indica que el `CTaskDialog` intervalo de devolución de llamada se establece en aproximadamente 200 milisegundos.|
|TDF_POSITION_RELATIVE_TO_WINDOW|Configura `CTaskDialog` para que se Centre en relación con la ventana primaria. Si esta marca no está habilitada, `CTaskDialog` se centra en relación con el monitor.|
|TDF_RTL_LAYOUT|Configura `CTaskDialog` para un diseño de lectura de derecha a izquierda.|
|TDF_NO_DEFAULT_RADIO_BUTTON|Indica que no se ha seleccionado ningún botón de `CTaskDialog` radio cuando aparece.|
|TDF_CAN_BE_MINIMIZED|Permite al usuario minimizar el `CTaskDialog`. Para admitir esta opción, el `CTaskDialog` no puede ser modal. MFC no admite esta opción porque MFC no admite ningún modelo `CTaskDialog`.|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setprogressbarmarquee"></a>  CTaskDialog::SetProgressBarMarquee

Configura una barra de Marquesina para el `CTaskDialog` y lo agrega al cuadro de diálogo.

```
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>Parámetros

*bEnabled*<br/>
de TRUE para habilitar la barra de marquesina; FALSE para deshabilitar la barra de marquesina y quitarla de `CTaskDialog`.

*nMarqueeSpeed*<br/>
de Un entero que indica la velocidad de la barra de marquesina.

### <a name="remarks"></a>Comentarios

La barra de marquesina aparece debajo del texto principal de la `CTaskDialog` clase.

Use *nMarqueeSpeed* para establecer la velocidad de la barra de marquesina; los valores mayores indican una velocidad más lenta. Un valor de 0 para *nMarqueeSpeed* hace que la barra de marquesina se mueva a la velocidad predeterminada para Windows.

Este método produce una excepción con la macro [sure](diagnostic-services.md#ensure) si *nMarqueeSpeed* es menor que 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarposition"></a>  CTaskDialog::SetProgressBarPosition

Ajusta la posición de la barra de progreso.

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parámetros

*nProgressPos*<br/>
de Posición de la barra de progreso.

### <a name="remarks"></a>Comentarios

Este método produce una excepción con la macro [sure](diagnostic-services.md#ensure) si *nProgressPos* no está en el intervalo de la barra de progreso. Puede cambiar el intervalo de la barra de progreso con [clase CTaskDialog:: SetProgressBarRange](#setprogressbarrange).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarrange"></a>  CTaskDialog::SetProgressBarRange

Ajusta el intervalo de la barra de progreso.

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parámetros

*nRangeMin*<br/>
de Límite inferior de la barra de progreso.

*nRangeMax*<br/>
de Límite superior de la barra de progreso.

### <a name="remarks"></a>Comentarios

La posición de la barra de progreso es relativa a *nRangeMin* y *nRangeMax*. Por ejemplo, si *nRangeMin* es 50 y *nRangeMax* es 100, una posición de 75 se encuentra a la mitad de la barra de progreso. Use [clase CTaskDialog:: SetProgressBarPosition](#setprogressbarposition) para establecer la posición de la barra de progreso.

Para mostrar la barra de progreso, la opción TDF_SHOW_PROGRESS_BAR debe estar habilitada y TDF_SHOW_MARQUEE_PROGRESS_BAR no debe estar habilitada. Este método establece TDF_SHOW_PROGRESS_BAR y borra TDF_SHOW_MARQUEE_PROGRESS_BAR automáticamente. Use [clase CTaskDialog:: SetOptions](#setoptions) para cambiar manualmente las opciones de esta instancia de la [clase clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

Este método produce una excepción con la macro [sure](diagnostic-services.md#ensure) si *nRangeMin* no es menor que *nRangeMax*. Este método también produce una excepción si `CTaskDialog` ya se muestra y tiene una barra de progreso de marquesina.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarstate"></a>  CTaskDialog::SetProgressBarState

Establece el estado de la barra de progreso y lo muestra en `CTaskDialog`.

```
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>Parámetros

*nState*<br/>
de Estado de la barra de progreso. Vea la sección Comentarios para ver los valores posibles.

### <a name="remarks"></a>Comentarios

Este método produce una excepción con la macro [sure](diagnostic-services.md#ensure) si `CTaskDialog` ya se muestra y tiene una barra de progreso de marquesina.

En la tabla siguiente se enumeran los posibles valores para *nState*. En todos estos casos, la barra de progreso se rellenará con el color normal hasta que alcance la posición de detención designada. En ese momento, cambiará el color en función del estado.

|||
|-|-|
|PBST_NORMAL|Una vez que se rellena la barra de `CTaskDialog` progreso, el no cambia el color de la barra. De forma predeterminada, el color normal es verde.|
|PBST_ERROR|Una vez que se rellena la barra de `CTaskDialog` progreso, el cambia el color de la barra al color del error. De forma predeterminada, es rojo.|
|PBST_PAUSED|Una vez que se rellena la barra de `CTaskDialog` progreso, el cambia el color de la barra al color en pausa. De forma predeterminada, es amarillo.|

Puede establecer dónde se detiene la barra de progreso con [clase CTaskDialog:: SetProgressBarPosition](#setprogressbarposition).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setradiobuttonoptions"></a>  CTaskDialog::SetRadioButtonOptions

Habilita o deshabilita un botón de radio.

```
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
de IDENTIFICADOR del control de botón de radio.

*bEnabled*<br/>
de TRUE para habilitar el botón de radio; FALSE para deshabilitar el botón de radio.

### <a name="remarks"></a>Comentarios

Este método produce una excepción con la macro [sure](diagnostic-services.md#ensure) si *nRadioButtonID* no es un identificador válido para un botón de radio.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setverificationcheckbox"></a>  CTaskDialog::SetVerificationCheckbox

Establece el estado activado de la casilla de verificación.

```
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>Parámetros

*bChecked*<br/>
de True para activar la casilla de verificación cuando se muestra `CTaskDialog` el control; FALSE para que `CTaskDialog` se anule la selección de la casilla de verificación cuando se muestre.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setverificationcheckboxtext"></a>  CTaskDialog::SetVerificationCheckboxText

Establece el texto que se muestra a la derecha de la casilla de verificación.

```
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>Parámetros

*strVerificationText*<br/>
de El texto que este método muestra junto a la casilla de verificación.

### <a name="remarks"></a>Comentarios

Este método produce una excepción con la macro [sure](diagnostic-services.md#ensure) si ya se muestra esta instancia `CTaskDialog` de la clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setwindowtitle"></a>  CTaskDialog::SetWindowTitle

Establece el título del `CTaskDialog`.

```
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>Parámetros

*strWindowTitle*<br/>
de Nuevo título para `CTaskDialog`.

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="showdialog"></a>  CTaskDialog::ShowDialog

Crea y muestra un `CTaskDialog`.

```
static INT_PTR ShowDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons = TDCBF_YES_BUTTON | TDCBF_NO_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>Parámetros

*strContent*<br/>
de Cadena que se va a usar para el contenido `CTaskDialog`de.

*strMainInstruction*<br/>
de Instrucción principal del `CTaskDialog`.

*strTitle*<br/>
de Título del `CTaskDialog`.

*nIDCommandControlsFirst*<br/>
de IDENTIFICADOR de cadena del primer comando.

*nIDCommandControlsLast*<br/>
de IDENTIFICADOR de cadena del último comando.

*nCommonButtons*<br/>
de Máscara de los botones que se van a agregar `CTaskDialog`a.

*nTaskDialogOptions*<br/>
de Conjunto de opciones que se va a usar `CTaskDialog`para.

*strFooter*<br/>
de Cadena que se va a usar como pie de página.

### <a name="return-value"></a>Valor devuelto

Entero que corresponde a la selección realizada por el usuario.

### <a name="remarks"></a>Comentarios

Este método estático le permite crear una instancia de la `CTaskDialog` clase sin crear explícitamente un `CTaskDialog` objeto en el código. Dado que no hay `CTaskDialog` ningún objeto, no se puede llamar a ningún otro `CTaskDialog` método de si se usa `CTaskDialog` este método para mostrar al usuario.

Este método crea controles de botón de comando mediante datos del archivo de recursos de la aplicación. La tabla de cadenas del archivo de recursos tiene varias cadenas con identificadores de cadena asociados. Este método agrega un control de botón de comando para cada entrada válida de la tabla de cadenas entre *nIDCommandControlsFirst* y *nCommandControlsLast*, ambos incluidos. Para estos controles de botón de comando, la cadena de la tabla de cadenas es el título del control y el identificador de cadena es el identificador del control.

Vea [clase CTaskDialog:: SetOptions](#setoptions) para obtener una lista de opciones válidas.

Se cierra cuando el usuario selecciona un botón común, un control de vínculo de comando o cierra `CTaskDialog`. `CTaskDialog` El valor devuelto es el identificador que indica cómo el usuario cerró el cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

##  <a name="taskdialogcallback"></a>  CTaskDialog::TaskDialogCallback

El marco de trabajo llama a este método en respuesta a varios mensajes de Windows.

```
friend:
HRESULT TaskDialogCallback(
    HWND hWnd,
    UINT uNotification,
    WPARAM wParam,
    LPARAM lParam,
    LONG_PTR dwRefData);
```

### <a name="parameters"></a>Parámetros

*hwnd*<br/>
de `m_hWnd` Identificador`CTaskDialog`de la estructura para.

*uNotification*<br/>
de Código de notificación que especifica el mensaje generado.

*wParam*<br/>
de Más información sobre el mensaje.

*lParam*<br/>
de Más información sobre el mensaje.

*dwRefData*<br/>
de Puntero al `CTaskDialog` objeto al que se aplica el mensaje de devolución de llamada.

### <a name="return-value"></a>Valor devuelto

Depende del código de notificación específico. Vea la sección Comentarios para obtener más información.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de `TaskDialogCallback` controla el mensaje específico y, a continuación, llama al método en de la [clase clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Por ejemplo, en respuesta al mensaje TDN_BUTTON_CLICKED, `TaskDialogCallback` llama a [clase CTaskDialog:: OnCommandControlClick](#oncommandcontrolclick).

Los valores de *wParam* e *lParam* dependen del mensaje generado específico. Es posible que uno o ambos de estos valores estén vacíos. En la tabla siguiente se enumeran las notificaciones predeterminadas que se admiten y cuáles representan los valores de *wParam* e *lParam* . Si invalida este método en una clase derivada, debe implementar el código de devolución de llamada para cada mensaje en la tabla siguiente.

|Mensaje de notificación|*wParam* Valor|*lParam* Valor|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|No se utiliza.|No se utiliza.|
|TDN_NAVIGATED|No se utiliza.|No se utiliza.|
|TDN_BUTTON_CLICKED|IDENTIFICADOR de control del botón de comando.|No se utiliza.|
|TDN_HYPERLINK_CLICKED|No se utiliza.|Estructura [LPCWSTR](/windows/win32/WinProg/windows-data-types) que contiene el vínculo.|
|TDN_TIMER|Tiempo en milisegundos desde que `CTaskDialog` se creó o se restableció el temporizador.|No se utiliza.|
|TDN_DESTROYED|No se utiliza.|No se utiliza.|
|TDN_RADIO_BUTTON_CLICKED|IDENTIFICADOR del botón de radio.|No se utiliza.|
|TDN_DIALOG_CONSTRUCTED|No se utiliza.|No se utiliza.|
|TDN_VERIFICATION_CLICKED|1 si la casilla está activada, 0 si no lo está.|No se utiliza.|
|TDN_HELP|No se utiliza.|No se utiliza.|
|TDN_EXPANDO_BUTTON_CLICKED|0 si el área de expansión está contraída; distinto de cero si se muestra el texto de la expansión.|No se utiliza.|

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Tutorial: agregar un CTaskDialog a una aplicación](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
