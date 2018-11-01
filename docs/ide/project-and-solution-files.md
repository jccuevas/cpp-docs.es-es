---
title: Archivos de proyecto y solución | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.files.projectandsolution
dev_langs:
- C++
helpviewer_keywords:
- project files [C++]
- file types [C++], makefiles
- .sdf, browsing database file
- Makefile projects
- browsing database file, .sdf
- file types [C++], project files
ms.assetid: 5823b954-36cf-42d3-8fd5-25bab3ef63d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f52041ef8049e0e7ad4b12677ac1599b2cfd5669
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408198"
---
# <a name="project-and-solution-files"></a>Archivos de proyecto y solución

Los archivos siguientes se generan al crear un proyecto en Visual Studio. Se usan para administrar los archivos de proyecto de la solución.

|Filename|Ubicación del directorio|Ubicación del Explorador de soluciones|Descripción|
|--------------|------------------------|--------------------------------|-----------------|
|*Nombre_solución*.sln|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El archivo de la *solución*. Organiza todos los elementos de un proyecto o varios proyectos en una solución.|
|*Nombre_proyecto*.suo|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El archivo de *opciones de solución*. Almacena personalizaciones para la solución para que cada vez que se abra un proyecto o archivo en la solución, tenga la apariencia y el comportamiento deseados.|
|*Nombre_proyecto*.vcxproj|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El archivo del *proyecto*. Almacena información específica de cada proyecto. (En versiones anteriores, este archivo se denominaba *Nombre_proyecto*.vcproj o *Nombre_proyecto*.dsp). Para obtener un ejemplo de un archivo de proyecto de Visual C++, vea [Archivos de proyecto](../ide/project-files.md).|
|*Nombre_proyecto*.vcxitems|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El archivo *Proyecto de elementos compartidos*. Este proyecto no se compila.  En su lugar, otro proyecto de C++ puede hacer referencia al proyecto, y sus archivos formarán parte del proceso de compilación del proyecto que hace referencia. Esto se puede usar para compartir código común con proyectos de C++ multiplataforma.|
|*Nombre_proyecto*.sdf|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El archivo de *base de datos de exploración*. Admite las características de exploración y navegación como **Ir a definición**, **Buscar todas las referencias**, y **Vista de clases**. Se genera mediante el análisis de los archivos de encabezado.|
|*Nombre_proyecto.* vcxproj.filters|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El archivo de *filtros*. Especifica dónde colocar un archivo que se agrega a la solución. Por ejemplo, un archivo .h se coloca en el nodo **Archivos de encabezado**.|
|*Nombre_proyecto.* vcxproj.user|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El archivo de *usuario de migración*. Después de migrar un proyecto de Visual Studio 2008, este archivo contiene la información que se convirtió desde un archivo .vsprops.|
|*Nombre_proyecto*.idl|*Nombre_proyecto*|Origen|(Específico del proyecto) Contiene el código fuente del lenguaje de descripción de interfaz (IDL) de una biblioteca de tipos de control. Visual C++ usa este archivo para generar una biblioteca de tipos. La biblioteca generada expone la interfaz del control a otros clientes de Automation. Para obtener más información, vea [Interface Definition (IDL) File](/windows/desktop/Rpc/the-interface-definition-language-idl-file) (Archivo de definición de interfaz [IDL]) en Windows SDK.|
|ReadMe.txt|*Nombre_proyecto*|Proyecto|El archivo *Léame*. Lo genera el asistente para aplicaciones y describe los archivos de un proyecto.|

## <a name="see-also"></a>Vea también

[Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)