---
title: Archivos de ayuda (Ayuda HTML)
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], HTML Help files
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
ms.openlocfilehash: cde4809fa270e66081088d68d806e637f64e5344
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826280"
---
# <a name="help-files-html-help"></a>Archivos de ayuda (Ayuda HTML)

Los archivos siguientes se crean al agregar el tipo Ayuda HTML de Ayuda y soporte técnico a la aplicación activando la casilla **Ayuda contextual** y, después, seleccionando **Formato de Ayuda HTML** en la página [Características avanzadas](../../mfc/reference/advanced-features-mfc-application-wizard.md) del Asistente para aplicaciones MFC.

|Nombre del archivo|Ubicación del directorio|Ubicación del Explorador de soluciones|Descripción|
|---------------|------------------------|--------------------------------|-----------------|
|*Nombre_proyecto*.hhp|*Nombre_proyecto*\hlp|archivos de Ayuda HTML|El archivo de proyecto de ayuda. Contiene los datos necesarios para compilar los archivos de ayuda en un archivo .hxs o .chm.|
|*Nombre_proyecto*.hhk|*Nombre_proyecto*\hlp|archivos de Ayuda HTML|Contiene un índice de los temas de ayuda.|
|*Nombre_proyecto*.hhc|*Nombre_proyecto*\hlp|archivos de Ayuda HTML|El contenido del proyecto de ayuda.|
|Makehtmlhelp.bat|*Nombre_proyecto*|Archivos de código fuente|El sistema los usa para compilar el proyecto de ayuda cuando se compila el proyecto.|
|Afxcore.htm|*Nombre_proyecto*\hlp|Temas de Ayuda HTML|Contiene los temas de ayuda estándar para los comandos de MFC estándar y los objetos de la pantalla. Agregue temas de ayuda propios a este archivo.|
|Afxprint.htm|*Nombre_proyecto*\hlp|Temas de Ayuda HTML|Contiene los temas de ayuda para los comandos de impresión.|
|*.jpg; \*.gif|*Nombre_proyecto*\hlp\Images|Archivos de recursos|Contienen imágenes para los diferentes temas de archivo de ayuda generados.|

## <a name="see-also"></a>Vea también

[Tipos de archivos creados para proyectos de Visual C++](file-types-created-for-visual-cpp-projects.md)
