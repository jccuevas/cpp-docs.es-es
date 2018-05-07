---
title: Ayudar a los archivos (Ayuda HTML) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], HTML Help files
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d180fe4f9cf1baf26b27423ffda975bfe0fe85ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="help-files-html-help"></a>Archivos de ayuda (Ayuda HTML)
Los siguientes archivos se crean al agregar el tipo de Ayuda HTML de ayuda y soporte técnico a la aplicación seleccionando el **ayuda contextual** casilla de verificación y, a continuación, seleccione **formato de Ayuda HTML** en el [Características avanzadas](../mfc/reference/advanced-features-mfc-application-wizard.md) página del Asistente para aplicaciones MFC.  
  
|Nombre del archivo|Ubicación del directorio|Ubicación del Explorador de soluciones|Descripción|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Nombre_proyecto*.hhp|*Nombre_proyecto*\hlp|archivos de Ayuda HTML|El archivo de proyecto de ayuda. Contiene los datos necesarios para compilar los archivos de ayuda en un archivo .hxs o un archivo .chm.|  
|*Nombre_proyecto*.hhk|*Nombre_proyecto*\hlp|archivos de Ayuda HTML|Contiene un índice de los temas de ayuda.|  
|*Nombre_proyecto*.hhc|*Nombre_proyecto*\hlp|archivos de Ayuda HTML|El contenido del proyecto de ayuda.|  
|Makehtmlhelp.bat|*Nombre_proyecto*|Archivos de origen|Utilizada por el sistema para compilar el proyecto de ayuda cuando se compila el proyecto.|  
|Afxcore.htm|*Nombre_proyecto*\hlp|Temas de Ayuda HTML|Contiene los temas de ayuda estándares para comandos MFC estándar y objetos de la pantalla. Agregue sus propios temas de ayuda para este archivo.|  
|Afxprint.htm|*Nombre_proyecto*\hlp|Temas de Ayuda HTML|Contiene los temas de ayuda para los comandos de impresión.|  
|\*.jpg; \*.gif|*Nombre_proyecto*\hlp\Images|Archivos de recursos|Contienen imágenes de los temas de ayuda generados diferentes.|  
  
## <a name="see-also"></a>Vea también  
 [Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)