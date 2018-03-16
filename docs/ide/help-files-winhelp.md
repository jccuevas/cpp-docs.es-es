---
title: Archivos de ayuda (WinHelp) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], WinHelp files
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a5698f7001512c5a4f8c45b5c787f35c9ce0ca6c
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2018
---
# <a name="help-files-winhelp"></a>Archivos de ayuda (WinHelp)
Los siguientes archivos se crean al agregar el tipo de WinHelp de ayuda y soporte técnico a la aplicación seleccionando el **ayuda contextual** casilla de verificación y, a continuación, seleccione **formato WinHelp** en el [Características avanzadas](../mfc/reference/advanced-features-mfc-application-wizard.md) página del Asistente para aplicaciones MFC.  
  
|Nombre del archivo|Ubicación del directorio|Ubicación del Explorador de soluciones|Descripción|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*.hpj|*Projname*\hlp|Archivos de origen|El archivo de proyecto de ayuda utilizado por el compilador de ayuda para crear el programa o archivo de Ayuda del control.|  
|*Projname*.rtf|*Projname*\hlp|Archivos de ayuda|Contiene información acerca de cómo personalizar el archivo .hpj y temas de plantilla que se pueden editar.|  
|*Nombre_proyecto*.cnt|*Projname*\hlp|Archivos de ayuda|Proporciona la estructura para el **contenido** ventana en la Ayuda de Windows.|  
|MakeHelp.bat|*Projname*|Archivos de origen|Utilizada por el sistema para compilar el proyecto de ayuda cuando se compila el proyecto.|  
|Print.rtf|*Projname*\hlp|Archivos de ayuda|Se crea si el proyecto incluye compatibilidad con la impresión (el valor predeterminado). Describe los cuadros de diálogo y comandos de impresión.|  
|*.bmp|*Projname*\hlp|Archivos de recursos|Contienen imágenes de los temas de ayuda generados diferentes.|  
  
 Puede agregar compatibilidad con WinHelp a un proyecto de ActiveX Control MFC seleccionando **generar archivos de Ayuda** en el [configuración de la aplicación](../mfc/reference/application-settings-mfc-activex-control-wizard.md) ficha del Asistente para el Control de ActiveX de MFC. Los siguientes archivos se agregan al proyecto cuando se agrega compatibilidad con la ayuda a un control ActiveX de MFC:  
  
|Nombre del archivo|Ubicación del directorio|Ubicación del Explorador de soluciones|Descripción|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*.hpj|*Projname*\hlp|Archivos de código fuente|El archivo de proyecto utilizado por el compilador de ayuda para crear el programa o archivo de Ayuda del control.|  
|*Projname*.rtf|*Projname*\hlp|Proyecto|Contiene información acerca de cómo personalizar el archivo .hpj y temas de plantilla que se pueden editar.|  
|MakeHelp.bat|*Projname*|Archivos de origen|Utilizada por el sistema para compilar el proyecto de ayuda cuando se compila el proyecto.|  
|Bullet.bmp|*Projname*|Archivos de recursos|Utiliza los temas de archivo de ayuda estándar para representar listas con viñetas.|  
  
## <a name="see-also"></a>Vea también  
 [Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)