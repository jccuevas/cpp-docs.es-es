---
title: Archivos creados para proyectos de CLR | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ projects, CLR programming
- .NET applications, C++
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9d66c3f55164a743bc395dc5e9b48f8bcd57654
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="files-created-for-clr-projects"></a>Archivos creados para proyectos de CLR
Cuando usa plantillas de Visual C++ para crear proyectos, se crean varios archivos, dependiendo de la plantilla que use. En la tabla siguiente se enumera todos los archivos que se crean mediante plantillas de proyecto para los proyectos de .NET Framework.  
  
|Nombre del archivo|Descripción del archivo|  
|---------------|----------------------|  
|AssemblyInfo.cpp|El archivo que contiene información (es decir, atributos, archivos, recursos, tipos, información de versiones, información de firma etc.) para modificar los metadatos del ensamblado del proyecto. Para obtener más información, consulte [ensamblado conceptos](/dotnet/framework/app-domains/assembly-contents).|  
|*Nombre_proyecto*.asmx|Un archivo de texto que las referencias a clases administran que encapsulan la funcionalidad del servicio Web XML.|  
|*Nombre_proyecto*.cpp|El archivo de código fuente principal y punto de entrada en la aplicación que Visual Studio crea automáticamente. Identifica el archivo .dll y el espacio de nombres del proyecto. Incluya su propio código en este archivo.|  
|*Nombre_proyecto*.vsdisco|Un archivo de implementación de XML que contiene vínculos a otros recursos que describen el servicio Web XML.|  
|*Nombre_proyecto*. h|El archivo de inclusión principal para el proyecto, que contiene todas las declaraciones, símbolos globales, y `#include` directivas para otros archivos de encabezado.|  
|*Nombre_proyecto*.sln|El archivo de solución utilizado dentro del entorno de desarrollo para organizar todos los elementos del proyecto en una única solución.|  
|*Nombre_proyecto*.suo|El archivo de opciones de solución utilizado dentro del entorno de desarrollo.|  
|*Nombre_proyecto*.vcxproj|El archivo de proyecto utilizado dentro del entorno de desarrollo que almacena la información específica de este proyecto.|  
|ReadMe.txt|Un archivo que describe cada archivo del proyecto mediante los nombres de archivo reales creados por la plantilla.|