---
title: "Pestaña de Editor de cuadro de diálogo, cuadro de herramientas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls ino dialog boxes
- custom controls [Visual Studio], dialog boxes
- controls [C++], standard
- Dialog editor, creating controls
- controls [C++], adding to dialog boxes
ms.assetid: 253885c2-dcb9-4d8e-ac9b-805ea31cbf5e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9db31d6e152be10f2c4934b7b1f239d1e08387f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-editor-tab-toolbox"></a>Editor de cuadros de diálogo (Ficha, Cuadro de herramientas)
La pestaña del Editor de cuadro de diálogo aparece en la [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox) cuando esté trabajando en el editor de cuadro de diálogo. Para agregar controles a un cuadro de diálogo nuevo, arrastre controles desde el cuadro de herramientas al cuadro de diálogo que está creando (para obtener más información, consulte [agregar un Control a un cuadro de diálogo](adding-a-control-to-a-dialog-box.md)). Después, puede mover los controles o cambiar su tamaño y su forma.  
  
 Los controles estándares disponibles en el cuadro de herramientas son:  
  
-   [Control de botón](../mfc/reference/cbutton-class.md)  
  
-   [Control de casilla de verificación](../mfc/reference/styles-used-by-mfc.md#button-styles)  
  
-   [Control de cuadro combinado](../mfc/reference/ccombobox-class.md)  
  
-   [Control de edición](../mfc/reference/cedit-class.md)  
  
-   Cuadro de grupo  
  
-   [Control de cuadro de lista](../mfc/reference/clistbox-class.md)  
  
-   [Control de botón de radio](../mfc/reference/styles-used-by-mfc.md#button-styles)  
  
-   [Control de texto estático](../mfc/reference/cstatic-class.md)  
  
-   [Control de imagen](../mfc/reference/cpictureholder-class.md)  
  
-   [Control Rich Edit 2.0](../mfc/using-cricheditctrl.md)  
  
-   [Control de barra de desplazamiento](../mfc/reference/cscrollbar-class.md)  
  
 El [controles comunes de Windows](../mfc/controls-mfc.md) disponible en el cuadro de herramientas ofrecen una mayor funcionalidad en la aplicación. Son los siguientes:  
  
-   [Control deslizante](../mfc/slider-control-styles.md)  
  
-   [Control de número](../mfc/using-cspinbuttonctrl.md)  
  
-   [Control de progreso](../mfc/styles-for-the-progress-control.md)  
  
-   [Hot Key (control)](../mfc/using-a-hot-key-control.md)  
  
-   [Control de lista](../mfc/list-control-and-list-view.md)  
  
-   [Control de árbol](../mfc/tree-control-styles.md)  
  
-   [Control de pestaña](../mfc/tab-controls-and-property-sheets.md)  
  
-   [Control de animación](../mfc/using-an-animation-control.md)  
  
-   [Control de selector de hora de fecha](../mfc/creating-the-date-and-time-picker-control.md)  
  
-   [Control de calendario mensual](../mfc/month-calendar-control-examples.md)  
  
-   [Control de dirección IP](../mfc/reference/cipaddressctrl-class.md)  
  
-   [Control de cuadro combinado extendido](../mfc/creating-an-extended-combo-box-control.md)  
  
-   [Control personalizado](custom-controls-in-the-dialog-editor.md)  
  
 Puede agregar controles personalizados al cuadro de diálogo seleccionando el **Control personalizado** icono en el cuadro de herramientas y arrástrelo al cuadro de diálogo. Para agregar un control Syslink, agregue un control personalizado y, a continuación, cambie el control **clase** propiedad **Syslink**. Esto hará que se actualicen las propiedades y que muestren las propiedades del control Syslink. Para obtener información sobre la clase contenedora MFC, vea [CLinkCtrl](../mfc/reference/clinkctrl-class.md).  
  
 También puede [agregar controles ActiveX a su cuadro de diálogo](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
 También puede personalizar la ventana del cuadro de herramientas para facilitar su uso. Para obtener más información, vea [Usar el cuadro de herramientas](/visualstudio/ide/using-the-toolbox).  

 Para obtener más información sobre cómo utilizar el control RichEdit 1.0 con MFC, vea [utilizar el Control RichEdit 1.0 con MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Controles](../mfc/controls-mfc.md)   
 [Clases de controles](../mfc/control-classes.md)   
 [Clases de cuadro de diálogo](../mfc/dialog-box-classes.md)   
 [Estilos de barra de desplazamiento](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)   
 [Ejemplos de Control Rich Edit](../mfc/rich-edit-control-examples.md)   
 [Agregar controladores de eventos para controles de cuadros de diálogo](../windows/adding-event-handlers-for-dialog-box-controls.md)   
 [Tipos de controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md)

