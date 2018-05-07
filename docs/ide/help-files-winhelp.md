---
title: Archivos de ayuda (WinHelp) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], WinHelp files
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 505506c7f3a14a73c6b0c859a70938fee3eed69e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="help-files-winhelp"></a>Archivos de ayuda (WinHelp)
Los siguientes archivos se crean al agregar el tipo de WinHelp de ayuda y soporte técnico a la aplicación seleccionando el **ayuda contextual** casilla de verificación y, a continuación, seleccione **formato WinHelp** en el [Características avanzadas](../mfc/reference/advanced-features-mfc-application-wizard.md) página del Asistente para aplicaciones MFC.  
  
|Nombre del archivo|Ubicación del directorio|Ubicación del Explorador de soluciones|Descripción|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Nombre_proyecto*.hpj|*Nombre_proyecto*\hlp|Archivos de origen|El archivo de proyecto de ayuda utilizado por el compilador de ayuda para crear el programa o archivo de Ayuda del control.|  
|*Nombre_proyecto*.rtf|*Nombre_proyecto*\hlp|Archivos de ayuda|Contiene información acerca de cómo personalizar el archivo .hpj y temas de plantilla que se pueden editar.|  
|*Nombre_proyecto*.cnt|*Nombre_proyecto*\hlp|Archivos de ayuda|Proporciona la estructura para el **contenido** ventana en la Ayuda de Windows.|  
|MakeHelp.bat|*Nombre_proyecto*|Archivos de origen|Utilizada por el sistema para compilar el proyecto de ayuda cuando se compila el proyecto.|  
|Print.rtf|*Nombre_proyecto*\hlp|Archivos de ayuda|Se crea si el proyecto incluye compatibilidad con la impresión (el valor predeterminado). Describe los cuadros de diálogo y comandos de impresión.|  
|*.bmp|*Nombre_proyecto*\hlp|Archivos de recursos|Contienen imágenes de los temas de ayuda generados diferentes.|  
  
 Puede agregar compatibilidad con WinHelp a un proyecto de ActiveX Control MFC seleccionando **generar archivos de Ayuda** en el [configuración de la aplicación](../mfc/reference/application-settings-mfc-activex-control-wizard.md) ficha del Asistente para el Control de ActiveX de MFC. Los siguientes archivos se agregan al proyecto cuando se agrega compatibilidad con la ayuda a un control ActiveX de MFC:  
  
|Nombre del archivo|Ubicación del directorio|Ubicación del Explorador de soluciones|Descripción|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Nombre_proyecto*.hpj|*Nombre_proyecto*\hlp|Archivos de código fuente|El archivo de proyecto utilizado por el compilador de ayuda para crear el programa o archivo de Ayuda del control.|  
|*Nombre_proyecto*.rtf|*Nombre_proyecto*\hlp|Proyecto|Contiene información acerca de cómo personalizar el archivo .hpj y temas de plantilla que se pueden editar.|  
|MakeHelp.bat|*Nombre_proyecto*|Archivos de origen|Utilizada por el sistema para compilar el proyecto de ayuda cuando se compila el proyecto.|  
|Bullet.bmp|*Nombre_proyecto*|Archivos de recursos|Utiliza los temas de archivo de ayuda estándar para representar listas con viñetas.|  
  
## <a name="see-also"></a>Vea también  
 [Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)