---
title: Archivos de encabezado y código fuente de controles o programas ATL
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
ms.openlocfilehash: 5c1e5fc111b38fc9e4173598f11fbad7a658d755
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707508"
---
# <a name="atl-program-or-control-source-and-header-files"></a>Archivos de encabezado y código fuente de controles o programas ATL

Los archivos siguientes se crean al crear un proyecto ATL en Visual Studio, en función de las opciones que se seleccionen para el proyecto que se crea.

Todos estos archivos se encuentran en el directorio *Nombre_proyecto* y en las carpetas Archivos de encabezado (archivos .h) o Archivos de código fuente (archivos .cpp) del Explorador de soluciones.

|Nombre del archivo|Descripción|
|---------------|-----------------|
|*Nombre_proyecto*.h|El archivo de inclusión principal que contiene las definiciones de interfaz de C++ y las declaraciones de GUID de los elementos definidos en ATLSample.idl. Se regenera mediante MIDL durante la compilación.|
|*Nombre_proyecto*.cpp|El archivo de código fuente principal del programa. Contiene la implementación de las exportaciones de los archivos DLL para un servidor en proceso y la implementación de `WinMain` para un servidor local. Para un servicio, implementa además todas las funciones de administración de servicios.|
|Resource.h|El archivo de encabezado para el archivo de recursos.|
|StdAfx.cpp|Incluye los archivos StdAfx.h y Atlimpl.cpp.|
|StdAfx.h|Incluye los archivos de encabezado de ATL.|

## <a name="see-also"></a>Vea también

[Tipos de archivos creados para proyectos de C++ de Visual Studio](file-types-created-for-visual-cpp-projects.md)<br>
[Archivos de encabezado y código fuente de controles o programas MFC](mfc-program-or-control-source-and-header-files.md)<br>
[Proyectos de CLR](files-created-for-clr-projects.md)
