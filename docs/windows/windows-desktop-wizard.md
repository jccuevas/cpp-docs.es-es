---
title: Asistente para escritorio de Windows
ms.date: 03/29/2019
f1_keywords:
- vc.appwiz.win32.overview
- vc.appwiz.win32.appset
helpviewer_keywords:
- Windows Desktop Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
ms.openlocfilehash: 3d8be0cc33e0435bc5a18191303dbbc91277de0b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075449"
---
# <a name="windows-desktop-wizard"></a>Asistente para escritorio de Windows

El Asistente para escritorio de Windows reemplaza al Asistente para aplicaciones Win32 de Visual Studio 2017 y versiones posteriores. El asistente le permite crear cuatro tipos de C++ proyecto (que se enumeran en el encabezado de la tabla siguiente). En cada caso, puede especificar opciones adicionales apropiadas para el tipo de proyecto que abra.

   ![Asistente para escritorio de Windows](media/windows-desktop-wizard.png)

En la tabla siguiente se indican las opciones disponibles para cada tipo de aplicación.

|Tipo de soporte|Aplicación de consola|Aplicación ejecutable (para Windows)|Biblioteca de vínculos dinámicos|Biblioteca estática|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**Proyecto vacío**|Sí|Sí|Sí|No|
|**Exportar símbolos**|No|No|Sí|No|
|**Encabezado precompilado**|No|No|No|Sí|
|**compatibilidad con ATL**|Sí|No|No|No|
|**compatibilidad con MFC**|Sí|No|No|Sí|

## <a name="overview"></a>Información general

En esta página del asistente se describe la configuración del proyecto actual para la aplicación Win32 que se está creando. De forma predeterminada, se establecen las siguientes opciones:

- El proyecto es una aplicación para Windows.

- El proyecto no está vacío.

- El proyecto no contiene símbolos para exportar.

- El proyecto no usa un archivo de encabezado precompilado (esta opción solo está disponible para proyectos de biblioteca estática).

- El proyecto no incluye compatibilidad con MFC ni con ATL.

## <a name="application-type"></a>Tipo de aplicación

Crea el tipo de aplicación especificado.

|Opción|Descripción|
|------------|-----------------|
|**Aplicación de consola**|Crea una aplicación de consola. Las C++ [bibliotecas en tiempo de ejecución](../c-runtime-library/c-run-time-library-reference.md) de Visual también proporcionan salida e información de las ventanas de la consola con funciones de e/s estándar, como `printf_s()` y `scanf_s()`. Las aplicaciones de consola no tienen interfaz gráfica de usuario. Al compilarse producen un archivo .exe que se puede ejecutar como una aplicación independiente desde la línea de comandos.<br /><br /> Puede agregar compatibilidad con MFC y ATL a las aplicaciones de consola.|
|**Aplicación para Windows**|Crea un programa Win32. Un programa Win32 es una aplicación ejecutable (EXE) escrita en C o C++, que utiliza llamadas a la API de Win32 para crear una interfaz gráfica de usuario.<br /><br /> No se puede agregar compatibilidad con MFC y ATL a una aplicación Windows.|
|**Biblioteca de vínculos dinámicos**|Crea una biblioteca de vínculos dinámicos (DLL) de Win32. Una DLL de Win32 es un archivo binario, escrito en C o C++, que utiliza llamadas a la API de Win32 en lugar de llamadas a clases MFC y que actúa como una biblioteca compartida de funciones que múltiples aplicaciones pueden utilizar simultáneamente.<br /><br /> No se puede Agregar compatibilidad con MFC o ATL a una aplicación DLL creada con este asistente, pero puede crear un archivo DLL de MFC si elige **nuevo > proyecto > dll de MFC**.|
|**Biblioteca estática**|Crea una biblioteca estática. Una biblioteca estática es un archivo que contiene objetos y sus funciones, así como datos que vincula al programa cuando se compila el archivo ejecutable. En este tema se explica cómo crear los archivos de inicio y [las propiedades del proyecto](../build/reference/property-pages-visual-cpp.md) para una biblioteca estática. Un archivo de biblioteca estática proporciona las siguientes ventajas:<br /><br />-Una biblioteca estática Win32 es útil si la aplicación en la que está trabajando realiza llamadas a la API Win32 en lugar de a clases MFC.<br />-El proceso de vinculación es el mismo si el resto de la aplicación Windows se escribe en C C++o en.<br />: Puede vincular una biblioteca estática a un programa basado en MFC o a un programa no MFC.|

## <a name="additional-options"></a>Opciones adicionales

Permite definir las compatibilidades y las opciones de la aplicación, en función de su tipo.

|Opción|Descripción|
|------------|-----------------|
|**Proyecto vacío**|Especifica que los archivos de proyecto están en blanco. Si tiene un conjunto de archivos de código fuente (como archivos .cpp, archivos de encabezado, iconos, barras de herramientas, cuadros de diálogo, etc.) y desea crear un proyecto en el entorno de desarrollo de Visual C++, primero deberá crear un archivo de proyecto en blanco y después agregar los archivos al proyecto.<br /><br /> Esta selección no está disponible para los proyectos de biblioteca estática.|
|**Exportar símbolos**|Especifica que el proyecto DLL exporta símbolos.|
|**Encabezado precompilado**|Especifica que el proyecto de biblioteca estática utiliza un encabezado precompilado.|
|**Comprobaciones del ciclo de vida de desarrollo de seguridad (SDL)**|Para obtener más información acerca de SDL, consulte [ciclo de vida de desarrollo de seguridad (SDL) de Microsoft guía de procesos](../build/reference/sdl-enable-additional-security-checks.md)|

## <a name="add-common-headers-for"></a>Agregue encabezados comunes para:

Permite agregar compatibilidad con una de las bibliotecas suministradas en Visual C++.

|Opción|Descripción|
|------------|-----------------|
|**ATL**|Compila en el proyecto compatibilidad con las clases ATL (Active Template Library). Solo para aplicaciones de consola Win32.<br /><br /> **Nota:** Esta opción no indica la compatibilidad para agregar objetos ATL mediante los asistentes de código ATL. Solo puede agregar objetos ATL a proyectos ATL o a proyectos MFC con compatibilidad ATL.|
|**MFC**|Compila en el proyecto compatibilidad con la biblioteca MFC (Microsoft Foundation Class). Solo para aplicaciones de consola Win32 y bibliotecas estáticas.|

## <a name="remarks"></a>Observaciones

Una vez creada una aplicación de escritorio de Windows, puede agregar clases C++ genéricas mediante el Asistente para código [genérico](../ide/generic-cpp-class-wizard.md) . Puede agregar otros elementos, como archivos HTML, archivos de encabezado, recursos o archivos de texto.

> [!NOTE]
> No es posible agregar clases ATL y solo pueden agregarse clases MFC en los tipos de aplicación de escritorio de Windows que sean compatibles con MFC (vea la tabla anterior).

Puede ver los archivos que el asistente crea para el proyecto en el **Explorador de soluciones**. Para obtener más información sobre los archivos que el asistente crea para el proyecto, vea el archivo generado por el proyecto `ReadMe.txt`. Para obtener más información sobre los tipos de archivo, los [tipos de archivo C++ creados para proyectos de Visual Studio](../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Consulte también

[Tipos de proyectos de C++ en Visual Studio](../build/reference/visual-cpp-project-types.md)