---
title: Clase CTaskDialog | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 856b704b25bed6d350d4e42cd08a138ad8fd8f8f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384577"
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
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|Agrega un control de botón de comando a la `CTaskDialog`.|
|[CTaskDialog::AddRadioButton](#addradiobutton)|Agrega un botón de radio a la `CTaskDialog`.|
|[CTaskDialog::ClickCommandControl](#clickcommandcontrol)|Hace clic en un control de botón de comando o botón comunes mediante programación.|
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|Hace clic en un botón de radio mediante programación.|
|[CTaskDialog::DoModal](#domodal)|Muestra el `CTaskDialog`.|
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|Recupera el número de botones comunes disponibles.|
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|Convierte un estándar de botón de Windows para el tipo de botón comunes asociado con la `CTaskDialog` clase.|
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|Convierte uno de los tipos comunes de botón asociados a la `CTaskDialog` clase a un botón estándar de Windows.|
|[CTaskDialog::GetOptions](#getoptions)|Devuelve las marcas de opción de esta `CTaskDialog`.|
|[CTaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|Devuelve el control de botón de comando seleccionado.|
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|Devuelve el botón de radio seleccionado.|
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|Recupera el estado de la casilla de verificación.|
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|Determina si un control de botón de comando o botón común está habilitado.|
|[CTaskDialog::IsRadioButtonEnabled](#isradiobuttonenabled)|Determina si un botón de radio está habilitado.|
|[IsSupported](#issupported)|Determina si el equipo que ejecuta la aplicación admite el `CTaskDialog`.|
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|Agrega controles de botón de comando mediante el uso de datos de la tabla de cadenas.|
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|Agrega los botones de radio con datos de la tabla de cadenas.|
|[CTaskDialog::NavigateTo](#navigateto)|Transfiere el foco a otro `CTaskDialog`.|
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|El marco llama a este método cuando el usuario hace clic en un control de botón de comando.|
|[CTaskDialog::OnCreate](#oncreate)|El marco llama a este método después de crear el `CTaskDialog`.|
|[CTaskDialog::OnDestroy](#ondestroy)|El marco llama a este método inmediatamente antes destruye el `CTaskDialog`.|
|[CTaskDialog::OnExpandButtonClick](#onexpandbuttonclick)|El marco llama a este método cuando el usuario hace clic en el botón de expansión.|
|[CTaskDialog::OnHelp](#onhelp)|El marco llama a este método cuando el usuario solicita ayuda.|
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|El marco llama a este método cuando el usuario hace clic en un hipervínculo.|
|[CTaskDialog::OnInit](#oninit)|El marco llama a este método cuando el `CTaskDialog` se ha inicializado.|
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|El marco llama a este método cuando el usuario mueve el foco con respecto a los controles el `CTaskDialog`.|
|[CTaskDialog::OnRadioButtonClick](#onradiobuttonclick)|El marco llama a este método cuando el usuario selecciona un control de botón de radio.|
|[CTaskDialog::OnTimer](#ontimer)|El marco llama a este método cuando el temporizador expire.|
|[CTaskDialog::OnVerificationCheckboxClick](#onverificationcheckboxclick)|El marco llama a este método cuando el usuario hace clic en la casilla de verificación.|
|[CTaskDialog::RemoveAllCommandControls](#removeallcommandcontrols)|Quita todos los controles de comando desde el `CTaskDialog`.|
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|Quita todos los botones de radio desde el `CTaskDialog`.|
|[CTaskDialog::SetCommandControlOptions](#setcommandcontroloptions)|Actualiza un control de botón de comando en el `CTaskDialog`.|
|[CTaskDialog::SetCommonButtonOptions](#setcommonbuttonoptions)|Actualiza un subconjunto de los botones comunes para habilitarse y requieren la elevación de UAC.|
|[CTaskDialog::SetCommonButtons](#setcommonbuttons)|Agrega los botones comunes para la `CTaskDialog`.|
|[CTaskDialog::SetContent](#setcontent)|Actualiza el contenido de la `CTaskDialog`.|
|[CTaskDialog::SetDefaultCommandControl](#setdefaultcommandcontrol)|Especifica el control de botón de comando predeterminado.|
|[CTaskDialog::SetDefaultRadioButton](#setdefaultradiobutton)|Especifica el botón de radio predeterminado.|
|[CTaskDialog::SetDialogWidth](#setdialogwidth)|Ajusta el ancho de la `CTaskDialog`.|
|[CTaskDialog::SetExpansionArea](#setexpansionarea)|Actualiza el área de expansión de la `CTaskDialog`.|
|[CTaskDialog::SetFooterIcon](#setfootericon)|Actualiza el icono de pie de página para el `CTaskDialog`.|
|[CTaskDialog::SetFooterText](#setfootertext)|Actualiza el texto en el pie de página de la `CTaskDialog`.|
|[CTaskDialog::SetMainIcon](#setmainicon)|Actualiza el icono principal de la `CTaskDialog`.|
|[CTaskDialog::SetMainInstruction](#setmaininstruction)|Actualiza la instrucción principal de la `CTaskDialog`.|
|[CTaskDialog::SetOptions](#setoptions)|Configura las opciones para el `CTaskDialog`.|
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|Configura una barra de marquesina para el `CTaskDialog` y lo agrega al cuadro de diálogo.|
|[CTaskDialog::SetProgressBarPosition](#setprogressbarposition)|Ajusta la posición de la barra de progreso.|
|[CTaskDialog::SetProgressBarRange](#setprogressbarrange)|Ajusta el intervalo de la barra de progreso.|
|[CTaskDialog::SetProgressBarState](#setprogressbarstate)|Establece el estado de la barra de progreso y lo muestra en el `CTaskDialog`.|
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|Habilita o deshabilita un botón de radio.|
|[CTaskDialog::SetVerificationCheckbox](#setverificationcheckbox)|Establece el estado activado de la casilla de verificación.|
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|Establece el texto en el lado derecho de la casilla de verificación.|
|[CTaskDialog::SetWindowTitle](#setwindowtitle)|Establece el título de la `CTaskDialog`.|
|[CTaskDialog::ShowDialog](#showdialog)|Crea y muestra un `CTaskDialog`.|
|[CTaskDialog::TaskDialogCallback](#taskdialogcallback)|El marco llama a esto en respuesta a diversos mensajes de Windows.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|`m_aButtons`|La matriz de controles de botón de comando para el `CTaskDialog`.|
|`m_aRadioButtons`|La matriz de controles de botón de radio para la `CTaskDialog`.|
|`m_bVerified`|`TRUE` indica que la casilla de verificación está activada; `FALSE` indica que no lo es.|
|`m_footerIcon`|El icono en el pie de página de la `CTaskDialog`.|
|`m_hWnd`|Identificador de la ventana para el `CTaskDialog`.|
|`m_mainIcon`|El icono principal de la `CTaskDialog`.|
|`m_nButtonDisabled`|Una máscara que indica cuál de los botones comunes están deshabilitadas.|
|`m_nButtonElevation`|Una máscara que indica cuál de los botones comunes requieren la elevación de UAC.|
|`m_nButtonId`|El identificador del control de botón de comando seleccionado.|
|`m_nCommonButton`|Una máscara que indica qué botones comunes se muestran en el `CTaskDialog`.|
|`m_nDefaultCommandControl`|El identificador del botón de comando de control que está seleccionada cuando la `CTaskDialog` se muestra.|
|`m_nDefaultRadioButton`|Controlar el identificador del botón de radio que está seleccionada cuando la `CTaskDialog` se muestra.|
|`m_nFlags`|Una máscara que indica las opciones para el `CTaskDialog`.|
|`m_nProgressPos`|La posición actual de la barra de progreso.  Dicho valor debe encontrarse entre `m_nProgressRangeMin` y `m_nProgressRangeMax`.|
|`m_nProgressRangeMax`|El valor máximo para la barra de progreso.|
|`m_nProgressRangeMin`|El valor mínimo de la barra de progreso.|
|`m_nProgressState`|El estado de la barra de progreso. Para obtener más información, consulte [CTaskDialog::SetProgressBarState](#setprogressbarstate).|
|`m_nRadioId`|El identificador del control de botón de radio seleccionado.|
|`m_nWidth`|Ancho del control `CTaskDialog`, en píxeles.|
|`m_strCollapse`|La cadena de la `CTaskDialog` muestra a la derecha del cuadro de expansión cuando se oculta la información expandida.|
|`m_strContent`|La cadena de contenido de la `CTaskDialog`.|
|`m_strExpand`|La cadena de la `CTaskDialog` muestra a la derecha del cuadro de expansión cuando se muestra la información expandida.|
|`m_strFooter`|El pie de página de la `CTaskDialog`.|
|`m_strInformation`|La información ampliada para la `CTaskDialog`.|
|`m_strMainInstruction`|La instrucción principal de la `CTaskDialog`.|
|`m_strTitle`|El título de la `CTaskDialog`.|
|`m_strVerification`|La cadena que el `CTaskDialog` muestra a la derecha de la casilla de verificación.|

## <a name="remarks"></a>Comentarios

La `CTaskDialog` clase reemplaza el cuadro de mensaje estándar de Windows y tiene una funcionalidad adicional, como los nuevos controles para recopilar información del usuario. Esta clase está en la biblioteca MFC en Visual Studio 2010 y versiones posteriores. El `CTaskDialog` está disponible a partir de Windows Vista. Las versiones anteriores de Windows no pueden mostrar el `CTaskDialog` objeto. Use `CTaskDialog::IsSupported` para determinar en tiempo de ejecución si el usuario actual puede mostrar el cuadro de diálogo de tarea. El cuadro de mensaje estándar de Windows todavía se admite.

El `CTaskDialog` está disponible solo cuando se crea la aplicación mediante el uso de la biblioteca de Unicode.

El `CTaskDialog` tiene dos constructores diferentes. Un constructor le permite especificar dos botones de comando y un máximo de seis controles de botón normal. Puede agregar más botones de comando después de crear el `CTaskDialog`. El segundo constructor no es compatible con los botones de comando, pero puede agregar un número ilimitado de controles de botón normal. Para obtener más información acerca de los constructores, vea [CTaskDialog::CTaskDialog](#ctaskdialog).

La siguiente imagen muestra un ejemplo `CTaskDialog` para ilustrar la ubicación de algunos de los controles.

![Ejemplo de CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "ctaskdialogsample") ejemplo de CTaskDialog

## <a name="requirements"></a>Requisitos

**Sistema operativo mínimo necesario:** Windows Vista

**Encabezado:** afxtaskdialog.h

##  <a name="addcommandcontrol"></a>  CTaskDialog::AddCommandControl

Agrega un nuevo control de botón de comando a la `CTaskDialog`.

```
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
[in] El número de identificación del control de comando.

*strCaption*<br/>
[in] La cadena que el `CTaskDialog` muestra al usuario. Use esta cadena para explicar el objetivo del comando.

*bHabilitado*<br/>
[in] Un parámetro booleano que indica si el nuevo botón está habilitado o deshabilitado.

*bRequiresElevation*<br/>
[in] Un parámetro booleano que indica si un comando requiere elevación.

### <a name="remarks"></a>Comentarios

El `CTaskDialog Class` puede mostrar un número ilimitado de controles de botón de comando. Sin embargo, si un `CTaskDialog` controla cualquier botón de comando de muestra, puede mostrar un máximo de seis botones. Si un `CTaskDialog` no tiene ningún control de botón de comando, puede mostrar un número ilimitado de botones.

Cuando el usuario selecciona un control de botón de comando, el `CTaskDialog` se cierra. Si la aplicación muestra el cuadro de diálogo mediante [CTaskDialog::DoModal](#domodal), `DoModal` devuelve el *nCommandControlID* del control de botón de comando seleccionado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="addradiobutton"></a>  CTaskDialog::AddRadioButton

Agrega un botón de radio a la `CTaskDialog`.

```
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
[in] El número de identificación del botón de radio.

*strCaption*<br/>
[in] La cadena que el `CTaskDialog` muestra junto al botón de radio.

*bHabilitado*<br/>
[in] Un parámetro booleano que indica si está habilitado el botón de radio.

### <a name="remarks"></a>Comentarios

Botones de radio para la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md) le permiten reunir información del usuario. Use la función [CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid) para determinar qué botón de radio está seleccionado.

El `CTaskDialog` no requiere que el *nRadioButtonID* parámetros son únicos para cada botón de radio. Sin embargo, puede experimentar comportamientos inesperados si no usa un identificador distinto para cada botón de radio.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="clickcommandcontrol"></a>  CTaskDialog::ClickCommandControl

Hace clic en un control de botón de comando o botón comunes mediante programación.

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
[in] El identificador de comando del control que se haga clic en.

### <a name="remarks"></a>Comentarios

Este método genera el mensaje de windows TDM_CLICK_BUTTON.

##  <a name="clickradiobutton"></a>  CTaskDialog::ClickRadioButton

Hace clic en un botón de radio mediante programación.

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
[in] El identificador de hacer clic en el botón de radio.

### <a name="remarks"></a>Comentarios

Este método genera el mensaje de windows TDM_CLICK_RADIO_BUTTON.

##  <a name="ctaskdialog"></a>  CTaskDialog::CTaskDialog

Crea una instancia de la [CTaskDialog Class](../../mfc/reference/ctaskdialog-class.md).

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
[in] La cadena que se utilizará para el contenido de la `CTaskDialog`.

*strMainInstruction*<br/>
[in] La instrucción principal de la `CTaskDialog`.

*strTitle*<br/>
[in] El título de la `CTaskDialog`.

*nCommonButtons*<br/>
[in] Una máscara de los botones comunes para agregar a la `CTaskDialog`.

*nTaskDialogOptions*<br/>
[in] El conjunto de opciones que se usará para el `CTaskDialog`.

*strFooter*<br/>
[in] Cadena que se usará como el pie de página.

*nIDCommandControlsFirst*<br/>
[in] El identificador de cadena del primer comando.

*nIDCommandControlsLast*<br/>
[in] El identificador de cadena del último comando.

### <a name="remarks"></a>Comentarios

Hay dos formas que puede agregar un `CTaskDialog` a la aplicación. La primera manera consiste en usar uno de los constructores para crear un `CTaskDialog` y mostrarlo utilizando [CTaskDialog::DoModal](#domodal). La segunda manera es usar la función estática [CTaskDialog::ShowDialog](#showdialog), que le permite mostrar un `CTaskDialog` sin crear explícitamente un `CTaskDialog` objeto.

El segundo constructor crea los controles de botón de comando mediante el uso de datos del archivo de recursos de la aplicación. La tabla de cadenas en el archivo de recursos tiene varias cadenas con los identificadores de cadena asociado. Este método agrega un control de botón de comando para cada entrada válida en la tabla de cadenas entre *nIDCommandControlsFirst* y *nCommandControlsLast*, ambos inclusive. Para estos controles de botón de comando, la cadena en la tabla de cadenas es el título del control y el identificador de cadena es el identificador. del control

Consulte [CTaskDialog::SetOptions](#setoptions) para obtener una lista de las opciones válidas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="domodal"></a>  CTaskDialog::DoModal

Muestra el `CTaskDialog` y hace que sea modal.

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parámetros

*hParent*<br/>
[in] La ventana primaria para el `CTaskDialog`.

### <a name="return-value"></a>Valor devuelto

Un entero que corresponde a la selección realizada por el usuario.

### <a name="remarks"></a>Comentarios

Muestra esta instancia de la [CTaskDialog](../../mfc/reference/ctaskdialog-class.md). La aplicación, a continuación, espera a que el usuario cerrar el cuadro de diálogo.

El `CTaskDialog` se cierra cuando el usuario selecciona un botón comunes, un control de vínculo de comando, o se cierra el `CTaskDialog`. El valor devuelto es el identificador que indica cómo el usuario ha cerrado el cuadro de diálogo.

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

Los botones comunes son los botones predeterminados que se proporcionan a [CTaskDialog::CTaskDialog](#ctaskdialog). El [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md) muestra los botones situados en la parte inferior del cuadro de diálogo.

Se proporciona la lista enumerada de los botones en CommCtrl.h.

##  <a name="getcommonbuttonflag"></a>  CTaskDialog::GetCommonButtonFlag

Convierte un estándar de botón de Windows para el tipo de botón comunes asociado con la [CTaskDialog Class](../../mfc/reference/ctaskdialog-class.md).

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>Parámetros

*nButtonId*<br/>
[in] El valor de botón estándar de Windows.

### <a name="return-value"></a>Valor devuelto

El valor de la correspondiente `CTaskDialog` botón comunes. Si no hay ningún botón correspondiente comunes, este método devuelve 0.

##  <a name="getcommonbuttonid"></a>  CTaskDialog::GetCommonButtonId

Convierte uno de los tipos comunes de botón asociados a la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md) a un botón estándar de Windows.

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>Parámetros

*Quitar marca*<br/>
[in] El tipo de botón comunes asociados con la `CTaskDialog` clase.

### <a name="return-value"></a>Valor devuelto

El valor del botón estándar de Windows correspondiente. Si no hay ningún botón de Windows correspondiente, el método devuelve 0.

##  <a name="getoptions"></a>  CTaskDialog::GetOptions

Devuelve las marcas de opción de esta `CTaskDialog`.

```
int GetOptions() const;
```

### <a name="return-value"></a>Valor devuelto

Las marcas para el `CTaskDialog`.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre las opciones disponibles para el [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md), consulte [CTaskDialog::SetOptions](#setoptions).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="getselectedcommandcontrolid"></a>  CTaskDialog::GetSelectedCommandControlID

Devuelve el control de botón de comando seleccionado.

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador del control de botón de comando seleccionado actualmente.

### <a name="remarks"></a>Comentarios

No es necesario usar este método para recuperar el identificador del botón de comando que el usuario seleccionado. Se devuelve ese identificador, ya sea por [CTaskDialog::DoModal](#domodal) o [CTaskDialog::ShowDialog](#showdialog).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="getselectedradiobuttonid"></a>  CTaskDialog::GetSelectedRadioButtonID

Devuelve el botón de radio seleccionado.

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador del botón de radio seleccionado.

### <a name="remarks"></a>Comentarios

Puede usar este método después de que el usuario cierra el cuadro de diálogo para recuperar el botón de radio seleccionado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="getverificationcheckboxstate"></a>  CTaskDialog::GetVerificationCheckboxState

Recupera el estado de la casilla de verificación.

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si la casilla de verificación está activada, es FALSE si no lo está.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="iscommandcontrolenabled"></a>  CTaskDialog::IsCommandControlEnabled

Determina si un control de botón de comando o botón está habilitado.

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
[in] El identificador del control de botón de comando o botón Probar.

### <a name="return-value"></a>Valor devuelto

TRUE si el control está habilitado, FALSE si no lo está.

### <a name="remarks"></a>Comentarios

Puede usar este método para determinar la disponibilidad de los controles de botón de comando y los botones comunes de la `CTaskDialog` clase *.

Si *nCommandControlID* es no es un identificador válido para el bien común `CTaskDialog` botón o un control de botón de comando, este método produce una excepción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="isradiobuttonenabled"></a>  CTaskDialog::IsRadioButtonEnabled

Determina si un botón de radio está habilitado.

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
[in] El identificador del botón de radio para probar.

### <a name="return-value"></a>Valor devuelto

TRUE si el botón de radio está habilitado, FALSE si no lo está.

### <a name="remarks"></a>Comentarios

Si *nRadioButtonID* no es un identificador válido para un botón de radio, este método produce una excepción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="issupported"></a>  IsSupported

Determina si el equipo que ejecuta la aplicación admite el `CTaskDialog`.

```
static BOOL IsSupported();
```

### <a name="return-value"></a>Valor devuelto

TRUE si el equipo es compatible con la `CTaskDialog`; FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Use esta función para determinar en tiempo de ejecución si el equipo que ejecuta la aplicación es compatible con la `CTaskDialog` clase. Si el equipo no admite el `CTaskDialog`, debe proporcionar otro método para comunicar información al usuario. La aplicación se bloqueará si intenta usar un `CTaskDialog` en un equipo que no admite la `CTaskDialog` clase.

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
[in] El identificador de cadena del primer comando.

*nIDCommandControlsLast*<br/>
[in] El identificador de cadena del último comando.

### <a name="remarks"></a>Comentarios

Este método crea los controles de botón de comando mediante el uso de datos del archivo de recursos de la aplicación. La tabla de cadenas en el archivo de recursos tiene varias cadenas con los identificadores de cadena asociado. Nuevos controles de botón de comando agregados mediante este método usar la cadena para el título del control y el identificador de cadena de identificador. del control Proporciona el rango de cadenas seleccionado *nIDCommandControlsFirst* y *nCommandControlsLast*, ambos inclusive. Si hay una entrada vacía en el intervalo, el método no agrega un control de botón de comando para esa entrada.

De forma predeterminada, los nuevos controles de botón de comando están habilitados y no requieren la elevación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="loadradiobuttons"></a>  CTaskDialog::LoadRadioButtons

Agrega controles de botón de radio con datos de la tabla de cadenas.

```
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>Parámetros

*nIDRadioButtonsFirst*<br/>
[in] El identificador de cadena del primer botón de radio.

*nIDRadioButtonsLast*<br/>
[in] El identificador de cadena del último botón de radio.

### <a name="remarks"></a>Comentarios

Este método crea los botones de radio con datos desde el archivo de recursos de la aplicación. La tabla de cadenas en el archivo de recursos tiene varias cadenas con los identificadores de cadena asociado. Agregado mediante este método nuevos botones de radio usan la cadena de título del botón de radio y el identificador de cadena para el Id. del botón de radio Proporciona el rango de cadenas seleccionado *nIDRadioButtonsFirst* y *nRadioButtonsLast*, ambos inclusive. Si hay una entrada vacía en el intervalo, el método no agrega un botón de radio para esa entrada.

De forma predeterminada, se habilitan nuevos botones de radio.

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
[in] El `CTaskDialog` que recibe el foco.

### <a name="remarks"></a>Comentarios

Este método oculta actual `CTaskDialog` cuando muestre el *oTaskDialog*. El *oTaskDialog* se muestra en la misma ubicación que el actual `CTaskDialog`.

##  <a name="oncommandcontrolclick"></a>  CTaskDialog::OnCommandControlClick

El marco llama a este método cuando el usuario hace clic en un control de botón de comando.

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
[in] El identificador del control de botón de comando que el usuario seleccionado.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

##  <a name="oncreate"></a>  CTaskDialog::OnCreate

El marco llama a este método después de crear el `CTaskDialog`.

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

##  <a name="ondestroy"></a>  CTaskDialog::OnDestroy

El marco llama a este método inmediatamente antes destruye el `CTaskDialog`.

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

##  <a name="onexpandbuttonclick"></a>  CTaskDialog::OnExpandButtonClick

El marco llama a este método cuando el usuario hace clic en el botón de expansión.

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>Parámetros

*bExpanded*<br/>
[in] Un valor distinto de cero indica que se muestra la información adicional; 0 indica que se oculta la información adicional.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

##  <a name="onhelp"></a>  CTaskDialog::OnHelp

El marco llama a este método cuando el usuario solicita ayuda.

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

##  <a name="onhyperlinkclick"></a>  CTaskDialog::OnHyperlinkClick

El marco llama a este método cuando el usuario hace clic en un hipervínculo.

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>Parámetros

*strHref*<br/>
[in] Cadena que representa el hipervínculo.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Comentarios

Este método llama a [ShellExecute](/windows/desktop/api/shellapi/nf-shellapi-shellexecutea) antes de devolver S_OK.

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

##  <a name="oninit"></a>  CTaskDialog::OnInit

El marco llama a este método cuando el `CTaskDialog` se ha inicializado.

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

##  <a name="onnavigatepage"></a>  CTaskDialog::OnNavigatePage

El marco llama a este método en respuesta a la [CTaskDialog::NavigateTo](#navigateto) método.

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

##  <a name="onradiobuttonclick"></a>  CTaskDialog::OnRadioButtonClick

El marco llama a este método cuando el usuario selecciona un control de botón de radio.

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
[in] El identificador del control de botón de radio que el usuario hizo clic.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

##  <a name="ontimer"></a>  CTaskDialog::OnTimer

El marco llama a este método cuando el temporizador expire.

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>Parámetros

*ni lTime*<br/>
[in] Tiempo en milisegundos desde el `CTaskDialog` se creó o se restablece el temporizador.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

##  <a name="onverificationcheckboxclick"></a>  CTaskDialog::OnVerificationCheckboxClick

El marco llama a este método cuando el usuario hace clic en la casilla de verificación.

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>Parámetros

*bChecked*<br/>
[in] TRUE indica que la casilla de verificación está seleccionada; FALSE indica que no es así.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar un comportamiento personalizado.

##  <a name="removeallcommandcontrols"></a>  CTaskDialog::RemoveAllCommandControls

Quita todos los controles de botón de comando desde el `CTaskDialog`.

```
void RemoveAllCommandControls();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="removeallradiobuttons"></a>  CTaskDialog::RemoveAllRadioButtons

Quita todos los botones de radio desde el `CTaskDialog`.

```
void RemoveAllRadioButtons();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setcommandcontroloptions"></a>  CTaskDialog::SetCommandControlOptions

Actualiza un control de botón de comando en el `CTaskDialog`.

```
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parámetros

*nCommandControlID*<br/>
[in] Identificador del control de comando que se va a actualizar.

*bHabilitado*<br/>
[in] Un parámetro booleano que indica si el control de botón de comando especificado está habilitado o deshabilitado.

*bRequiresElevation*<br/>
[in] Un parámetro booleano que indica si el control de botón de comando especificado requiere elevación.

### <a name="remarks"></a>Comentarios

Utilice este método para cambiar si un control de botón de comando está habilitado o si requiere elevación después de que se agregó a la `CTaskDialog` clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setcommonbuttonoptions"></a>  CTaskDialog::SetCommonButtonOptions

Actualiza un subconjunto de los botones comunes para habilitarse y requieren la elevación de UAC.

```
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parámetros

*nDisabledButtonMask*<br/>
[in] Una máscara para los botones comunes deshabilitar.

*nElevationButtonMask*<br/>
[in] Una máscara para los botones comunes que requieren la elevación.

### <a name="remarks"></a>Comentarios

Puede establecer los botones comunes disponibles para una instancia de la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md) utilizando el constructor [CTaskDialog::CTaskDialog](#ctaskdialog) y el método [CTaskDialog::SetCommonButtons ](#setcommonbuttons). `CTaskDialog::SetCommonButtonOptions` no admite la adición de nuevos botones comunes.

Si usa este método para deshabilitar o elevar un botón comunes que no está disponible para este `CTaskDialog`, este método produce una excepción mediante el uso de la [Asegúrese](diagnostic-services.md#ensure) macro.

Este método permite cualquier botón que está disponible para el `CTaskDialog` pero no está en el *nDisabledButtonMask*, incluso si se deshabilitó anteriormente. Este método trata la elevación de una manera similar: registra los botones comunes que no requiere una elevación si el botón común está disponible pero no está incluido en *nElevationButtonMask*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcommonbuttons"></a>  CTaskDialog::SetCommonButtons

Agrega los botones comunes para la `CTaskDialog`.

```
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parámetros

*nButtonMask*<br/>
[in] Una máscara de los botones para agregar a la `CTaskDialog`.

*nDisabledButtonMask*<br/>
[in] Una máscara de los botones para deshabilitar.

*nElevationButtonMask*<br/>
[in] Una máscara de los botones que requieren la elevación.

### <a name="remarks"></a>Comentarios

No se puede llamar este método después de la ventana de presentación de esta instancia de la `CTaskDialog` se crea la clase. Si lo hace, este método produce una excepción.

Indican los botones *nButtonMask* invalidar cualquier botones comunes que se agregaron previamente a la `CTaskDialog`. Sólo los botones indican en *nButtonMask* están disponibles.

Si bien *nDisabledButtonMask* o *nElevationButtonMask* contienen un botón que no esté en *nButtonMask*, este método produce una excepción mediante el uso de la [Asegúrese](diagnostic-services.md#ensure) macro.

De forma predeterminada, todos los botones comunes están habilitados y no requieren la elevación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcontent"></a>  CTaskDialog::SetContent

Actualiza el contenido de la `CTaskDialog`.

```
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>Parámetros

*strContent*<br/>
[in] Cadena que se muestra al usuario.

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
[in] El identificador del control de botón de comando en el valor predeterminado.

### <a name="remarks"></a>Comentarios

El control de botón de comando predeterminado es el control que está seleccionado cuando el `CTaskDialog` en primer lugar se muestra al usuario.

Este método produce una excepción si no encuentra el control de botón de comando especificado por *nCommandControlID*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setdefaultradiobutton"></a>  CTaskDialog::SetDefaultRadioButton

Especifica el botón de radio predeterminado.

```
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>Parámetros

*nRadioButtonID*<br/>
[in] El identificador del botón de radio en el valor predeterminado.

### <a name="remarks"></a>Comentarios

El botón de radio predeterminado es el botón que está seleccionado cuando el `CTaskDialog` en primer lugar se muestra al usuario.

Este método produce una excepción si no encuentra el botón de radio especificado por *nRadioButtonID*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setdialogwidth"></a>  CTaskDialog::SetDialogWidth

Ajusta el ancho de la `CTaskDialog`.

```
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>Parámetros

*nWidth*<br/>
[in] El ancho del cuadro de diálogo, en píxeles.

### <a name="remarks"></a>Comentarios

El parámetro *nWidth* debe ser mayor o igual que 0. En caso contrario, este método produce una excepción.

Si *nWidth* se establece en 0, este método establece el cuadro de diálogo en el tamaño predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setexpansionarea"></a>  CTaskDialog::SetExpansionArea

Actualiza el área de expansión de la `CTaskDialog`.

```
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>Parámetros

*strExpandedInformation*<br/>
[in] La cadena que el `CTaskDialog` muestra en el cuerpo principal del cuadro de diálogo cuando el usuario hace clic en el botón de expansión.

*strCollapsedLabel*<br/>
[in] La cadena que el `CTaskDialog` muestra junto al botón de expansión cuando se contrae el área expandida.

*strExpandedLabel*<br/>
[in] La cadena que el `CTaskDialog` muestra junto al botón de expansión cuando se muestre el área expandida.

### <a name="remarks"></a>Comentarios

El área de expansión de la `CTaskDialog` clase le permite proporcionar información adicional al usuario. El área de expansión está en la parte principal de la `CTaskDialog`, que se encuentra inmediatamente debajo de la cadena de título y el contenido.

Cuando el `CTaskDialog` es la primera muestra, no se muestra la información expandida y coloca `strCollapsedLabel` situada junto al botón de expansión. Cuando el usuario hace clic en el botón de expansión, el `CTaskDialog` muestra *strExpandedInformation* y cambia la etiqueta a *strExpandedLabel*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootericon"></a>  CTaskDialog::SetFooterIcon

Actualiza el icono de pie de página de la `CTaskDialog`.

```
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>Parámetros

*hFooterIcon*<br/>
[in] El icono nuevo para el `CTaskDialog`.

*lpszFooterIcon*<br/>
[in] El icono nuevo para el `CTaskDialog`.

### <a name="remarks"></a>Comentarios

El icono de pie de página se muestra en la parte inferior de la [CTaskDialog Class](../../mfc/reference/ctaskdialog-class.md). Puede tener asociados texto de pie de página. Puede cambiar el texto de pie de página con [CTaskDialog::SetFooterText](#setfootertext).

Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si la `CTaskDialog` se muestra o el parámetro de entrada es NULL.

Un `CTaskDialog` sólo puede aceptar un `HICON` o `LPCWSTR` como un icono de pie de página. Esto se configura estableciendo la opción TDF_USE_HICON_FOOTER en el constructor o [CTaskDialog::SetOptions](#setoptions). De forma predeterminada, el `CTaskDialog` está configurado para usar `LPCWSTR` como el tipo de entrada para el icono de pie de página. Este método genera una excepción si se intenta establecer el icono con el tipo inadecuado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootertext"></a>  CTaskDialog::SetFooterText

Actualiza el texto en el pie de página de la `CTaskDialog`.

```
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>Parámetros

*strFooterText*<br/>
[in] El nuevo texto del pie de página.

### <a name="remarks"></a>Comentarios

El icono de pie de página aparece al lado del texto de pie de página en la parte inferior de la `CTaskDialog`. Puede cambiar el icono de pie de página con [CTaskDialog::SetFooterIcon](#setfootericon).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmainicon"></a>  CTaskDialog::SetMainIcon

Actualiza el icono principal de la `CTaskDialog`.

```
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>Parámetros

*hMainIcon*<br/>
[in] El nuevo icono.

*lpszMainIcon*<br/>
[in] El nuevo icono.

### <a name="remarks"></a>Comentarios

Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si la `CTaskDialog` se muestra o el parámetro de entrada es NULL.

Un `CTaskDialog` sólo puede aceptar un `HICON` o `LPCWSTR` como un icono principal. Puede configurar esto estableciendo la opción TDF_USE_HICON_MAIN en el constructor o en el [CTaskDialog::SetOptions](#setoptions) método. De forma predeterminada, el `CTaskDialog` está configurado para usar `LPCWSTR` como el tipo de entrada para el icono principal. Este método genera una excepción si se intenta establecer el icono con el tipo inadecuado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmaininstruction"></a>  CTaskDialog::SetMainInstruction

Actualiza la instrucción principal de la `CTaskDialog`.

```
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>Parámetros

*strInstructions*<br/>
[in] La instrucción principal nuevo.

### <a name="remarks"></a>Comentarios

La instrucción principal de la `CTaskDialog` clase es el texto que se muestra al usuario en un tamaño de fuente negrita. Se encuentra en el cuadro de diálogo debajo de la barra de título.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setoptions"></a>  CTaskDialog::SetOptions

Configura las opciones para el `CTaskDialog`.

```
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>Parámetros

*nOptionFlag*<br/>
[in] El conjunto de indicadores que se usará para el `CTaskDialog`.

### <a name="remarks"></a>Comentarios

Este método borra todas las opciones actuales de la `CTaskDialog`. Para conservar las opciones actuales, se debe recuperar primero con [CTaskDialog::GetOptions](#getoptions) y combinarlos con las opciones que desea establecer.

En la tabla siguiente se enumera todas las opciones válidas.

|||
|-|-|
|TDF_ENABLE_HYPERLINKS|Permite que los hipervínculos en el `CTaskDialog`.|
|TDF_USE_HICON_MAIN|Configura el `CTaskDialog` para usar un `HICON` el icono principal. La alternativa es usar un `LPCWSTR`.|
|TDF_USE_HICON_FOOTER|Configura el `CTaskDialog` para usar un `HICON` para el icono de pie de página. La alternativa es usar un `LPCWSTR`.|
|TDF_ALLOW_DIALOG_CANCELLATION|Permite al usuario cerrar la `CTaskDialog` mediante el teclado o mediante el icono en la esquina superior derecha del cuadro de diálogo, incluso si la **cancelar** botón no está habilitado. Si no se establece esta marca y el **cancelar** botón no está habilitado, el usuario no puede cerrar el cuadro de diálogo con ALT+F4, la tecla Escape, o la barra de título botón Cerrar.|
|TDF_USE_COMMAND_LINKS|Configura el `CTaskDialog` usar controles de botón de comando.|
|TDF_USE_COMMAND_LINKS_NO_ICON|Configura el `CTaskDialog` usar controles de botón de comando sin mostrar un icono junto al control. TDF_USE_COMMAND_LINKS invalida TDF_USE_COMMAND_LINKS_NO_ICON.|
|TDF_EXPAND_FOOTER_AREA|Indica que el área de expansión está expandido actualmente.|
|TDF_EXPANDED_BY_DEFAULT|Determina si el área de expansión se expande de forma predeterminada.|
|TDF_VERIFICATION_FLAG_CHECKED|Indica que la casilla de verificación está seleccionada actualmente.|
|TDF_SHOW_PROGRESS_BAR|Configura el `CTaskDialog` para mostrar una barra de progreso.|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|Configura la barra de progreso para que sea una barra de progreso de marquesina. Si habilita esta opción, debe establecer TDF_SHOW_PROGRESS_BAR tengan el comportamiento esperado.|
|TDF_CALLBACK_TIMER|Indica que el `CTaskDialog` intervalo de devolución de llamada se establece en aproximadamente 200 milisegundos.|
|TDF_POSITION_RELATIVE_TO_WINDOW|Configura el `CTaskDialog` se centre en relación con la ventana primaria. Si no se habilita esta marca, el `CTaskDialog` se centra en relación con el monitor.|
|TDF_RTL_LAYOUT|Configura el `CTaskDialog` para un diseño de lectura de derecha a izquierda.|
|TDF_NO_DEFAULT_RADIO_BUTTON|Indica que ningún botón de radio está seleccionado cuando el `CTaskDialog` aparece.|
|TDF_CAN_BE_MINIMIZED|Permite al usuario minimizar la `CTaskDialog`. Para admitir esta opción, el `CTaskDialog` no puede ser modal. MFC no admite esta opción porque MFC no admite un no modal `CTaskDialog`.|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setprogressbarmarquee"></a>  CTaskDialog::SetProgressBarMarquee

Configura una barra de marquesina para el `CTaskDialog` y lo agrega al cuadro de diálogo.

```
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>Parámetros

*bHabilitado*<br/>
[in] TRUE para habilitar la barra de marquesina. FALSE para deshabilitar la barra de marquesina y lo quita de la `CTaskDialog`.

*nMarqueeSpeed*<br/>
[in] Un entero que indica la velocidad de la barra de marquesina.

### <a name="remarks"></a>Comentarios

La barra de marquesina aparece debajo del texto principal de la `CTaskDialog` clase.

Use *nMarqueeSpeed* para establecer la velocidad de la barra de marquesina; los valores mayores indican una velocidad. Un valor de 0 para *nMarqueeSpeed* hace que la barra de marquesina se mueva a la velocidad predeterminada para Windows.

Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si *nMarqueeSpeed* es menor que 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarposition"></a>  CTaskDialog::SetProgressBarPosition

Ajusta la posición de la barra de progreso.

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parámetros

*nProgressPos*<br/>
[in] La posición de la barra de progreso.

### <a name="remarks"></a>Comentarios

Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si *nProgressPos* no está en el intervalo de la barra de progreso. Puede cambiar el intervalo de la barra de progreso con [CTaskDialog::SetProgressBarRange](#setprogressbarrange).

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
[in] El límite inferior de la barra de progreso.

*nRangeMax*<br/>
[in] El límite superior de la barra de progreso.

### <a name="remarks"></a>Comentarios

La posición de la barra de progreso es relativa a *nRangeMin* y *nRangeMax*. Por ejemplo, si *nRangeMin* es 50 y *nRangeMax* es 100, una posición de 75 a mitad de camino a través de la barra de progreso. Use [CTaskDialog::SetProgressBarPosition](#setprogressbarposition) para establecer la posición de la barra de progreso.

Para mostrar la barra de progreso, la opción que debe habilitarse TDF_SHOW_PROGRESS_BAR y TDF_SHOW_MARQUEE_PROGRESS_BAR no deben estar habilitada. Este método establece TDF_SHOW_PROGRESS_BAR y borra TDF_SHOW_MARQUEE_PROGRESS_BAR automáticamente. Use [CTaskDialog::SetOptions](#setoptions) para cambiar manualmente las opciones para esta instancia de la [CTaskDialog Class](../../mfc/reference/ctaskdialog-class.md).

Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si *nRangeMin* es menos *nRangeMax*. Este método también produce una excepción si el `CTaskDialog` ya se muestra y tiene una barra de progreso de marquesina.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarstate"></a>  CTaskDialog::SetProgressBarState

Establece el estado de la barra de progreso y lo muestra en el `CTaskDialog`.

```
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>Parámetros

*nState*<br/>
[in] El estado de la barra de progreso. Consulte la sección Comentarios para los valores posibles.

### <a name="remarks"></a>Comentarios

Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si la `CTaskDialog` ya se muestra y tiene una barra de progreso de marquesina.

La tabla siguiente enumeran los valores posibles para *nState*. En todos estos casos, la barra de progreso rellenará con el color normal hasta que alcance la posición de tabulación designado. En ese momento cambiará de color en función del estado.

|||
|-|-|
|PBST_NORMAL|Después el progreso de la barra se complete, el `CTaskDialog` no cambia el color de la barra. De forma predeterminada, el color normal es verde.|
|PBST_ERROR|Después el progreso de la barra se complete, el `CTaskDialog` cambia el color de la barra en el color del error. De forma predeterminada, esto está en rojo.|
|PBST_PAUSED|Después el progreso de la barra se complete, el `CTaskDialog` cambia el color de la barra en el color en pausa. De forma predeterminada, esto está en amarillo.|

Puede establecer que la barra de progreso se detiene con [CTaskDialog::SetProgressBarPosition](#setprogressbarposition).

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
[in] El identificador del control de botón de radio.

*bHabilitado*<br/>
[in] TRUE para habilitar el botón de radio; FALSE para deshabilitar el botón de radio.

### <a name="remarks"></a>Comentarios

Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si *nRadioButtonID* no es un identificador válido para un botón de radio.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setverificationcheckbox"></a>  CTaskDialog::SetVerificationCheckbox

Establece el estado activado de la casilla de verificación.

```
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>Parámetros

*bChecked*<br/>
[in] True para la casilla de verificación seleccionó cuando la `CTaskDialog` se muestra; FALSE para que la casilla de verificación no está seleccionada cuando la `CTaskDialog` se muestra.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setverificationcheckboxtext"></a>  CTaskDialog::SetVerificationCheckboxText

Establece el texto que se muestra a la derecha de la casilla de verificación.

```
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>Parámetros

*strVerificationText*<br/>
[in] El texto que este método se muestra junto a la casilla de verificación.

### <a name="remarks"></a>Comentarios

Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si esta instancia de la `CTaskDialog` ya se muestra la clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setwindowtitle"></a>  CTaskDialog::SetWindowTitle

Establece el título de la `CTaskDialog`.

```
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>Parámetros

*strWindowTitle*<br/>
[in] El nuevo título para el `CTaskDialog`.

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
[in] La cadena que se utilizará para el contenido de la `CTaskDialog`.

*strMainInstruction*<br/>
[in] La instrucción principal de la `CTaskDialog`.

*strTitle*<br/>
[in] El título de la `CTaskDialog`.

*nIDCommandControlsFirst*<br/>
[in] El identificador de cadena del primer comando.

*nIDCommandControlsLast*<br/>
[in] El identificador de cadena del último comando.

*nCommonButtons*<br/>
[in] Una máscara de los botones para agregar a la `CTaskDialog`.

*nTaskDialogOptions*<br/>
[in] El conjunto de opciones que se usará para el `CTaskDialog`.

*strFooter*<br/>
[in] Cadena que se usará como el pie de página.

### <a name="return-value"></a>Valor devuelto

Un entero que corresponde a la selección realizada por el usuario.

### <a name="remarks"></a>Comentarios

Este método estático le permite crear una instancia de la `CTaskDialog` clase sin crear explícitamente un `CTaskDialog` objeto en el código. Porque no hay ningún `CTaskDialog` objeto, no puede llamar a otros métodos de la `CTaskDialog` si usa este método para mostrar un `CTaskDialog` al usuario.

Este método crea los controles de botón de comando mediante el uso de datos del archivo de recursos de la aplicación. La tabla de cadenas en el archivo de recursos tiene varias cadenas con los identificadores de cadena asociado. Este método agrega un control de botón de comando para cada entrada válida en la tabla de cadenas entre *nIDCommandControlsFirst* y *nCommandControlsLast*, ambos inclusive. Para estos controles de botón de comando, la cadena en la tabla de cadenas es el título del control y el identificador de cadena es el identificador. del control

Consulte [CTaskDialog::SetOptions](#setoptions) para obtener una lista de las opciones válidas.

El `CTaskDialog` se cierra cuando el usuario selecciona un botón comunes, un control de vínculo de comando, o se cierra el `CTaskDialog`. El valor devuelto es el identificador que indica cómo el usuario ha cerrado el cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

##  <a name="taskdialogcallback"></a>  CTaskDialog::TaskDialogCallback

El marco llama a este método en respuesta a diversos mensajes de Windows.

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

*HWND*<br/>
[in] Un identificador de la `m_hWnd` de estructura para el `CTaskDialog`.

*uNotification*<br/>
[in] El código de notificación que especifica el mensaje generado.

*wParam*<br/>
[in] Más información sobre el mensaje.

*lParam*<br/>
[in] Más información sobre el mensaje.

*dwRefData*<br/>
[in] Un puntero a la `CTaskDialog` objeto que se aplica el mensaje de devolución de llamada.

### <a name="return-value"></a>Valor devuelto

Depende del código de notificación específico. Vea la sección Comentarios para obtener más información.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de `TaskDialogCallback` controla el mensaje específico y, a continuación, llama a la correspondiente en el método de la [CTaskDialog Class](../../mfc/reference/ctaskdialog-class.md). Por ejemplo, en respuesta al mensaje TDN_BUTTON_CLICKED, `TaskDialogCallback` llamadas [CTaskDialog::OnCommandControlClick](#oncommandcontrolclick).

Los valores de *wParam* y *lParam* dependen el mensaje generado específico. Es posible que uno o ambos de estos valores para estar vacío. La siguiente tabla enumera las notificaciones de predeterminado que se admiten y lo que los valores de *wParam* y *lParam* representan. Si invalida este método en una clase derivada, debe implementar el código de devolución de llamada para cada mensaje en la tabla siguiente.

|Mensaje de notificación|*wParam* valor|*lParam* valor|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|No usado.|No usado.|
|TDN_NAVIGATED|No usado.|No usado.|
|TDN_BUTTON_CLICKED|Identificador de control de botón de comando|No usado.|
|TDN_HYPERLINK_CLICKED|No usado.|Un [LPCWSTR](/windows/desktop/WinProg/windows-data-types) estructura que contiene el vínculo.|
|TDN_TIMER|Tiempo en milisegundos desde el `CTaskDialog` se creó o se restablece el temporizador.|No usado.|
|TDN_DESTROYED|No usado.|No usado.|
|TDN_RADIO_BUTTON_CLICKED|El identificador del botón de radio.|No usado.|
|TDN_DIALOG_CONSTRUCTED|No usado.|No usado.|
|TDN_VERIFICATION_CLICKED|1 si está activada la casilla de verificación, 0 si no lo está.|No usado.|
|TDN_HELP|No usado.|No usado.|
|TDN_EXPANDO_BUTTON_CLICKED|0 si el área de expansión está contraída; distinto de cero si se muestra el texto de expansión.|No usado.|

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Tutorial: Agregar una clase CTaskDialog a una aplicación](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
