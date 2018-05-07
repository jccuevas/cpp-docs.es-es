---
title: Archivos de encabezado y código fuente de controles o programas ATL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e8e5065cebab002e9c48aef560eb9f2feab67e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="atl-program-or-control-source-and-header-files"></a>Archivos de encabezado y código fuente de controles o programas ATL
Los siguientes archivos se crean al crear un proyecto ATL en Visual Studio, dependiendo de las opciones que seleccione para el proyecto que cree.  
  
 Todos estos archivos se encuentran en el *Nombre_proyecto* directorio y en la carpeta Header Files (archivos. h) o la carpeta Source Files (archivos .cpp) en el Explorador de soluciones.  
  
|Nombre del archivo|Descripción|  
|---------------|-----------------|  
|*Nombre_proyecto*. h|El archivo de inclusión principal que contiene las definiciones de interfaz de C++ y declaraciones de GUID de los elementos definidos en ATLSample.idl. Se volverá a generar mediante MIDL durante la compilación.|  
|*Nombre_proyecto*.cpp|El archivo de origen principal del programa. Contiene la implementación de las exportaciones de la DLL para un servidor en proceso y la implementación de `WinMain` para un servidor local. Para un servicio, implementa además todas las funciones de administración de servicio.|  
|Resource.h|El archivo de encabezado para el archivo de recursos.|  
|StdAfx.cpp|Incluye los archivos StdAfx.h y Atlimpl.cpp.|  
|StdAfx.h|Incluye los archivos de encabezado ATL.|  
  
## <a name="see-also"></a>Vea también  
 [Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Archivos de encabezado y código fuente de controles o programas MFC](../ide/mfc-program-or-control-source-and-header-files.md)   
 [Proyectos de CLR](../ide/files-created-for-clr-projects.md)