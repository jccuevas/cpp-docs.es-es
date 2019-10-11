---
title: 'Tutorial: Crear y usar una biblioteca personalizada de vínculos dinámicos (C++)'
description: Use C++ para crear una biblioteca de vínculos dinámicos (DLL) de Windows en Visual Studio.
ms.custom: conceptual
ms.date: 08/22/2019
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: 7bc0cb58cbbe995aa9d74e3ccb627ddc442bd4fb
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "70026030"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Tutorial: Crear y usar una biblioteca personalizada de vínculos dinámicos (C++)

En este tutorial paso a paso se muestra cómo usar el IDE de Visual Studio para crear su propia biblioteca de vínculos dinámicos (DLL) escrita C++ en Microsoft (MSVC). A continuación, se muestra cómo usar el archivo DLL C++ desde otra aplicación. Los archivos DLL (también conocidos como *bibliotecas compartidas* en sistemas operativos basados en UNIX) son uno de los tipos de componentes de Windows más útiles. Puede usarlos como una manera de compartir código y recursos, y reducir el tamaño de las aplicaciones. Los archivos dll pueden incluso facilitar el servicio y la ampliación de las aplicaciones.

En este tutorial, creará un archivo DLL que implementa algunas funciones matemáticas. Después, creará una aplicación de consola que usa las funciones del archivo DLL. También obtendrá una introducción a algunas de las técnicas y convenciones de programación que se usan en los archivos dll de Windows.

En este tutorial se tratan las siguientes tareas:

- Cree un proyecto de DLL en Visual Studio.

- Agregue funciones exportadas y variables al archivo DLL.

- Cree un proyecto de aplicación de consola en Visual Studio.

- Utilice las funciones y variables que se importaron desde el archivo DLL en la aplicación de consola.

- Ejecute la aplicación completada.

Al igual que una biblioteca vinculada estáticamente, un archivo DLL _exporta_ variables, funciones y recursos por nombre. Una aplicación cliente _importa_ los nombres para usar esas variables, funciones y recursos. A diferencia de una biblioteca vinculada estáticamente, Windows conecta las importaciones de la aplicación a las exportaciones de un archivo DLL en el tiempo de carga o de ejecución, en lugar de conectarse a ellos en el tiempo de vinculación. Windows requiere información adicional que no forma parte del modelo de compilación de C++ estándar para realizar estas conexiones. El compilador de MSVC implementa algunas extensiones específicas de Microsoft en C++ para proporcionar esta información adicional. Se explicarán estas extensiones según avanzamos.

Este tutorial crea dos soluciones de Visual Studio; uno que compila el archivo DLL y otro que compila la aplicación cliente. El archivo DLL usa la Convención de llamada de C. Se puede llamar desde aplicaciones escritas en otros lenguajes de programación, siempre y cuando la plataforma, las convenciones de llamada y las convenciones de vinculación coincidan. La aplicación cliente usa la _vinculación implícita_, donde Windows vincula la aplicación al archivo DLL en el tiempo de carga. Esta vinculación permite que la aplicación llame a las funciones proporcionadas por el archivo DLL al igual que las funciones de una biblioteca vinculada de forma estática.

En este tutorial no se tratan algunas situaciones comunes. El código no muestra el uso de C++ dll por parte de otros lenguajes de programación. No se muestra cómo [crear un archivo dll de solo recursos](creating-a-resource-only-dll.md)o cómo usar la [vinculación explícita](linking-an-executable-to-a-dll.md#linking-explicitly) para cargar archivos dll en tiempo de ejecución, en lugar de en tiempo de carga. En reposo, puede usar MSVC y Visual Studio para realizar todas estas acciones.

Para consultar vínculos con más información sobre los archivos DLL, consulte [Crear archivos DLL de C o C++ en Visual Studio](dlls-in-visual-cpp.md). Para obtener más información sobre la vinculación implícita y la vinculación explícita, vea [determinar el método de vinculación que se va a usar](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Para obtener información sobre C++ cómo crear archivos DLL para su uso con lenguajes de programación que usan convenciones de vinculación de lenguaje c, vea [exportar C++ funciones para usarlas en ejecutables en lenguaje c](exporting-cpp-functions-for-use-in-c-language-executables.md). Para obtener información sobre cómo crear archivos DLL para usarse con lenguajes de. NET, consulte [Llamar a funciones de un archivo DLL desde aplicaciones programadas en Visual Basic](calling-dll-functions-from-visual-basic-applications.md).

## <a name="prerequisites"></a>Requisitos previos

- Un equipo que ejecuta Microsoft Windows 7 o versiones posteriores. Recomendamos Windows 10 para obtener la mejor experiencia de desarrollo.

::: moniker range=">=vs-2017"

- Una copia de Visual Studio. Para obtener información sobre cómo descargar e instalar Visual Studio, consulte [Instalación de Visual Studio](/visualstudio/install/install-visual-studio). Al ejecutar el programa de instalación, asegúrese de que la carga de trabaja **Desarrollo para el escritorio con C++** está activada. No se preocupe si no ha instalado esta carga de trabajo al instalar Visual Studio. Puede ejecutar de nuevo el programa de instalación e instalarla ahora.

   ![Desarrollo para el escritorio con C++](media/desktop-development-with-cpp.png "Desktop development with C++")

::: moniker-end

::: moniker range="vs-2015"

- Una copia de Visual Studio. Para obtener información sobre cómo descargar e instalar Visual Studio 2015, vea [instalar Visual studio 2015](/visualstudio/install/install-visual-studio-2015?view=vs-2015). Use una instalación **personalizada** para instalar el C++ compilador y las herramientas, ya que no están instaladas de forma predeterminada.

::: moniker-end

- Comprensión de los aspectos básicos del uso de IDE de Visual Studio. Si ha usado antes las aplicaciones de escritorio de Windows, probablemente esté al día. Para ver una introducción, consulte [Paseo por las características del IDE de Visual Studio](/visualstudio/ide/visual-studio-ide).

- Conocer todos los fundamentos del lenguaje C++ para poder continuar. No se preocupe, no hacemos nada que sea muy complicado.

::: moniker range="vs-2017"

> [!NOTE]
> En este tutorial se da por supuesto que está usando Visual Studio 2017 versión 15,9 o posterior. Algunas versiones anteriores de Visual Studio 2017 tenían defectos en las plantillas de código o usaban diferentes cuadros de diálogo de la interfaz de usuario. Para evitar problemas, use el Instalador de Visual Studio para actualizar Visual Studio 2017 a la versión 15,9 o posterior.

::: moniker-end

## <a name="create-the-dll-project"></a>Creación del proyecto DLL

En este conjunto de tareas, creará un proyecto para el archivo DLL, agregará el código y lo generará. Para comenzar, inicie el IDE de Visual Studio e inicie sesión si lo necesita. Las instrucciones varían ligeramente en función de la versión de Visual Studio que esté usando. Asegúrese de que tiene la versión correcta seleccionada en el control de la parte superior izquierda de esta página.

::: moniker range=">=vs-2019"

### <a name="to-create-a-dll-project-in-visual-studio-2019"></a>Crear un proyecto de DLL en Visual Studio 2019

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Crear nuevo proyecto**.

   ![Cree un nuevo proyecto DLL](media/create-new-dll-project-2019.png "Crear el proyecto MathLibrary")

1. En la parte superior del cuadro de diálogo, establezca **Lenguaje** en **C++** , establezca **Plataforma** en **Windows** y establezca **Tipo de proyecto** en **Biblioteca**.

1. En la lista filtrada de tipos de proyecto, seleccione **biblioteca de vínculos dinámicos (dll)** y, a continuación, elija **siguiente**.

1. En la página **configurar el nuevo proyecto** , escriba *MathLibrary* en el cuadro **nombre de proyecto** para especificar un nombre para el proyecto. Deje los valores de **nombre de solución** y **Ubicación** predeterminados. Establezca **solución** para **crear una nueva solución**. Desactive **colocar solución y proyecto en el mismo directorio** si está activado.

1. Elija el botón **Crear** para crear el proyecto.

Cuando se crea la solución, puede ver los archivos de proyecto y de código fuente generados en la ventana de **Explorador de soluciones** en Visual Studio.

![Solución generada en Visual Studio](media/mathlibrary-solution-explorer-162.png "Generated solution in Visual Studio")

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-dll-project-in-visual-studio-2017"></a>Crear un proyecto de DLL en Visual Studio 2017

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**.

1. En el panel izquierdo del cuadro de diálogo **nuevo proyecto** , seleccione **instalado** >   > **Visual C++**  **Windows Desktop**. En el panel central, seleccione **biblioteca de vínculos dinámicos (dll)** . Escriba *MathLibrary* en el cuadro **nombre** para especificar un nombre para el proyecto. Deje los valores de **nombre de solución** y **Ubicación** predeterminados. Establezca **solución** para **crear una nueva solución**. Active la casilla **Crear directorio para la solución** si está desactivada.

   ![Denominar el proyecto MathLibrary](media/mathlibrary-new-project-name-159.png "Name the MathLibrary project")

1. Seleccione el botón **Aceptar** para crear el proyecto.

Cuando se crea la solución, puede ver los archivos de proyecto y de código fuente generados en la ventana de **Explorador de soluciones** en Visual Studio.

![Solución generada en Visual Studio](media/mathlibrary-solution-explorer-159.png "Generated solution in Visual Studio")

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-dll-project-in-visual-studio-2015-and-older-versions"></a>Para crear un proyecto DLL en Visual Studio 2015 y versiones anteriores

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **Instalado** > **Plantillas** y seleccione **Visual C++** ; a continuación, en el panel central, seleccione **Aplicación de consola Win32**. Escriba *MathLibrary* en el cuadro de edición **nombre** para especificar un nombre para el proyecto. Deje los valores de **nombre de solución** y **Ubicación** predeterminados. Establezca **solución** para **crear una nueva solución**. Active la casilla **Crear directorio para la solución** si está desactivada.

   ![Denominar el proyecto MathLibrary](media/mathlibrary-project-name.png "Name the MathLibrary project")

1. Elija el botón **Aceptar** para descartar el cuadro de diálogo **Nuevo proyecto** e iniciar el **Asistente para aplicaciones Win32**.

   ![Introducción al Asistente para aplicaciones Win32](media/mathlibrary-project-wizard-1.png "Win32 Application Wizard Overview")

1. Elija el botón **Siguiente**. En la página **Configuración de la aplicación**, en **Tipo de aplicación**, seleccione **DLL**.

   ![Crear el archivo DLL en el Asistente para aplicaciones Win32](media/mathlibrary-project-wizard-2.png "Create DLL in Win32 Application Wizard")

1. Elija el botón **Finalizar** para crear el proyecto.

Una vez el asistente complete la solución, puede ver los archivos de origen y el proyecto generados en la ventana **Explorador de soluciones** de Visual Studio.

![Solución generada en Visual Studio](media/mathlibrary-solution-explorer-153.png "Generated solution in Visual Studio")

::: moniker-end

Ahora, este archivo DLL no sirve de mucho. A continuación, creará un archivo de encabezado para declarar las funciones que exporta el archivo DLL y, a continuación, agrega las definiciones de función al archivo DLL para que resulte más útil.

### <a name="to-add-a-header-file-to-the-dll"></a>Agregar un archivo de encabezado al archivo DLL

1. Para crear un archivo de encabezado para las funciones, en la barra de menús, elija **Proyecto**  >  **Agregar nuevo elemento**.

1. En el cuadro de diálogo **Agregar nuevo elemento**, en el panel izquierdo, seleccione **Visual C++** . En el panel central, seleccione **Archivo de encabezado (.h)** . Especifique *MathLibrary. h* como nombre del archivo de encabezado.

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

Observe las instrucciones de preprocesador en la parte superior del archivo. La nueva plantilla de proyecto para un proyecto dll agrega **exportaciones _projectname_&#95;exportación** a las macros de preprocesador definidas. En este ejemplo, Visual Studio define **MATHLIBRARY&#95;EXPORTS** cuando se compila el proyecto de DLL de MathLibrary.

Cuando la macro **MATHLIBRARY&#95;EXPORTS** está definida, la macro **MATHLIBRARY&#95;API** establece el modificador `__declspec(dllexport)` en las declaraciones de función. Este modificador indica al compilador y al vinculador que exporte una función o una variable de la DLL para que las usen otras aplicaciones. Cuando **MATHLIBRARY&#95;EXPORTS** está definido, por ejemplo, cuando se incluye el archivo de encabezado de una aplicación cliente, **MATHLIBRARY&#95;API** aplica el modificador `__declspec(dllimport)` en las declaraciones. Este modificador optimiza la importación de la función o la variable en una aplicación. Para obtener más información, consulte [dllexport, dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>Agregar la implementación al archivo DLL

::: moniker range=">=vs-2019"

1. En **Explorador de soluciones**, haga clic con el botón secundario en el nodo **archivos de código fuente** y elija **Agregar** > **nuevo elemento**. Cree un nuevo archivo. cpp denominado *MathLibrary. cpp*, de la misma manera que agregó un nuevo archivo de encabezado en el paso anterior.

1. En la ventana del editor, seleccione la pestaña de **MathLibrary.cpp** si ya se ha abierto. Si no es así, en **Explorador de soluciones**, haga doble clic en **MathLibrary. cpp** en la carpeta **archivos de código fuente** del proyecto **MathLibrary** para abrirlo.

1. En el editor, reemplace el contenido del archivo Northwind.cs por el código siguiente:

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "pch.h" // use stdafx.h in Visual Studio 2017 and earlier
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

::: moniker-end

::: moniker range="<=vs-2017"

1. En la ventana del editor, seleccione la pestaña de **MathLibrary.cpp** si ya se ha abierto. Si no es así, en **Explorador de soluciones**, haga doble clic en **MathLibrary. cpp** en la carpeta **archivos de código fuente** del proyecto **MathLibrary** para abrirlo.

1. En el editor, reemplace el contenido del archivo Northwind.cs por el código siguiente:

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h" // use pch.h in Visual Studio 2019 and later
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

::: moniker-end

Para comprobar que todo funciona, compile la biblioteca de vínculos dinámicos. En la barra de menús, elija **Compilar** > **Compilar solución**. El archivo DLL y la salida del compilador relacionado se colocan en una carpeta denominada *depurar* directamente debajo de la carpeta de la solución. Si crea una versión de lanzamiento, la salida se coloca en una carpeta denominada *Release*. La salida debe tener un aspecto similar al siguiente:

::: moniker range=">=vs-2019"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>pch.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="vs-2017"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="vs-2015"

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

::: moniker-end

Enhorabuena, ha creado un archivo DLL con Visual Studio. A continuación, creará una aplicación cliente que usa las funciones exportadas por el archivo DLL.

## <a name="create-a-client-app-that-uses-the-dll"></a>Creación de una aplicación cliente que utiliza el archivo DLL

Cuando cree un archivo DLL, piense en cómo pueden usarlo las aplicaciones cliente. Para llamar a las funciones o tener acceso a los datos exportados por un archivo DLL, el código fuente del cliente debe tener las declaraciones disponibles en tiempo de compilación. En el momento de la vinculación, el enlazador requiere información para resolver las llamadas de función o los accesos a datos. Una DLL proporciona esta información en una *biblioteca de importación*, un archivo que contiene información sobre cómo buscar las funciones y los datos, en lugar del código real. Y en tiempo de ejecución, el archivo DLL debe estar disponible para el cliente, en una ubicación que el sistema operativo puede encontrarlo.

Ya sea propio o de terceros, el proyecto de aplicación cliente necesita varios fragmentos de información para usar un archivo DLL. Debe buscar los encabezados que declaran las exportaciones de DLL, las bibliotecas de importación para el vinculador y el propio archivo DLL. Una solución consiste en copiar todos estos archivos en el proyecto de cliente. Para archivos DLL de terceros que no es probable que cambien mientras el cliente los está desarrollando, este método puede ser la mejor manera de usarlos. Sin embargo, cuando se compila también el archivo DLL, es mejor evitar la duplicación. Si realiza una copia local de los archivos DLL que están en desarrollo, puede cambiar accidentalmente un archivo de encabezado en una copia, pero no el otro, o usar una biblioteca no actualizada.

Para evitar el código no sincronizado, se recomienda establecer la ruta de acceso de inclusión en el proyecto de cliente para incluir los archivos de encabezado de la DLL directamente desde el proyecto DLL. Además, establezca la ruta de acceso de la biblioteca en el proyecto de cliente para incluir las bibliotecas de importación de DLL desde el proyecto DLL. Y, por último, copie la DLL compilada del proyecto DLL en el directorio de salida de la compilación del cliente. Este paso permite que la aplicación cliente utilice el mismo código DLL que se compila.

::: moniker range=">=vs-2019"

### <a name="to-create-a-client-app-in-visual-studio"></a>Para crear una aplicación cliente en Visual Studio

1. En la barra de menús, elija **archivo** > **nuevo** > **proyecto** para abrir el cuadro de diálogo **crear un nuevo proyecto** .

1. En la parte superior del cuadro de diálogo, establezca **Lenguaje** en **C++** , establezca **Plataforma** en **Windows** y establezca **Tipo de proyecto** en **Consola**.

1. En la lista de plantillas de proyecto, seleccione **Aplicación de consola** y **Siguiente**.

1. En la página **configurar el nuevo proyecto** , escriba *MathClient* en el cuadro **nombre de proyecto** para especificar un nombre para el proyecto. Deje los valores de **nombre de solución** y **Ubicación** predeterminados. Establezca **solución** para **crear una nueva solución**. Desactive **colocar solución y proyecto en el mismo directorio** si está activado.

   ![Denominar el proyecto de cliente](media/mathclient-project-name-2019.png "Name the client project")

1. Haga clic en el botón **Crear** para crear el proyecto de cliente.

Se crea un proyecto de aplicación de consola mínimo. El nombre del archivo de origen principal será el mismo que el elegido anteriormente. En este ejemplo, se denomina **MathClient.cpp**. Se puede compilar, pero aún no usa el archivo DLL.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-client-app-in-visual-studio-2017"></a>Crear una aplicación cliente en Visual Studio 2017

1. Para crear una aplicación de C++ que haga referencia al archivo DLL que acaba de crear, en la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, seleccione **Escritorio de Windows** en **Instalado** > **Visual C++** . En el panel central, seleccione **aplicación de consola de Windows**. Especifique el nombre del proyecto, *MathClient*, en el cuadro de edición **nombre** .  Deje los valores de **nombre de solución** y **Ubicación** predeterminados. Establezca **solución** para **crear una nueva solución**. Active la casilla **Crear directorio para la solución** si está desactivada.

   ![Denominar el proyecto de cliente](media/mathclient-new-project-name-159.png "Name the client project")

1. Elija **Aceptar** para crear el proyecto de aplicación cliente.

Se crea un proyecto de aplicación de consola mínimo. El nombre del archivo de origen principal será el mismo que el elegido anteriormente. En este ejemplo, se denomina **MathClient.cpp**. Se puede compilar, pero aún no usa el archivo DLL.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-client-app-in-visual-studio-2015"></a>Para crear una aplicación cliente en Visual Studio 2015

1. Para crear una aplicación de C++ que haga referencia al archivo DLL que acaba de crear, en la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, seleccione **Win32** en **Instalado** > **Plantillas** > **Visual C++** . En el panel central, seleccione **Aplicación de consola Win32**. Especifique el nombre del proyecto, *MathClient*, en el cuadro de edición **nombre** . Deje los valores de **nombre de solución** y **Ubicación** predeterminados. Establezca **solución** para **crear una nueva solución**. Active la casilla **Crear directorio para la solución** si está desactivada.

   ![Denominar el proyecto de cliente](media/mathclient-project-name.png "Name the client project")

1. Elija el botón **Aceptar** para descartar el cuadro de diálogo **Nuevo proyecto** e iniciar el **Asistente para aplicaciones Win32**. En la página **Información general** del cuadro de diálogo **Asistente para aplicaciones Win32** , elija el botón **Siguiente** .

1. En la página **Configuración de la aplicación** en **Tipo de aplicación**, seleccione **Aplicación de consola** si aún no se ha seleccionado.

1. Elija el botón **Finalizar** para crear el proyecto.

Cuando finaliza el asistente, se crea un proyecto de aplicación de consola mínimo automáticamente. El nombre del archivo de origen principal será el mismo que el elegido anteriormente. En este ejemplo, se denomina **MathClient.cpp**. Se puede compilar, pero aún no usa el archivo DLL.

::: moniker-end

A continuación, para llamar a las funciones de MathLibrary en el código fuente, el proyecto debe incluir el archivo *MathLibrary. h* . Puede copiar este archivo de encabezado en el proyecto de aplicación cliente y, a continuación, agregarlo al proyecto como un elemento existente. Este método puede ser una buena elección para las bibliotecas de terceros. Sin embargo, si está trabajando en el código del archivo DLL y el cliente al mismo tiempo, los archivos de encabezado podrían no estar sincronizados. Para evitar este problema, establezca la ruta de acceso de **directorios de inclusión adicionales** en el proyecto para incluir la ruta de acceso al encabezado original.

### <a name="to-add-the-dll-header-to-your-include-path"></a>Agregar el encabezado DLL a la ruta de inclusión

1. Haga clic en el botón derecho en el nodo **MathClient** del **Explorador de soluciones** para abrir el cuadro de diálogo **Páginas de propiedades**.

1. En el cuadro desplegable **configuración** , seleccione **todas las configuraciones** si aún no está seleccionada.

1. En el panel izquierdo, seleccione **propiedades** > de configuración**CC++/**  > **General**.

1. En el panel de propiedades, seleccione el control de lista desplegable junto al cuadro de edición **Directorios de inclusión adicionales** y, a continuación, elija **Editar**.

   ![Editar la propiedad Directorios de inclusión adicionales](media/mathclient-additional-include-directories-property.png "Edit the Additional Include Directories property")

1. Haga doble clic en el panel superior del cuadro de diálogo **Directorios de inclusión adicionales** para habilitar un control de edición. O bien, elija el icono de carpeta para crear una nueva entrada.

1. En el control de edición, especifique la ruta de acceso a la ubicación del archivo **MathLibrary.h**. Puede elegir el control de puntos suspensivos ( **...** ) para ir a la carpeta correcta.

   También puede especificar una ruta de acceso relativa de los archivos de origen de cliente en la carpeta que contiene los archivos de encabezado de la DLL. Si ha seguido las instrucciones para colocar el proyecto de cliente en una solución independiente del archivo DLL, la ruta de acceso relativa debe ser similar a la siguiente:

   `..\..\MathLibrary\MathLibrary`

   Si el archivo DLL y los proyectos de cliente están en la misma solución, la ruta de acceso relativa podría ser similar a la siguiente:

   `..\MathLibrary`

   Cuando el archivo DLL y los proyectos de cliente están en otras carpetas, ajuste la ruta de acceso relativa para que coincida. O bien, use el control de puntos suspensivos para buscar la carpeta.

   ![Agregar la ubicación del encabezado a la propiedad Directorios de inclusión adicionales](media/mathclient-additional-include-directories.png "Add the header location to the Additional Include Directories property")

1. Después de escribir la ruta de acceso al archivo de encabezado en el cuadro de diálogo **directorios de inclusión adicionales** , elija el botón **Aceptar** . En el cuadro de diálogo **páginas de propiedades** , elija el botón **Aceptar** para guardar los cambios.

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

Este código se puede compilar, pero no vincular. Si compila la aplicación cliente ahora, la lista de errores muestra varios errores LNK2019. Esto se debe a que falta información en el proyecto: Todavía no ha especificado que el proyecto tiene una dependencia de la biblioteca *MathLibrary. lib* . Además, no ha indicado al enlazador cómo encontrar el archivo *MathLibrary. lib* .

Para corregir este problema, puede copiar el archivo de biblioteca directamente en el proyecto de aplicación cliente. El enlazador lo encontraría y lo usaría automáticamente. Sin embargo, si la biblioteca y la aplicación cliente están en desarrollo, eso podría provocar cambios en una copia que no se muestran en la otra. Para evitar este problema, puede establecer la propiedad **dependencias adicionales** para indicar al sistema de compilación que el proyecto depende de *MathLibrary. lib*. Además, puede establecer una ruta de **directorios de biblioteca adicional** en el proyecto para incluir la ruta de acceso a la biblioteca original al vincular.

### <a name="to-add-the-dll-import-library-to-your-project"></a>Agregar la biblioteca de importación de DLL al proyecto

1. Haga clic con el botón secundario en el nodo **MathClient** en **Explorador de soluciones** y elija **propiedades** para abrir el cuadro de diálogo **páginas de propiedades** .

1. En el cuadro desplegable **configuración** , seleccione **todas las configuraciones** si aún no está seleccionada. Garantiza que los cambios de propiedad se aplican a las compilaciones de depuración y de versión.

1. En el panel izquierdo, seleccione **propiedades** > de configuración**enlazador** > de**entrada**. En el panel de propiedades, seleccione el control de lista desplegable junto al cuadro de edición **Dependencias adicionales** y, a continuación, elija **Editar**.

   ![Editar la propiedad Dependencias adicionales](media/mathclient-additional-dependencies-property.png "Edit the Additional Dependencies property")

1. En el cuadro de diálogo **dependencias adicionales** , agregue *MathLibrary. lib* a la lista en el control de edición superior.

   ![Agregar la dependencia de biblioteca](media/mathclient-additional-dependencies.png "Add the library dependency")

1. Elija **Aceptar** para volver al cuadro de diálogo **Páginas de propiedades**.

1. En el panel izquierdo, seleccione **propiedades** > de configuración**enlazador** > **General**. En el panel de propiedades, seleccione el control de lista desplegable junto al cuadro de edición **Directorios de bibliotecas adicionales** y, a continuación, elija **Editar**.

   ![Editar la propiedad Directorios de bibliotecas adicionales](media/mathclient-additional-library-directories-property.png "Edit the Additional Library Directories property")

1. Haga doble clic en el panel superior del cuadro de diálogo **Directorios de bibliotecas adicionales** para habilitar un control de edición. En el control de edición, especifique la ruta de acceso a la ubicación del archivo **MathLibrary.lib**. De forma predeterminada, se encuentra en una carpeta denominada *depurar* directamente en la carpeta de la solución dll. Si crea una versión de lanzamiento, el archivo se coloca en una carpeta denominada *Release*. Puede usar la `$(IntDir)` macro para que el enlazador pueda encontrar el archivo dll, con independencia del tipo de compilación que cree. Si ha seguido las instrucciones para colocar el proyecto de cliente en una solución independiente del proyecto DLL, la ruta de acceso relativa debe ser similar a la siguiente:

   `..\..\MathLibrary\$(IntDir)`

   Si el archivo DLL y los proyectos de cliente están en la misma solución, la ruta de acceso relativa debe ser similar a la siguiente:

   `..\MathLibrary\$(IntDir)`

   ![Agregar el directorio de bibliotecas](media/mathclient-additional-library-directories.png "Add the library directory")

1. Después de escribir la ruta de acceso al archivo de biblioteca en el cuadro de diálogo **Directorios de bibliotecas adicionales**, elija el botón **Aceptar** para volver al cuadro de diálogo **Páginas de propiedades**. Elija **Aceptar** para guardar los cambios de propiedad.

La aplicación cliente ahora se puede compilar y vincular correctamente, pero todavía no tiene todo lo que necesita para ejecutarse. Cuando el sistema operativo carga la aplicación, busca el archivo DLL MathLibrary. Si no encuentra el archivo DLL en ciertos directorios del sistema, la ruta de acceso de entorno o el directorio de aplicaciones local, se produce un error de carga. En función del sistema operativo, verá un mensaje de error similar al siguiente:

![Error de MATHLIBRARY dll no encontrado](media/mathclient-system-error-mathlibrary-dll-not-found.png "Error de MATHLIBRARY dll no encontrado")

Una forma de evitar este problema es copiar el archivo DLL en el directorio que contiene el archivo ejecutable del cliente como parte del proceso de compilación. Puede Agregar un **evento posterior** a la compilación al proyecto para agregar un comando que copie el archivo dll en el directorio de salida de la compilación. El comando especificado aquí copia el archivo DLL solo si falta o ha cambiado. Usa macros para copiar a y desde las ubicaciones de depuración o de versión, en función de la configuración de compilación.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>Copiar el archivo DLL en un evento posterior a la compilación

1. Haga clic con el botón secundario en el nodo **MathClient** en **Explorador de soluciones** y elija **propiedades** para abrir el cuadro de diálogo **páginas de propiedades** .

1. En el cuadro desplegable **Configuración**, seleccione **Todas las configuraciones** si aún no se ha seleccionado.

1. En el panel izquierdo, seleccione **propiedades** > de configuración**eventos de compilación eventos** > **posteriores a la compilación**.

1. En el panel de propiedades, seleccione el control editar en el campo **línea de comandos** . Si ha seguido las instrucciones para colocar el proyecto de cliente en una solución independiente del proyecto DLL, escriba este comando:

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   Si el archivo DLL y los proyectos de cliente están en el mismo directorio de la solución, escriba este comando:

   `xcopy /y /d "..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![Agregar el comando posterior a la compilación](media/mathclient-post-build-command-line.png "Add the post-build command")

1. Elija el botón **Aceptar** para guardar los cambios en las propiedades del proyecto.

Ahora la aplicación cliente tiene todo que lo necesario para compilarse y ejecutarse. Compile la aplicación seleccionando **Compilar** > **Compilar solución** en la barra de menús. La ventana de **salida** de Visual Studio debe tener algo parecido al ejemplo siguiente, en función de la versión de Visual Studio:

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Ha creado una aplicación que llama a funciones del archivo DLL. Ahora ejecute la aplicación para ver lo que hace. En la barra de menús, seleccione **Depurar** > **Iniciar sin depuración**. Visual Studio abre una ventana de comandos para que se ejecute el programa. La última parte de la salida debe tener un aspecto parecido al siguiente:

![Iniciar la aplicación cliente sin depurar](media/mathclient-run-without-debugging.png "Start the client app without debugging")

Pulse cualquier tecla para cerrar la ventana de comandos.

Ahora que ha creado un archivo DLL y una aplicación cliente, puede experimentar. Intente establecer puntos de interrupción en el código de la aplicación cliente y ejecutar la aplicación en el depurador. Vea qué sucede cuando depure paso a paso por instrucciones una llamada a la biblioteca. Agregue otras funciones a la biblioteca o escriba otra aplicación cliente que use el archivo DLL.

Al implementar la aplicación, también debe implementar los archivos DLL que utiliza. La manera más sencilla de hacer que los archivos DLL que se compilan, o que se incluyen de terceros, estén disponibles es colocarlos en el mismo directorio que la aplicación. Se conoce como *implementación local*de la aplicación. Para obtener más información sobre la implementación, vea [Deployment in Visual C++](../windows/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Vea también

[Llamada a funciones de un archivo DLL desde aplicaciones programadas en Visual Basic](calling-dll-functions-from-visual-basic-applications.md)
