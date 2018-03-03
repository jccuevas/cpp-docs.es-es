---
title: Crear un proyecto de archivos MAKE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.makefile.project
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5e86bedbf83cd417cfc41317e5887304cda7ee76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-makefile-project"></a>Crear un proyecto de archivos MAKE
Si tiene un proyecto que se compila desde la línea de comandos con un archivo MAKE, el entorno de desarrollo de Visual Studio no lo reconocerá. Para abrir y compilar el proyecto mediante [!INCLUDE[vsUltShort](../ide/includes/vsultshort_md.md)], Visual Studio Professional o Visual Studio Express para escritorio de Windows, primero cree un proyecto vacío seleccionando la plantilla de proyecto de archivos MAKE. Después podrá utilizar este proyecto para compilar el proyecto de archivos MAKE desde el entorno de desarrollo de Visual Studio.  
  
 El proyecto no mostrará ningún archivo en el Explorador de soluciones. El proyecto especifica la configuración de compilación mostrada en su página de propiedades.  
  
 El archivo de salida que especifique en el proyecto no afectará al nombre que genera el script de compilación; sólo declara una intención.  
  
### <a name="to-create-a-makefile-project"></a>Para crear un proyecto de archivos MAKE  
  
1.  Siga las instrucciones del tema de Ayuda [crear un proyecto con un Asistente para aplicaciones de Visual C++](../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
2.  En el **nuevo proyecto** cuadro de diálogo, seleccione **proyecto de archivos MAKE** en el panel Plantillas para abrir el asistente.  
  
3.  En el [configuración de la aplicación](../ide/application-settings-makefile-project-wizard.md) página, proporciona el comando, de salida, limpiar y volver a generar información.  
  
4.  Haga clic en **finalizar** para cerrar el asistente y abrir el proyecto recién creado en **el Explorador de soluciones**.  
  
 Puede ver y editar las propiedades del proyecto en la página de propiedades. Vea [establecer las propiedades de un proyecto de Visual C++](../ide/working-with-project-properties.md) para obtener información acerca de cómo mostrar la página de propiedades.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para proyecto de archivos MAKE](../ide/makefile-project-wizard.md)   
 [Caracteres especiales en un archivo MAKE](../build/special-characters-in-a-makefile.md)   
 [Contenido de un archivo MAKE](../build/contents-of-a-makefile.md)