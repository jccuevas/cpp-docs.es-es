---
title: Archivos de recursos (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- resource files
- resources [C++]
- file types [C++], resource files
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
ms.openlocfilehash: b3e15c024b84bdf04c7c5611584dc1b14d82816f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827174"
---
# <a name="resource-files-c"></a>Archivos de recursos (C++)

Los recursos son elementos de interfaz que proporcionan información al usuario. Los mapas de bits, los iconos, las barras de herramientas y los cursores son todos recursos. Algunos recursos se pueden manipular para llevar a cabo una acción, como seleccionar en un menú o escribir datos en un cuadro de diálogo.

Vea [Trabajar con recursos](../../windows/working-with-resource-files.md) para obtener más información.

|Nombre del archivo|Ubicación del directorio|Ubicación del Explorador de soluciones|Descripción|
|---------------|------------------------|--------------------------------|-----------------|
|*Nombre_proyecto*.rc|*Nombre_proyecto*|Archivos de código fuente|El archivo de script de recursos para el proyecto. El archivo de script de recursos contiene lo siguiente, según el tipo de proyecto y la compatibilidad seleccionada para el proyecto (por ejemplo, barras de herramientas, cuadros de diálogo o HTML):<br /><br />- Definición de menú predeterminada.<br />- Tablas de cadenas y aceleradores.<br />- Cuadro de diálogo **Acerca de** predeterminado.<br />- Otros cuadros de diálogo.<br />- Archivo de icono (res\\*Projname*.ico).<br />- Información de versión.<br />- Mapas de bits.<br />- Barra de herramientas.<br />- Archivos HTML.<br /><br /> El archivo de recursos incluye el archivo Afxres.rc para los recursos estándar de Microsoft Foundation Class.|
|Resource.h|*Nombre_proyecto*|Archivos de encabezado|El archivo de encabezado de recursos que incluye definiciones para los recursos usados por el proyecto.|
|*Nombre_proyecto*.rc2|*Nombre_proyecto*\res|Archivos de código fuente|El archivo de script que contiene recursos adicionales usados por el proyecto. El archivo .rc2 se puede incluir en el archivo .rc del proyecto.<br /><br /> Un archivo .rc2 resulta útil para incluir recursos usados por varios proyectos diferentes. En lugar de tener que crear los mismos recursos varias veces para otros proyectos, se pueden colocar en un archivo .rc2 e incluir ese archivo .rc2 en el archivo .rc principal.|
|*Nombre_proyecto*.def|*Nombre_proyecto*|Archivos de código fuente|El archivo de definición de módulos para un proyecto DLL. Para un control, proporciona el nombre y la descripción del control, así como el tamaño del montón de tiempo de ejecución.|
|*Nombre_proyecto*.ico|*Nombre_proyecto*\res|Archivos de recursos|El archivo de icono para el proyecto o el control. Este icono aparece cuando se minimiza la aplicación. También se usa en el cuadro **Acerca de** de la aplicación. De forma predeterminada, MFC proporciona el icono MFC y ATL proporciona el icono ATL.|
|*Nombre_proyecto*Doc.ico|*Nombre_proyecto*\res|Archivos de recursos|El archivo de icono para un proyecto MFC que incluye compatibilidad con la arquitectura de documento o vista.|
|Toolbar.bmp|*Nombre_proyecto*\res|Archivos de recursos|El archivo de mapa de bits que representa la aplicación o el control en una barra de herramientas o una paleta. Este mapa de bits se incluye en el archivo de recursos del proyecto. La barra de herramientas y la barra de estado iniciales se construyen en la clase **CMainFrame**.|
|ribbon.mfcribbon-ms|*Nombre_proyecto*\res|Archivos de recursos|El archivo de recursos contiene el código XML que define los botones, controles y atributos de la cinta de opciones. Para obtener más información, vea [Ribbon Designer (MFC)](../../mfc/ribbon-designer-mfc.md).|

## <a name="see-also"></a>Vea también

[Tipos de archivos creados para proyectos de Visual C++](file-types-created-for-visual-cpp-projects.md)
