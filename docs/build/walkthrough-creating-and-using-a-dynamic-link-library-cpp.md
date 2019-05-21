---
title: 'Tutorial: Crear y usar una biblioteca personalizada de vínculos dinámicos (C++)'
description: Use C++ para crear una biblioteca de vínculos dinámicos (DLL) de Windows en Visual Studio.
ms.custom: conceptual
ms.date: 04/22/2019
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: 53cde029973c14bfc5aae521946ebeadbed738ca
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611991"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Tutorial: Crear y usar una biblioteca personalizada de vínculos dinámicos (C++)

En este tutorial paso a paso se muestra cómo usar el IDE de Visual Studio para crear su propia biblioteca de vínculos dinámicos (DLL) escrita en C++ y, a continuación, usarla desde otra aplicación de C++. Los archivos DLL (también conocidas como "bibliotecas compartidas" en los sistemas operativos basados en UNIX) son uno de los tipos más útiles de componentes de Windows. Puede usarlas como una manera de compartir recursos y el código para reducir el tamaño de las aplicaciones y para que sea más sencillo dar servicio a las aplicaciones y ampliarlas. En este tutorial, creará un archivo DLL que implementa algunas funciones matemáticas y, a continuación, compilará una aplicación de consola que usa las funciones del archivo DLL. También se ofrece una introducción a algunas de las técnicas de programación y a las convenciones utilizadas en archivos DLL de Windows.

En este tutorial se tratan las siguientes tareas:

- Cree un proyecto de DLL en Visual Studio.

- Agregue funciones exportadas y variables al archivo DLL.

- Cree un proyecto de aplicación de consola en Visual Studio.

- Utilice las funciones y variables que se importaron desde el archivo DLL en la aplicación de consola.

- Ejecute la aplicación completada.

Al igual que una biblioteca vinculada estáticamente, un archivo DLL _exporta_ variables, funciones y recursos por nombre, y la aplicación _importa_ esos nombres para usar esos recursos, funciones y variables. A diferencia de una biblioteca vinculada estáticamente, Windows conecta las importaciones de la aplicación a las exportaciones de un archivo DLL en el tiempo de carga o de ejecución, en lugar de conectarse a ellos en el tiempo de vinculación. Windows requiere información adicional que no forma parte del modelo de compilación de C++ estándar para realizar estas conexiones. El compilador de MSVC implementa algunas extensiones específicas de Microsoft en C++ para proporcionar esta información adicional. Se explicarán estas extensiones según avanzamos.

Este tutorial crea dos soluciones de Visual Studio; uno que compila el archivo DLL y otro que compila la aplicación cliente. El archivo DLL utiliza la convención de llamada de C, por lo que puede llamarse desde las aplicaciones compiladas con otros lenguajes, siempre que la plataforma y las convenciones de llamada y vinculación coincidan. La aplicación cliente usa la _vinculación implícita_, donde Windows vincula la aplicación al archivo DLL en el tiempo de carga. Esta vinculación permite que la aplicación llame a las funciones proporcionadas por el archivo DLL al igual que las funciones de una biblioteca vinculada de forma estática.

En este tutorial no se tratan algunas situaciones comunes. No muestra el uso de archivos DLL de C++ con otros lenguajes de programación. No se explica cómo crear un archivo DLL solo de recursos. No se muestra el uso de la vinculación explícita para cargar los archivos DLL en tiempo de ejecución en lugar de en tiempo de carga. Puede usar Visual C++ sin problemas para realizar todas estas operaciones. Para consultar vínculos con más información sobre los archivos DLL, consulte [Crear archivos DLL de C o C++ en Visual Studio](dlls-in-visual-cpp.md). Para obtener más información sobre la vinculación implícita y vinculación explícita, vea [Determinar el método de vinculación que se debe utilizar](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Para obtener información sobre cómo crear archivos DLL de C++ para usarse con lenguajes de programación que utilizan las convenciones de vinculación del lenguaje C, consulte [Exportar funciones de C++ para utilizarlas en ejecutables creados en C](exporting-cpp-functions-for-use-in-c-language-executables.md). Para obtener información sobre cómo crear archivos DLL para usarse con lenguajes de. NET, consulte [Llamar a funciones de un archivo DLL desde aplicaciones programadas en Visual Basic](calling-dll-functions-from-visual-basic-applications.md).

## <a name="prerequisites"></a>Requisitos previos

- Un equipo que ejecuta Microsoft Windows 7 o versiones posteriores. Recomendamos Windows 10 para obtener la mejor experiencia de desarrollo.

- Una copia de Visual Studio. Para obtener información sobre cómo descargar e instalar Visual Studio, consulte [Instalación de Visual Studio](/visualstudio/install/install-visual-studio). Al ejecutar el programa de instalación, asegúrese de que la carga de trabaja **Desarrollo para el escritorio con C++** está activada. No se preocupe si no ha instalado esta carga de trabajo al instalar Visual Studio. Puede ejecutar de nuevo el programa de instalación e instalarla ahora.

   ![Desarrollo para el escritorio con C++](media/desktop-development-with-cpp.png "Desktop development with C++")

- Comprensión de los aspectos básicos del uso de IDE de Visual Studio. Si ha usado antes las aplicaciones de escritorio de Windows, probablemente esté al día. Para ver una introducción, consulte [Paseo por las características del IDE de Visual Studio](/visualstudio/ide/visual-studio-ide).

- Conocer todos los fundamentos del lenguaje C++ para poder continuar. No se preocupe, no hacemos nada que sea muy complicado.

## <a name="create-the-dll-project"></a>Creación del proyecto DLL

En este conjunto de tareas, creará un proyecto para el archivo DLL, agregará el código y lo generará. Para comenzar, inicie el IDE de Visual Studio e inicie sesión si lo necesita. Las instrucciones que aparecen varían ligeramente según la versión de Visual Studio que use. Asegúrese de que tiene la versión correcta seleccionada en el control de la parte superior izquierda de esta página.

::: moniker range="=vs-2019"

### <a name="to-create-a-dll-project-in-visual-studio-2019"></a>Crear un proyecto de DLL en Visual Studio 2019

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Crear nuevo proyecto**.

   ![Cree un nuevo proyecto DLL](media/create-new-dll-project-2019.png "Crear el proyecto MathLibrary")

1. En la parte superior del cuadro de diálogo, establezca **Lenguaje** en **C++** , establezca **Plataforma** en **Windows** y establezca **Tipo de proyecto** en **Biblioteca**. 

1. En la lista filtrada de tipos de proyecto, elija **biblioteca de vínculos dinámicos (DLL)** y, a continuación, elija **Siguiente**. En la siguiente página, escriba `MathLibrary` en el cuadro **Nombre** con el fin de especificar un nombre para el proyecto y, si lo desea, especifique la ubicación del proyecto.

1. Elija el botón **Crear** para crear el proyecto.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-dll-project-in-visual-studio-2017"></a>Crear un proyecto de DLL en Visual Studio 2017

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**.

1. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **Instalado** y **Visual C++** si es necesario y, a continuación, elija **Escritorio de Windows**. En el panel central, seleccione **Asistente de Escritorio de Windows**. Escriba `MathLibrary` En el cuadro **Nombre** para especificar un nombre para el proyecto.

   ![Denominar el proyecto MathLibrary](media/mathlibrary-new-project-name-153.png "Name the MathLibrary project")

1. Elija el botón **Aceptar** para descartar el cuadro de diálogo **Nuevo proyecto** e iniciar el asisten te **Proyecto de escritorio de Windows** asistente.

1. En el asistente **Proyecto de escritorio de Windows**, en **Tipo de aplicación**, seleccione **Biblioteca de vínculos dinámicos (.dll)**.

   ![Crear el archivo DLL en el Asistente para proyectos de escritorio de Windows](media/mathlibrary-desktop-project-wizard-dll.png "Create DLL in Windows Desktop Project Wizard")

1. Seleccione el botón **Aceptar** para crear el proyecto.

> [!NOTE]
> Se requieren más pasos para solucionar un problema en Visual Studio 2017, versión 15.3. Siga estas instrucciones para ver si es necesario realizar este cambio.
>
>1. En el **Explorador de soluciones**, si aún no está seleccionado, seleccione el proyecto **MathLibrary** en **Solución "MathLibrary"**.
>
>1. En la barra de menús, seleccione **Proyecto** > **Propiedades**.
>
>1. En el panel de la izquierda del cuadro de diálogo **Páginas de propiedades**, seleccione **Preprocesador** en **Propiedades de configuración** > **C/C++**. Compruebe el contenido de la propiedad **Definiciones de preprocesador**.<br/><br/>![Comprobar la propiedad de las definiciones de preprocesador](media/mathlibrary-153bug-preprocessor-definitions-check.png "Check the Preprocessor Definitions property")<br/><br/>Si ve **MATHLIBRARY&#95;EXPORTS** en la lista **Definiciones de preprocesador**, no es necesario cambiar nada. Si ve **MATHLIBRARY&#95;EXPORTS** en su lugar, continúe para seguir estos pasos.
>
>1. En el cuadro de diálogo **Páginas de propiedades**, cambie el valor de la lista desplegable **Configuración** a **Todas las configuraciones**.
>
>1. En el panel de propiedades, seleccione el control de lista desplegable situada junto al cuadro de edición de **Definiciones de preprocesador** y, a continuación, elija **Editar**.<br/><br/>![Editar la propiedad de las definiciones de preprocesador](media/mathlibrary-153bug-preprocessor-definitions-property.png "Edit the Preprocessor Definitions property")
>
>1. En el panel superior del cuadro de diálogo **Definiciones de preprocesador**, agregue un nuevo símbolo, `MATHLIBRARY_EXPORTS`.<br/><br/>![Agregar el símbolo de MATHLIBRARY_EXPORTS](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "Add the MATHLIBRARY_EXPORTS symbol")
>
>1. Elija **Aceptar** para descartar el cuadro de diálogo **Definiciones de preprocesador** y, a continuación, elija **Aceptar** para guardar los cambios en las propiedades del proyecto.

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>Crear un proyecto de DLL en versiones anteriores de Visual Studio

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **Instalado** > **Plantillas** y seleccione **Visual C++** ; a continuación, en el panel central, seleccione **Aplicación de consola Win32**. Escriba `MathLibrary` en el cuadro de edición **Nombre** para especificar un nombre para el proyecto.

   ![Denominar el proyecto MathLibrary](media/mathlibrary-project-name.png "Name the MathLibrary project")

1. Elija el botón **Aceptar** para descartar el cuadro de diálogo **Nuevo proyecto** e iniciar el **Asistente para aplicaciones Win32**.

   ![Introducción al Asistente para aplicaciones Win32](media/mathlibrary-project-wizard-1.png "Win32 Application Wizard Overview")

1. Elija el botón **Siguiente**. En la página **Configuración de la aplicación**, en **Tipo de aplicación**, seleccione **DLL**.

   ![Crear el archivo DLL en el Asistente para aplicaciones Win32](media/mathlibrary-project-wizard-2.png "Create DLL in Win32 Application Wizard")

1. Elija el botón **Finalizar** para crear el proyecto.

Una vez el asistente complete la solución, puede ver los archivos de origen y el proyecto generados en la ventana **Explorador de soluciones** de Visual Studio.

![Solución generada en Visual Studio](media/mathlibrary-solution-explorer-153.png "Generated solution in Visual Studio")

Ahora, este archivo DLL no sirve de mucho. Después, cree un archivo de encabezado para declarar las funciones de las exportaciones de DLL y, a continuación, agregue las definiciones de función al archivo DLL para que resulte más útil.

::: moniker-end

### <a name="to-add-a-header-file-to-the-dll"></a>Agregar un archivo de encabezado al archivo DLL

1. Para crear un archivo de encabezado para las funciones, en la barra de menús, elija **Proyecto**  >  **Agregar nuevo elemento**.

1. En el cuadro de diálogo **Agregar nuevo elemento**, en el panel izquierdo, seleccione **Visual C++**. En el panel central, seleccione **Archivo de encabezado (.h)**. Especifique `MathLibrary.h` como el nombre del archivo de encabezado.

   ![Agregar encabezado en el cuadro de diálogo Agregar nuevo elemento](media/mathlibrary-add-new-item-header-file.png "Add header in Add New Item dialog")

1. Elija el botón **Agregar** para generar un archivo de encabezado en blanco, que se muestra en una nueva ventana del editor.

   ![Archivo MathLibrary.h vacío en el editor](media/edit-empty-mathlibrary-header.png "Empty MathLibrary.h file in editor")

1. Reemplace el contenido del archivo por el código siguiente:

   ```cpp
   // MathLibrary.h - Contains declarations of math functions
   #pragma once

   #ifdef MATHLIBRARY_EXPORTS
   #define MATHLIBRARY_API __declspec(dllexport)
   #else
   #define MATHLIBRARY_API __declspec(dllimport)
   #endif

   // The Fibonacci recurrence relation describes a sequence F
   // where F(n) is { n = 0, a
   //               { n = 1, b
   //               { n > 1, F(n-2) + F(n-1)
   // for some initial integral values a and b.
   // If the sequence is initialized F(0) = 1, F(1) = 1,
   // then this relation produces the well-known Fibonacci
   // sequence: 1, 1, 2, 3, 5, 8, 13, 21, 34, ...

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   extern "C" MATHLIBRARY_API void fibonacci_init(
       const unsigned long long a, const unsigned long long b);

   // Produce the next value in the sequence.
   // Returns true on success and updates current value and index;
   // false on overflow, leaves current value and index unchanged.
   extern "C" MATHLIBRARY_API bool fibonacci_next();

   // Get the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned long long fibonacci_current();

   // Get the position of the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned fibonacci_index();
   ```

Este archivo de encabezado declara algunas funciones para generar una secuencia de Fibonacci generalizada, dados dos valores iniciales. Una llamada a `fibonacci_init(1, 1)` genera la secuencia de números de Fibonacci familiar.

Observe las instrucciones de preprocesador en la parte superior del archivo. De forma predeterminada, la plantilla Nuevo proyecto de un archivo DLL agrega **\<em>NOMBREPROYECTO\</em>&#95;EXPORTS** a las macros de preprocesador definidas del proyecto de DLL. En este ejemplo, Visual Studio define **MATHLIBRARY&#95;EXPORTS** cuando se compila el proyecto de DLL de MathLibrary. 

::: moniker range="=vs-2017"

El Asistente en Visual Studio 2017 versión 15.3 no fuerza esta definición de símbolos a mayúsculas. Si denomina a su proyecto "MathLibrary", el símbolo definido es Library&#95;EXPORTS en lugar de MATHLIBRARY&#95;EXPORTS. (Por eso hay pasos adicionales arriba para agregar este símbolo).

::: moniker-end

Cuando la macro **MATHLIBRARY&#95;EXPORTS** está definida, la macro **MATHLIBRARY&#95;API** establece el modificador `__declspec(dllexport)` en las declaraciones de función. Este modificador indica al compilador y al vinculador que exporte una función o variable en el archivo DLL para que se pueda usar en otras aplicaciones. Cuando **MATHLIBRARY&#95;EXPORTS** está definido, por ejemplo, cuando se incluye el archivo de encabezado de una aplicación cliente, **MATHLIBRARY&#95;API** aplica el modificador `__declspec(dllimport)` en las declaraciones. Este modificador optimiza la importación de la función o la variable en una aplicación. Para obtener más información, consulte [dllexport, dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>Agregar la implementación al archivo DLL

::: moniker range="vs-2019"

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo **Archivos de origen** y agregue un nuevo archivo .cpp denominado `MathLibrary.cpp` de la misma manera que agregó un nuevo archivo de encabezado en el paso anterior.

::: moniker-end

1. En la ventana del editor, seleccione la pestaña de **MathLibrary.cpp** si ya se ha abierto. Si no es así, en el **Explorador de soluciones**, abra **MathLibrary.cpp** en la carpeta **Archivos de origen** del proyecto **MathLibrary**.

1. En el editor, reemplace el contenido del archivo Northwind.cs por el código siguiente:

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h" // use pch.h in Visual Studio 2019
   #include <utility>
   #include <limits.h>
   #include "MathLibrary.h"

   // DLL internal state variables:
   static unsigned long long previous_;  // Previous value, if any
   static unsigned long long current_;   // Current sequence value
   static unsigned index_;               // Current seq. position

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   void fibonacci_init(
       const unsigned long long a,
       const unsigned long long b)
   {
       index_ = 0;
       current_ = a;
       previous_ = b; // see special case when initialized
   }

   // Produce the next value in the sequence.
   // Returns true on success, false on overflow.
   bool fibonacci_next()
   {
       // check to see if we'd overflow result or position
       if ((ULLONG_MAX - previous_ < current_) ||
           (UINT_MAX == index_))
       {
           return false;
       }

       // Special case when index == 0, just return b value
       if (index_ > 0)
       {
           // otherwise, calculate next sequence value
           previous_ += current_;
       }
       std::swap(current_, previous_);
       ++index_;
       return true;
   }

   // Get the current value in the sequence.
   unsigned long long fibonacci_current()
   {
       return current_;
   }

   // Get the current index position in the sequence.
   unsigned fibonacci_index()
   {
       return index_;
   }
   ```

Para comprobar que todo funciona, compile la biblioteca de vínculos dinámicos. En la barra de menús, elija **Compilar** > **Compilar solución**. El resultado que obtenga debe tener un aspecto similar a este:

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Ya ha creado un archivo DLL mediante Visual C++. A continuación, creará una aplicación cliente que usa las funciones exportadas por el archivo DLL.

## <a name="create-a-client-app-that-uses-the-dll"></a>Creación de una aplicación cliente que utiliza el archivo DLL

Cuando se crea un archivo DLL, debe pensar cómo se puede usar. Para compilar el código que llama a las funciones exportadas mediante un archivo DLL, las declaraciones deben incluirse en el código fuente del cliente. En tiempo de vinculación, cuando estas llamadas a funciones DLL se resuelven, el vinculador debe tener una *biblioteca de importación*, un archivo de biblioteca especial que contiene información de Windows sobre cómo buscar las funciones, en lugar del código real. Y en tiempo de ejecución, el archivo DLL debe estar disponible para el cliente, en una ubicación que el sistema operativo puede encontrarlo.

Para usar un archivo DLL, con independencia de que sea suyo o un archivo DLL de terceros, el proyecto de aplicación cliente debe encontrar los encabezados que declaran las exportaciones de DLL, las bibliotecas de importación del enlazador y el propio archivo DLL. Una manera es copiar todos estos archivos en el proyecto de cliente. Para archivos DLL de terceros que no es probable que cambien mientras el cliente los está desarrollando, este método puede ser la mejor manera de usarlos. Sin embargo, cuando se compila también el archivo DLL, es mejor evitar la duplicación. Si realiza una copia de archivos DLL que están en desarrollo, accidentalmente puede cambiar un archivo de encabezado de una copia, pero no el otro, o usar una biblioteca obsoleta. Para evitar este problema, se recomienda establecer la ruta de inclusión en el proyecto de cliente para incluir los archivos de encabezado DLL desde el proyecto DLL. Además, establezca la ruta de acceso de la biblioteca en el proyecto de cliente para incluir las bibliotecas de importación de DLL desde el proyecto DLL. Y por último, copie el archivo DLL compilado desde el proyecto DLL en el directorio de salida de compilación. Este paso permite que la aplicación cliente utilice el mismo código DLL que se compila.

::: moniker range="vs-2019"

### <a name="to-create-a-client-app-in-visual-studio-2019"></a>Crear una aplicación de consola de C++ en Visual Studio 2019

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Crear nuevo proyecto**.

1. En la parte superior del cuadro de diálogo, establezca **Lenguaje** en **C++** , establezca **Plataforma** en **Windows** y establezca **Tipo de proyecto** en **Consola**. 

1. En la lista de plantillas de proyecto, seleccione **Aplicación de consola** y **Siguiente**. En la siguiente página, escriba `MathClient` en el cuadro **Nombre** con el fin de especificar un nombre para el proyecto y, si lo desea, especifique la ubicación del proyecto.

   ![Denominar el proyecto de cliente](media/mathclient-project-name-2019.png "Name the client project")

1. Haga clic en el botón **Crear** para crear el proyecto de cliente.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-client-app-in-visual-studio-2017"></a>Crear una aplicación cliente en Visual Studio 2017

1. Para crear una aplicación de C++ que haga referencia al archivo DLL que acaba de crear, en la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, seleccione **Escritorio de Windows** en **Instalado** > **Visual C++** . En el panel central, seleccione **Asistente de Escritorio de Windows**. Especifique el nombre para el proyecto, `MathClient`, en el cuadro de edición **Nombre**.

   ![Denominar el proyecto de cliente](media/mathclient-new-project-name-153.png "Name the client project")

1. Seleccione **Aceptar** para iniciar el asistente **Proyecto de escritorio de Windows**. En el asistente, elija **Aceptar** para crear el proyecto de aplicación cliente.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>Crear una aplicación cliente en las versiones anteriores de Visual Studio 2017

1. Para crear una aplicación de C++ que haga referencia al archivo DLL que acaba de crear, en la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, seleccione **Win32** en **Instalado** > **Plantillas** > **Visual C++**. En el panel central, seleccione **Aplicación de consola Win32**. Especifique el nombre para el proyecto, `MathClient`, en el cuadro de edición **Nombre**.

   ![Denominar el proyecto de cliente](media/mathclient-project-name.png "Name the client project")

1. Elija el botón **Aceptar** para descartar el cuadro de diálogo **Nuevo proyecto** e iniciar el **Asistente para aplicaciones Win32**. En la página **Información general** del cuadro de diálogo **Asistente para aplicaciones Win32** , elija el botón **Siguiente** .

1. En la página **Configuración de la aplicación** en **Tipo de aplicación**, seleccione **Aplicación de consola** si aún no se ha seleccionado.

1. Elija el botón **Finalizar** para crear el proyecto.

::: moniker-end

Cuando finaliza el asistente, se crea un proyecto de aplicación de consola mínimo automáticamente. El nombre del archivo de origen principal será el mismo que el elegido anteriormente. En este ejemplo, se denomina **MathClient.cpp**. Se puede compilar, pero aún no usa el archivo DLL.

A continuación, para llamar a las funciones de MathLibrary en el código fuente, el proyecto debe incluir el archivo MathLibrary.h. Puede copiar este archivo de encabezado en el proyecto de aplicación cliente y, a continuación, agregarlo al proyecto como un elemento existente. Este método puede ser una buena elección para las bibliotecas de terceros. Sin embargo, si está trabajando en el código para el archivo DLL al mismo tiempo que el cliente, podría provocar cambios en el archivo de un encabezado que no se muestran en el otro. Para evitar este problema, puede cambiar la ruta de acceso **Directorios de inclusión adicional** del proyecto para incluir la ruta de acceso en el encabezado original.

### <a name="to-add-the-dll-header-to-your-include-path"></a>Agregar el encabezado DLL a la ruta de inclusión

1. Haga clic en el botón derecho en el nodo **MathClient** del **Explorador de soluciones** para abrir el cuadro de diálogo **Páginas de propiedades**.

1. En el cuadro desplegable **Configuración**, seleccione **Todas las configuraciones** si aún no se ha seleccionado.

1. En el panel izquierdo, seleccione **General** en **Propiedades de configuración** > **C/C++**.

1. En el panel de propiedades, seleccione el control de lista desplegable junto al cuadro de edición **Directorios de inclusión adicionales** y, a continuación, elija **Editar**.

   ![Editar la propiedad Directorios de inclusión adicionales](media/mathclient-additional-include-directories-property.png "Edit the Additional Include Directories property")

1. Haga doble clic en el panel superior del cuadro de diálogo **Directorios de inclusión adicionales** para habilitar un control de edición.

1. En el control de edición, especifique la ruta de acceso a la ubicación del archivo **MathLibrary.h**. En este caso, puede usar una ruta de acceso relativa desde la carpeta que contiene los archivos .cpp del proyecto de cliente a la carpeta que contiene el archivo .h en el proyecto DLL. Si el proyecto de cliente es una solución independiente en la misma carpeta que la solución DLL, la ruta de acceso relativa debe tener este aspecto:

   `..\..\MathLibrary\MathLibrary`

   Si los proyectos DLL y el cliente están en la misma solución, o las soluciones están en carpetas diferentes, debe ajustar la ruta de acceso relativa en consecuencia.

   ![Agregar la ubicación del encabezado a la propiedad Directorios de inclusión adicionales](media/mathclient-additional-include-directories.png "Add the header location to the Additional Include Directories property")

1. Después de escribir la ruta de acceso al archivo de encabezado en el cuadro de diálogo **Directorios de inclusión adicionales**, elija el botón **Aceptar** para volver al cuadro de diálogo **Páginas de propiedades** y, a continuación, elija el botón **Aceptar** para guardar los cambios.

Ahora puede incluir el archivo **MathLibrary.h** y utilizar las funciones que declara en la aplicación cliente. Reemplace el contenido de **MathClient.cpp** mediante este código:

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
// #include "pch.h" Uncomment for Visual Studio 2017 and earlier
#include <iostream>
#include "MathLibrary.h"

int main()
{
    // Initialize a Fibonacci relation sequence.
    fibonacci_init(1, 1);
    // Write out the sequence values until overflow.
    do {
        std::cout << fibonacci_index() << ": "
            << fibonacci_current() << std::endl;
    } while (fibonacci_next());
    // Report count of values written before overflow.
    std::cout << fibonacci_index() + 1 <<
        " Fibonacci sequence values fit in an " <<
        "unsigned 64-bit integer." << std::endl;
}
```

Este código puede compilarse, pero no vincularse, porque el vinculador no puede encontrar aún la biblioteca de importación necesaria para compilar la aplicación. El vinculador debe buscar el archivo MathLibrary.lib para realizar la vinculación correctamente. Agregar el archivo MathLibrary.lib a la compilación estableciendo la propiedad **Dependencias adicionales**. Una vez más, podría copiar el archivo de biblioteca en el proyecto de aplicación cliente, pero si la biblioteca y la aplicación cliente están en desarrollo, podría dar lugar a cambios en una copia que no se muestran en la otro. Para evitar este problema, puede cambiar la ruta de acceso **Directorios de bibliotecas adicionales** en el proyecto para incluir la ruta de acceso a la biblioteca original al vincular.

### <a name="to-add-the-dll-import-library-to-your-project"></a>Agregar la biblioteca de importación de DLL al proyecto

1. Haga clic en el botón derecho en el nodo **MathClient** del **Explorador de soluciones** para abrir el cuadro de diálogo **Páginas de propiedades**.

1. En el cuadro desplegable **Configuración**, seleccione **Todas las configuraciones** si aún no se ha seleccionado. Esta configuración garantiza que se establezca la ruta de acceso para las versiones de depuración y lanzamiento.

1. En el panel izquierdo, seleccione **Entrada** en **Propiedades de configuración** > **Vinculador**. En el panel de propiedades, seleccione el control de lista desplegable junto al cuadro de edición **Dependencias adicionales** y, a continuación, elija **Editar**.

   ![Editar la propiedad Dependencias adicionales](media/mathclient-additional-dependencies-property.png "Edit the Additional Dependencies property")

1. En el cuadro de diálogo **Dependencias adicionales**, agregue `MathLibrary.lib` a la lista del control de edición superior.

   ![Agregar la dependencia de biblioteca](media/mathclient-additional-dependencies.png "Add the library dependency")

1. Elija **Aceptar** para volver al cuadro de diálogo **Páginas de propiedades**.

1. En el panel izquierdo, seleccione **General** en **Propiedades de configuración** > **Vinculador**. En el panel de propiedades, seleccione el control de lista desplegable junto al cuadro de edición **Directorios de bibliotecas adicionales** y, a continuación, elija **Editar**.

   ![Editar la propiedad Directorios de bibliotecas adicionales](media/mathclient-additional-library-directories-property.png "Edit the Additional Library Directories property")

1. Haga doble clic en el panel superior del cuadro de diálogo **Directorios de bibliotecas adicionales** para habilitar un control de edición. En el control de edición, especifique la ruta de acceso a la ubicación del archivo **MathLibrary.lib**. Especifique este valor para utilizar una macro que funcione para las compilaciones de depuración y lanzamiento:

   `..\..\MathLibrary\$(IntDir)`

   ![Agregar el directorio de bibliotecas](media/mathclient-additional-library-directories.png "Add the library directory")

1. Después de escribir la ruta de acceso al archivo de biblioteca en el cuadro de diálogo **Directorios de bibliotecas adicionales**, elija el botón **Aceptar** para volver al cuadro de diálogo **Páginas de propiedades**.

La aplicación cliente ahora se puede compilar y vincular correctamente, pero todavía no tiene todo lo que necesita para ejecutarse. Cuando el sistema operativo carga la aplicación, busca el archivo DLL MathLibrary. Si no encuentra el archivo DLL en ciertos directorios del sistema, la ruta de acceso de entorno o el directorio de aplicaciones local, se produce un error de carga. Una forma de evitar este problema es copiar el archivo DLL en el directorio que contiene el archivo ejecutable del cliente como parte del proceso de compilación. Para copiar el archivo DLL, puede agregar un **evento posterior a la compilación** al proyecto, para agregar un comando que copie el archivo DLL en el directorio de salida de compilación. El comando especificado aquí copia el archivo DLL solo si falta o ha cambiado, y usa macros para copiar con origen y destino en las ubicaciones de depuración o lanzamiento de la configuración.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>Copiar el archivo DLL en un evento posterior a la compilación

1. Haga clic en el botón derecho en el nodo **MathClient** del **Explorador de soluciones** para abrir el cuadro de diálogo **Páginas de propiedades**.

1. En el cuadro de lista desplegable Configuración, seleccione **Todas las configuraciones** si aún no se ha seleccionado.

1. En el panel izquierdo, seleccione **Evento posterior a la compilación** en **Propiedades de configuración** > **Eventos de compilación**.

1. En el panel de propiedades, seleccione el control de edición en el campo **Línea de comandos** y, a continuación, escriba este comando:

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![Agregar el comando posterior a la compilación](media/mathclient-post-build-command-line.png "Add the post-build command")

1. Elija el botón **Aceptar** para guardar los cambios en las propiedades del proyecto.

Ahora la aplicación cliente tiene todo que lo necesario para compilarse y ejecutarse. Compile la aplicación seleccionando **Compilar** > **Compilar solución** en la barra de menús. La ventana **Salida** de Visual Studio debe tener algo parecido a esto:

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>pch.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Ha creado una aplicación que llama a funciones del archivo DLL. Ahora ejecute la aplicación para ver lo que hace. En la barra de menús, seleccione **Depurar** > **Iniciar sin depuración**. Visual Studio abre una ventana de comandos para que se ejecute el programa. La última parte de la salida debe tener un aspecto parecido al siguiente:

![Iniciar la aplicación cliente sin depurar](media/mathclient-run-without-debugging.png "Start the client app without debugging")

Pulse cualquier tecla para cerrar la ventana de comandos.

Ahora que ha creado un archivo DLL y una aplicación cliente, puede experimentar. Intente establecer puntos de interrupción en el código de la aplicación cliente y ejecutar la aplicación en el depurador. Vea qué sucede cuando depure paso a paso por instrucciones una llamada a la biblioteca. Agregue otras funciones a la biblioteca o escriba otra aplicación cliente que use el archivo DLL.

Al implementar la aplicación, también debe implementar los archivos DLL que utiliza. La manera más sencilla para que los archivos DLL que compile o que incluya de terceros estén disponibles para la aplicación es colocarlos en el mismo directorio que la aplicación, también conocido como *implementación local de la aplicación*. Para obtener más información sobre la implementación, vea [Deployment in Visual C++](../windows/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Vea también

[Llamada a funciones de un archivo DLL desde aplicaciones programadas en Visual Basic](calling-dll-functions-from-visual-basic-applications.md)
