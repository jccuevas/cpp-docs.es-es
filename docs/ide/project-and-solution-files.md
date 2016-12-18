---
title: "Archivos de proyecto y soluci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.files.projectandsolution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".sdf, examinar el archivo de base de datos"
  - "examinar el archivo de base de datos, .sdf"
  - "tipos de archivo [C++], Make (archivos)"
  - "tipos de archivo [C++], archivos de proyecto"
  - "proyectos de archivos Make"
  - "archivos de proyecto [C++]"
ms.assetid: 5823b954-36cf-42d3-8fd5-25bab3ef63d9
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Archivos de proyecto y soluci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los archivos siguientes se generan al crear un proyecto en Visual Studio.  Se usan para administrar los archivos de proyecto de la solución.  
  
|Filename|Ubicación del directorio|Ubicación del Explorador de soluciones|Descripción|  
|--------------|------------------------------|--------------------------------------------|-----------------|  
|*Nombre\_solución*.sln|*Nombre\_proyecto*|No se muestra en el Explorador de soluciones|Archivo de *solución*.  Organiza todos los elementos de un proyecto o varios proyectos en una solución.|  
|*Nombre\_proyecto*.suo|*Nombre\_proyecto*|No se muestra en el Explorador de soluciones|Archivo de *opciones de solución*.  Almacena personalizaciones para la solución para que cada vez que se abra un proyecto o archivo en la solución, tenga la apariencia y el comportamiento deseados.|  
|*Nombre\_proyecto*.vcxproj|*Nombre\_proyecto*|No se muestra en el Explorador de soluciones|Archivo de *proyecto*.  Almacena información específica de cada proyecto.  \(En versiones anteriores, este archivo se denominaba *Nombre\_proyecto*.vcproj o *Nombre\_proyecto*.dsp\). Para obtener un ejemplo de un archivo de proyecto de Visual C\+\+, vea [Archivos de proyecto](../ide/project-files.md).|  
|*Nombre\_proyecto*.sdf|*Nombre\_proyecto*|No se muestra en el Explorador de soluciones|Archivo de *base de datos de exploración*.  Admite las características de exploración y navegación como **Ir a definición**, **Buscar todas las referencias** y **Vista de clases**.  Se genera mediante el análisis de los archivos de encabezado.|  
|*Nombre\_proyecto.*vcxproj.filters|*Nombre\_proyecto*|No se muestra en el Explorador de soluciones|Archivo de *filtros*.  Especifica dónde colocar un archivo que se agrega a la solución.  Por ejemplo, un archivo .h se coloca en el nodo **Archivos de encabezado**.|  
|*Nombre\_proyecto.*vcxproj.user|*Nombre\_proyecto*|No se muestra en el Explorador de soluciones|Archivo de *usuario migración*.  Después de migrar un proyecto de Visual Studio 2008, este archivo contiene la información que se convirtió desde un archivo .vsprops.|  
|*Nombre\_proyecto*.idl|*Nombre\_proyecto*|Origen|\(Específico del proyecto\) Contiene el código fuente del lenguaje de descripción de interfaz \(IDL\) de una biblioteca de tipos de control.  Visual C\+\+ usa este archivo para generar una biblioteca de tipos.  La biblioteca generada expone la interfaz del control a otros clientes de automatización.  Para obtener más información, vea [Archivo de definición de interfaz \(IDL\)](http://msdn.microsoft.com/library/windows/desktop/aa378712) en [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)].|  
|ReadMe.txt|*Nombre\_proyecto*|Proyecto|Archivo *Léame*.  Lo genera el asistente para aplicaciones y describe los archivos de un proyecto.|  
  
## Vea también  
 [Tipos de archivos creados para proyectos de Visual C\+\+](../ide/file-types-created-for-visual-cpp-projects.md)