---
title: 'Tutorial: Crear y usar su propia biblioteca de vínculo dinámico (C++)'
ms.custom: conceptual
ms.date: 09/24/2018
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: c1f59c704e96ade82295f4ae88265f549987e981
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813973"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Tutorial: Crear y usar su propia biblioteca de vínculo dinámico (C++)

Este tutorial paso a paso muestra cómo usar el IDE de Visual Studio para crear su propia biblioteca de vínculos dinámicos (DLL) escrita en C++ y, a continuación, usarla desde otra aplicación de C++. Archivos DLL es uno de los tipos más útiles de componentes de Windows. Puede usarlos como una manera de compartir recursos y el código para reducir el tamaño de las aplicaciones y para que sea más fácil de servicio y amplíe sus aplicaciones. En este tutorial, cree un archivo DLL que implementa algunas funciones matemáticas y, a continuación, cree una aplicación de consola que usa las funciones de la DLL. En el camino, se ofrece una introducción a algunas de las técnicas de programación y las convenciones utilizadas en archivos DLL de Windows.

En este tutorial se tratan las siguientes tareas:

- Cree un proyecto DLL en Visual Studio.

- Agregue las funciones exportadas y variables a la DLL.

- Cree un proyecto de aplicación de consola en Visual Studio.

- Utilice las funciones y variables que se importó desde el archivo DLL en la aplicación de consola.

- Ejecute la aplicación completada.

Al igual que una biblioteca vinculada estáticamente, un archivo DLL _exporta_ variables, funciones y los recursos por nombre y la aplicación _importa_ esos nombres para usar esos recursos, funciones y variables. A diferencia de una biblioteca vinculada estáticamente, Windows conecta a las importaciones de la aplicación a las exportaciones en un archivo DLL en tiempo de carga o en tiempo de ejecución, en lugar de conectarse a ellos en tiempo de vinculación. Windows requiere información adicional que no forma parte del modelo de compilación de C++ estándar para realizar estas conexiones. El compilador de MSVC implementa algunas extensiones específicas de Microsoft para C++ para proporcionar esta información adicional. Se explican estas extensiones según avanzamos.

Este tutorial crea dos soluciones de Visual Studio; uno que compila el archivo DLL y otro que compila la aplicación cliente. El archivo DLL utiliza la convención de llamada de C, por lo que puede llamarse desde las aplicaciones compiladas con otros lenguajes, siempre que coincidan con la plataforma y una llamada y las convenciones de vinculación. La aplicación cliente usa _vinculación implícita_, donde Windows vincula la aplicación a la DLL en tiempo de carga. Esta vinculación permite que la aplicación llame a las funciones de proporcionado por el archivo DLL al igual que las funciones en una biblioteca estática vinculada.

En este tutorial no se tratan algunas situaciones comunes. No muestra el uso de archivos DLL de C++ con otros lenguajes de programación. No muestra cómo crear un archivo DLL de recursos. No muestra el uso de la vinculación explícita para cargar los archivos DLL en tiempo de ejecución en lugar de en tiempo de carga. Descanse tranquilo, puede usar Visual C++ para realizar todas estas operaciones. Para obtener vínculos para obtener más información sobre los archivos DLL, consulte [archivos DLL en Visual C++](dlls-in-visual-cpp.md). Para obtener más información sobre la vinculación implícita y vinculación explícita, vea [determinar que el método de vinculación que se usarán](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Para obtener información acerca de cómo crear archivos DLL de C++ para su uso con idiomas que utilizan las convenciones de vinculación de lenguaje de programación, vea [exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](exporting-cpp-functions-for-use-in-c-language-executables.md). Para obtener información sobre cómo crear archivos DLL para su uso con lenguajes de. NET, consulte [llamar a funciones DLL desde aplicaciones de Visual Basic](calling-dll-functions-from-visual-basic-applications.md).

En este tutorial se usa Visual Studio 2017, pero el código y la mayoría de las instrucciones es aplicable a versiones anteriores. Puede cambiar los pasos para crear nuevos proyectos a partir de Visual Studio 2017 versión 15.3. Este tutorial describe cómo crear proyectos para las versiones anteriores y más recientes. Busque los pasos que coinciden con su versión de Visual Studio.

## <a name="prerequisites"></a>Requisitos previos

- Un equipo que ejecuta Microsoft Windows 7 o versiones posteriores. Se recomienda Windows 10 para una mejor experiencia de desarrollo.

- Una copia de Visual Studio 2017. Para obtener información sobre cómo descargar e instalar Visual Studio, consulte [instalar Visual Studio 2017](/visualstudio/install/install-visual-studio). Al ejecutar el programa de instalación, asegúrese de que el **desarrollo de escritorio con C++** está activada la carga de trabajo. No se preocupe si no ha instalado esta carga de trabajo al instalar Visual Studio. Puede ejecutar de nuevo el instalador y lo instale ahora.

   ![Desarrollo de escritorio con C++](media/desktop-development-with-cpp.png "desarrollo de escritorio con C++")

- Comprensión de los aspectos básicos del uso de IDE de Visual Studio. Si ha usado las aplicaciones de escritorio de Windows antes, probablemente puede mantenerse al día. Para obtener una introducción, consulte [Guía de características del IDE de Visual Studio](/visualstudio/ide/visual-studio-ide).

- Comprensión de lo suficiente los aspectos básicos del lenguaje C++ para seguir el tutorial. No se preocupe, no hacemos algo muy complicado.

## <a name="create-the-dll-project"></a>Crear el proyecto DLL

En este conjunto de tareas, crear un proyecto para el archivo DLL, agregue el código y genérelo. Para comenzar, inicie el IDE de Visual Studio e inicie sesión si necesita. Las instrucciones para Visual Studio 2017 versión 15.3 aparecer en primer lugar. Instrucciones para las versiones anteriores más adelante, por lo que vaya si necesita.

### <a name="to-create-a-dll-project-in-visual-studio-2017-version-153-or-later"></a>Para crear un proyecto DLL en Visual Studio 2017 versión 15.3 o posterior

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**.

1. En el panel izquierdo de la **nuevo proyecto** cuadro de diálogo, expanda **instalado** y **Visual C++** si es necesario y, a continuación, elija **Windows Desktop** . En el panel central, seleccione **Asistente de escritorio de Windows**. Escriba `MathLibrary` en el **nombre** cuadro para especificar un nombre para el proyecto.

   ![Denomine el proyecto MathLibrary](media/mathlibrary-new-project-name-153.png "denomine el proyecto MathLibrary")

1. Elija la **Aceptar** botón para descartar el **nuevo proyecto** diálogo e iniciar el **proyecto de escritorio de Windows** asistente.

1. En el **proyecto de escritorio de Windows** Asistente bajo **tipo de aplicación**, seleccione **biblioteca de vínculos dinámicos (.dll)**.

   ![Crear el archivo DLL en el Asistente para proyecto de escritorio de Windows](media/mathlibrary-desktop-project-wizard-dll.png "crear el archivo DLL en el Asistente para proyecto de escritorio de Windows")

1. Seleccione el botón **Aceptar** para crear el proyecto.

> [!NOTE]
> Se requieren pasos adicionales para solucionar un problema en Visual Studio 2017 versión 15.3. Siga estas instrucciones para ver si es necesario realizar este cambio.
>
>1. En **el Explorador de soluciones**, si aún no está seleccionada, seleccione el **MathLibrary** proyecto bajo **solución 'MathLibrary'**.
>
>1. En la barra de menús, seleccione **Proyecto** > **Propiedades**.
>
>1. En el panel izquierdo de la **páginas de propiedades** cuadro de diálogo, seleccione **preprocesador** en **propiedades de configuración** > **C o C++**. Comprobar el contenido de la **definiciones del preprocesador** propiedad.<br/><br/>![Compruebe la propiedad de las definiciones del preprocesador](media/mathlibrary-153bug-preprocessor-definitions-check.png "Compruebe la propiedad de las definiciones del preprocesador")<br/><br/>Si ve **MATHLIBRARY&#95;exportaciones** en el **definiciones del preprocesador** lista, no es necesario cambiar nada. Si ve **MathLibrary&#95;exportaciones** en su lugar, a continuación, continuar seguir estos pasos.
>
>1. En la parte superior de la **páginas de propiedades** cuadro de diálogo, cambie el **configuración** lista desplegable para **todas las configuraciones de**.
>
>1. En el panel de propiedades, seleccione el control de lista desplegable situada junto al cuadro de edición para **definiciones del preprocesador**y, a continuación, elija **editar**.<br/><br/>![Editar la propiedad de las definiciones del preprocesador](media/mathlibrary-153bug-preprocessor-definitions-property.png "editar la propiedad de las definiciones del preprocesador")
>
>1. En el panel superior de la **definiciones del preprocesador** cuadro de diálogo, agregar un nuevo símbolo `MATHLIBRARY_EXPORTS`.<br/><br/>![Agregue el símbolo MATHLIBRARY_EXPORTS](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "agregar el símbolo MATHLIBRARY_EXPORTS")
>
>1. Elija **Aceptar** para descartar el **definiciones del preprocesador** cuadro de diálogo y, a continuación, elija **Aceptar** para guardar los cambios en las propiedades del proyecto.

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>Para crear un proyecto DLL en versiones anteriores de Visual Studio

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En el panel izquierdo de la **nuevo proyecto** cuadro de diálogo, expanda **instalado** > **plantillas**y seleccione **Visual C++**, y a continuación, en el panel central, seleccione **aplicación de consola Win32**. Escriba `MathLibrary` en el **nombre** Editar cuadro para especificar un nombre para el proyecto.

   ![Denomine el proyecto MathLibrary](media/mathlibrary-project-name.png "denomine el proyecto MathLibrary")

1. Elija la **Aceptar** botón para descartar el **nuevo proyecto** diálogo e iniciar el **Asistente para aplicaciones Win32**.

   ![Introducción al Asistente para aplicaciones Win32](media/mathlibrary-project-wizard-1.png "Introducción al Asistente para aplicaciones Win32")

1. Elija el botón **Siguiente**. En el **configuración de la aplicación** página, en **tipo de aplicación**, seleccione **DLL**.

   ![Crear el archivo DLL en el Asistente para aplicaciones Win32](media/mathlibrary-project-wizard-2.png "crear DLL en el Asistente para aplicaciones Win32")

1. Elija el botón **Finalizar** para crear el proyecto.

Una vez el Asistente para la solución, puede ver los archivos de origen y el proyecto generados en el **el Explorador de soluciones** ventana de Visual Studio.

![Genera la solución en Visual Studio](media/mathlibrary-solution-explorer-153.png "genera la solución en Visual Studio")

Derecha ahora, este archivo DLL no hace gran cosa. Después, cree un archivo de encabezado para declarar las funciones de la DLL exporta y, a continuación, agregue las definiciones de función a la DLL para que resulte más útil.

### <a name="to-add-a-header-file-to-the-dll"></a>Para agregar un archivo de encabezado para el archivo DLL

1. Para crear un archivo de encabezado para las funciones, en la barra de menús, elija **proyecto** > **Agregar nuevo elemento**.

1. En el **Agregar nuevo elemento** cuadro de diálogo, en el panel izquierdo, seleccione **Visual C++**. En el panel central, seleccione **Archivo de encabezado (.h)**. Especificar `MathLibrary.h` como el nombre del archivo de encabezado.

   ![Agregar encabezado en el cuadro de diálogo Agregar nuevo elemento](media/mathlibrary-add-new-item-header-file.png "Agregar archivo de encabezado en el cuadro de diálogo Agregar nuevo elemento")

1. Elija la **agregar** botón para generar un archivo de encabezado en blanco, que se muestra en una nueva ventana del editor.

   ![Archivo MathLibrary.h vacío en el editor de](media/edit-empty-mathlibrary-header.png "archivo MathLibrary.h vacío en el editor")

1. Reemplace el contenido del archivo de encabezado con este código:

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

Tenga en cuenta las instrucciones de preprocesador en la parte superior del archivo. De forma predeterminada, se agrega la plantilla de proyecto nuevo para un archivo DLL  **<em>PROJECTNAME</em>&#95;exportaciones** a las macros de preprocesador definidas para el proyecto DLL. En este ejemplo, Visual Studio define **MATHLIBRARY&#95;exportaciones** cuando se compila el proyecto MathLibrary DLL. (El Asistente en Visual Studio 2017 versión 15.3 no fuerza esta definición de símbolos a mayúsculas. Si se denomine a su proyecto "MathLibrary", entonces el símbolo definido es MathLibrary&#95;exportaciones en lugar de MATHLIBRARY&#95;exportaciones. That's ¿por qué hay pasos adicionales anteriores para agregar este símbolo.)

Cuando el **MATHLIBRARY&#95;exportaciones** está definida la macro, el **MATHLIBRARY&#95;API** macro establece el `__declspec(dllexport)` modificador en las declaraciones de función. Este modificador indica que el compilador y vinculador para exportar una función o variable en el archivo DLL para que se pueden usar otras aplicaciones. Cuando **MATHLIBRARY&#95;exportaciones** está definido, por ejemplo, cuando se incluye el archivo de encabezado de una aplicación cliente, **MATHLIBRARY&#95;API** se aplica el `__declspec(dllimport)` modificador para el declaraciones. Este modificador optimiza la importación de la función o variable en una aplicación. Para obtener más información, consulte [dllexport, dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>Para agregar una implementación a la DLL

1. En la ventana del editor, seleccione la pestaña **MathLibrary.cpp** si ya está abierto. Si no es así, en **el Explorador de soluciones**, abra **MathLibrary.cpp** en el **archivos de código fuente** carpeta de la **MathLibrary** proyecto.

1. En el editor, reemplace el contenido del archivo MathLibrary.cpp con el código siguiente:

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h"
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

Para comprobar que todo funciona hasta ahora, compile la biblioteca de vínculos dinámicos. Para compilar, elija **compilar** > **compilar solución** en la barra de menús. La salida debe ser similar:

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Enhorabuena, ha creado un archivo DLL mediante Visual C++. A continuación, creará una aplicación de cliente que usa las funciones exportadas por el archivo DLL.

## <a name="create-a-client-app-that-uses-the-dll"></a>Creación de una aplicación cliente que utiliza el archivo DLL

Cuando se crea un archivo DLL, debe pensar cómo se puede usar el archivo DLL. Para compilar el código que llama a las funciones exportadas mediante un archivo DLL, las declaraciones deben incluirse en el código fuente del cliente. En tiempo de vinculación, cuando estas llamadas a funciones DLL se resuelven, el vinculador debe tener un *importar biblioteca*, un archivo de biblioteca especial que contiene información de Windows sobre cómo buscar las funciones, en lugar del código real. Y en tiempo de ejecución debe estar disponible para el cliente, en una ubicación que el sistema operativo puede encontrar el archivo DLL.

Para usar un archivo DLL, si el propietario o un archivo DLL de terceros, el proyecto de aplicación cliente debe encontrar los encabezados que se declaran la DLL exporta, las bibliotecas de importación para el enlazador y el propio archivo DLL. Una manera es copiar todos estos archivos en el proyecto de cliente. Para archivos DLL de terceros que no es probable que cambie mientras el cliente está en desarrollo, este método puede ser la mejor manera de usarlos. Sin embargo, cuando se compila también el archivo DLL, es mejor evitar la duplicación. Si realiza una copia de archivos DLL que están en desarrollo, accidentalmente puede cambiar un archivo de encabezado en una copia, pero no el otro o usar una biblioteca obsoleta. Para evitar este problema, se recomienda que establecer la ruta de inclusión en el proyecto de cliente para incluir los archivos de encabezado DLL desde el proyecto DLL. Además, establecer la ruta de acceso de la biblioteca en el proyecto de cliente para incluir las bibliotecas de importación DLL desde el proyecto DLL. Y por último, copie el archivo DLL compilada desde el proyecto DLL en el directorio de salida de compilación. Este paso permite que la aplicación cliente para utilizar el mismo código DLL que se compila.

### <a name="to-create-a-client-app-in-visual-studio-2017-version-153-or-later"></a>Para crear una aplicación cliente en Visual Studio 2017 versión 15.3 o posterior

1. Para crear una aplicación de C++ que utiliza el archivo DLL que ha creado, en la barra de menús, elija **archivo** > **New** > **proyecto**.

1. En el panel izquierdo de la **nuevo proyecto** cuadro de diálogo, seleccione **Windows Desktop** en **instalado** > **Visual C++**. En el panel central, seleccione **Asistente de escritorio de Windows**. Especifique el nombre del proyecto, `MathClient`, en el **nombre** cuadro de edición.

   ![Denomine el proyecto de cliente](media/mathclient-new-project-name-153.png "denomine el proyecto de cliente")

1. Elija **Aceptar** para iniciar el **proyecto de escritorio de Windows** asistente. En el asistente, elija **Aceptar** para crear el proyecto de aplicación cliente.

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>Para crear una aplicación cliente en las versiones anteriores de Visual Studio 2017

1. Para crear una aplicación de C++ que utiliza el archivo DLL que ha creado, en la barra de menús, elija **archivo** > **New** > **proyecto**.

1. En el panel izquierdo de la **nuevo proyecto** cuadro de diálogo, seleccione **Win32** en **instalado** > **plantillas**  >  **Visual C++**. En el panel central, seleccione **Aplicación de consola Win32**. Especifique el nombre del proyecto, `MathClient`, en el **nombre** cuadro de edición.

   ![Denomine el proyecto de cliente](media/mathclient-project-name.png "denomine el proyecto de cliente")

1. Elija la **Aceptar** botón para descartar el **nuevo proyecto** diálogo e iniciar el **Asistente para aplicaciones Win32**. En la página **Información general** del cuadro de diálogo **Asistente para aplicaciones Win32** , elija el botón **Siguiente** .

1. En el **configuración de la aplicación** página, en **tipo de aplicación**, seleccione **aplicación de consola** si aún no está seleccionado.

1. Elija el botón **Finalizar** para crear el proyecto.

Cuando finalice el asistente, se crea un proyecto de aplicación de consola mínimo para usted. El nombre del archivo de origen principal es el mismo que el nombre del proyecto que especificó anteriormente. En este ejemplo, se llama **MathClient.cpp**. Se puede compilar, pero aún no usa el archivo DLL.

A continuación, para llamar a las funciones de MathLibrary en el código fuente, el proyecto debe incluir el archivo MathLibrary.h. Puede copiar este archivo de encabezado en el proyecto de aplicación cliente, a continuación, agregarlo al proyecto como un elemento existente. Este método puede ser una buena elección para las bibliotecas de terceros. Sin embargo, si está trabajando en el código para el archivo DLL al mismo tiempo que el cliente, que podría provocar cambios en el archivo de un encabezado que no se muestran en el otro. Para evitar este problema, puede cambiar el **directorios de inclusión adicionales** ruta de acceso en el proyecto para incluir la ruta de acceso para el encabezado original.

### <a name="to-add-the-dll-header-to-your-include-path"></a>Para agregar el encabezado DLL para la ruta de inclusión

1. Abra el **páginas de propiedades** cuadro de diálogo para la **MathClient** proyecto.

1. En el **configuración** cuadro de lista desplegable, seleccione **todas las configuraciones** si aún no está seleccionado.

1. En el panel izquierdo, seleccione **General** en **propiedades de configuración** > **C o C++**.

1. En el panel de propiedades, seleccione el control de lista desplegable junto a la **directorios de inclusión adicionales** cuadro de edición y, a continuación, elija **editar**.

   ![Editar la propiedad de directorios de inclusión adicionales](media/mathclient-additional-include-directories-property.png "editar la propiedad de directorios de inclusión adicionales")

1. Haga doble clic en el panel superior de la **directorios de inclusión adicionales** cuadro de diálogo para habilitar un control de edición.

1. En el control de edición, especifique la ruta de acceso a la ubicación de la **MathLibrary.h** archivo de encabezado. En este caso, puede usar una ruta de acceso relativa:

   `..\..\MathLibrary\MathLibrary`

   ![Agregue la ubicación del encabezado a la propiedad de directorios de inclusión adicionales](media/mathclient-additional-include-directories.png "agregue la ubicación del encabezado a la propiedad de directorios de inclusión adicionales")

1. Después de escribir la ruta de acceso al archivo de encabezado en el **directorios de inclusión adicionales** diálogo cuadro, elija el **Aceptar** botón para volver a la **páginas de propiedades** cuadro de diálogo, y a continuación, elija el **Aceptar** botón para guardar los cambios.

Ahora puede incluir el **MathLibrary.h** de archivos y utilizar las funciones que declara en la aplicación cliente. Reemplace el contenido de **MathClient.cpp** mediante este código:

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
#include "pch.h"
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

Este código puede compilar, pero no vinculado, porque el vinculador no puede encontrar la biblioteca de importación necesaria para compilar la aplicación todavía. El vinculador debe buscar el archivo MathLibrary.lib para vincular correctamente. Agregar el archivo MathLibrary.lib a la compilación estableciendo el **dependencias adicionales** propiedad. Una vez más, podría copiar el archivo de biblioteca en el proyecto de aplicación cliente, pero si la biblioteca y la aplicación de cliente están en desarrollo, que podría dar lugar a cambios en una copia que no se muestran en el otro. Para evitar este problema, puede cambiar el **directorios de bibliotecas adicionales** ruta de acceso en el proyecto para incluir la ruta de acceso a la biblioteca original al vincular.

### <a name="to-add-the-dll-import-library-to-your-project"></a>Para agregar la biblioteca de importación DLL al proyecto

1. Abra el **páginas de propiedades** cuadro de diálogo para la **MathClient** proyecto.

1. En el **configuración** cuadro de lista desplegable, seleccione **todas las configuraciones** si aún no está seleccionado.

1. En el panel izquierdo, seleccione **entrada** en **propiedades de configuración** > **vinculador**. En el panel de propiedades, seleccione el control de lista desplegable junto a la **dependencias adicionales** cuadro de edición y, a continuación, elija **editar**.

   ![Editar la propiedad dependencias adicionales](media/mathclient-additional-dependencies-property.png "editar la propiedad dependencias adicionales")

1. En el **dependencias adicionales** cuadro de diálogo, agregar `MathLibrary.lib` a la lista en la parte superior de control de edición.

   ![Agregue la dependencia de biblioteca](media/mathclient-additional-dependencies.png "agregar la dependencia de biblioteca")

1. Elija **Aceptar** para volver a la **páginas de propiedades** cuadro de diálogo.

1. En el panel izquierdo, seleccione **General** en **propiedades de configuración** > **vinculador**. En el panel de propiedades, seleccione el control de lista desplegable junto a la **directorios de bibliotecas adicionales** cuadro de edición y, a continuación, elija **editar**.

   ![Editar la propiedad de directorios de bibliotecas adicionales](media/mathclient-additional-library-directories-property.png "editar la propiedad de directorios de bibliotecas adicionales")

1. Haga doble clic en el panel superior de la **directorios de bibliotecas adicionales** cuadro de diálogo para habilitar un control de edición. En el control de edición, especifique la ruta de acceso a la ubicación de la **MathLibrary.lib** archivo. Especifique este valor para utilizar una macro que funciona para la depuración y lanzamiento compila:

   `..\..\MathLibrary\$(IntDir)`

   ![Agregue el directorio de la biblioteca](media/mathclient-additional-library-directories.png "agregue el directorio de biblioteca")

1. Después de escribir la ruta de acceso al archivo de biblioteca en el **directorios de bibliotecas adicionales** diálogo cuadro, elija el **Aceptar** botón para volver a la **páginas de propiedades** cuadro de diálogo.

La aplicación cliente ahora puede compilar y vincular correctamente, pero todavía no tiene todo lo que necesita para ejecutarse. Cuando el sistema operativo carga la aplicación, busca la DLL MathLibrary. Si no encuentra el archivo DLL en ciertos directorios del sistema, la ruta de acceso de entorno o el directorio de aplicaciones local, la carga sufre un error. Una forma de evitar este problema es copiar el archivo DLL en el directorio que contiene el archivo ejecutable del cliente como parte del proceso de compilación. Para copiar el archivo DLL, puede agregar un **evento posterior a la compilación** al proyecto, para agregar un comando que copia el archivo DLL en el directorio de salida de compilación. El comando especificado aquí copia el archivo DLL sólo si falta o ha cambiado y usa macros para copiar hacia y desde las ubicaciones correctas comercial o de depuración para la configuración.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>Para copiar el archivo DLL en un evento posterior a la compilación

1. Abra el **páginas de propiedades** cuadro de diálogo para la **MathClient** proyecto si no está abierta.

1. En el cuadro de lista desplegable de configuración, seleccione **todas las configuraciones** si aún no está seleccionado.

1. En el panel izquierdo, seleccione **evento posterior a la compilación** en **propiedades de configuración** > **eventos de compilación**.

1. En el panel de propiedades, seleccione el control de edición en el **línea de comandos** campo y, a continuación, escriba este comando:

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![Agregue el comando posterior a la compilación](media/mathclient-post-build-command-line.png "agregue el comando posterior a la compilación")

1. Elija la **Aceptar** botón para guardar los cambios en las propiedades del proyecto.

Ahora la aplicación cliente tiene todo que lo necesario para compilar y ejecutar. Compile la aplicación con **compilar** > **compilar solución** en la barra de menús. El **salida** ventana de Visual Studio debe tener algo parecido:

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>pch.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Enhorabuena, ha creado una aplicación que llama a funciones en el archivo DLL. Ahora ejecute la aplicación para ver lo que hace. En la barra de menús, elija **depurar** > **iniciar sin depurar**. Visual Studio abre una ventana de comandos para que se ejecute el programa. La última parte de la salida debería ser similar:

![Iniciar la aplicación cliente sin depurar](media/mathclient-run-without-debugging.png "iniciar la aplicación de cliente sin depuración")

Presione cualquier tecla para cerrar la ventana de comandos.

Ahora que ha creado un archivo DLL y una aplicación cliente, puede experimentar. Intente establecer puntos de interrupción en el código de la aplicación cliente y ejecutar la aplicación en el depurador. Vea Qué sucede cuando entre en una llamada a la biblioteca. Agregar otras funciones a la biblioteca o escribir otra aplicación de cliente que utiliza el archivo DLL.

Al implementar la aplicación, también debe implementar los archivos DLL utiliza. La manera más sencilla para que los archivos DLL que se compila o que incluyen de terceros estén disponibles para la aplicación es colocarlos en el mismo directorio que la aplicación, también conocido como *implementación local de la aplicación*. Para obtener más información sobre la implementación, vea [Deployment in Visual C++](../ide/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Vea también

[Llamada a funciones de un archivo DLL desde aplicaciones programadas en Visual Basic](calling-dll-functions-from-visual-basic-applications.md)
