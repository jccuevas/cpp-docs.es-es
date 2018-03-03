---
title: Crear un Control ActiveX MFC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.activex.project
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 47207d80fc36b8f80fafbb495fa9592312bde09c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-an-mfc-activex-control"></a>Crear un control ActiveX MFC
Los programas de control ActiveX son programas modulares diseñados para ofrecer un tipo específico de funcionalidad a una aplicación primaria. Por ejemplo, puede crear un control, como un botón, para utilizarlo en un cuadro de diálogo o una barra de herramientas para su uso en una página Web.  
  
 La manera más fácil de crear un control ActiveX de MFC es utilizar el [Asistente para controles ActiveX de MFC](../../mfc/reference/mfc-activex-control-wizard.md).  
  
### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>Para crear un control ActiveX de MFC mediante el Asistente para controles ActiveX MFC  
  
1.  Siga las instrucciones del tema de Ayuda [crear un proyecto con un Asistente para aplicaciones de Visual C++](../../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
2.  En el **nuevo proyecto** cuadro de diálogo, seleccione la **ActiveX Control MFC** icono en el panel Plantillas para abrir el Asistente para controles de ActiveX de MFC.  
  
3.  Definir la [configuración de la aplicación](../../mfc/reference/application-settings-mfc-activex-control-wizard.md), [nombres del control](../../mfc/reference/control-names-mfc-activex-control-wizard.md), y [controlar la configuración de](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) mediante el Asistente para controles de ActiveX de MFC.  
  
    > [!NOTE]
    >  Omita este paso para mantener la configuración predeterminada del asistente.  
  
4.  Haga clic en **finalizar** para cerrar el asistente y abrir el proyecto nuevo en el entorno de desarrollo.  
  
 Una vez haya creado el proyecto, puede ver los archivos creados en **el Explorador de soluciones**. Para obtener más información sobre los archivos que crea el asistente para el proyecto, vea el archivo Readme.txt generado por el proyecto. Para obtener más información acerca de los tipos de archivo, consulte [tipos de archivo creados para proyectos de Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md).  
  
 Una vez haya creado el proyecto, puede usar los asistentes para código para agregar [funciones](../../ide/add-member-function-wizard.md), [variables](../../ide/add-member-variable-wizard.md), [eventos](../../ide/add-event-wizard.md), [propiedades](../../ide/names-add-property-wizard.md), y [métodos](../../ide/add-method-wizard.md). Para obtener más información acerca de cómo personalizar el control ActiveX, vea [controles ActiveX MFC](../../mfc/mfc-activex-controls.md).  
  
## <a name="see-also"></a>Vea también  
 [Agregar funcionalidad con los asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Páginas de propiedades](../../ide/property-pages-visual-cpp.md)   
 [Implementación de aplicaciones](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)

