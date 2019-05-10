---
title: Archivos creados para proyectos de CLR
ms.date: 11/04/2016
helpviewer_keywords:
- Visual Studio C++ projects, CLR programming
- .NET applications, C++
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
ms.openlocfilehash: e41544adb040175fc8e53ab0e6bc4f8275891580
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446320"
---
# <a name="files-created-for-clr-projects"></a>Archivos creados para proyectos de CLR

Cuando se usan las plantillas de Visual C++ para crear proyectos, se crean varios archivos, en función de la plantilla que se use. En la tabla siguiente se enumeran todos los archivos que se crean mediante plantillas de proyecto para los proyectos de .NET Framework.

|Nombre del archivo|Descripción del archivo|
|---------------|----------------------|
|AssemblyInfo.cpp|Archivo que contiene información (es decir, atributos, archivos, recursos, tipos, información sobre versiones, información de firma, etc.) para modificar los metadatos de ensamblado del proyecto. Para obtener más información, vea [Contenido de los ensamblados](/dotnet/framework/app-domains/assembly-contents).|
|*Nombre_proyecto*.asmx|Un archivo de texto que hace referencia a clases administradas que encapsulan la funcionalidad del servicio Web XML.|
|*Nombre_proyecto*.cpp|El archivo de código fuente principal y punto de entrada a la aplicación que Visual Studio crea de manera automática. Identifica el archivo .dll y el espacio de nombres del proyecto. Incluya su propio código en este archivo.|
|*Nombre_proyecto*.vsdisco|Un archivo de implementación XML que contiene vínculos a otros recursos que describen el servicio Web XML.|
|*Nombre_proyecto*.h|El archivo de inclusión principal para el proyecto, que contiene todas las declaraciones, símbolos globales y directivas `#include` para otros archivos de encabezado.|
|*Nombre_proyecto*.sln|El archivo de solución que se usa dentro del entorno de desarrollo para organizar todos los elementos del proyecto en una única solución.|
|*Nombre_proyecto*.suo|El archivo de opciones de solución que se usa dentro del entorno de desarrollo.|
|*Nombre_proyecto*.vcxproj|El archivo de proyecto que se usa dentro del entorno de desarrollo que almacena la información específica de este proyecto.|
|ReadMe.txt|Un archivo que describe cada archivo del proyecto mediante los nombres de archivo reales creados por la plantilla.|