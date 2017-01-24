---
title: "Archivos de encabezado y c&#243;digo fuente de controles o programas ATL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tipos de archivo [C++], código fuente y encabezados de ATL"
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Archivos de encabezado y c&#243;digo fuente de controles o programas ATL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al crear un proyecto ATL en Visual Studio se crearán los siguientes archivos, en función de las opciones que seleccione para el proyecto que va a crear.  
  
 Todos estos archivos se encuentran en el directorio *Nombre\_proyecto* y en la carpeta Header Files \(archivos .h\) o en la carpeta Source Files \(archivos .cpp\) en el Explorador de soluciones.  
  
|Nombre de archivo|Descripción|  
|-----------------------|-----------------|  
|*Nombre\_proyecto*.h|Archivo de inclusión principal que contiene las definiciones de interfaz y las declaraciones de GUID de C\+\+ de los elementos definidos en ATLSample.idl.  MIDL lo vuelve a generar durante la compilación.|  
|*Nombre\_proyecto.*cpp|Archivo de código fuente del programa principal.  Contiene la implementación de las exportaciones del archivo DLL para un servidor en proceso y la implementación de `WinMain` para un servidor local.  Para un servicio, implementa además todas las funciones de administración de servicios.|  
|Resource.h|Archivo de encabezado del archivo de recursos.|  
|StdAfx.cpp|Incluye los archivos StdAfx.h y Atlimpl.cpp.|  
|StdAfx.h|Incluye los archivos de encabezado ATL.|  
  
## Vea también  
 [Tipos de archivos creados para proyectos de Visual C\+\+](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Archivos de encabezado y código fuente de controles o programas MFC](../ide/mfc-program-or-control-source-and-header-files.md)   
 [Proyectos de CLR](../ide/files-created-for-clr-projects.md)