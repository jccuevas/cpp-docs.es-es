---
title: Archivos de proyecto y solución
ms.date: 05/06/2019
helpviewer_keywords:
- project files [C++]
- file types [C++], makefiles
- .sdf, browsing database file
- Makefile projects
- browsing database file, .sdf
- file types [C++], project files
ms.assetid: 5823b954-36cf-42d3-8fd5-25bab3ef63d9
ms.openlocfilehash: 73d1733afde9dd62081d071df025c76bba5729d1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492654"
---
# <a name="project-and-solution-files"></a>Archivos de proyecto y solución

Los archivos siguientes se generan al crear un proyecto en Visual Studio. Se usan para administrar los archivos de proyecto de la solución.

|Filename|Ubicación del directorio|Ubicación del Explorador de soluciones|DESCRIPCIÓN|
|--------------|------------------------|--------------------------------|-----------------|
|*Nombre_solución*.sln|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El archivo de la *solución*. Organiza todos los elementos de un proyecto o varios proyectos en una solución.|
|*Nombre_proyecto*.suo|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El archivo de *opciones de solución*. Almacena personalizaciones para la solución para que cada vez que se abra un proyecto o archivo en la solución, tenga la apariencia y el comportamiento deseados.|
|*Nombre_proyecto*.vcxproj|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El archivo del *proyecto*. Almacena información específica de cada proyecto. (En versiones anteriores, este archivo se denominaba *Nombre_proyecto*.vcproj o *Nombre_proyecto*.dsp). Para obtener un ejemplo de un archivo de proyecto de C++ (.vcxproj), vea [Archivos de proyecto](project-files.md).|
|*Nombre_proyecto*.vcxitems|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El archivo *Proyecto de elementos compartidos*. Este proyecto no se compila.  En su lugar, otro proyecto de C++ puede hacer referencia al proyecto, y sus archivos formarán parte del proceso de compilación del proyecto que hace referencia. Esto se puede usar para compartir código común con proyectos de C++ multiplataforma.|
|*Nombre_proyecto*.sdf|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El archivo de *base de datos de exploración*. Admite las características de exploración y navegación como **Ir a definición**, **Buscar todas las referencias**, y **Vista de clases**. Se genera mediante el análisis de los archivos de encabezado.|
|*Projname*.vcxproj.filters|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El archivo de *filtros*. Especifica dónde colocar un archivo que se agrega a la solución. Por ejemplo, un archivo .h se coloca en el nodo **Archivos de encabezado**.|
|*Projname*.vcxproj.user|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El archivo de *usuario de migración*. Después de migrar un proyecto de Visual Studio 2008, este archivo contiene la información que se convirtió desde un archivo .vsprops.|
|*Nombre_proyecto*.idl|*Nombre_proyecto*|source|(Específico del proyecto) Contiene el código fuente del lenguaje de descripción de interfaz (IDL) de una biblioteca de tipos de control. Visual C++ usa este archivo para generar una biblioteca de tipos. La biblioteca generada expone la interfaz del control a otros clientes de automatización. Para obtener más información, vea [Interface Definition (IDL) File](/windows/win32/Rpc/the-interface-definition-language-idl-file) (Archivo de definición de interfaz [IDL]) en Windows SDK.|
|ReadMe.txt|*Nombre_proyecto*|Proyecto|El archivo *Léame*. Lo genera el asistente para aplicaciones y describe los archivos de un proyecto.|

## <a name="see-also"></a>Vea también

[Tipos de archivos creados para proyectos de C++ de Visual Studio](file-types-created-for-visual-cpp-projects.md)
