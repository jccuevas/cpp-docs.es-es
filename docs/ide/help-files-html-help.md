---
title: Ayudar a los archivos (Ayuda HTML) | Documentos de Microsoft
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
- file types [C++], HTML Help files
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c96cd6ad904439f556f2baa51602353ea00c5ac7
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2018
---
# <a name="help-files-html-help"></a>Archivos de ayuda (Ayuda HTML)
Los siguientes archivos se crean al agregar el tipo de Ayuda HTML de ayuda y soporte técnico a la aplicación seleccionando el **ayuda contextual** casilla de verificación y, a continuación, seleccione **formato de Ayuda HTML** en el [Características avanzadas](../mfc/reference/advanced-features-mfc-application-wizard.md) página del Asistente para aplicaciones MFC.  
  
|Nombre del archivo|Ubicación del directorio|Ubicación del Explorador de soluciones|Descripción|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*.hhp|*Projname*\hlp|archivos de Ayuda HTML|El archivo de proyecto de ayuda. Contiene los datos necesarios para compilar los archivos de ayuda en un archivo .hxs o un archivo .chm.|  
|*Projname*.hhk|*Projname*\hlp|archivos de Ayuda HTML|Contiene un índice de los temas de ayuda.|  
|*Projname*.hhc|*Projname*\hlp|archivos de Ayuda HTML|El contenido del proyecto de ayuda.|  
|Makehtmlhelp.bat|*Projname*|Archivos de origen|Utilizada por el sistema para compilar el proyecto de ayuda cuando se compila el proyecto.|  
|Afxcore.htm|*Projname*\hlp|Temas de Ayuda HTML|Contiene los temas de ayuda estándares para comandos MFC estándar y objetos de la pantalla. Agregue sus propios temas de ayuda para este archivo.|  
|Afxprint.htm|*Projname*\hlp|Temas de Ayuda HTML|Contiene los temas de ayuda para los comandos de impresión.|  
|\*.jpg; \*.gif|*Nombre_proyecto*\hlp\Images|Archivos de recursos|Contienen imágenes de los temas de ayuda generados diferentes.|  
  
## <a name="see-also"></a>Vea también  
 [Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)