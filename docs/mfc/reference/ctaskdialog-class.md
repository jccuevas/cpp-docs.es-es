---
title: Clase CTaskDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ecde926a27fbf4fa74cabdec6ff4d54f7d89216
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
|[CTaskDialog::ClickCommandControl](#clickcommandcontrol)|Haga clic en un control de botón de comando o un botón comunes mediante programación.|  
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|Haga clic en un botón de radio mediante programación.|  
|[CTaskDialog::DoModal](#domodal)|Muestra el `CTaskDialog`.|  
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|Recupera el número de botones comunes disponibles.|  
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|Convierte un estándar de botón de Windows para el tipo de botón común asociado a la `CTaskDialog` clase.|  
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|Convierte uno de los tipos comunes de botón asociados a la `CTaskDialog` clase a un botón de Windows estándar.|  
|[CTaskDialog::GetOptions](#getoptions)|Devuelve las marcas de opción de este `CTaskDialog`.|  
|[CTaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|Devuelve el control de botón de comando seleccionado.|  
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|Devuelve el botón de radio seleccionado.|  
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|Recupera el estado de la casilla de verificación.|  
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|Determina si un control de botón de comando o un botón común está habilitado.|  
|[CTaskDialog::IsRadioButtonEnabled](#isradiobuttonenabled)|Determina si un botón de radio está habilitado.|  
|[CTaskDialog::IsSupported](#issupported)|Determina si el equipo que ejecuta la aplicación admite la `CTaskDialog`.|  
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|Agrega controles de botón de comando mediante el uso de datos de la tabla de cadenas.|  
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|Agrega botones de radio con datos de la tabla de cadenas.|  
|[CTaskDialog::NavigateTo](#navigateto)|Transfiere el foco a otra `CTaskDialog`.|  
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|El marco de trabajo llama a este método cuando el usuario hace clic en un control de botón de comando.|  
|[CTaskDialog::OnCreate](#oncreate)|El marco de trabajo llama a este método después de crear el `CTaskDialog`.|  
|[CTaskDialog::OnDestroy](#ondestroy)|El marco de trabajo llama a este método inmediatamente antes de que se destruirán los `CTaskDialog`.|  
|[CTaskDialog::OnExpandButtonClick](#onexpandbuttonclick)|El marco de trabajo llama a este método cuando el usuario hace clic en el botón de expansión.|  
|[CTaskDialog::OnHelp](#onhelp)|El marco de trabajo llama a este método cuando el usuario solicita ayuda.|  
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|El marco de trabajo llama a este método cuando el usuario hace clic en un hipervínculo.|  
|[CTaskDialog::OnInit](#oninit)|El marco de trabajo llama a este método cuando el `CTaskDialog` se inicializa.|  
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|El marco de trabajo llama a este método cuando el usuario mueve el foco con respecto a los controles el `CTaskDialog`.|  
|[CTaskDialog::OnRadioButtonClick](#onradiobuttonclick)|El marco de trabajo llama a este método cuando el usuario selecciona un control de botón de radio.|  
|[CTaskDialog::OnTimer](#ontimer)|El marco de trabajo llama a este método cuando el temporizador expire.|  
|[CTaskDialog::OnVerificationCheckboxClick](#onverificationcheckboxclick)|El marco de trabajo llama a este método cuando el usuario hace clic en la casilla de verificación.|  
|[CTaskDialog::RemoveAllCommandControls](#removeallcommandcontrols)|Quita todos los controles de comando de la `CTaskDialog`.|  
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|Quita todos los botones de radio de la `CTaskDialog`.|  
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
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|Configura una barra de marquesina de la `CTaskDialog` y lo agrega al cuadro de diálogo.|  
|[CTaskDialog::SetProgressBarPosition](#setprogressbarposition)|Ajusta la posición de la barra de progreso.|  
|[CTaskDialog::SetProgressBarRange](#setprogressbarrange)|Ajusta el intervalo de la barra de progreso.|  
|[CTaskDialog::SetProgressBarState](#setprogressbarstate)|Establece el estado de la barra de progreso y lo muestra en el `CTaskDialog`.|  
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|Habilita o deshabilita un botón de radio.|  
|[CTaskDialog::SetVerificationCheckbox](#setverificationcheckbox)|Establece el estado de activación de la casilla de verificación.|  
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|Establece el texto en el lado derecho de la casilla de verificación.|  
|[CTaskDialog::SetWindowTitle](#setwindowtitle)|Establece el título de la `CTaskDialog`.|  
|[CTaskDialog::ShowDialog](#showdialog)|Crea y muestra un `CTaskDialog`.|  
|[CTaskDialog::TaskDialogCallback](#taskdialogcallback)|El marco de trabajo llama a esto en respuesta a diversos mensajes de Windows.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|`m_aButtons`|La matriz de controles de botón de comando para el `CTaskDialog`.|  
|`m_aRadioButtons`|La matriz de controles de botón de radio para la `CTaskDialog`.|  
|`m_bVerified`|`TRUE`indica que la casilla de verificación está activada; `FALSE` indica no lo es.|  
|`m_footerIcon`|El icono en el pie de página de la `CTaskDialog`.|  
|`m_hWnd`|Un identificador de la ventana para el `CTaskDialog`.|  
|`m_mainIcon`|El icono principal de la `CTaskDialog`.|  
|`m_nButtonDisabled`|Una máscara que indica cuál de los botones comunes están deshabilitados.|  
|`m_nButtonElevation`|Una máscara que indica cuál de los botones comunes requieren la elevación de UAC.|  
|`m_nButtonId`|El identificador del control de botón de comando seleccionado.|  
|`m_nCommonButton`|Una máscara que indica qué botones comunes se muestran en la `CTaskDialog`.|  
|`m_nDefaultCommandControl`|El identificador del botón de comando de control que se activa cuando la `CTaskDialog` se muestra.|  
|`m_nDefaultRadioButton`|Controlar el identificador del botón de radio que se activa cuando la `CTaskDialog` se muestra.|  
|`m_nFlags`|Una máscara que indica las opciones para el `CTaskDialog`.|  
|`m_nProgressPos`|La posición actual de la barra de progreso.  Dicho valor debe encontrarse entre `m_nProgressRangeMin` y `m_nProgressRangeMax`.|  
|`m_nProgressRangeMax`|El valor máximo de la barra de progreso.|  
|`m_nProgressRangeMin`|El valor mínimo de la barra de progreso.|  
|`m_nProgressState`|El estado de la barra de progreso. Para obtener más información, consulte [CTaskDialog::SetProgressBarState](#setprogressbarstate).|  
|`m_nRadioId`|El identificador del control de botón de radio seleccionado.|  
|`m_nWidth`|El ancho de la `CTaskDialog` en píxeles.|  
|`m_strCollapse`|La cadena de la `CTaskDialog` muestra a la derecha del cuadro de expansión cuando se oculta la información ampliada.|  
|`m_strContent`|La cadena de contenido de la `CTaskDialog`.|  
|`m_strExpand`|La cadena de la `CTaskDialog` muestra a la derecha del cuadro de expansión cuando se muestra la información ampliada.|  
|`m_strFooter`|El pie de página de la `CTaskDialog`.|  
|`m_strInformation`|La información ampliada para la `CTaskDialog`.|  
|`m_strMainInstruction`|La instrucción principal de la `CTaskDialog`.|  
|`m_strTitle`|El título de la `CTaskDialog`.|  
|`m_strVerification`|La cadena que el `CTaskDialog` muestra a la derecha de la casilla de verificación.|  
  
## <a name="remarks"></a>Comentarios  
 La `CTaskDialog` clase reemplaza el cuadro de mensaje de Windows estándar y tiene funcionalidad adicional, como los nuevos controles para recopilar información del usuario. Esta clase está en la biblioteca MFC en [!INCLUDE[vs_dev10_long](../../build/includes/vs_dev10_long_md.md)]. El `CTaskDialog` está disponible a partir de [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]. Las versiones anteriores de Windows no pueden mostrar el `CTaskDialog` objeto. Utilice `CTaskDialog::IsSupported` para determinar en tiempo de ejecución si el usuario actual pueda mostrar el cuadro de diálogo de tarea. El cuadro de mensaje estándar de Windows se sigue admitiendo en [!INCLUDE[vs_dev10_long](../../build/includes/vs_dev10_long_md.md)].  
  
 La `CTaskDialog` está disponible solo cuando se compila la aplicación mediante el uso de la biblioteca de Unicode.  
  
 El `CTaskDialog` tiene dos constructores diferentes. Un constructor permite especificar dos botones de comando y un máximo de seis controles de botón normal. Puede agregar más botones de comando después de crear el `CTaskDialog`. El segundo constructor no es compatible con los botones de comando, pero puede agregar un número ilimitado de controles de botón normal. Para obtener más información acerca de los constructores, vea [CTaskDialog::CTaskDialog](#ctaskdialog).  
  
 La siguiente imagen muestra un ejemplo `CTaskDialog` para ilustrar la ubicación de algunos de los controles.  
  
 ![Ejemplo de CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "ctaskdialogsample")  
Ejemplo de la clase CTaskDialog  
  
## <a name="requirements"></a>Requisitos  
 **Sistema operativo mínimo necesario:**[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
 **Encabezado:** afxtaskdialog.h  
  
##  <a name="addcommandcontrol"></a>CTaskDialog::AddCommandControl  
 Agrega un nuevo control de botón de comando a la `CTaskDialog`.  
  
```  
void AddCommandControl(
    int nCommandControlID,  
    const CString& strCaption,  
    BOOL bEnabled = TRUE,  
    BOOL bRequiresElevation = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nCommandControlID`  
 El número de identificación del control de comando.  
  
 [in] `strCaption`  
 La cadena que el `CTaskDialog` muestra al usuario. Utilice esta cadena para explicar el objetivo del comando.  
  
 [in] `bEnabled`  
 Un parámetro booleano que indica si el nuevo botón está habilitado o deshabilitado.  
  
 [in] `bRequiresElevation`  
 Un parámetro booleano que indica si un comando requiere elevación.  
  
### <a name="remarks"></a>Comentarios  
 La `CTaskDialog Class` puede mostrar un número ilimitado de controles de botón de comando. Sin embargo, si un `CTaskDialog` controla cualquier botón de comando de muestra, puede mostrar un máximo de seis botones. Si un `CTaskDialog` no tiene ningún control de botón de comando, puede mostrar un número ilimitado de botones.  
  
 Cuando el usuario selecciona un control de botón de comando, el `CTaskDialog` se cierra. Si la aplicación muestra el cuadro de diálogo mediante [CTaskDialog::DoModal](#domodal), `DoModal` devuelve el `nCommandControlID` del control de botón de comando seleccionado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="addradiobutton"></a>CTaskDialog::AddRadioButton  
 Agrega un botón de radio a la `CTaskDialog`.  
  
```  
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,  
    const CString& strCaption,  
    BOOL bEnabled = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nRadioButtonID`  
 El número de identificación del botón de radio.  
  
 [in] `strCaption`  
 La cadena que el `CTaskDialog` muestra situada junto al botón de radio.  
  
 [in] `bEnabled`  
 Un parámetro booleano que indica si está habilitado el botón de radio.  
  
### <a name="remarks"></a>Comentarios  
 Botones de radio para la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md) permiten recopilar información del usuario. Use la función [CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid) para determinar qué botón de radio está seleccionado.  
  
 El `CTaskDialog` no requiere que el `nRadioButtonID` parámetros son únicos para cada botón de radio. Sin embargo, puede experimentar un comportamiento inesperado si no usa un identificador distinto para cada botón de radio.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="clickcommandcontrol"></a>CTaskDialog::ClickCommandControl  
 Haga clic en un control de botón de comando o un botón comunes mediante programación.  
  
```  
protected:  
void ClickCommandControl(int nCommandControlID) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nCommandControlID`  
 El identificador de comando del control que se haga clic en.  
  
### <a name="remarks"></a>Comentarios  
 Este método genera el mensaje de windows `TDM_CLICK_BUTTON`.  
  
##  <a name="clickradiobutton"></a>CTaskDialog::ClickRadioButton  
 Haga clic en un botón de radio mediante programación.  
  
```  
protected:  
void ClickRadioButton(int nRadioButtonID) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nRadioButtonID`  
 El identificador de haga clic en el botón de radio.  
  
### <a name="remarks"></a>Comentarios  
 Este método genera el mensaje de windows `TDM_CLICK_RADIO_BUTTON`.  
  
##  <a name="ctaskdialog"></a>CTaskDialog::CTaskDialog  
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
 [in] `strContent`  
 La cadena que se utilizará para el contenido de la `CTaskDialog`.  
  
 [in] `strMainInstruction`  
 La instrucción principal de la `CTaskDialog`.  
  
 [in] `strTitle`  
 El título de la `CTaskDialog`.  
  
 [in] `nCommonButtons`  
 Una máscara de los botones comunes para agregar a la `CTaskDialog`.  
  
 [in] `nTaskDialogOptions`  
 El conjunto de opciones que se usará para el `CTaskDialog`.  
  
 [in] `strFooter`  
 La cadena que se usará como el pie de página.  
  
 [in] `nIDCommandControlsFirst`  
 El identificador de cadena del primer comando.  
  
 [in] `nIDCommandControlsLast`  
 El identificador de cadena del último comando.  
  
### <a name="remarks"></a>Comentarios  
 Hay dos maneras que puede agregar un `CTaskDialog` a la aplicación. La primera manera consiste en usar uno de los constructores para crear un `CTaskDialog` y mostrarlo mediante [CTaskDialog::DoModal](#domodal). La segunda manera consiste en utilizar la función estática [CTaskDialog::ShowDialog](#showdialog), lo que permite mostrar un `CTaskDialog` sin crear explícitamente un `CTaskDialog` objeto.  
  
 El segundo constructor crea controles de botón de comando mediante el uso de datos desde el archivo de recursos de la aplicación. La tabla de cadenas en el archivo de recursos tiene varias cadenas con identificadores de cadena asociado. Este método agrega un control de botón de comando para cada entrada válida en la tabla de cadenas entre `nIDCommandControlsFirst` y `nCommandControlsLast`, ambos inclusive. Para estos controles de botón de comando, la cadena de la tabla de cadenas es el título del control y el identificador de cadena es el identificador. del control  
  
 Vea [CTaskDialog::SetOptions](#setoptions) para obtener una lista de opciones válidas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="domodal"></a>CTaskDialog::DoModal  
 Muestra el `CTaskDialog` y la convierte en modal.  
  
```  
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hParent`  
 La ventana primaria para el `CTaskDialog`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero que corresponde a la selección realizada por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 Muestra esta instancia de la [CTaskDialog](../../mfc/reference/ctaskdialog-class.md). La aplicación, a continuación, espera a que el usuario cierre el cuadro de diálogo.  
  
 El `CTaskDialog` se cierra cuando el usuario selecciona un botón comunes, un control de vínculo de comando, o se cierra el `CTaskDialog`. El valor devuelto es el identificador que indica cómo el usuario ha cerrado el cuadro de diálogo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="getcommonbuttoncount"></a>CTaskDialog::GetCommonButtonCount  
 Recupera el número de botones comunes.  
  
```  
int GetCommonButtonCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de botones comunes disponibles.  
  
### <a name="remarks"></a>Comentarios  
 Los botones comunes son los botones predeterminados que se proporcionan a [CTaskDialog::CTaskDialog](#ctaskdialog). El [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md) muestra los botones situados en la parte inferior del cuadro de diálogo.  
  
 La lista enumerada de botones se proporciona en CommCtrl.h.  
  
##  <a name="getcommonbuttonflag"></a>CTaskDialog::GetCommonButtonFlag  
 Convierte un estándar de botón de Windows para el tipo de botón común asociado a la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md).  
  
```  
int GetCommonButtonFlag(int nButtonId) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nButtonId`  
 El valor de botón estándar de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de la correspondiente `CTaskDialog` botón comunes. Si no hay ningún botón comunes correspondiente, este método devuelve 0.  
  
##  <a name="getcommonbuttonid"></a>CTaskDialog::GetCommonButtonId  
 Convierte uno de los tipos comunes de botón asociados a la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md) a un botón de Windows estándar.  
  
```  
int GetCommonButtonId(int nFlag);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nFlag`  
 El tipo de botón común asociado a la `CTaskDialog` clase.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor del botón estándar de Windows correspondiente. Si no hay ningún botón de Windows correspondiente, el método devuelve 0.  
  
##  <a name="getoptions"></a>CTaskDialog::GetOptions  
 Devuelve las marcas de opción de este `CTaskDialog`.  
  
```  
int GetOptions() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Las marcas para el `CTaskDialog`.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de las opciones disponibles para la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md), consulte [CTaskDialog::SetOptions](#setoptions).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="getselectedcommandcontrolid"></a>CTaskDialog::GetSelectedCommandControlID  
 Devuelve el control de botón de comando seleccionado.  
  
```  
int GetSelectedCommandControlID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del control de botón de comando seleccionado actualmente.  
  
### <a name="remarks"></a>Comentarios  
 No es necesario utilizar este método para recuperar el identificador del botón de comando que el usuario seleccionado. Este identificador es devuelto por [CTaskDialog::DoModal](#domodal) o [CTaskDialog::ShowDialog](#showdialog).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="getselectedradiobuttonid"></a>CTaskDialog::GetSelectedRadioButtonID  
 Devuelve el botón de radio seleccionado.  
  
```  
int GetSelectedRadioButtonID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del botón de radio seleccionado.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizar este método después de que el usuario cierra el cuadro de diálogo para recuperar el botón de radio seleccionado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="getverificationcheckboxstate"></a>CTaskDialog::GetVerificationCheckboxState  
 Recupera el estado de la casilla de verificación.  
  
```  
BOOL GetVerificationCheckboxState() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se activa la casilla de verificación, `FALSE` si no lo está.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]  
  
##  <a name="iscommandcontrolenabled"></a>CTaskDialog::IsCommandControlEnabled  
 Determina si un control de botón de comando o un botón está habilitado.  
  
```  
BOOL IsCommandControlEnabled(int nCommandControlID) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nCommandControlID`  
 El identificador del control de botón de comando o botón Probar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el control está habilitado, `FALSE` si no lo está.  
  
### <a name="remarks"></a>Comentarios  
 Puede usar este método para determinar la disponibilidad de los controles de botón de comando y los botones comunes de la `CTaskDialog Class`.  
  
 Si `nCommandControlID` es no es un identificador válido para cada uno un común `CTaskDialog` botón o un control de botón de comando, este método produce una excepción.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="isradiobuttonenabled"></a>CTaskDialog::IsRadioButtonEnabled  
 Determina si un botón de radio está habilitado.  
  
```  
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nRadioButtonID`  
 El identificador del botón de radio para probar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si está habilitado el botón de radio, `FALSE` si no lo está.  
  
### <a name="remarks"></a>Comentarios  
 Si `nRadioButtonID` no es un identificador válido para un botón de radio, este método produce una excepción.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="issupported"></a>CTaskDialog::IsSupported  
 Determina si el equipo que ejecuta la aplicación admite la `CTaskDialog`.  
  
```  
static BOOL IsSupported();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el equipo es compatible con la `CTaskDialog`; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para determinar en tiempo de ejecución si el equipo que ejecuta la aplicación es compatible con la `CTaskDialog Class`. Si el equipo no admite el `CTaskDialog`, debe proporcionar otro método para comunicar información al usuario. La aplicación se bloqueará si intenta usar un `CTaskDialog` en un equipo que no es compatible con la `CTaskDialog` clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]  
  
##  <a name="loadcommandcontrols"></a>CTaskDialog::LoadCommandControls  
 Agrega controles de botón de comando mediante el uso de datos de la tabla de cadenas.  
  
```  
void LoadCommandControls(
    int nIDCommandControlsFirst,  
    int nIDCommandControlsLast);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIDCommandControlsFirst`  
 El identificador de cadena del primer comando.  
  
 [in] `nIDCommandControlsLast`  
 El identificador de cadena del último comando.  
  
### <a name="remarks"></a>Comentarios  
 Este método crea controles de botón de comando mediante el uso de datos desde el archivo de recursos de la aplicación. La tabla de cadenas en el archivo de recursos tiene varias cadenas con identificadores de cadena asociado. Nuevos controles de botón de comando agregados mediante este método usa la cadena para el título del control y el identificador de cadena para el identificador. del control Proporciona el intervalo de cadenas seleccionado `nIDCommandControlsFirst` y `nCommandControlsLast`, ambos inclusive. Si hay una entrada vacía en el intervalo, el método no agrega un control de botón de comando para esa entrada.  
  
 De forma predeterminada, los nuevos controles de botón de comando están habilitados y no requieren la elevación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="loadradiobuttons"></a>CTaskDialog::LoadRadioButtons  
 Agrega controles de botón de radio con datos de la tabla de cadenas.  
  
```  
void LoadRadioButtons(
    int nIDRadioButtonsFirst,  
    int nIDRadioButtonsLast);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIDRadioButtonsFirst`  
 El identificador de cadena del primer botón de radio.  
  
 [in] `nIDRadioButtonsLast`  
 El identificador de cadena del último botón de radio.  
  
### <a name="remarks"></a>Comentarios  
 Este método crea botones de radio con datos desde el archivo de recursos de la aplicación. La tabla de cadenas en el archivo de recursos tiene varias cadenas con identificadores de cadena asociado. Nuevos botones de radio agregados mediante este método usa la cadena para el título del botón de radio y el identificador de cadena para Id. del botón de radio Proporciona el intervalo de cadenas seleccionado `nIDRadioButtonsFirst` y `nRadioButtonsLast`, ambos inclusive. Si hay una entrada vacía en el intervalo, el método no agrega un botón de radio correspondiente a esa entrada.  
  
 De forma predeterminada, se habilitan los nuevos botones de radio.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="navigateto"></a>CTaskDialog::NavigateTo  
 Transfiere el foco a otra `CTaskDialog`.  
  
```  
protected:  
void NavigateTo(CTaskDialog& oTaskDialog) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `oTaskDialog`  
 El `CTaskDialog` que recibe el foco.  
  
### <a name="remarks"></a>Comentarios  
 Este método oculta actual `CTaskDialog` cuando muestre el `oTaskDialog`. El `oTaskDialog` se muestra en la misma ubicación que el actual `CTaskDialog`.  
  
##  <a name="oncommandcontrolclick"></a>CTaskDialog::OnCommandControlClick  
 El marco de trabajo llama a este método cuando el usuario hace clic en un control de botón de comando.  
  
```  
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nCommandControlID`  
 El identificador del control de botón de comando que el usuario seleccionado.  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para implementar un comportamiento personalizado.  
  
##  <a name="oncreate"></a>CTaskDialog::OnCreate  
 El marco de trabajo llama a este método después de crear el `CTaskDialog`.  
  
```  
virtual HRESULT OnCreate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para implementar un comportamiento personalizado.  
  
##  <a name="ondestroy"></a>CTaskDialog::OnDestroy  
 El marco de trabajo llama a este método inmediatamente antes de que se destruirán los `CTaskDialog`.  
  
```  
virtual HRESULT OnDestroy();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para implementar un comportamiento personalizado.  
  
##  <a name="onexpandbuttonclick"></a>CTaskDialog::OnExpandButtonClick  
 El marco de trabajo llama a este método cuando el usuario hace clic en el botón de expansión.  
  
```  
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bExpanded`  
 Un valor distinto de cero indica que se muestra la información adicional; 0 indica que se oculta la información adicional.  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para implementar un comportamiento personalizado.  
  
##  <a name="onhelp"></a>CTaskDialog::OnHelp  
 El marco de trabajo llama a este método cuando el usuario solicita ayuda.  
  
```  
virtual HRESULT OnHelp();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para implementar un comportamiento personalizado.  
  
##  <a name="onhyperlinkclick"></a>CTaskDialog::OnHyperlinkClick  
 El marco de trabajo llama a este método cuando el usuario hace clic en un hipervínculo.  
  
```  
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strHref`  
 La cadena que representa el hipervínculo.  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a [ShellExecute](http://msdn.microsoft.com/library/windows/desktop/bb762153) antes de devolver `S_OK`.  
  
 Invalide este método en una clase derivada para implementar un comportamiento personalizado.  
  
##  <a name="oninit"></a>CTaskDialog::OnInit  
 El marco de trabajo llama a este método cuando el `CTaskDialog` se inicializa.  
  
```  
virtual HRESULT OnInit();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para implementar un comportamiento personalizado.  
  
##  <a name="onnavigatepage"></a>CTaskDialog::OnNavigatePage  
 El marco de trabajo llama a este método en respuesta a la [CTaskDialog::NavigateTo](#navigateto) método.  
  
```  
virtual HRESULT OnNavigatePage();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para implementar un comportamiento personalizado.  
  
##  <a name="onradiobuttonclick"></a>CTaskDialog::OnRadioButtonClick  
 El marco de trabajo llama a este método cuando el usuario selecciona un control de botón de radio.  
  
```  
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nRadioButtonID`  
 El identificador del control de botón de radio que el usuario ha hecho clic.  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para implementar un comportamiento personalizado.  
  
##  <a name="ontimer"></a>CTaskDialog::OnTimer  
 El marco de trabajo llama a este método cuando el temporizador expire.  
  
```  
virtual HRESULT OnTimer(long lTime);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lTime`  
 Tiempo en milisegundos desde el `CTaskDialog` se creó o se ha restablecido el temporizador.  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para implementar un comportamiento personalizado.  
  
##  <a name="onverificationcheckboxclick"></a>CTaskDialog::OnVerificationCheckboxClick  
 El marco de trabajo llama a este método cuando el usuario hace clic en la casilla de verificación.  
  
```  
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bChecked`  
 `TRUE`indica que la casilla de verificación está seleccionada; `FALSE` indica no lo es.  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para implementar un comportamiento personalizado.  
  
##  <a name="removeallcommandcontrols"></a>CTaskDialog::RemoveAllCommandControls  
 Quita todos los controles de botón de comando de la `CTaskDialog`.  
  
```  
void RemoveAllCommandControls();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="removeallradiobuttons"></a>CTaskDialog::RemoveAllRadioButtons  
 Quita todos los botones de radio de la `CTaskDialog`.  
  
```  
void RemoveAllRadioButtons();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="setcommandcontroloptions"></a>CTaskDialog::SetCommandControlOptions  
 Actualiza un control de botón de comando en el `CTaskDialog`.  
  
```  
void SetCommandControlOptions(
    int nCommandControlID,  
    BOOL bEnabled,  
    BOOL bRequiresElevation = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nCommandControlID`  
 El identificador del control de comando para actualizar.  
  
 [in] `bEnabled`  
 Un parámetro booleano que indica si el control de botón de comando especificado está habilitado o deshabilitado.  
  
 [in] `bRequiresElevation`  
 Un parámetro booleano que indica si el control de botón de comando especificado requiere elevación.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para cambiar si un control de botón de comando está habilitado o si requiere elevación después de que se ha agregado a la `CTaskDialog Class`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="setcommonbuttonoptions"></a>CTaskDialog::SetCommonButtonOptions  
 Actualiza un subconjunto de los botones comunes para habilitarse y requieren la elevación de UAC.  
  
```  
void SetCommonButtonOptions(
    int nDisabledButtonMask,  
    int nElevationButtonMask = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nDisabledButtonMask`  
 Una máscara de los botones comunes deshabilitar.  
  
 [in] `nElevationButtonMask`  
 Una máscara de los botones comunes que requieren elevación.  
  
### <a name="remarks"></a>Comentarios  
 Puede establecer los botones comunes disponibles para una instancia de la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md) utilizando el constructor [CTaskDialog::CTaskDialog](#ctaskdialog) y el método [CTaskDialog::SetCommonButtons ](#setcommonbuttons). `CTaskDialog::SetCommonButtonOptions`no admite la adición de nuevos botones comunes.  
  
 Si utiliza este método para deshabilitar o elevar un botón comunes que no está disponible para el `CTaskDialog`, este método produce una excepción utilizando la [Asegúrese](diagnostic-services.md#ensure) macro.  
  
 Este método permite que cualquier botón que está disponible para el `CTaskDialog` pero no está en el `nDisabledButtonMask`, incluso si se deshabilitó anteriormente. Este método trata la elevación de una manera similar: registra los botones comunes como no requerir elevación de permisos si el botón común está disponible pero no se incluye en `nElevationButtonMask`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]  
  
##  <a name="setcommonbuttons"></a>CTaskDialog::SetCommonButtons  
 Agrega los botones comunes para la `CTaskDialog`.  
  
```  
void SetCommonButtons(
    int nButtonMask,  
    int nDisabledButtonMask = 0,  
    int nElevationButtonMask = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nButtonMask`  
 Una máscara de los botones para agregar a la `CTaskDialog`.  
  
 [in] `nDisabledButtonMask`  
 Una máscara de los botones para deshabilitar.  
  
 [in] `nElevationButtonMask`  
 Una máscara de los botones que requieren elevación.  
  
### <a name="remarks"></a>Comentarios  
 No puede llamar a este método después de la ventana para esta instancia de la `CTaskDialog Class` se crea. Si lo hace, este método produce una excepción.  
  
 Los botones indican por `nButtonMask` invalidar cualquier botones comunes agregado anteriormente a la `CTaskDialog`. Sólo los botones indican en `nButtonMask` están disponibles.  
  
 Si el valor `nDisabledButtonMask` o `nElevationButtonMask` contienen un botón que no esté en `nButtonMask`, este método produce una excepción utilizando la [Asegúrese](diagnostic-services.md#ensure) macro.  
  
 De forma predeterminada, todos los botones comunes están habilitados y no requieren la elevación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]  
  
##  <a name="setcontent"></a>CTaskDialog::SetContent  
 Actualiza el contenido de la `CTaskDialog`.  
  
```  
void SetContent(const CString& strContent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strContent`  
 Cadena que se muestra al usuario.  
  
### <a name="remarks"></a>Comentarios  
 El contenido de la `CTaskDialog Class` es el texto que se muestra al usuario en la sección principal del cuadro de diálogo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setdefaultcommandcontrol"></a>CTaskDialog::SetDefaultCommandControl  
 Especifica el control de botón de comando predeterminado.  
  
```  
void SetDefaultCommandControl(int nCommandControlID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nCommandControlID`  
 El identificador del control de botón de comando como el valor predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 El control de botón de comando predeterminado es el control que está seleccionado cuando la `CTaskDialog` en primer lugar se muestra al usuario.  
  
 Este método produce una excepción si no se encuentra el control de botón de comando especificado por `nCommandControlID`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="setdefaultradiobutton"></a>CTaskDialog::SetDefaultRadioButton  
 Especifica el botón de radio predeterminado.  
  
```  
void SetDefaultRadioButton(int nRadioButtonID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nRadioButtonID`  
 El identificador del botón de radio para que sea el predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 El botón de radio predeterminada es la que está seleccionado cuando la `CTaskDialog` en primer lugar se muestra al usuario.  
  
 Este método produce una excepción si no se encuentra el botón de radio especificado por `nRadioButtonID`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="setdialogwidth"></a>CTaskDialog::SetDialogWidth  
 Ajusta el ancho de la `CTaskDialog`.  
  
```  
void SetDialogWidth(int nWidth = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nWidth`  
 El ancho del cuadro de diálogo, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro `nWidth` debe ser mayor o igual que 0. En caso contrario, este método produce una excepción.  
  
 Si `nWidth` se establece en 0, este método establece el cuadro de diálogo para el tamaño predeterminado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setexpansionarea"></a>CTaskDialog::SetExpansionArea  
 Actualiza el área de expansión de la `CTaskDialog`.  
  
```  
void SetExpansionArea(
    const CString& strExpandedInformation,  
    const CString& strCollapsedLabel = _T(""),  
    const CString& strExpandedLabel = _T(""));
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strExpandedInformation`  
 La cadena que el `CTaskDialog` muestra en el cuerpo principal del cuadro de diálogo cuando el usuario hace clic en el botón de expansión.  
  
 [in] `strCollapsedLabel`  
 La cadena que el `CTaskDialog` muestra situada junto al botón de expansión cuando se contrae el área expandida.  
  
 [in] `strExpandedLabel`  
 La cadena que el `CTaskDialog` muestra situada junto al botón de expansión cuando se muestra el área expandida.  
  
### <a name="remarks"></a>Comentarios  
 El área de expansión de la `CTaskDialog Class` le permite proporcionar información adicional al usuario. El área de expansión está en la parte principal de la `CTaskDialog`, que se encuentra inmediatamente debajo de la cadena de título y el contenido.  
  
 Cuando el `CTaskDialog` es la primera muestra, no se muestra la información ampliada y coloca `strCollapsedLabel` situada junto al botón de expansión. Cuando el usuario hace clic en el botón de expansión, el `CTaskDialog` muestra `strExpandedInformation` y cambia la etiqueta a `strExpandedLabel`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setfootericon"></a>CTaskDialog::SetFooterIcon  
 Actualiza el icono de pie de página de la `CTaskDialog`.  
  
```  
void SetFooterIcon(HICON hFooterIcon);  
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hFooterIcon`  
 El icono nuevo para el `CTaskDialog`.  
  
 [in] `lpszFooterIcon`  
 El icono nuevo para el `CTaskDialog`.  
  
### <a name="remarks"></a>Comentarios  
 El icono de pie de página se muestra en la parte inferior de la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Puede tener asociados texto de pie de página. Puede cambiar el texto de pie de página con [CTaskDialog::SetFooterText](#setfootertext).  
  
 Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si la `CTaskDialog` se muestra o el parámetro de entrada es `NULL`.  
  
 A `CTaskDialog` sólo pueden aceptar un `HICON` o `LPCWSTR` como un icono de pie de página. Esto se configura al establecer la opción `TDF_USE_HICON_FOOTER` en el constructor o [CTaskDialog::SetOptions](#setoptions). De forma predeterminada, el `CTaskDialog` está configurado para usar `LPCWSTR` como el tipo de entrada para el icono de pie de página. Este método genera una excepción si se intenta establecer el icono con el tipo apropiado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setfootertext"></a>CTaskDialog::SetFooterText  
 Actualiza el texto en el pie de página de la `CTaskDialog`.  
  
```  
void SetFooterText(const CString& strFooterText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strFooterText`  
 El nuevo texto del pie de página.  
  
### <a name="remarks"></a>Comentarios  
 El icono de pie de página aparece al lado del texto de pie de página en la parte inferior de la `CTaskDialog`. Puede cambiar el icono de pie de página con [CTaskDialog::SetFooterIcon](#setfootericon).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setmainicon"></a>CTaskDialog::SetMainIcon  
 Actualiza el icono principal de la `CTaskDialog`.  
  
```  
void SetMainIcon(HICON hMainIcon);  
void SetMainIcon(LPCWSTR lpszMainIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hMainIcon`  
 El icono de nuevo.  
  
 [in] `lpszMainIcon`  
 El icono de nuevo.  
  
### <a name="remarks"></a>Comentarios  
 Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si la `CTaskDialog` se muestra o el parámetro de entrada es `NULL`.  
  
 A `CTaskDialog` sólo pueden aceptar un `HICON` o `LPCWSTR` como un icono principal. Puede configurar esto estableciendo el `TDF_USE_HICON_MAIN` opción en el constructor o en la [CTaskDialog::SetOptions](#setoptions) método. De forma predeterminada, el `CTaskDialog` está configurado para usar `LPCWSTR` como el tipo de entrada para el icono principal. Este método genera una excepción si se intenta establecer el icono con el tipo apropiado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setmaininstruction"></a>CTaskDialog::SetMainInstruction  
 Actualiza la instrucción principal de la `CTaskDialog`.  
  
```  
void SetMainInstruction(const CString& strInstructions);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strInstructions`  
 La nueva instrucción principal.  
  
### <a name="remarks"></a>Comentarios  
 La instrucción principal de la `CTaskDialog Class` es texto que se muestra al usuario en un tamaño de fuente negrita. Se encuentra en el cuadro de diálogo debajo de la barra de título.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setoptions"></a>CTaskDialog::SetOptions  
 Configura las opciones para el `CTaskDialog`.  
  
```  
void SetOptions(int nOptionFlag);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nOptionFlag`  
 El conjunto de indicadores que se usará para el `CTaskDialog`.  
  
### <a name="remarks"></a>Comentarios  
 Este método borra todas las opciones actuales de la `CTaskDialog`. Para conservar las opciones actuales, se debe recuperar primero con [CTaskDialog::GetOptions](#getoptions) y combinarlos con las opciones que desea establecer.  
  
 En la tabla siguiente se enumera todas las opciones válidas.  
  
 `TDF_ENABLE_HYPERLINKS`  
 Habilita los hipervínculos en el `CTaskDialog`.  
  
 `TDF_USE_HICON_MAIN`  
 Configura el `CTaskDialog` utilizar un `HICON` del icono principal. La alternativa es usar un `LPCWSTR`.  
  
 `TDF_USE_HICON_FOOTER`  
 Configura el `CTaskDialog` utilizar un `HICON` del icono de pie de página. La alternativa es usar un `LPCWSTR`.  
  
 `TDF_ALLOW_DIALOG_CANCELLATION`  
 Permite al usuario cerrar la `CTaskDialog` mediante el teclado o mediante el icono en la esquina superior derecha del cuadro de diálogo, incluso si la **cancelar** botón no está habilitado. Si no se establece esta marca y el **cancelar** botón no está habilitado, el usuario no puede cerrar el cuadro de diálogo mediante el uso de ALT+F4, la tecla ESC, o el botón Cerrar de la barra de título.  
  
 `TDF_USE_COMMAND_LINKS`  
 Configura el `CTaskDialog` usar controles de botón de comando.  
  
 `TDF_USE_COMMAND_LINKS_NO_ICON`  
 Configura el `CTaskDialog` usar controles de botón de comando sin mostrar un icono junto al control. `TDF_USE_COMMAND_LINKS` reemplaza a `TDF_USE_COMMAND_LINKS_NO_ICON`.  
  
 `TDF_EXPAND_FOOTER_AREA`  
 Indica que actualmente se expande el área de expansión.  
  
 `TDF_EXPANDED_BY_DEFAULT`  
 Determina si el área de expansión se expande de forma predeterminada.  
  
 `TDF_VERIFICATION_FLAG_CHECKED`  
 Indica que la casilla de verificación está seleccionada actualmente.  
  
 `TDF_SHOW_PROGRESS_BAR`  
 Configura el `CTaskDialog` para mostrar una barra de progreso.  
  
 `TDF_SHOW_MARQUEE_PROGRESS_BAR`  
 Configura la barra de progreso para que sea una barra de progreso de marquesina. Si habilita esta opción, debe establecer `TDF_SHOW_PROGRESS_BAR` tenga el comportamiento esperado.  
  
 `TDF_CALLBACK_TIMER`  
 Indica que el `CTaskDialog` intervalo de devolución de llamada está establecido en aproximadamente 200 milisegundos.  
  
 `TDF_POSITION_RELATIVE_TO_WINDOW`  
 Configura el `CTaskDialog` se centre en relación con la ventana primaria. Si esta marca no está habilitada, el `CTaskDialog` se centra en relación con el monitor.  
  
 `TDF_RTL_LAYOUT`  
 Configura el `CTaskDialog` para un diseño de lectura de derecha a izquierda.  
  
 `TDF_NO_DEFAULT_RADIO_BUTTON`  
 Indica que no se ha seleccionado ningún botón de radio cuando el `CTaskDialog` aparece.  
  
 `TDF_CAN_BE_MINIMIZED`  
 Permite al usuario minimizar la `CTaskDialog`. Para admitir esta opción, el `CTaskDialog` no puede ser modal. MFC no admite esta opción porque MFC no admite un no modal `CTaskDialog`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setprogressbarmarquee"></a>CTaskDialog::SetProgressBarMarquee  
 Configura una barra de marquesina de la `CTaskDialog` y lo agrega al cuadro de diálogo.  
  
```  
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,  
    int nMarqueeSpeed = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnabled`  
 `TRUE`Para habilitar la barra de marquesina. `FALSE` para deshabilitar la barra de marquesina y quítelo de la `CTaskDialog`.  
  
 [in] `nMarqueeSpeed`  
 Un entero que indica la velocidad de la barra de marquesina.  
  
### <a name="remarks"></a>Comentarios  
 La barra de marquesina aparece debajo del texto principal de la `CTaskDialog Class`.  
  
 Use `nMarqueeSpeed` para establecer la velocidad de la barra de marquesina; valores mayores indican una velocidad más lenta. Un valor de 0 para `nMarqueeSpeed` hace que la barra de marquesina se mueva a la velocidad predeterminada para [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)].  
  
 Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si `nMarqueeSpeed` es menor que 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]  
  
##  <a name="setprogressbarposition"></a>CTaskDialog::SetProgressBarPosition  
 Ajusta la posición de la barra de progreso.  
  
```  
void SetProgressBarPosition(int nProgressPos);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nProgressPos`  
 La posición de la barra de progreso.  
  
### <a name="remarks"></a>Comentarios  
 Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si `nProgressPos` no está en el intervalo de la barra de progreso. Puede cambiar el intervalo de la barra de progreso con [CTaskDialog::SetProgressBarRange](#setprogressbarrange).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]  
  
##  <a name="setprogressbarrange"></a>CTaskDialog::SetProgressBarRange  
 Ajusta el intervalo de la barra de progreso.  
  
```  
void SetProgressBarRange(
    int nRangeMin,  
    int nRangeMax);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nRangeMin`  
 El límite inferior de la barra de progreso.  
  
 [in] `nRangeMax`  
 El límite superior de la barra de progreso.  
  
### <a name="remarks"></a>Comentarios  
 La posición de la barra de progreso es relativa a `nRangeMin` y `nRangeMax`. Por ejemplo, si `nRangeMin` es 50 y `nRangeMax` es 100, una posición de 75 está en medio a través de la barra de progreso. Use [CTaskDialog::SetProgressBarPosition](#setprogressbarposition) para establecer la posición de la barra de progreso.  
  
 Para mostrar el progreso de la barra, la opción `TDF_SHOW_PROGRESS_BAR` debe estar habilitado y `TDF_SHOW_MARQUEE_PROGRESS_BAR` no debe estar habilitada. Este método establece automáticamente `TDF_SHOW_PROGRESS_BAR` y borra `TDF_SHOW_MARQUEE_PROGRESS_BAR`. Use [CTaskDialog::SetOptions](#setoptions) para cambiar manualmente las opciones de esta instancia de la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md).  
  
 Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si `nRangeMin` es no es menor que `nRangeMax`. Este método también produce una excepción si el `CTaskDialog` ya se está mostrando y tiene una barra de progreso de marquesina.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]  
  
##  <a name="setprogressbarstate"></a>CTaskDialog::SetProgressBarState  
 Establece el estado de la barra de progreso y lo muestra en el `CTaskDialog`.  
  
```  
void SetProgressBarState(int nState = PBST_NORMAL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nState`  
 El estado de la barra de progreso. Vea la sección Comentarios de los valores posibles.  
  
### <a name="remarks"></a>Comentarios  
 Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si la `CTaskDialog` ya se está mostrando y tiene una barra de progreso de marquesina.  
  
 En la tabla siguiente se enumera los posibles valores para `nState`. En todos estos casos, la barra de progreso se rellenará con el color normal hasta que alcance la posición de tabulación designado. En ese momento cambiará de color en función del estado.  
  
 PBST_NORMAL  
 Después el progreso de la barra se rellena, el `CTaskDialog` no cambia el color de la barra. De forma predeterminada, el color normal es verde.  
  
 PBST_ERROR  
 Después el progreso de la barra se rellena, el `CTaskDialog` cambia el color de la barra en el color de error. De forma predeterminada, esto está en rojo.  
  
 PBST_PAUSED  
 Después el progreso de la barra se rellena, el `CTaskDialog` cambia el color de la barra en el color en pausa. De forma predeterminada, esto está de color amarillo.  
  
 Puede establecer que la barra de progreso se detiene con [CTaskDialog::SetProgressBarPosition](#setprogressbarposition).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]  
  
##  <a name="setradiobuttonoptions"></a>CTaskDialog::SetRadioButtonOptions  
 Habilita o deshabilita un botón de radio.  
  
```  
void SetRadioButtonOptions(
    int nRadioButtonID,  
    BOOL bEnabled);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nRadioButtonID`  
 El identificador del control de botón de radio.  
  
 [in] `bEnabled`  
 `TRUE`Para habilitar el botón de radio; `FALSE` para deshabilitar el botón de radio.  
  
### <a name="remarks"></a>Comentarios  
 Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si `nRadioButtonID` no es un identificador válido para un botón de radio.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="setverificationcheckbox"></a>CTaskDialog::SetVerificationCheckbox  
 Establece el estado de activación de la casilla de verificación.  
  
```  
void SetVerificationCheckbox(BOOL bChecked);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bChecked`  
 `TRUE`para que la comprobación de la casilla de verificación seleccionada cuando la `CTaskDialog` se muestra; `FALSE` para que la comprobación de la casilla de verificación no está seleccionada cuando la `CTaskDialog` se muestra.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]  
  
##  <a name="setverificationcheckboxtext"></a>CTaskDialog::SetVerificationCheckboxText  
 Establece el texto que se muestra a la derecha de la casilla de verificación.  
  
```  
void SetVerificationCheckboxText(CString& strVerificationText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strVerificationText`  
 El texto que este método se muestra junto a la casilla de verificación.  
  
### <a name="remarks"></a>Comentarios  
 Este método produce una excepción con el [Asegúrese](diagnostic-services.md#ensure) macro si esta instancia de la `CTaskDialog Class` ya se está mostrando.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]  
  
##  <a name="setwindowtitle"></a>CTaskDialog::SetWindowTitle  
 Establece el título de la `CTaskDialog`.  
  
```  
void SetWindowTitle(CString& strWindowTitle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strWindowTitle`  
 El nuevo título para el `CTaskDialog`.  
  
### <a name="remarks"></a>Comentarios  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="showdialog"></a>CTaskDialog::ShowDialog  
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
 [in] `strContent`  
 La cadena que se utilizará para el contenido de la `CTaskDialog`.  
  
 [in] `strMainInstruction`  
 La instrucción principal de la `CTaskDialog`.  
  
 [in] `strTitle`  
 El título de la `CTaskDialog`.  
  
 [in] `nIDCommandControlsFirst`  
 El identificador de cadena del primer comando.  
  
 [in] `nIDCommandControlsLast`  
 El identificador de cadena del último comando.  
  
 [in] `nCommonButtons`  
 Una máscara de los botones para agregar a la `CTaskDialog`.  
  
 [in] `nTaskDialogOptions`  
 El conjunto de opciones que se usará para el `CTaskDialog`.  
  
 [in] `strFooter`  
 La cadena que se usará como el pie de página.  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero que corresponde a la selección realizada por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 Este método estático le permite crear una instancia de la `CTaskDialog Class` sin crear explícitamente un `CTaskDialog` objeto en el código. Porque no hay ningún `CTaskDialog` objeto, no puede llamar a ningún otro método de la `CTaskDialog` si utiliza este método para mostrar un `CTaskDialog` al usuario.  
  
 Este método crea controles de botón de comando mediante el uso de datos desde el archivo de recursos de la aplicación. La tabla de cadenas en el archivo de recursos tiene varias cadenas con identificadores de cadena asociado. Este método agrega un control de botón de comando para cada entrada válida en la tabla de cadenas entre `nIDCommandControlsFirst` y `nCommandControlsLast`, ambos inclusive. Para estos controles de botón de comando, la cadena de la tabla de cadenas es el título del control y el identificador de cadena es el identificador. del control  
  
 Vea [CTaskDialog::SetOptions](#setoptions) para obtener una lista de opciones válidas.  
  
 El `CTaskDialog` se cierra cuando el usuario selecciona un botón comunes, un control de vínculo de comando, o se cierra el `CTaskDialog`. El valor devuelto es el identificador que indica cómo el usuario ha cerrado el cuadro de diálogo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]  
  
##  <a name="taskdialogcallback"></a>CTaskDialog::TaskDialogCallback  
 El marco de trabajo llama a este método en respuesta a diversos mensajes de Windows.  
  
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
 [in] `hwnd`  
 Un identificador de la `m_hWnd` estructura para el `CTaskDialog`.  
  
 [in] `uNotification`  
 El código de notificación que especifica el mensaje generado.  
  
 [in] `wParam`  
 Más información sobre el mensaje.  
  
 [in] `lParam`  
 Más información sobre el mensaje.  
  
 [in] `dwRefData`  
 Un puntero a la `CTaskDialog` objeto que se aplica el mensaje de devolución de llamada.  
  
### <a name="return-value"></a>Valor devuelto  
 Depende del código de notificación específico. Vea la sección Comentarios para obtener más información.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de `TaskDialogCallback` controla el mensaje específico y, a continuación, llama a la correspondiente en el método de la [clase CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Por ejemplo, en respuesta a la `TDN_BUTTON_CLICKED` mensaje, `TaskDialogCallback` llamadas [CTaskDialog::OnCommandControlClick](#oncommandcontrolclick).  
  
 Los valores de `wParam` y `lParam` dependen el mensaje generado específico. Es posible que uno o ambos de estos valores para que esté vacía. En la tabla siguiente se enumera las notificaciones de predeterminada que se admiten y lo que los valores de `wParam` y `lParam` representan. Si invalida este método en una clase derivada, debe implementar el código de devolución de llamada para cada mensaje en la tabla siguiente.  
  
|Mensaje de notificación|Valor de `wParam`|Valor de `lParam`|  
|--------------------------|--------------------|--------------------|  
|`TDN_CREATED`|No usado.|No usado.|  
|`TDN_NAVIGATED`|No usado.|No usado.|  
|`TDN_BUTTON_CLICKED`|Id. de control de botón de comando|No usado.|  
|`TDN_HYPERLINK_CLICKED`|No usado.|A [LPCWSTR](http://msdn.microsoft.com/library/windows/desktop/aa383751) estructura que contiene el vínculo.|  
|`TDN_TIMER`|Tiempo en milisegundos desde el `CTaskDialog` se creó o se ha restablecido el temporizador.|No usado.|  
|`TDN_DESTROYED`|No usado.|No usado.|  
|`TDN_RADIO_BUTTON_CLICKED`|El identificador del botón de radio.|No usado.|  
|`TDN_DIALOG_CONSTRUCTED`|No usado.|No usado.|  
|`TDN_VERIFICATION_CLICKED`|1 si está activada la casilla de verificación, 0 si no lo está.|No usado.|  
|`TDN_HELP`|No usado.|No usado.|  
|`TDN_EXPANDO_BUTTON_CLICKED`|0 si el área de expansión está contraída; es distinto de cero si se muestra el texto de expansión.|No usado.|  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Tutorial: Agregar una clase CTaskDialog a una aplicación](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)



