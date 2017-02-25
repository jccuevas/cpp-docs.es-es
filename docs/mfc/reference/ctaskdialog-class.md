---
title: "CTaskDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CTaskDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTaskDialog class"
ms.assetid: 1991ec98-ae56-4483-958b-233809c8c559
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 31
---
# CTaskDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un cuadro de diálogo emergente que funciona como un cuadro de mensaje pero puede mostrar información adicional al usuario.  `CTaskDialog` también incluye funcionalidad para recopilar información del usuario.  
  
## Sintaxis  
  
```  
class CTaskDialog : public CObject  
```  
  
## Miembros  
  
### Constructores  
  
|||  
|-|-|  
|[CTaskDialog::CTaskDialog](../Topic/CTaskDialog::CTaskDialog.md)|Crea un objeto `CTaskDialog`.|  
  
### Métodos  
  
|||  
|-|-|  
|[CTaskDialog::AddCommandControl](../Topic/CTaskDialog::AddCommandControl.md)|Agrega un control de Botón de comando a `CTaskDialog`.|  
|[CTaskDialog::AddRadioButton](../Topic/CTaskDialog::AddRadioButton.md)|Agrega un botón de radio a `CTaskDialog`.|  
|[CTaskDialog::ClickCommandControl](../Topic/CTaskDialog::ClickCommandControl.md)|Haga clic en un botón del control de Botón de comando o campo común mediante programación.|  
|[CTaskDialog::ClickRadioButton](../Topic/CTaskDialog::ClickRadioButton.md)|Haga clic en un botón de radio mediante programación.|  
|[CTaskDialog::DoModal](../Topic/CTaskDialog::DoModal.md)|Muestra el `CTaskDialog`.|  
|[CTaskDialog::GetCommonButtonCount](../Topic/CTaskDialog::GetCommonButtonCount.md)|Recupera el número de botones comunes disponibles.|  
|[CTaskDialog::GetCommonButtonFlag](../Topic/CTaskDialog::GetCommonButtonFlag.md)|Convierte un botón estándar de Windows al tipo de botón común asociado a la clase de `CTaskDialog` .|  
|[CTaskDialog::GetCommonButtonId](../Topic/CTaskDialog::GetCommonButtonId.md)|Convierten uno de los tipos de botón comunes asociados a la clase de `CTaskDialog` un botón estándar de Windows.|  
|[CTaskDialog::GetOptions](../Topic/CTaskDialog::GetOptions.md)|Devuelve marcadores de opciones para este `CTaskDialog`.|  
|[CTaskDialog::GetSelectedCommandControlID](../Topic/CTaskDialog::GetSelectedCommandControlID.md)|Devuelve el control de botón de comando seleccionado.|  
|[CTaskDialog::GetSelectedRadioButtonID](../Topic/CTaskDialog::GetSelectedRadioButtonID.md)|Devuelve el botón de radio.|  
|[CTaskDialog::GetVerificationCheckboxState](../Topic/CTaskDialog::GetVerificationCheckboxState.md)|Recupera el estado de la casilla de comprobación.|  
|[CTaskDialog::IsCommandControlEnabled](../Topic/CTaskDialog::IsCommandControlEnabled.md)|Determina si un control de Botón de comando o un botón común está habilitado.|  
|[CTaskDialog::IsRadioButtonEnabled](../Topic/CTaskDialog::IsRadioButtonEnabled.md)|Determina si un botón de radio está habilitado.|  
|[CTaskDialog::IsSupported](../Topic/CTaskDialog::IsSupported.md)|determina si el equipo que está ejecutando la aplicación admite `CTaskDialog`.|  
|[CTaskDialog::LoadCommandControls](../Topic/CTaskDialog::LoadCommandControls.md)|Agregar controles de Botón de comando utilizando los datos de la tabla de cadenas.|  
|[CTaskDialog::LoadRadioButtons](../Topic/CTaskDialog::LoadRadioButtons.md)|Agregue los botones de radio utilizando los datos de la tabla de cadenas.|  
|[CTaskDialog::NavigateTo](../Topic/CTaskDialog::NavigateTo.md)|Transfiere el foco a otro `CTaskDialog`.|  
|[CTaskDialog::OnCommandControlClick](../Topic/CTaskDialog::OnCommandControlClick.md)|El marco de trabajo llama a este método cuando el usuario hace clic en un control de Botón de comando.|  
|[CTaskDialog::OnCreate](../Topic/CTaskDialog::OnCreate.md)|El marco de trabajo llama a este método después de crear `CTaskDialog`.|  
|[CTaskDialog::OnDestroy](../Topic/CTaskDialog::OnDestroy.md)|El marco de trabajo llama a este método inmediatamente antes que destruye `CTaskDialog`.|  
|[CTaskDialog::OnExpandButtonClick](../Topic/CTaskDialog::OnExpandButtonClick.md)|El marco de trabajo llama a este método cuando el usuario hace clic en el botón de expansión.|  
|[CTaskDialog::OnHelp](../Topic/CTaskDialog::OnHelp.md)|El marco de trabajo llama a este método cuando la ayuda de las solicitudes de usuario.|  
|[CTaskDialog::OnHyperlinkClick](../Topic/CTaskDialog::OnHyperlinkClick.md)|El marco de trabajo llama a este método cuando el usuario hace clic en un hipervínculo.|  
|[CTaskDialog::OnInit](../Topic/CTaskDialog::OnInit.md)|El marco de trabajo llama a este método cuando se inicializa `CTaskDialog` .|  
|[CTaskDialog::OnNavigatePage](../Topic/CTaskDialog::OnNavigatePage.md)|El marco de trabajo llama a este método cuando el usuario mueve el foco con respecto a los controles de `CTaskDialog`.|  
|[CTaskDialog::OnRadioButtonClick](../Topic/CTaskDialog::OnRadioButtonClick.md)|El marco de trabajo llama a este método cuando el usuario selecciona un control de botón de radio.|  
|[CTaskDialog::OnTimer](../Topic/CTaskDialog::OnTimer.md)|El marco de trabajo llama a este método cuando expira el temporizador.|  
|[CTaskDialog::OnVerificationCheckboxClick](../Topic/CTaskDialog::OnVerificationCheckboxClick.md)|El marco de trabajo llama a este método cuando el usuario hace clic en la casilla de comprobación.|  
|[CTaskDialog::RemoveAllCommandControls](../Topic/CTaskDialog::RemoveAllCommandControls.md)|Quita todos los controles de comando de `CTaskDialog`.|  
|[CTaskDialog::RemoveAllRadioButtons](../Topic/CTaskDialog::RemoveAllRadioButtons.md)|Quita todos los botones de radio de `CTaskDialog`.|  
|[CTaskDialog::SetCommandControlOptions](../Topic/CTaskDialog::SetCommandControlOptions.md)|Actualiza un control de Botón de comando en `CTaskDialog`.|  
|[CTaskDialog::SetCommonButtonOptions](../Topic/CTaskDialog::SetCommonButtonOptions.md)|Actualizar un subconjunto de botones comunes que se habilitarán y requiere la elevación de UAC.|  
|[CTaskDialog::SetCommonButtons](../Topic/CTaskDialog::SetCommonButtons.md)|Agregue los botones comunes a `CTaskDialog`.|  
|[CTaskDialog::SetContent](../Topic/CTaskDialog::SetContent.md)|actualiza el contenido de `CTaskDialog`.|  
|[CTaskDialog::SetDefaultCommandControl](../Topic/CTaskDialog::SetDefaultCommandControl.md)|Especifica el control de Botón de comando predeterminado.|  
|[CTaskDialog::SetDefaultRadioButton](../Topic/CTaskDialog::SetDefaultRadioButton.md)|Especifica el botón de radio predeterminado.|  
|[CTaskDialog::SetDialogWidth](../Topic/CTaskDialog::SetDialogWidth.md)|Ajustar el ancho de `CTaskDialog`.|  
|[CTaskDialog::SetExpansionArea](../Topic/CTaskDialog::SetExpansionArea.md)|Actualiza el área de la extensión de `CTaskDialog`.|  
|[CTaskDialog::SetFooterIcon](../Topic/CTaskDialog::SetFooterIcon.md)|Actualiza el icono de pie de página para `CTaskDialog`.|  
|[CTaskDialog::SetFooterText](../Topic/CTaskDialog::SetFooterText.md)|actualiza el texto en el pie de página de `CTaskDialog`.|  
|[CTaskDialog::SetMainIcon](../Topic/CTaskDialog::SetMainIcon.md)|actualiza el icono principal de `CTaskDialog`.|  
|[CTaskDialog::SetMainInstruction](../Topic/CTaskDialog::SetMainInstruction.md)|actualiza la instrucción principal de `CTaskDialog`.|  
|[CTaskDialog::SetOptions](../Topic/CTaskDialog::SetOptions.md)|Configurar las opciones para `CTaskDialog`.|  
|[CTaskDialog::SetProgressBarMarquee](../Topic/CTaskDialog::SetProgressBarMarquee.md)|Configura una barra de la marquesina para `CTaskDialog` y la agrega al cuadro de diálogo.|  
|[CTaskDialog::SetProgressBarPosition](../Topic/CTaskDialog::SetProgressBarPosition.md)|Incluye la posición de la barra de progreso.|  
|[CTaskDialog::SetProgressBarRange](../Topic/CTaskDialog::SetProgressBarRange.md)|ajusta el radio de acción de barra de progreso.|  
|[CTaskDialog::SetProgressBarState](../Topic/CTaskDialog::SetProgressBarState.md)|Establece el estado de la barra de progreso y la muestra en `CTaskDialog`.|  
|[CTaskDialog::SetRadioButtonOptions](../Topic/CTaskDialog::SetRadioButtonOptions.md)|Habilita o deshabilita un botón de opción.|  
|[CTaskDialog::SetVerificationCheckbox](../Topic/CTaskDialog::SetVerificationCheckbox.md)|Establece el estado activada de casilla de comprobación.|  
|[CTaskDialog::SetVerificationCheckboxText](../Topic/CTaskDialog::SetVerificationCheckboxText.md)|Establece el texto a la derecha de la casilla de comprobación.|  
|[CTaskDialog::SetWindowTitle](../Topic/CTaskDialog::SetWindowTitle.md)|Establece el título de `CTaskDialog`.|  
|[CTaskDialog::ShowDialog](../Topic/CTaskDialog::ShowDialog.md)|Crea y muestra `CTaskDialog`.|  
|[CTaskDialog::TaskDialogCallback](../Topic/CTaskDialog::TaskDialogCallback.md)|El marco de trabajo llama a esto en respuesta a varios mensajes de Windows.|  
  
### miembros de datos  
  
|||  
|-|-|  
|`m_aButtons`|Matriz de los controles de Botón de comando para `CTaskDialog`.|  
|`m_aRadioButtons`|Matriz de los controles de botón de opción para `CTaskDialog`.|  
|`m_bVerified`|`TRUE` indica que la casilla de comprobación está activada; `FALSE` indica que no es.|  
|`m_footerIcon`|El icono en el pie de página de `CTaskDialog`.|  
|`m_hWnd`|Un identificador de la ventana para `CTaskDialog`.|  
|`m_mainIcon`|El icono principal de `CTaskDialog`.|  
|`m_nButtonDisabled`|Una máscara que indica cuál de los botones comunes se deshabilitan.|  
|`m_nButtonElevation`|Una máscara que indica cuál de los botones comunes requieren la elevación de UAC.|  
|`m_nButtonId`|El id. del control de botón de comando seleccionado.|  
|`m_nCommonButton`|Una máscara que indica los botones comunes se muestran en `CTaskDialog`.|  
|`m_nDefaultCommandControl`|El id. del control de Botón de comando está seleccionado cuando se muestra `CTaskDialog` .|  
|`m_nDefaultRadioButton`|El id. del control de botón de radio está seleccionado cuando se muestra `CTaskDialog` .|  
|`m_nFlags`|Una máscara que indica las opciones para `CTaskDialog`.|  
|`m_nProgressPos`|La posición actual para la barra de progreso.  Dicho valor debe encontrarse entre `m_nProgressRangeMin` y `m_nProgressRangeMax`.|  
|`m_nProgressRangeMax`|El valor máximo de la barra de progreso.|  
|`m_nProgressRangeMin`|El valor mínimo de la barra de progreso.|  
|`m_nProgressState`|El estado de la barra de progreso.  Para obtener más información, vea [CTaskDialog::SetProgressBarState](../Topic/CTaskDialog::SetProgressBarState.md).|  
|`m_nRadioId`|El id. del control seleccionado de botón de radio.|  
|`m_nWidth`|Ancho del control `CTaskDialog`, en píxeles.|  
|`m_strCollapse`|La cadena que `CTaskDialog` muestra a la derecha del cuadro de la extensión cuando se oculta información expandida.|  
|`m_strContent`|La cadena de contenido de `CTaskDialog`.|  
|`m_strExpand`|La cadena que `CTaskDialog` muestra a la derecha del cuadro de la extensión cuando se muestra información expandida.|  
|`m_strFooter`|El pie de página de `CTaskDialog`.|  
|`m_strInformation`|Información ampliada para `CTaskDialog`.|  
|`m_strMainInstruction`|la instrucción principal de `CTaskDialog`.|  
|`m_strTitle`|Título de la página `CTaskDialog`.|  
|`m_strVerification`|La cadena que `CTaskDialog` muestra a la derecha de la casilla de comprobación.|  
  
## Comentarios  
 La clase de `CTaskDialog` reemplaza el cuadro de mensaje estándar de Windows y tiene funciones adicionales como nuevos controles para recopilar información del usuario.  Esta clase en la biblioteca MFC en [!INCLUDE[vs_dev10_long](../../build/includes/vs_dev10_long_md.md)].  `CTaskDialog` es el iniciar disponibles con [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)].  Las versiones anteriores de Windows no pueden mostrar el objeto de `CTaskDialog` .  Utilice `CTaskDialog::IsSupported` para determinar en el runtime si el usuario actual puede mostrar el cuadro de diálogo de tarea.  El cuadro de mensaje estándar de Windows se admite todavía en [!INCLUDE[vs_dev10_long](../../build/includes/vs_dev10_long_md.md)].  
  
 `CTaskDialog` solo está disponible cuando se compila la aplicación mediante la biblioteca de Unicode.  
  
 `CTaskDialog` tiene dos diferentes constructores.  Un constructor permite especificar dos botones de comando y un máximo de seis controles de botón regulares.  Puede agregar varios botones de comando después de crear `CTaskDialog`.  El segundo constructor no admite ninguna botones de comando, pero puede agregar un número ilimitado de controles de botón regulares.  Para obtener más información sobre los constructores, vea [CTaskDialog::CTaskDialog](../Topic/CTaskDialog::CTaskDialog.md).  
  
 La ilustración siguiente se muestra un ejemplo `CTaskDialog` para mostrar la ubicación de algunos de los controles.  
  
 ![Ejemplo de CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "CTaskDialogSample")  
Ejemplo CTaskDialog  
  
## Requisitos  
 **Sistema operativo mínimo necesario:** [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
 **encabezado:** afxtaskdialog.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Tutorial: Agregar una clase CTaskDialog a una aplicación](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)