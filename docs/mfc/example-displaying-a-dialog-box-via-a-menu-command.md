---
title: 'Ejemplo: Mostrar un cuadro de diálogo a través de un comando de menú'
ms.date: 09/07/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
ms.openlocfilehash: 281fa77f4954691002268d1e597146a615264695
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616033"
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>Ejemplo: Mostrar un cuadro de diálogo a través de un comando de menú

Este tema contiene procedimientos para:

- Muestra un cuadro de diálogo modal a través de un comando de menú.

- Muestra un cuadro de diálogo no modal a través de un comando de menú.

Ambos procedimientos de ejemplo son para las aplicaciones MFC y funcionarán en una aplicación creada con el [Asistente para aplicaciones MFC](reference/mfc-application-wizard.md).

Los procedimientos usan los siguientes nombres y valores:

|Artículo|Nombre o valor|
|----------|-------------------|
|Application|DisplayDialog|
|Comando de menú|Comando probar en el menú Ver; IDENTIFICADOR de comando = ID_VIEW_TEST|
|Cuadro de diálogo|Cuadro de diálogo probar; Clase = CTestDialog; Archivo de encabezado = TestDialog. h; Variable = testdlg, ptestdlg|
|Controlador de comandos|OnViewTest|

### <a name="to-display-a-modal-dialog-box"></a>Para mostrar un cuadro de diálogo modal

1. Cree el comando de menú. vea [crear menús o elementos de menú](../windows/creating-a-menu.md).

1. Crear el cuadro de diálogo; vea [iniciar el editor de cuadros de diálogo](../windows/creating-a-new-dialog-box.md).

1. Agregue una clase para el cuadro de diálogo. Vea [Agregar una clase](../ide/adding-a-class-visual-cpp.md) para obtener más información.

1. En **vista de clases**, seleccione la clase de documento (CDisplayDialogDoc). En la ventana **Propiedades** , haga clic en el botón **Eventos** . Haga doble clic en el identificador del comando de menú (ID_VIEW_TEST). A continuación, haga clic en la flecha abajo y seleccione ** \<Add> OnViewTest**.

   Si ha agregado el comando de menú al gran sistema (mainframe) de una aplicación MDI, en su lugar, seleccione la clase de aplicación (CDisplayDialogApp).

1. Agregue la siguiente instrucción include a CDisplayDialogDoc. cpp (o CDisplayDialogApp. cpp) después de las instrucciones include existentes:

   ```cpp
   #include "TestDialog.h"
   ```

1. Agregue el código siguiente a `OnViewTest` para implementar la función:

   ```cpp
   CTestDialog testdlg;
   testdlg.DoModal();
   ```

### <a name="to-display-a-modeless-dialog-box"></a>Para mostrar un cuadro de diálogo no modal

1. Siga los cuatro primeros pasos para mostrar un cuadro de diálogo modal, excepto seleccionar la clase de vista (CDisplayDialogView) en el paso 4.

1. Edite DisplayDialogView. h:

   - Declare la clase de cuadro de diálogo que precede a la primera declaración de clase:

   ```cpp
   class CTestDialog;
   ```

   - Declare un puntero al cuadro de diálogo después de la sección de atributos Public:

   ```cpp
   CTestDialog* m_pTestDlg;
   ```

1. Edite DisplayDialogView. cpp:

   - Agregue la siguiente instrucción include después de las instrucciones include existentes:

   ```cpp
   #include "TestDialog.h"
   ```

   - Agregue el código siguiente al constructor:

   ```cpp
   m_pTestDlg = NULL;
   ```

   - Agregue el código siguiente al destructor:

   ```cpp
   delete m_pTestDlg;
   ```

   - Agregue el código siguiente a `OnViewTest` para implementar la función:

   ```cpp
   if (NULL == m_pTestDlg)
   {
      m_pTestDlg = new CTestDialog(this);
      m_pTestDlg->Create(CTestDialog::IDD, this);
   }
   m_pTestDlg->ShowWindow(SW_SHOW);
   ```

## <a name="see-also"></a>Consulte también

[Cuadros de diálogo](dialog-boxes.md)<br/>
[Cuadros de diálogo modales y no modales](modal-and-modeless-dialog-boxes.md)
