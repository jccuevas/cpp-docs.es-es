---
title: Archivos de ayuda (WinHelp)
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], WinHelp files
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
ms.openlocfilehash: 142702699523633bf810d0077ce7ba6355557d21
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496315"
---
# <a name="help-files-winhelp"></a>Archivos de ayuda (WinHelp)

Los archivos siguientes se crean al agregar el tipo WinHelp de Ayuda y soporte técnico a la aplicación activando la casilla **Ayuda contextual** y, después, seleccionando **Formato de WinHelp** en la página [Características avanzadas](../mfc/reference/advanced-features-mfc-application-wizard.md) del Asistente para aplicaciones MFC.

|Nombre del archivo|Ubicación del directorio|Ubicación del Explorador de soluciones|Descripción|
|---------------|------------------------|--------------------------------|-----------------|
|*Nombre_proyecto*.hpj|*Nombre_proyecto*\hlp|Archivos de origen|El archivo de ayuda que el compilador de ayuda usa para crear el archivo de ayuda del control o el programa.|
|*Nombre_proyecto*.rtf|*Nombre_proyecto*\hlp|Archivos de ayuda|Contiene temas de plantilla que se pueden modificar e información sobre cómo personalizar el archivo .hpj.|
|*Nombre_proyecto*.cnt|*Nombre_proyecto*\hlp|Archivos de ayuda|Proporciona la estructura para la ventana **Contenido** en la Ayuda de Windows.|
|Makehelp.bat|*Nombre_proyecto*|Archivos de origen|El sistema los usa para compilar el proyecto de ayuda cuando se compila el proyecto.|
|Print.rtf|*Nombre_proyecto*\hlp|Archivos de ayuda|Se crea si el proyecto incluye compatibilidad con la impresión (el valor predeterminado). Describe los cuadros de diálogo y comandos de impresión.|
|*.bmp|*Nombre_proyecto*\hlp|Archivos de recursos|Contienen imágenes para los diferentes temas de archivo de ayuda generados.|

Puede agregar compatibilidad con WinHelp a un proyecto Control ActiveX MFC si selecciona **Generar archivos de ayuda** en la pestaña [Configuración de la aplicación](../mfc/reference/application-settings-mfc-activex-control-wizard.md) del Asistente para controles ActiveX MFC. Los archivos siguientes se agregan al proyecto cuando se agrega compatibilidad con la ayuda a un control ActiveX de MFC:

|Nombre del archivo|Ubicación del directorio|Ubicación del Explorador de soluciones|Descripción|
|---------------|------------------------|--------------------------------|-----------------|
|*Nombre_proyecto*.hpj|*Nombre_proyecto*\hlp|Archivos de código fuente|El archivo del proyecto que el compilador de ayuda usa para crear el archivo de ayuda del control o el programa.|
|*Nombre_proyecto*.rtf|*Nombre_proyecto*\hlp|Proyecto|Contiene temas de plantilla que se pueden modificar e información sobre cómo personalizar el archivo .hpj.|
|Makehelp.bat|*Nombre_proyecto*|Archivos de origen|El sistema los usa para compilar el proyecto de ayuda cuando se compila el proyecto.|
|Bullet.bmp|*Nombre_proyecto*|Archivos de recursos|Los usan los temas del archivo de ayuda estándar para representar listas con viñetas.|

## <a name="see-also"></a>Vea también

[Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)