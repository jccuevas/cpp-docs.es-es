---
title: 'Ejemplo: Mostrar un cuadro de diálogo a través de un comando de menú | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20d355215388861a7bc2586c2c253cd551124809
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>Ejemplo: Mostrar un cuadro de diálogo a través de un comando de menú
Este tema contiene procedimientos para:  
  
-   Mostrar un cuadro de diálogo modal mediante un comando de menú.  
  
-   Mostrar un cuadro de diálogo no modal mediante un comando de menú.  
  
 Ambos procedimientos de ejemplo son para aplicaciones MFC y funcionará en una aplicación que cree con la [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md).  
  
 Los procedimientos utilizan los nombres y los valores siguientes:  
  
|Elemento|Nombre o valor|  
|----------|-------------------|  
|Application|DisplayDialog|  
|Comando de menú|Comando de prueba en el menú Ver; Id. de comando = ID_VIEW_TEST|  
|Cuadro de diálogo|Cuadro de diálogo de prueba; Clase = CTestDialog; Archivo de encabezado = TestDialog.h; Variable = testdlg, ptestdlg|  
|Controlador de comandos.|OnViewTest|  
  
### <a name="to-display-a-modal-dialog-box"></a>Para mostrar un cuadro de diálogo modal  
  
1.  Crear un comando de menú; vea [crear menús o elementos de menú](../windows/creating-a-menu.md).  
  
2.  Crear el cuadro de diálogo; vea [al iniciar el Editor de cuadro de diálogo](../windows/creating-a-new-dialog-box.md).  
  
3.  Agregue una clase para el cuadro de diálogo. Vea [agregar una clase](../ide/adding-a-class-visual-cpp.md) para obtener más información.  
  
4.  En **vista de clases**, seleccione la clase de documento (CDisplayDialogDoc). En la ventana **Propiedades** , haga clic en el botón **Eventos** . Haga doble clic en el identificador del comando de menú (ID_VIEW_TEST) en el panel izquierdo de la **propiedades** ventana y seleccione **comando**. En el panel derecho, haga clic en la flecha hacia abajo y seleccione  **\<Agregar > OnViewTest**.  
  
     Si agrega el comando de menú al gran sistema de una aplicación MDI, seleccione la clase de aplicación (CDisplayDialogApp) en su lugar.  
  
5.  Agregue la siguiente instrucción de inclusión a CDisplayDialogDoc.cpp (o CDisplayDialogApp.cpp) después de las instrucciones de inclusión de las existentes:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
6.  Agregue el código siguiente a `OnViewTest` para implementar la función:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#43](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_2.cpp)]  
  
### <a name="to-display-a-modeless-dialog-box"></a>Para mostrar un cuadro de diálogo no modales  
  
1.  Siga los cuatro primeros pasos para mostrar un cuadro de diálogo modal, excepto la selección de la clase de vista (CDisplayDialogView) en el paso 4.  
  
2.  Edite DisplayDialogView.h:  
  
    -   Declare la clase de cuadro de diálogo anterior a la primera declaración de clase:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#44](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_3.h)]  
  
    -   Declarar un puntero al cuadro de diálogo después de la sección pública atributos:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#45](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_4.h)]  
  
3.  Edite DisplayDialogView.cpp:  
  
    -   Agregue que la siguiente instrucción de inclusión después instrucciones de inclusión existentes:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
    -   Agregue el código siguiente al constructor:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#46](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_5.cpp)]  
  
    -   Agregue el código siguiente al destructor:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#47](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_6.cpp)]  
  
    -   Agregue el código siguiente a `OnViewTest` para implementar la función:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#48](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_7.cpp)]  
  
 Además, vea el artículo de Knowledge Base siguiente:  
  
-   Q251059: Cómo: proporcionar su propio nombre de clase de ventana para un cuadro de diálogo MFC  
  
## <a name="see-also"></a>Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Cuadros de diálogo modales y no modales](../mfc/modal-and-modeless-dialog-boxes.md)

