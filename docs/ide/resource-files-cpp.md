---
title: Archivos de recursos (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource files
- resources [C++]
- file types [C++], resource files
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c295b9a3aa4996cdcd2afb17b5a4ff4c90c1159
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="resource-files-c"></a>Archivos de recursos (C++)
Los recursos son elementos de interfaz que proporcionan información al usuario. Mapas de bits, iconos, barras de herramientas y los cursores son todos los recursos. Algunos recursos se pueden manipular para llevar a cabo una acción, como seleccionar en un menú o escribir datos en el cuadro de diálogo.  
  
 Vea [trabajar con recursos](../windows/working-with-resource-files.md) para obtener más información.  
  
|Nombre del archivo|Ubicación del directorio|Ubicación del Explorador de soluciones|Descripción|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Nombre_proyecto*.rc|*Nombre_proyecto*|Archivos de origen|El archivo de script de recursos para el proyecto. El archivo de script de recursos contiene los siguientes, según el tipo de proyecto y la compatibilidad seleccionada para el proyecto (por ejemplo, las barras de herramientas, cuadros de diálogo o HTML):<br /><br /> -Definición de menú de default.<br />-Tablas de cadenas y acelerador.<br />-Valor predeterminado **sobre** cuadro de diálogo.<br />-Otros cuadros de diálogo.<br />-Archivo de icono (res\\*Nombre_proyecto*.ico).<br />-Información de versión.<br />-Mapas de bits.<br />-Barra de herramientas.<br />-Archivos HTML.<br /><br /> El archivo de recursos incluye el archivo Afxres.rc para recursos estándar de Microsoft Foundation Class.|  
|Resource.h|*Nombre_proyecto*|Archivos de encabezado|El archivo de encabezado de recursos que incluye definiciones para los recursos utilizados por el proyecto.|  
|*Nombre_proyecto*. RC2|*Nombre_proyecto*\res|Archivos de origen|El archivo de script que contiene recursos adicionales utilizados por el proyecto. Puede incluir el archivo. RC2 en la parte superior del archivo .rc del proyecto.<br /><br /> Un archivo. RC2 resulta útil para incluir recursos utilizados por varios proyectos diferentes. En lugar de tener que crear los mismos recursos varias veces para proyectos diferentes, puede colocarlos en un archivo. RC2 e incluir el archivo. RC2 en el archivo .rc principal.|  
|*Nombre_proyecto*.def|*Nombre_proyecto*|Archivos de origen|El archivo de definición de módulo para un proyecto DLL. Para un control, proporciona el nombre y la descripción del control, así como el tamaño del montón de tiempo de ejecución.|  
|*Nombre_proyecto*.ico|*Nombre_proyecto*\res|Archivos de recursos|El archivo de icono para el proyecto o el control. Este icono aparece cuando se minimiza la aplicación. También se utiliza en la aplicación **sobre** cuadro. De forma predeterminada, MFC proporciona el icono MFC y ATL proporciona el icono ATL.|  
|*Nombre_proyecto*.ico|*Nombre_proyecto*\res|Archivos de recursos|El archivo de icono para un proyecto MFC que incluye compatibilidad con la arquitectura documento/vista.|  
|Archivo ToolBar.bmp|*Nombre_proyecto*\res|Archivos de recursos|El archivo de mapa de bits que representa la aplicación o control en una barra de herramientas o una paleta. Este mapa de bits se incluye en el archivo de recursos del proyecto. La barra de herramientas inicial y la barra de estado se construyen en la **CMainFrame** clase.|  
|Ribbon.mfcribbon ms|*Nombre_proyecto*\res|Archivos de recursos|El archivo de recursos que contiene el código XML que define los botones, controles y atributos de la cinta de opciones. Para obtener más información, vea [Ribbon Designer (MFC)](../mfc/ribbon-designer-mfc.md).|  
  
## <a name="see-also"></a>Vea también  
 [Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)