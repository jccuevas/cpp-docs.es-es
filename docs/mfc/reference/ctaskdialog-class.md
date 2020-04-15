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
ms.openlocfilehash: e9aeee31d2952d5362c983934ce85f0332f553fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366631"
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
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|Agrega un control de `CTaskDialog`botón de comando al archivo .|
|[CTaskDialog::AddRadioButton](#addradiobutton)|Agrega un botón `CTaskDialog`de opción al archivo .|
|[CTaskDialog::ClickCommandControl](#clickcommandcontrol)|Hace clic en un control de botón de comando o botón común mediante programación.|
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|Hace clic en un botón de opción mediante programación.|
|[CTaskDialog::DoModal](#domodal)|Muestra el `CTaskDialog`.|
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|Recupera el número de botones comunes disponibles.|
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|Convierte un botón estándar de Windows en `CTaskDialog` el tipo de botón común asociado a la clase.|
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|Convierte uno de los tipos de `CTaskDialog` botón comunes asociados a la clase en un botón estándar de Windows.|
|[CTaskDialog::GetOptions](#getoptions)|Devuelve los indicadores `CTaskDialog`de opción para este archivo .|
|[CTaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|Devuelve el control de botón de comando seleccionado.|
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|Devuelve el botón de opción seleccionado.|
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|Recupera el estado de la casilla de verificación.|
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|Determina si un control de botón de comando o un botón común está habilitado.|
|[CTaskDialog::IsRadioButtonEnabled](#isradiobuttonenabled)|Determina si un botón de opción está habilitado.|
|[CTaskDialog::IsSupported](#issupported)|Determina si el equipo que ejecuta `CTaskDialog`la aplicación admite el archivo .|
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|Agrega controles de botón de comando mediante los datos de la tabla de cadenas.|
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|Agrega botones de opción mediante los datos de la tabla de cadenas.|
|[CTaskDialog::NavigateTo](#navigateto)|Transfiere el foco `CTaskDialog`a otro archivo .|
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|El marco de trabajo llama a este método cuando el usuario hace clic en un control de botón de comando.|
|[CTaskDialog::OnCreate](#oncreate)|El marco de trabajo llama `CTaskDialog`a este método después de crear el archivo .|
|[CTaskDialog::OnDestroy](#ondestroy)|El marco de trabajo llama a `CTaskDialog`este método inmediatamente antes de que destruya el archivo .|
|[CTaskDialog::OnExpandButtonClick](#onexpandbuttonclick)|El marco de trabajo llama a este método cuando el usuario hace clic en el botón de expansión.|
|[CTaskDialog::OnHelp](#onhelp)|El marco de trabajo llama a este método cuando el usuario solicita ayuda.|
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|El marco de trabajo llama a este método cuando el usuario hace clic en un hipervínculo.|
|[CTaskDialog::OnInit](#oninit)|El marco de trabajo `CTaskDialog` llama a este método cuando se inicializa.|
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|El marco de trabajo llama a este método cuando `CTaskDialog`el usuario mueve el foco con respecto a los controles en el archivo .|
|[CTaskDialog::OnRadioButtonClick](#onradiobuttonclick)|El marco de trabajo llama a este método cuando el usuario selecciona un control de botón de opción.|
|[CTaskDialog::OnTimer](#ontimer)|El marco de trabajo llama a este método cuando expira el temporizador.|
|[CTaskDialog::OnVerificationCheckboxClick](#onverificationcheckboxclick)|El marco de trabajo llama a este método cuando el usuario hace clic en la casilla de verificación.|
|[CTaskDialog::RemoveAllCommandControls](#removeallcommandcontrols)|Quita todos los controles `CTaskDialog`de comando del archivo .|
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|Elimina todos los botones `CTaskDialog`de opción del archivo .|
|[CTaskDialog::SetCommandControlOptions](#setcommandcontroloptions)|Actualiza un control de `CTaskDialog`botón de comando en el archivo .|
|[CTaskDialog::SetCommonButtonOptions](#setcommonbuttonoptions)|Actualiza un subconjunto de botones comunes que se habilitarán y requieren elevación De UAC.|
|[CTaskDialog::SetCommonButtons](#setcommonbuttons)|Agrega botones comunes `CTaskDialog`al archivo .|
|[CTaskDialog::SetContent](#setcontent)|Actualiza el contenido `CTaskDialog`del archivo .|
|[CTaskDialog::SetDefaultCommandControl](#setdefaultcommandcontrol)|Especifica el control de botón de comando predeterminado.|
|[CTaskDialog::SetDefaultRadioButton](#setdefaultradiobutton)|Especifica el botón de opción predeterminado.|
|[CTaskDialog::SetDialogWidth](#setdialogwidth)|Ajusta el ancho `CTaskDialog`del archivo .|
|[CTaskDialog::SetExpansionArea](#setexpansionarea)|Actualiza el área `CTaskDialog`de expansión del archivo .|
|[CTaskDialog::SetFooterIcon](#setfootericon)|Actualiza el icono de `CTaskDialog`pie de página para el archivo .|
|[CTaskDialog::SetFooterText](#setfootertext)|Actualiza el texto en `CTaskDialog`el pie de página del archivo .|
|[CTaskDialog::SetMainIcon](#setmainicon)|Actualiza el icono principal `CTaskDialog`del archivo .|
|[CTaskDialog::SetMainInstruction](#setmaininstruction)|Actualiza la instrucción `CTaskDialog`principal del archivo .|
|[CTaskDialog::SetOptions](#setoptions)|Configura las opciones `CTaskDialog`para el archivo .|
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|Configura una barra de `CTaskDialog` marco para el y la agrega al cuadro de diálogo.|
|[CTaskDialog::SetProgressBarPosition](#setprogressbarposition)|Ajusta la posición de la barra de progreso.|
|[CTaskDialog::SetProgressBarRange](#setprogressbarrange)|Ajusta el rango de la barra de progreso.|
|[CTaskDialog::SetProgressBarState](#setprogressbarstate)|Establece el estado de la barra `CTaskDialog`de progreso y lo muestra en el archivo .|
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|Habilita o deshabilita un botón de opción.|
|[CTaskDialog::SetVerificationCheckbox](#setverificationcheckbox)|Establece el estado activado de la casilla de verificación.|
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|Establece el texto en el lado derecho de la casilla de verificación.|
|[CTaskDialog::SetWindowTitle](#setwindowtitle)|Establece el título `CTaskDialog`del archivo .|
|[CTaskDialog::ShowDialog](#showdialog)|Crea y `CTaskDialog`muestra un archivo .|
|[CTaskDialog::TaskDialogCallback](#taskdialogcallback)|El marco de trabajo llama a esto en respuesta a varios mensajes de Windows.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|`m_aButtons`|Matriz de controles de `CTaskDialog`botón de comando para el archivo .|
|`m_aRadioButtons`|La matriz de controles `CTaskDialog`de botón de opción para el archivo .|
|`m_bVerified`|`TRUE`indica que la casilla de verificación está marcada; `FALSE` indica que no lo es.|
|`m_footerIcon`|El icono en el `CTaskDialog`pie de página de la .|
|`m_hWnd`|Un identificador de la `CTaskDialog`ventana para el archivo .|
|`m_mainIcon`|El icono principal `CTaskDialog`de la .|
|`m_nButtonDisabled`|Una máscara que indica cuáles de los botones comunes están deshabilitados.|
|`m_nButtonElevation`|Máscara que indica cuáles de los botones comunes requieren elevación UAC.|
|`m_nButtonId`|El identificador del control de botón de comando seleccionado.|
|`m_nCommonButton`|Una máscara que indica qué botones `CTaskDialog`comunes se muestran en el archivo .|
|`m_nDefaultCommandControl`|El identificador del control de botón `CTaskDialog` de comando que se selecciona cuando se muestra.|
|`m_nDefaultRadioButton`|El identificador del control de botón `CTaskDialog` de opción que se selecciona cuando se muestra.|
|`m_nFlags`|Una máscara que indica las `CTaskDialog`opciones para el archivo .|
|`m_nProgressPos`|La posición actual de la barra de progreso.  Dicho valor debe encontrarse entre `m_nProgressRangeMin` y `m_nProgressRangeMax`.|
|`m_nProgressRangeMax`|El valor máximo de la barra de progreso.|
|`m_nProgressRangeMin`|El valor mínimo para la barra de progreso.|
|`m_nProgressState`|El estado de la barra de progreso. Para obtener más información, vea [CTaskDialog::SetProgressBarState](#setprogressbarstate).|
|`m_nRadioId`|El ID del control de botón de opción seleccionado.|
|`m_nWidth`|Ancho del control `CTaskDialog`, en píxeles.|
|`m_strCollapse`|La cadena `CTaskDialog` se muestra a la derecha del cuadro de expansión cuando se oculta la información expandida.|
|`m_strContent`|La cadena de `CTaskDialog`contenido del archivo .|
|`m_strExpand`|La cadena `CTaskDialog` se muestra a la derecha del cuadro de expansión cuando se muestra la información expandida.|
|`m_strFooter`|El pie `CTaskDialog`de página de la .|
|`m_strInformation`|La información ampliada `CTaskDialog`para el archivo .|
|`m_strMainInstruction`|La instrucción `CTaskDialog`principal de la .|
|`m_strTitle`|Título de la página `CTaskDialog`.|
|`m_strVerification`|La cadena `CTaskDialog` que se muestra a la derecha de la casilla de verificación.|

## <a name="remarks"></a>Observaciones

La `CTaskDialog` clase reemplaza el cuadro de mensaje estándar de Windows y tiene funcionalidad adicional, como nuevos controles para recopilar información del usuario. Esta clase se encuentra en la biblioteca MFC en Visual Studio 2010 y versiones posteriores. Está `CTaskDialog` disponible a partir de Windows Vista. Las versiones anteriores `CTaskDialog` de Windows no pueden mostrar el objeto. Se `CTaskDialog::IsSupported` utiliza para determinar en tiempo de ejecución si el usuario actual puede mostrar el cuadro de diálogo de tarea. El cuadro de mensaje estándar de Windows sigue siendo compatible.

Solo `CTaskDialog` está disponible cuando se compila la aplicación mediante la biblioteca Unicode.

Tiene `CTaskDialog` dos constructores diferentes. Un constructor permite especificar dos botones de comando y un máximo de seis controles de botón normales. Puede agregar más botones de `CTaskDialog`comando después de crear el archivo . El segundo constructor no admite ningún botón de comando, pero puede agregar un número ilimitado de controles de botón normales. Para obtener más información acerca de los constructores, vea [CTaskDialog::CTaskDialog](#ctaskdialog).

La siguiente imagen `CTaskDialog` muestra un ejemplo para ilustrar la ubicación de algunos de los controles.

![Ejemplo de CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "Ejemplo de CTaskDialog") <br/>
Ejemplo de CTaskDialog

## <a name="requirements"></a>Requisitos

**Sistema operativo mínimo requerido:** Windows Vista

**Encabezado:** afxtaskdialog.h

## <a name="ctaskdialogaddcommandcontrol"></a><a name="addcommandcontrol"></a>CTaskDialog::AddCommandControl

Agrega un nuevo control de `CTaskDialog`botón de comando al archivo .

```
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
[en] El número de identificación del control de comandos.

*strCaption*<br/>
[en] La cadena `CTaskDialog` que el muestra al usuario. Utilice esta cadena para explicar el propósito del comando.

*bHabilitado*<br/>
[en] Un parámetro booleano que indica si el nuevo botón está habilitado o deshabilitado.

*bRequiresElevation*<br/>
[en] Parámetro booleano que indica si un comando requiere elevación.

### <a name="remarks"></a>Observaciones

Puede `CTaskDialog Class` mostrar un número ilimitado de controles de botón de comando. Sin embargo, si un `CTaskDialog` muestra cualquier control de botón de comando, puede mostrar un máximo de seis botones. Si `CTaskDialog` a no tiene controles de botón de comando, puede mostrar un número ilimitado de botones.

Cuando el usuario selecciona un control `CTaskDialog` de botón de comando, se cierra. Si la aplicación muestra el cuadro de diálogo mediante `DoModal` [CTaskDialog::DoModal](#domodal), devuelve el *nCommandControlID* del control de botón de comando seleccionado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogaddradiobutton"></a><a name="addradiobutton"></a>CTaskDialog::AddRadioButton

Agrega un botón `CTaskDialog`de opción al archivo .

```
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
[en] El número de identificación del botón de radio.

*strCaption*<br/>
[en] La cadena `CTaskDialog` que se muestra junto al botón de opción.

*bHabilitado*<br/>
[en] Un parámetro booleano que indica si el botón de opción está habilitado.

### <a name="remarks"></a>Observaciones

Los botones de opción para la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md) permiten recopilar información del usuario. Utilice la función [CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid) para determinar qué botón de opción está seleccionado.

El `CTaskDialog` no requiere que los parámetros *nRadioButtonID* sean únicos para cada botón de opción. Sin embargo, puede experimentar un comportamiento inesperado si no utiliza un identificador distinto para cada botón de opción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogclickcommandcontrol"></a><a name="clickcommandcontrol"></a>CTaskDialog::ClickCommandControl

Hace clic en un control de botón de comando o botón común mediante programación.

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
[en] El identificador de comando del control para hacer clic.

### <a name="remarks"></a>Observaciones

Este método genera el TDM_CLICK_BUTTON de mensajes de Windows.

## <a name="ctaskdialogclickradiobutton"></a><a name="clickradiobutton"></a>CTaskDialog::ClickRadioButton

Hace clic en un botón de opción mediante programación.

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
[en] El ID del botón de radio para hacer clic.

### <a name="remarks"></a>Observaciones

Este método genera el mensaje de Windows TDM_CLICK_RADIO_BUTTON.

## <a name="ctaskdialogctaskdialog"></a><a name="ctaskdialog"></a>CTaskDialog::CTaskDialog

Crea una instancia de la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

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
[en] La cadena que se usará `CTaskDialog`para el contenido del archivo .

*strMainInstruction*<br/>
[en] La instrucción `CTaskDialog`principal de la .

*strTitle*<br/>
[en] El título `CTaskDialog`de la .

*nCommonButtons*<br/>
[en] Una máscara de los botones `CTaskDialog`comunes para agregar a la .

*nTaskDialogOptions*<br/>
[en] El conjunto de opciones `CTaskDialog`que se va a utilizar para el archivo .

*strFooter*<br/>
[en] La cadena que se va a utilizar como pie de página.

*nIDCommandControlsFirst*<br/>
[en] El identificador de cadena del primer comando.

*nIDCommandControlsLast*<br/>
[en] El identificador de cadena del último comando.

### <a name="remarks"></a>Observaciones

Hay dos maneras de `CTaskDialog` agregar a la aplicación. La primera forma es usar uno de `CTaskDialog` los constructores para crear un y mostrarlo mediante [CTaskDialog::DoModal](#domodal). La segunda forma es utilizar la función estática [CTaskDialog::ShowDialog](#showdialog), que permite mostrar un `CTaskDialog` objeto sin crear explícitamente. `CTaskDialog`

El segundo constructor crea controles de botón de comando mediante datos del archivo de recursos de la aplicación. La tabla de cadenas del archivo de recursos tiene varias cadenas con identificadores de cadena asociados. Este método agrega un control de botón de comando para cada entrada válida en la tabla de cadenas entre *nIDCommandControlsFirst* y *nCommandControlsLast*, inclusive. Para estos controles de botón de comando, la cadena de la tabla de cadenas es el título del control y el identificador de cadena es el identificador del control.

Vea [CTaskDialog::SetOptions](#setoptions) para obtener una lista de opciones válidas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogdomodal"></a><a name="domodal"></a>CTaskDialog::DoModal

Muestra `CTaskDialog` el y lo hace modal.

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parámetros

*hParent*<br/>
[en] La ventana primaria `CTaskDialog`para el archivo .

### <a name="return-value"></a>Valor devuelto

Entero que corresponde a la selección realizada por el usuario.

### <a name="remarks"></a>Observaciones

Muestra esta instancia de [CTaskDialog](../../mfc/reference/ctaskdialog-class.md). A continuación, la aplicación espera a que el usuario cierre el cuadro de diálogo.

Se `CTaskDialog` cierra cuando el usuario selecciona un botón común, un `CTaskDialog`control de vínculo de comando o cierra el archivo . El valor devuelto es el identificador que indica cómo el usuario cerró el cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetcommonbuttoncount"></a><a name="getcommonbuttoncount"></a>CTaskDialog::GetCommonButtonCount

Recupera el número de botones comunes.

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de botones comunes disponibles.

### <a name="remarks"></a>Observaciones

Los botones comunes son los botones predeterminados que se proporcionan a [CTaskDialog::CTaskDialog](#ctaskdialog). El [CTaskDialog clase](../../mfc/reference/ctaskdialog-class.md) muestra los botones a lo largo de la parte inferior del cuadro de diálogo.

La lista enumerada de botones se proporciona en CommCtrl.h.

## <a name="ctaskdialoggetcommonbuttonflag"></a><a name="getcommonbuttonflag"></a>CTaskDialog::GetCommonButtonFlag

Convierte un botón estándar de Windows en el tipo de botón común asociado a la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>Parámetros

*nButtonId*<br/>
[en] El valor estándar del botón de Windows.

### <a name="return-value"></a>Valor devuelto

El valor del `CTaskDialog` botón común correspondiente. Si no hay ningún botón común correspondiente, este método devuelve 0.

## <a name="ctaskdialoggetcommonbuttonid"></a><a name="getcommonbuttonid"></a>CTaskDialog::GetCommonButtonId

Convierte uno de los tipos de botón comunes asociados con la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md) en un botón estándar de Windows.

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>Parámetros

*nFlag*<br/>
[en] El tipo de botón común asociado a la `CTaskDialog` clase.

### <a name="return-value"></a>Valor devuelto

El valor del botón estándar de Windows correspondiente. Si no hay ningún botón de Windows correspondiente, el método devuelve 0.

## <a name="ctaskdialoggetoptions"></a><a name="getoptions"></a>CTaskDialog::GetOptions

Devuelve los indicadores `CTaskDialog`de opción para este archivo .

```
int GetOptions() const;
```

### <a name="return-value"></a>Valor devuelto

Las banderas `CTaskDialog`de la .

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de las opciones disponibles para la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md), vea [CTaskDialog::SetOptions](#setoptions).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetselectedcommandcontrolid"></a><a name="getselectedcommandcontrolid"></a>CTaskDialog::GetSelectedCommandControlID

Devuelve el control de botón de comando seleccionado.

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador del control de botón de comando seleccionado actualmente.

### <a name="remarks"></a>Observaciones

No es necesario utilizar este método para recuperar el identificador del botón de comando seleccionado por el usuario. Ese identificador es devuelto por [CTaskDialog::DoModal](#domodal) o [CTaskDialog::ShowDialog](#showdialog).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialoggetselectedradiobuttonid"></a><a name="getselectedradiobuttonid"></a>CTaskDialog::GetSelectedRadioButtonID

Devuelve el botón de opción seleccionado.

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>Valor devuelto

El ID del botón de opción seleccionado.

### <a name="remarks"></a>Observaciones

Puede utilizar este método después de que el usuario cierre el cuadro de diálogo para recuperar el botón de opción seleccionado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialoggetverificationcheckboxstate"></a><a name="getverificationcheckboxstate"></a>CTaskDialog::GetVerificationCheckboxState

Recupera el estado de la casilla de verificación.

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi la casilla de verificación está activada, FALSE si no lo está.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogiscommandcontrolenabled"></a><a name="iscommandcontrolenabled"></a>CTaskDialog::IsCommandControlEnabled

Determina si un control de botón de comando o un botón están habilitados.

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
[en] El identificador del control del botón de comando o del botón para probar.

### <a name="return-value"></a>Valor devuelto

TRUESi el control está habilitado, FALSE si no lo está.

### <a name="remarks"></a>Observaciones

Puede utilizar este método para determinar la disponibilidad de los `CTaskDialog` controles de botón de comando y los botones comunes de la Class*.

Si *nCommandControlID* no es un identificador `CTaskDialog` válido para un botón común o un control de botón de comando, este método produce una excepción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogisradiobuttonenabled"></a><a name="isradiobuttonenabled"></a>CTaskDialog::IsRadioButtonEnabled

Determina si un botón de opción está habilitado.

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
[en] El ID del botón de opción para probar.

### <a name="return-value"></a>Valor devuelto

TRUESi el botón de opción está habilitado, FALSE si no lo está.

### <a name="remarks"></a>Observaciones

Si *nRadioButtonID* no es un identificador válido para un botón de opción, este método produce una excepción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogissupported"></a><a name="issupported"></a>CTaskDialog::IsSupported

Determina si el equipo que ejecuta `CTaskDialog`la aplicación admite el archivo .

```
static BOOL IsSupported();
```

### <a name="return-value"></a>Valor devuelto

TRUESi el equipo `CTaskDialog`admite el ; FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Utilice esta función para determinar en tiempo de `CTaskDialog` ejecución si el equipo que ejecuta la aplicación admite la clase. Si el equipo no `CTaskDialog`admite el , debe proporcionar otro método de comunicación de información al usuario. La aplicación se bloqueará si `CTaskDialog` intenta usar un en `CTaskDialog` un equipo que no admite la clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogloadcommandcontrols"></a><a name="loadcommandcontrols"></a>CTaskDialog::LoadCommandControls

Agrega controles de botón de comando mediante los datos de la tabla de cadenas.

```
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>Parámetros

*nIDCommandControlsFirst*<br/>
[en] El identificador de cadena del primer comando.

*nIDCommandControlsLast*<br/>
[en] El identificador de cadena del último comando.

### <a name="remarks"></a>Observaciones

Este método crea controles de botón de comando mediante datos del archivo de recursos de la aplicación. La tabla de cadenas del archivo de recursos tiene varias cadenas con identificadores de cadena asociados. Nuevos controles de botón de comando agregados mediante este método usan la cadena para el título del control y el identificador de cadena para el identificador del control. *NIDCommandControlsFirst* y *nCommandControlsLast*proporcionan el intervalo de cadenas seleccionados, inclusive. Si hay una entrada vacía en el intervalo, el método no agrega un control de botón de comando para esa entrada.

De forma predeterminada, los nuevos controles de botón de comando están habilitados y no requieren elevación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogloadradiobuttons"></a><a name="loadradiobuttons"></a>CTaskDialog::LoadRadioButtons

Agrega controles de botón de opción mediante datos de la tabla de cadenas.

```
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>Parámetros

*nIDRadioButtonsFirst*<br/>
[en] El id de cadena del primer botón de opción.

*nIDRadioButtonsLast*<br/>
[en] El ID de cadena del último botón de opción.

### <a name="remarks"></a>Observaciones

Este método crea botones de opción mediante el uso de datos del archivo de recursos de la aplicación. La tabla de cadenas del archivo de recursos tiene varias cadenas con identificadores de cadena asociados. Los nuevos botones de opción agregados mediante este método utilizan la cadena para el título del botón de opción y el identificador de cadena para el identificador del botón de opción. *NIDRadioButtonsFirst* y *nRadioButtonsLast*proporcionan el rango de cadenas seleccionados, ambos inclusive. Si hay una entrada vacía en el rango, el método no agrega un botón de opción para esa entrada.

De forma predeterminada, los nuevos botones de opción están habilitados.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialognavigateto"></a><a name="navigateto"></a>CTaskDialog::NavigateTo

Transfiere el foco `CTaskDialog`a otro archivo .

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>Parámetros

*oTaskDialog*<br/>
[en] El `CTaskDialog` que recibe el foco.

### <a name="remarks"></a>Observaciones

Este método oculta `CTaskDialog` el actual cuando se muestra el *oTaskDialog*. El *oTaskDialog* se muestra en la `CTaskDialog`misma ubicación que el archivo .

## <a name="ctaskdialogoncommandcontrolclick"></a><a name="oncommandcontrolclick"></a>CTaskDialog::OnCommandControlClick

El marco de trabajo llama a este método cuando el usuario hace clic en un control de botón de comando.

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
[en] El identificador del botón de comando controla que el usuario seleccionó.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

## <a name="ctaskdialogoncreate"></a><a name="oncreate"></a>CTaskDialog::OnCreate

El marco de trabajo llama `CTaskDialog`a este método después de crear el archivo .

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

## <a name="ctaskdialogondestroy"></a><a name="ondestroy"></a>CTaskDialog::OnDestroy

El marco de trabajo llama a `CTaskDialog`este método inmediatamente antes de que destruya el archivo .

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

## <a name="ctaskdialogonexpandbuttonclick"></a><a name="onexpandbuttonclick"></a>CTaskDialog::OnExpandButtonClick

El marco de trabajo llama a este método cuando el usuario hace clic en el botón de expansión.

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>Parámetros

*bAmpliado*<br/>
[en] Un valor distinto de cero indica que se muestra la información adicional; 0 indica que la información adicional está oculta.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

## <a name="ctaskdialogonhelp"></a><a name="onhelp"></a>CTaskDialog::OnHelp

El marco de trabajo llama a este método cuando el usuario solicita ayuda.

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

## <a name="ctaskdialogonhyperlinkclick"></a><a name="onhyperlinkclick"></a>CTaskDialog::OnHyperlinkClick

El marco de trabajo llama a este método cuando el usuario hace clic en un hipervínculo.

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>Parámetros

*strHref*<br/>
[en] Cadena que representa el hipervínculo.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Observaciones

Este método llama a [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) antes de devolver S_OK.

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

## <a name="ctaskdialogoninit"></a><a name="oninit"></a>CTaskDialog::OnInit

El marco de trabajo `CTaskDialog` llama a este método cuando se inicializa.

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

## <a name="ctaskdialogonnavigatepage"></a><a name="onnavigatepage"></a>CTaskDialog::OnNavigatePage

El marco de trabajo llama a este método en respuesta a la [CTaskDialog::NavigateTo](#navigateto) método.

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

## <a name="ctaskdialogonradiobuttonclick"></a><a name="onradiobuttonclick"></a>CTaskDialog::OnRadioButtonClick

El marco de trabajo llama a este método cuando el usuario selecciona un control de botón de opción.

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
[en] El ID del control del botón de radio que el usuario ha haciendo clic.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

## <a name="ctaskdialogontimer"></a><a name="ontimer"></a>CTaskDialog::OnTimer

El marco de trabajo llama a este método cuando expira el temporizador.

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>Parámetros

*lTime*<br/>
[en] Tiempo en milisegundos `CTaskDialog` desde que se creó o se restableció el temporizador.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

## <a name="ctaskdialogonverificationcheckboxclick"></a><a name="onverificationcheckboxclick"></a>CTaskDialog::OnVerificationCheckboxClick

El marco de trabajo llama a este método cuando el usuario hace clic en la casilla de verificación.

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>Parámetros

*bChecked*<br/>
[en] TRUE indica que la casilla de verificación está activada; FALSE indica que no lo es.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

## <a name="ctaskdialogremoveallcommandcontrols"></a><a name="removeallcommandcontrols"></a>CTaskDialog::RemoveAllCommandControls

Quita todos los controles del `CTaskDialog`botón de comando del archivo .

```
void RemoveAllCommandControls();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogremoveallradiobuttons"></a><a name="removeallradiobuttons"></a>CTaskDialog::RemoveAllRadioButtons

Elimina todos los botones `CTaskDialog`de opción del archivo .

```
void RemoveAllRadioButtons();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetcommandcontroloptions"></a><a name="setcommandcontroloptions"></a>CTaskDialog::SetCommandControlOptions

Actualiza un control de `CTaskDialog`botón de comando en el archivo .

```
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
[en] El identificador del control de comandos que se debe actualizar.

*bHabilitado*<br/>
[en] Un parámetro booleano que indica si el control de botón de comando especificado está habilitado o deshabilitado.

*bRequiresElevation*<br/>
[en] Parámetro booleano que indica si el control de botón de comando especificado requiere elevación.

### <a name="remarks"></a>Observaciones

Utilice este método para cambiar si un control de botón de comando `CTaskDialog` está habilitado o requiere elevación después de que se ha agregado a la clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetcommonbuttonoptions"></a><a name="setcommonbuttonoptions"></a>CTaskDialog::SetCommonButtonOptions

Actualiza un subconjunto de botones comunes que se habilitarán y que requieren elevación De UAC.

```
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parámetros

*nDisabledButtonMask*<br/>
[en] Una máscara para los botones comunes que se va a deshabilitar.

*nElevationButtonMask*<br/>
[en] Una máscara para los botones comunes que requieren elevación.

### <a name="remarks"></a>Observaciones

Puede establecer los botones comunes disponibles para una instancia de la [Clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md) mediante el constructor [CTaskDialog::CTaskDialog](#ctaskdialog) y el método [CTaskDialog::SetCommonButtons](#setcommonbuttons). `CTaskDialog::SetCommonButtonOptions`no admite la adición de nuevos botones comunes.

Si utiliza este método para deshabilitar o elevar un `CTaskDialog`botón común que no está disponible para esto , este método produce una excepción mediante el uso de la [ENSURE](diagnostic-services.md#ensure) macro.

Este método habilita cualquier botón `CTaskDialog` que esté disponible para el *nDisabledButtonMask*, incluso si se deshabilitó anteriormente. Este método trata la elevación de una manera similar: registra los botones comunes como que no requieren elevación si el botón común está disponible pero no se incluye en *nElevationButtonMask*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcommonbuttons"></a><a name="setcommonbuttons"></a>CTaskDialog::SetCommonButtons

Agrega botones comunes `CTaskDialog`al archivo .

```
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parámetros

*nButtonMask*<br/>
[en] Una máscara de los botones para agregar a la `CTaskDialog`.

*nDisabledButtonMask*<br/>
[en] Una máscara de los botones para desactivar.

*nElevationButtonMask*<br/>
[en] Una máscara de los botones que requieren elevación.

### <a name="remarks"></a>Observaciones

No se puede llamar a este método `CTaskDialog` después de crear la ventana de visualización de esta instancia de la clase. Si lo hace, este método produce una excepción.

Los botones indicados por *nButtonMask* invalidan `CTaskDialog`los botones comunes agregados anteriormente al archivo . Solo están disponibles los botones indicados en *nButtonMask.*

Si *nDisabledButtonMask* o *nElevationButtonMask* contienen un botón que no está en *nButtonMask*, este método produce una excepción mediante la macro [ENSURE.](diagnostic-services.md#ensure)

De forma predeterminada, todos los botones comunes están habilitados y no requieren elevación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcontent"></a><a name="setcontent"></a>CTaskDialog::SetContent

Actualiza el contenido `CTaskDialog`del archivo .

```
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>Parámetros

*strContent*<br/>
[en] Cadena que se va a mostrar al usuario.

### <a name="remarks"></a>Observaciones

El contenido `CTaskDialog` de la clase es el texto que se muestra al usuario en la sección principal del cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetdefaultcommandcontrol"></a><a name="setdefaultcommandcontrol"></a>CTaskDialog::SetDefaultCommandControl

Especifica el control de botón de comando predeterminado.

```
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
[en] El identificador del control de botón de comando para que sea el valor predeterminado.

### <a name="remarks"></a>Observaciones

El control de botón de comando `CTaskDialog` predeterminado es el control que se selecciona cuando se muestra por primera vez al usuario.

Este método produce una excepción si no puede encontrar el control de botón de comando especificado por *nCommandControlID*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetdefaultradiobutton"></a><a name="setdefaultradiobutton"></a>CTaskDialog::SetDefaultRadioButton

Especifica el botón de opción predeterminado.

```
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
[en] El ID del botón de radio para ser el valor predeterminado.

### <a name="remarks"></a>Observaciones

El botón de opción predeterminado es `CTaskDialog` el botón que se selecciona cuando se muestra por primera vez al usuario.

Este método produce una excepción si no puede encontrar el botón de opción especificado por *nRadioButtonID*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetdialogwidth"></a><a name="setdialogwidth"></a>CTaskDialog::SetDialogWidth

Ajusta el ancho `CTaskDialog`del archivo .

```
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>Parámetros

*nAncho*<br/>
[en] El ancho del cuadro de diálogo, en píxeles.

### <a name="remarks"></a>Observaciones

El parámetro *nWidth* debe ser mayor o igual que 0. De lo contrario, este método produce una excepción.

Si *nWidth* se establece en 0, este método establece el cuadro de diálogo en el tamaño predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetexpansionarea"></a><a name="setexpansionarea"></a>CTaskDialog::SetExpansionArea

Actualiza el área `CTaskDialog`de expansión del archivo .

```
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>Parámetros

*strExpandedInformation*<br/>
[en] Cadena que `CTaskDialog` se muestra en el cuerpo principal del cuadro de diálogo cuando el usuario hace clic en el botón de expansión.

*strCollapsedLabel*<br/>
[en] Cadena que `CTaskDialog` se muestra junto al botón de expansión cuando se contrae el área expandida.

*strExpandedLabel*<br/>
[en] Cadena que `CTaskDialog` se muestra junto al botón de expansión cuando se muestra el área expandida.

### <a name="remarks"></a>Observaciones

El área de `CTaskDialog` expansión de la clase le permite proporcionar información adicional al usuario. El área de expansión se `CTaskDialog`encuentra en la parte principal de la , situada inmediatamente debajo del título y la cadena de contenido.

Cuando `CTaskDialog` se muestra por primera vez, no muestra la `strCollapsedLabel` información expandida y coloca junto al botón de expansión. Cuando el usuario hace clic `CTaskDialog` en el botón de expansión, muestra *strExpandedInformation* y cambia la etiqueta a *strExpandedLabel*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootericon"></a><a name="setfootericon"></a>CTaskDialog::SetFooterIcon

Actualiza el icono de `CTaskDialog`pie de página del archivo .

```
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>Parámetros

*hFooterIcon*<br/>
[en] El nuevo icono `CTaskDialog`para el archivo .

*lpszFooterIcon*<br/>
[en] El nuevo icono `CTaskDialog`para el archivo .

### <a name="remarks"></a>Observaciones

El icono de pie de página se muestra en la parte inferior de la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Puede tener texto de pie de página asociado. Puede cambiar el texto del pie de página con [CTaskDialog::SetFooterText](#setfootertext).

Este método produce una [ENSURE](diagnostic-services.md#ensure) excepción con `CTaskDialog` la macro ENSURE si se muestra o el parámetro de entrada es NULL.

A `CTaskDialog` solo puede `HICON` `LPCWSTR` aceptar un icono o como un icono de pie de página. Esto se configura estableciendo la opción TDF_USE_HICON_FOOTER en el constructor o [CTaskDialog::SetOptions](#setoptions). De forma `CTaskDialog` predeterminada, está `LPCWSTR` configurado para usarse como tipo de entrada para el icono de pie de página. Este método genera una excepción si intenta establecer el icono mediante el tipo inapropiado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootertext"></a><a name="setfootertext"></a>CTaskDialog::SetFooterText

Actualiza el texto en `CTaskDialog`el pie de página del archivo .

```
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>Parámetros

*strFooterText*<br/>
[en] El nuevo texto para el pie de página.

### <a name="remarks"></a>Observaciones

El icono de pie de página aparece junto `CTaskDialog`al texto del pie de página en la parte inferior del archivo . Puede cambiar el icono de pie de página con [CTaskDialog::SetFooterIcon](#setfootericon).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmainicon"></a><a name="setmainicon"></a>CTaskDialog::SetMainIcon

Actualiza el icono principal `CTaskDialog`del archivo .

```
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>Parámetros

*hMainIcon*<br/>
[en] El nuevo icono.

*lpszMainIcon*<br/>
[en] El nuevo icono.

### <a name="remarks"></a>Observaciones

Este método produce una [ENSURE](diagnostic-services.md#ensure) excepción con `CTaskDialog` la macro ENSURE si se muestra o el parámetro de entrada es NULL.

A `CTaskDialog` solo puede `HICON` `LPCWSTR` aceptar un icono principal o como uno. Puede configurar esto estableciendo la TDF_USE_HICON_MAIN opción en el constructor o en el [CTaskDialog::SetOptions](#setoptions) método. De forma `CTaskDialog` predeterminada, está `LPCWSTR` configurado para usarse como tipo de entrada para el icono principal. Este método genera una excepción si intenta establecer el icono mediante el tipo inapropiado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmaininstruction"></a><a name="setmaininstruction"></a>CTaskDialog::SetMainInstruction

Actualiza la instrucción `CTaskDialog`principal del archivo .

```
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>Parámetros

*strInstrucciones*<br/>
[en] La nueva instrucción principal.

### <a name="remarks"></a>Observaciones

La instrucción `CTaskDialog` principal de la clase es el texto que se muestra al usuario en una fuente en negrita grande. Se encuentra en el cuadro de diálogo debajo de la barra de título.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetoptions"></a><a name="setoptions"></a>CTaskDialog::SetOptions

Configura las opciones `CTaskDialog`para el archivo .

```
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>Parámetros

*nOptionFlag*<br/>
[en] El conjunto de indicadores `CTaskDialog`que se usará para el archivo .

### <a name="remarks"></a>Observaciones

Este método borra todas las `CTaskDialog`opciones actuales para el archivo . Para conservar las opciones actuales, primero debe recuperarlas con [CTaskDialog::GetOptions](#getoptions) y combinarlas con las opciones que desea establecer.

En la tabla siguiente se enumeran todas las opciones válidas.

|||
|-|-|
|TDF_ENABLE_HYPERLINKS|Habilita hipervínculos `CTaskDialog`en el archivo .|
|TDF_USE_HICON_MAIN|Configura el `CTaskDialog` uso `HICON` de a para el icono principal. La alternativa es `LPCWSTR`utilizar un archivo .|
|TDF_USE_HICON_FOOTER|Configura el `CTaskDialog` uso `HICON` de a para el icono de pie de página. La alternativa es `LPCWSTR`utilizar un archivo .|
|TDF_ALLOW_DIALOG_CANCELLATION|Permite al usuario `CTaskDialog` cerrar el uso del teclado o mediante el icono en la esquina superior derecha del cuadro de diálogo, incluso si el botón **Cancelar** no está habilitado. Si esta marca no está establecida y el botón **Cancelar** no está habilitado, el usuario no puede cerrar el cuadro de diálogo mediante Alt+F4, la tecla Escape o el botón de cierre de la barra de título.|
|TDF_USE_COMMAND_LINKS|Configura los `CTaskDialog` controles de botón de uso.|
|TDF_USE_COMMAND_LINKS_NO_ICON|Configura el `CTaskDialog` uso de controles de botón de comando sin mostrar un icono junto al control. TDF_USE_COMMAND_LINKS anula TDF_USE_COMMAND_LINKS_NO_ICON.|
|TDF_EXPAND_FOOTER_AREA|Indica que el área de expansión está expandida actualmente.|
|TDF_EXPANDED_BY_DEFAULT|Determina si el área de expansión está expandida de forma predeterminada.|
|TDF_VERIFICATION_FLAG_CHECKED|Indica que la casilla de verificación está seleccionada actualmente.|
|TDF_SHOW_PROGRESS_BAR|Configura la `CTaskDialog` para mostrar una barra de progreso.|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|Configura la barra de progreso para que sea una barra de progreso de marco. Si habilita esta opción, debe establecer TDF_SHOW_PROGRESS_BAR para que tenga el comportamiento esperado.|
|TDF_CALLBACK_TIMER|Indica que `CTaskDialog` el intervalo de devolución de llamada se establece en aproximadamente 200 milisegundos.|
|TDF_POSITION_RELATIVE_TO_WINDOW|Configura el `CTaskDialog` centrado en relación con la ventana primaria. Si esta marca no está `CTaskDialog` habilitada, se centra en relación con el monitor.|
|TDF_RTL_LAYOUT|Configura el `CTaskDialog` diseño de lectura de derecha a izquierda.|
|TDF_NO_DEFAULT_RADIO_BUTTON|Indica que no se selecciona `CTaskDialog` ningún botón de opción cuando aparece.|
|TDF_CAN_BE_MINIMIZED|Permite al usuario `CTaskDialog`minimizar el archivo . Para admitir esta `CTaskDialog` opción, no puede ser modal. MFC no admite esta opción porque MFC no `CTaskDialog`admite una no versión.|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetprogressbarmarquee"></a><a name="setprogressbarmarquee"></a>CTaskDialog::SetProgressBarMarquee

Configura una barra de `CTaskDialog` marco para el y la agrega al cuadro de diálogo.

```
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>Parámetros

*bHabilitado*<br/>
[en] TRUE para habilitar la barra de marcos; FALSE para deshabilitar la barra de `CTaskDialog`marquesina y quitarla del archivo .

*nMarqueeSpeed*<br/>
[en] Entero que indica la velocidad de la barra de marquesina.

### <a name="remarks"></a>Observaciones

La barra de marquesina `CTaskDialog` aparece debajo del texto principal de la clase.

Utilice *nMarqueeSpeed* para establecer la velocidad de la barra de marquesina; valores más grandes indican una velocidad más lenta. Un valor de 0 para *nMarqueeSpeed* hace que la barra de marquesina se mueva a la velocidad predeterminada para Windows.

Este método produce una excepción con la macro [ENSURE](diagnostic-services.md#ensure) si *nMarqueeSpeed* es menor que 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarposition"></a><a name="setprogressbarposition"></a>CTaskDialog::SetProgressBarPosition

Ajusta la posición de la barra de progreso.

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parámetros

*nProgressPos*<br/>
[en] La posición de la barra de progreso.

### <a name="remarks"></a>Observaciones

Este método produce una excepción con la macro [ENSURE](diagnostic-services.md#ensure) si *nProgressPos* no está en el intervalo de barras de progreso. Puede cambiar el intervalo de la barra de progreso con [CTaskDialog::SetProgressBarRange](#setprogressbarrange).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarrange"></a><a name="setprogressbarrange"></a>CTaskDialog::SetProgressBarRange

Ajusta el rango de la barra de progreso.

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parámetros

*nRangeMin*<br/>
[en] El límite inferior de la barra de progreso.

*nRangeMax*<br/>
[en] El límite superior de la barra de progreso.

### <a name="remarks"></a>Observaciones

La posición de la barra de progreso es relativa a *nRangeMin* y *nRangeMax*. Por ejemplo, si *nRangeMin* es 50 y *nRangeMax* es 100, una posición de 75 está a mitad de camino a través de la barra de progreso. Utilice [CTaskDialog::SetProgressBarPosition](#setprogressbarposition) para establecer la posición de la barra de progreso.

Para mostrar la barra de progreso, la opción TDF_SHOW_PROGRESS_BAR debe estar habilitada y TDF_SHOW_MARQUEE_PROGRESS_BAR no debe estar habilitada. Este método establece automáticamente TDF_SHOW_PROGRESS_BAR y borra TDF_SHOW_MARQUEE_PROGRESS_BAR. Utilice [CTaskDialog::SetOptions](#setoptions) para cambiar manualmente las opciones de esta instancia de la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

Este método produce una excepción con la macro [ENSURE](diagnostic-services.md#ensure) si *nRangeMin* no es menor que *nRangeMax*. Este método también produce una `CTaskDialog` excepción si el ya se muestra y tiene una barra de progreso de marco.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarstate"></a><a name="setprogressbarstate"></a>CTaskDialog::SetProgressBarState

Establece el estado de la barra `CTaskDialog`de progreso y lo muestra en el archivo .

```
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>Parámetros

*nEstado*<br/>
[en] El estado de la barra de progreso. Consulte la sección Comentarios para ver los valores posibles.

### <a name="remarks"></a>Observaciones

Este método produce una [ENSURE](diagnostic-services.md#ensure) excepción con `CTaskDialog` la macro ENSURE si ya se muestra y tiene una barra de progreso de marco.

En la tabla siguiente se enumeran los valores posibles para *nState*. En todos estos casos, la barra de progreso se llenará con el color normal hasta que alcance la posición de parada designada. En ese momento cambiará de color en función del estado.

|||
|-|-|
|PBST_NORMAL|Después de que se `CTaskDialog` llene la barra de progreso, el no cambia el color de la barra. De forma predeterminada, el color normal es verde.|
|PBST_ERROR|Una vez que se `CTaskDialog` llena la barra de progreso, el color de la barra cambia al color del error. De forma predeterminada, es rojo.|
|PBST_PAUSED|Después de que se `CTaskDialog` llene la barra de progreso, el color de la barra cambia al color en pausa. De forma predeterminada, es amarillo.|

Puede establecer dónde se detiene la barra de progreso con [CTaskDialog::SetProgressBarPosition](#setprogressbarposition).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetradiobuttonoptions"></a><a name="setradiobuttonoptions"></a>CTaskDialog::SetRadioButtonOptions

Habilita o deshabilita un botón de opción.

```
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
[en] El ID del control del botón de radio.

*bHabilitado*<br/>
[en] TRUE para habilitar el botón de opción; FALSE para desactivar el botón de opción.

### <a name="remarks"></a>Observaciones

Este método produce una excepción con la macro [ENSURE](diagnostic-services.md#ensure) si *nRadioButtonID* no es un identificador válido para un botón de opción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetverificationcheckbox"></a><a name="setverificationcheckbox"></a>CTaskDialog::SetVerificationCheckbox

Establece el estado activado de la casilla de verificación.

```
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>Parámetros

*bChecked*<br/>
[en] TRUE para tener activada la `CTaskDialog` casilla de verificación cuando se muestra la casilla de verificación; FALSE para que la casilla de `CTaskDialog` verificación no esté seleccionada cuando se muestre.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetverificationcheckboxtext"></a><a name="setverificationcheckboxtext"></a>CTaskDialog::SetVerificationCheckboxText

Establece el texto que se muestra a la derecha de la casilla de verificación.

```
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>Parámetros

*strVerificationText*<br/>
[en] Texto que se muestra en este método junto a la casilla de verificación.

### <a name="remarks"></a>Observaciones

Este método produce una [ENSURE](diagnostic-services.md#ensure) excepción con la `CTaskDialog` macro ENSURE si esta instancia de la clase ya se muestra.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetwindowtitle"></a><a name="setwindowtitle"></a>CTaskDialog::SetWindowTitle

Establece el título `CTaskDialog`del archivo .

```
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>Parámetros

*strWindowTitle*<br/>
[en] El nuevo título `CTaskDialog`para el archivo .

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogshowdialog"></a><a name="showdialog"></a>CTaskDialog::ShowDialog

Crea y `CTaskDialog`muestra un archivo .

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
[en] La cadena que se usará `CTaskDialog`para el contenido del archivo .

*strMainInstruction*<br/>
[en] La instrucción `CTaskDialog`principal de la .

*strTitle*<br/>
[en] El título `CTaskDialog`de la .

*nIDCommandControlsFirst*<br/>
[en] El identificador de cadena del primer comando.

*nIDCommandControlsLast*<br/>
[en] El identificador de cadena del último comando.

*nCommonButtons*<br/>
[en] Una máscara de los botones para agregar a la `CTaskDialog`.

*nTaskDialogOptions*<br/>
[en] El conjunto de opciones `CTaskDialog`que se va a utilizar para el archivo .

*strFooter*<br/>
[en] La cadena que se va a utilizar como pie de página.

### <a name="return-value"></a>Valor devuelto

Entero que corresponde a la selección realizada por el usuario.

### <a name="remarks"></a>Observaciones

Este método estático le permite crear `CTaskDialog` una instancia de `CTaskDialog` la clase sin crear explícitamente un objeto en el código. Dado que `CTaskDialog` no hay ningún objeto, no `CTaskDialog` puede llamar a ningún `CTaskDialog` otro método de la si se utiliza este método para mostrar un al usuario.

Este método crea controles de botón de comando mediante datos del archivo de recursos de la aplicación. La tabla de cadenas del archivo de recursos tiene varias cadenas con identificadores de cadena asociados. Este método agrega un control de botón de comando para cada entrada válida en la tabla de cadenas entre *nIDCommandControlsFirst* y *nCommandControlsLast*, inclusive. Para estos controles de botón de comando, la cadena de la tabla de cadenas es el título del control y el identificador de cadena es el identificador del control.

Vea [CTaskDialog::SetOptions](#setoptions) para obtener una lista de opciones válidas.

Se `CTaskDialog` cierra cuando el usuario selecciona un botón común, un `CTaskDialog`control de vínculo de comando o cierra el archivo . El valor devuelto es el identificador que indica cómo el usuario cerró el cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogtaskdialogcallback"></a><a name="taskdialogcallback"></a>CTaskDialog::TaskDialogCallback

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

*Hwnd*<br/>
[en] Un identificador `m_hWnd` de la `CTaskDialog`estructura para el archivo .

*uNotification*<br/>
[en] El código de notificación que especifica el mensaje generado.

*wParam*<br/>
[en] Más información sobre el mensaje.

*lParam*<br/>
[en] Más información sobre el mensaje.

*dwRefData*<br/>
[en] Puntero al `CTaskDialog` objeto al que se aplica el mensaje de devolución de llamada.

### <a name="return-value"></a>Valor devuelto

Depende del código de notificación específico. Para obtener más información, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

La implementación `TaskDialogCallback` predeterminada de controla el mensaje específico y, a continuación, llama al método On adecuado de la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Por ejemplo, en respuesta al `TaskDialogCallback` mensaje TDN_BUTTON_CLICKED, llama a [CTaskDialog::OnCommandControlClick](#oncommandcontrolclick).

Los valores de *wParam* y *lParam* dependen del mensaje generado específico. Es posible que uno o ambos de estos valores estén vacíos. En la tabla siguiente se enumeran las notificaciones predeterminadas que se admiten y qué representan los valores de *wParam* y *lParam.* Si invalida este método en una clase derivada, debe implementar el código de devolución de llamada para cada mensaje de la tabla siguiente.

|Mensaje de notificación|*wParam* Valor|*lParam* Valor|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|No se usa.|No se usa.|
|TDN_NAVIGATED|No se usa.|No se usa.|
|TDN_BUTTON_CLICKED|El ID de control del botón de comando.|No se usa.|
|TDN_HYPERLINK_CLICKED|No se usa.|Estructura [LPCWSTR](/windows/win32/WinProg/windows-data-types) que contiene el vínculo.|
|TDN_TIMER|Tiempo en milisegundos `CTaskDialog` desde que se creó o se restableció el temporizador.|No se usa.|
|TDN_DESTROYED|No se usa.|No se usa.|
|TDN_RADIO_BUTTON_CLICKED|El ID del botón de radio.|No se usa.|
|TDN_DIALOG_CONSTRUCTED|No se usa.|No se usa.|
|TDN_VERIFICATION_CLICKED|1 si la casilla de verificación está marcada, 0 si no está.|No se usa.|
|TDN_HELP|No se usa.|No se usa.|
|TDN_EXPANDO_BUTTON_CLICKED|0 si el área de expansión está colapsada; distinto de cero si se muestra el texto de expansión.|No se usa.|

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Tutorial: Agregar una clase CTaskDialog a una aplicación](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
