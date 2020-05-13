---
title: 'Cómo: Crear aplicaciones de consola CLR (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- console applications, templates
- CLR console applications, project template
ms.assetid: e89bce3c-706f-4ae0-8a90-cb1a0f674e70
ms.openlocfilehash: 86e5abe330b0edc514fed74a12188ab73e8bfdd8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368534"
---
# <a name="how-to-create-clr-console-applications-ccli"></a>Cómo: Crear aplicaciones de consola CLR (C++/CLI)

Puede utilizar la plantilla Aplicación de consola para crear un proyecto de aplicación de consola que ya tiene referencias y archivos esenciales del proyecto.

Normalmente, una aplicación de consola se compila en un archivo ejecutable independiente, pero no tiene una interfaz gráfica de usuario. Un usuario ejecuta la aplicación de consola en un símbolo del sistema y utiliza el símbolo del sistema para emitir instrucciones a la aplicación en ejecución. También en el símbolo del sistema, la aplicación proporciona información de salida. La inmediatez de una aplicación de consola simplifica en gran medida el aprendizaje de las técnicas de programación sin preocuparse por implementar una interfaz de usuario.

Cuando se utiliza la plantilla Aplicación de consola para crear un proyecto, agrega automáticamente los archivos y referencias siguientes:

- Hace referencia a estos espacios de nombres de .NET Framework:

  - <xref:System.AppDomainManager>: contiene clases fundamentales y clases base que definen valores de uso común y tipos de datos de referencia, eventos y controladores de eventos, interfaces, atributos y excepciones de procesamiento.

  - mscorlib: el archivo DLL de ensamblado que admite el desarrollo de .NET Framework.

- Archivos de código fuente:

  - Consola (archivo .cpp): archivo de código fuente principal y punto de entrada a la aplicación que acaba de crear. Identifica el archivo .dll y el espacio de nombres del proyecto. Incluya su propio código en este archivo.

  - AssemblyInfo.cpp: contiene atributos, archivos, recursos, tipos, información de versiones, información de firma, etc. que se pueden usar para modificar los metadatos de ensamblado del proyecto. Para obtener más información, vea [Contenido del ensamblado](/dotnet/framework/app-domains/assembly-contents).

  - Stdafx.cpp: se utiliza para compilar un archivo de encabezado precompilado denominado Win32.pch y un archivo de tipos precompilado denominado StdAfx.obj.

- Archivos de encabezado:

  - Stdafx.h: se utiliza para compilar un archivo de encabezado precompilado denominado Win32.pch y un archivo de tipos precompilado denominado StdAfx.obj.

  - resource.h: archivo de inclusión generado para app.rc.

- Archivos de recursos:

  - app.rc: archivo de script de recursos de un programa.

  - app.ico: archivo de icono de un programa.

- ReadMe.txt: describe los archivos del proyecto.

## <a name="to-create-a-common-language-runtime-clr-console-app-project"></a>Para crear un proyecto de aplicación de consola de Common Language Runtime (CLR)

1. En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.

1. En el cuadro de diálogo **Nuevo proyecto** , bajo **Plantillas instaladas**, seleccione el nodo **Visual C++** , seleccione el nodo **CLR** y, a continuación, seleccione la plantilla Aplicación de consola.

1. En el cuadro **Nombre** , escriba un nombre único para la aplicación.

   Puede especificar otros valores del proyecto y de la solución, pero no son necesarios.

1. Elija el botón **Aceptar** .

## <a name="see-also"></a>Consulte también

[Proyectos de CLR](../build/reference/files-created-for-clr-projects.md)
