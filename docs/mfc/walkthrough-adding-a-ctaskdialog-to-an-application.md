---
title: 'Tutorial: Agregar una clase CTaskDialog a una aplicación | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTaskDialog, adding
- walkthroughs [MFC], dialogs
ms.assetid: 3a62abb8-2d86-4bec-bdb8-5784d5f9a9f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b2c10583a4c3fc2b988e50c15b6c1dcf206af65
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384916"
---
# <a name="walkthrough-adding-a-ctaskdialog-to-an-application"></a>Tutorial: Agregar una clase CTaskDialog a una aplicación
En este tutorial se presenta la [CTaskDialog Class](../mfc/reference/ctaskdialog-class.md) y se muestra cómo agregar una a la aplicación.  
  
 El `CTaskDialog` es un cuadro de diálogo de tarea que reemplaza el cuadro de mensaje de Windows en Windows Vista o posterior. La clase `CTaskDialog` mejora el cuadro de mensaje original y agrega funcionalidad. El cuadro de mensaje de Windows todavía se admite en Visual Studio.  
  
> [!NOTE]
> Las versiones de Windows anteriores a Windows Vista no admiten la `CTaskDialog`. Debe programar una opción de cuadro de diálogo alternativa si quiere mostrar un mensaje a un usuario que ejecute la aplicación en una versión anterior de Windows. Puede usar el método estático [CTaskDialog::IsSupported](../mfc/reference/ctaskdialog-class.md#issupported) para determinar en tiempo de ejecución si el equipo de un usuario puede mostrar una clase `CTaskDialog`. Además, la clase `CTaskDialog` solo está disponible cuando la aplicación se compila con la biblioteca de Unicode.  
  
 La clase `CTaskDialog` admite varios elementos opcionales para recopilar y mostrar información. Por ejemplo, una clase `CTaskDialog` puede mostrar vínculos de comandos, botones personalizados, iconos personalizados y un pie de página. La clase `CTaskDialog` también tiene varios métodos que permiten consultar el estado del cuadro de diálogo de tarea para determinar qué elementos opcionales seleccionó el usuario.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
- Visual Studio 2010 o versiones posteriores  
  
- Windows Vista o posterior  
  
## <a name="replacing-a-windows-message-box-with-a-ctaskdialog"></a>Reemplazar un cuadro de mensaje de Windows por una clase CTaskDialog  
 En el procedimiento siguiente se muestra el uso más básico de la clase `CTaskDialog`, que consiste en reemplazar el cuadro de mensaje de Windows. En este ejemplo también se cambia el icono asociado al cuadro de diálogo de tarea. Si se cambia el icono, la clase `CTaskDialog` parece idéntica al cuadro de mensaje de Windows.  
  
#### <a name="to-replace-a-windows-message-box-with-a-ctaskdialog"></a>Para reemplazar un cuadro de mensaje de Windows con una clase CTaskDialog  
  
1.  Cree un nuevo proyecto de aplicación MFC con la configuración predeterminada. Asígnele el nombre `MyProject`.  
  
2.  Use el **Explorador de soluciones** para abrir el archivo MyProject.cpp.  
  
3.  Agregue `#include "afxtaskdialog.h"` después de la lista de incluye.  
  
4.  Busque el método `CMyProjectApp::InitInstance`. Inserte las siguientes líneas de código antes de la instrucción `return TRUE;` . Este código crea las cadenas que se usan en el cuadro de mensaje de Windows o en la clase `CTaskDialog`.  
  
 ```  
    CString message("My message to the user");

    CString dialogTitle("My Task Dialog title");

    CString emptyString;  
 ```  
  
5.  Agregue el código siguiente después del código del paso 4. Este código garantiza que el equipo del usuario admita la clase `CTaskDialog`. Si no se admite el cuadro de diálogo, la aplicación muestra en su lugar un cuadro de mensaje de Windows.  
  
 ```  
    if (CTaskDialog::IsSupported())  
 {  
 
 }  
    else 
 {  
    AfxMessageBox(message);

 }  
 ```  
  
6.  Inserte el siguiente código entre corchetes después de la instrucción `if` del paso 5. Este código crea la clase `CTaskDialog`.  
  
 ```  
    CTaskDialog taskDialog(message,
    emptyString,
    dialogTitle,
    TDCBF_OK_BUTTON);

 ```  
  
7.  En la línea siguiente, agregue el código siguiente. Este código establece el icono de advertencia.  
  
 ```  
    taskDialog.SetMainIcon(TD_WARNING_ICON);

 ```  
  
8.  En la línea siguiente, agregue el código siguiente. Este código muestra el cuadro de diálogo de tarea.  
  
 ```  
    taskDialog.DoModal();

 ```  
  
 Puede omitir el paso 7 si no quiere que la clase `CTaskDialog` muestre el mismo icono que el cuadro de mensaje de Windows. Si omite este paso, la clase `CTaskDialog` no tendrá icono cuando la aplicación la muestre.  
  
 Compile y ejecute la aplicación. La aplicación muestra el cuadro de diálogo de tareas después de iniciarse.  
  
## <a name="adding-functionality-to-the-ctaskdialog"></a>Agregar funcionalidad a la clase CTaskDialog  
 En el procedimiento siguiente se muestra cómo agregar funcionalidad a la clase `CTaskDialog` que creó en el procedimiento anterior. En el código de ejemplo se muestra cómo ejecutar instrucciones específicas según las selecciones del usuario.  
  
#### <a name="to-add-functionality-to-the-ctaskdialog"></a>Para agregar funcionalidad a la clase CTaskDialog  
  
1.  Vaya a la **Vista de recursos**. Si no ve la **Vista de recursos**, puede abrirla desde el menú **Vista** .  
  
2.  Expanda la **Vista de recursos** hasta que pueda seleccionar la carpeta **Tabla de cadenas** . Expándala y haga doble clic en la entrada **Tabla de cadenas** .  
  
3.  Desplácese a la parte inferior de la tabla de cadenas y agregue una nueva entrada. Cambie el identificador a `TEMP_LINE1`. Establezca el título en **Línea de comandos 1**.  
  
4.  Agregue otra entrada nueva. Cambie el identificador a `TEMP_LINE2`. Establezca el título en **Línea de comandos 2**.  
  
5.  Vuelva a MyProject.cpp.  
  
6.  Después de `CString emptyString;`, agregue el código siguiente:  
  
 ```  
    CString expandedLabel("Hide extra information");

    CString collapsedLabel("Show extra information");

    CString expansionInfo("This is the additional information to the user,\nextended over two lines.");

 ```  
  
7.  Busque la instrucción `taskDialog.DoModal()` y reemplácela por el código siguiente. Este código actualiza el cuadro de diálogo de tarea y agrega nuevos controles:  
  
 ```  
    taskDialog.SetMainInstruction(L"Warning");

 taskDialog.SetCommonButtons(TDCBF_YES_BUTTON | TDCBF_NO_BUTTON | TDCBF_CANCEL_BUTTON);

    taskDialog.LoadCommandControls(TEMP_LINE1,
    TEMP_LINE2);

    taskDialog.SetExpansionArea(expansionInfo,
    collapsedLabel,
    expandedLabel);

    taskDialog.SetFooterText(L"This is the a small footnote to the user");

    taskDialog.SetVerificationCheckboxText(L"Remember your selection");

 ```  
  
8.  Agregue la siguiente línea de código que muestra al usuario el cuadro de diálogo de tarea y recupera la selección del usuario:  
  
 ```  
    INT_PTR result = taskDialog.DoModal();

 ```  
  
9. Inserte el código siguiente detrás de la llamada a `taskDialog.DoModal()`. Esta sección de código procesa la entrada del usuario:  
  
 ```  
    if (taskDialog.GetVerificationCheckboxState())  
 { *// PROCESS IF the user selects the verification checkbox   
 }  
 
    switch (result)  
 {  
    case TEMP_LINE1: *// PROCESS IF the first command line  
    break; 
    case TEMP_LINE2: *// PROCESS IF the second command line  
    break; 
    case IDYES: *// PROCESS IF the user clicks yes  
    break; 
    case IDNO: *// PROCESS IF the user clicks no  
    break; 
    case IDCANCEL: *// PROCESS IF the user clicks cancel  
    break; 
    default: *// This case should not be hit because closing the dialog box results in IDCANCEL  
    break; 
 }  
 ```  
  
 En el código del paso 9, reemplace los comentarios que comienzan con PROCESS IF por el código que quiere ejecutar en las condiciones especificadas.  
  
 Compile y ejecute la aplicación. La aplicación muestra el cuadro de diálogo de tarea que usa los controles nuevos y la información adicional.  
  
## <a name="displaying-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Mostrar una clase CTaskDialog sin crear un objeto CTaskDialog  
 En el procedimiento siguiente se muestra cómo mostrar una clase `CTaskDialog` sin crear primero un objeto `CTaskDialog` . En este ejemplo se siguen los procedimientos anteriores.  
  
#### <a name="to-display-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Para mostrar una clase CTaskDialog sin crear un objeto CTaskDialog  
  
1.  Abra el archivo MyProject.cpp si todavía no está abierto.  
  
2.  Vaya al corchete de cierre de la instrucción `if (CTaskDialog::IsSupported())` .  
  
3.  Inserte el código siguiente inmediatamente antes del corchete de cierre de la instrucción `if` (antes del bloque `else` ):  
  
 ```  
    HRESULT result2 = CTaskDialog::ShowDialog(L"My error message",
    L"Error",
    L"New Title",
    TEMP_LINE1,
    TEMP_LINE2);

 ```  
  
 Compile y ejecute la aplicación. La aplicación muestra dos cuadros de diálogo de tarea. El primer cuadro de diálogo es del procedimiento Para agregar funcionalidad a la clase CTaskDialog; el segundo cuadro de diálogo es del último procedimiento.  
  
 En estos ejemplos no se muestran todas las opciones disponibles para una clase `CTaskDialog`, pero le ayudarán a empezar a trabajar. Vea [CTaskDialog Class](../mfc/reference/ctaskdialog-class.md) para obtener una descripción completa de la clase.  
  
## <a name="see-also"></a>Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Clase CTaskDialog](../mfc/reference/ctaskdialog-class.md)   
 [CTaskDialog::CTaskDialog](../mfc/reference/ctaskdialog-class.md#ctaskdialog)

