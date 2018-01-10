---
title: "Archivos de proyecto y solución | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.files.projectandsolution
dev_langs: C++
helpviewer_keywords:
- project files [C++]
- file types [C++], makefiles
- .sdf, browsing database file
- Makefile projects
- browsing database file, .sdf
- file types [C++], project files
ms.assetid: 5823b954-36cf-42d3-8fd5-25bab3ef63d9
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 03797d266dc0f3104d6153b9d946d06ac963fafc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="project-and-solution-files"></a>Archivos de proyecto y solución
Los archivos siguientes se generan al crear un proyecto en Visual Studio. Se usan para administrar los archivos de proyecto de la solución.  
  
|Filename|Ubicación del directorio|Ubicación del Explorador de soluciones|Descripción|  
|--------------|------------------------|--------------------------------|-----------------|  
|*Nombre_solución*.sln|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El *solución* archivo. Organiza todos los elementos de un proyecto o varios proyectos en una solución.|  
|*Nombre_proyecto*.suo|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El *opciones de la solución* archivo. Almacena personalizaciones para la solución para que cada vez que se abra un proyecto o archivo en la solución, tenga la apariencia y el comportamiento deseados.|  
|*Nombre_proyecto*.vcxproj|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El *proyecto* archivo. Almacena información específica de cada proyecto. (En versiones anteriores, este archivo se denominaba *Nombre_proyecto*.vcproj o *Nombre_proyecto*.dsp.) Para obtener un ejemplo de un archivo de proyecto de Visual C++, vea [archivos de proyecto](../ide/project-files.md).|  
|*Nombre_proyecto*.vcxitems|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El *proyecto elementos compartidos* archivo. Este proyecto no se compila.  En su lugar, el proyecto puede hacer referencia a otro proyecto de C++, y sus archivos formará parte del proceso de compilación del proyecto que hace referencia. Esto se puede utilizar para compartir código común con los proyectos de C++ multiplataforma.|
|*Nombre_proyecto*.sdf|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El *examinar la base de datos* archivo. Admite las características de exploración y navegación como **ir a definición**, **buscar todas las referencias**, y **vista de clases**. Se genera mediante el análisis de los archivos de encabezado.|  
|*Nombre_proyecto.* vcxproj.filters|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El *filtros* archivo. Especifica dónde colocar un archivo que se agrega a la solución. Por ejemplo, un archivo .h se coloca en el **archivos de encabezado** nodo.|  
|*Nombre_proyecto.* vcxproj.user|*Nombre_proyecto*|No se muestra en el Explorador de soluciones|El *usuario migración* archivo. Después de migrar un proyecto de Visual Studio 2008, este archivo contiene la información que se convirtió desde un archivo .vsprops.|  
|*Nombre_proyecto*.idl|*Nombre_proyecto*|Origen|(Específico del proyecto) Contiene el código fuente del lenguaje de descripción de interfaz (IDL) de una biblioteca de tipos de control. Visual C++ usa este archivo para generar una biblioteca de tipos. La biblioteca generada expone la interfaz del control a otros clientes de Automation. Para obtener más información, consulte [archivo de definición de interfaz (IDL)](http://msdn.microsoft.com/library/windows/desktop/aa378712) del SDK de Windows.|  
|ReadMe.txt|*Nombre_proyecto*|Proyecto|El *Léame* archivo. Lo genera el asistente para aplicaciones y describe los archivos de un proyecto.|  
  
## <a name="see-also"></a>Vea también  
 [Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)