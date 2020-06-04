---
title: 'Tutorial: Creación y uso de una biblioteca estática (C++)'
description: Use C++ para crear una biblioteca estática (.lib) en Visual Studio.
ms.custom: get-started-article
ms.date: 04/13/2020
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.openlocfilehash: 7148cc1de7c06ae57d61560311b342a1fc9dda1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335147"
---
# <a name="walkthrough-create-and-use-a-static-library"></a>Tutorial: Creación y uso de una biblioteca estática

En este tutorial paso a paso se muestra cómo crear una biblioteca estática (archivo .lib) para su uso con aplicaciones de C++. Utilizar una biblioteca estática es una excelente manera de reutilizar el código. En lugar de volver a implementar las mismas rutinas en todas las aplicaciones que requieran la funcionalidad, escríbalas una vez en una biblioteca estática y, a continuación, haga referencia a ellas desde las aplicaciones. El código vinculado desde una biblioteca estática pasa a formar parte de la aplicación (no es necesario instalar otro archivo para usar el código).

En este tutorial se tratan las siguientes tareas:

- [Creación de un proyecto de biblioteca estática](#CreateLibProject)

- [Adición de una clase a la biblioteca estática](#AddClassToLib)

- [Creación de una aplicación de consola de C++ que haga referencia a la biblioteca estática](#CreateAppToRefTheLib)

- [Uso de la funcionalidad de la biblioteca estática en la aplicación](#UseLibInApp)

- [Ejecución de la aplicación](#RunApp)

## <a name="prerequisites"></a>Requisitos previos

Descripción de los fundamentos del lenguaje C++.

## <a name="create-a-static-library-project"></a><a name="CreateLibProject"></a> Creación de un proyecto de biblioteca estática

Las instrucciones para crear el proyecto varían en función de la versión de Visual Studio. Para ver la documentación de su versión preferida de Visual Studio, use el control de selector **Versión**. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>Para crear un proyecto de biblioteca estática en Visual Studio 2019

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Crear un nuevo proyecto**.

1. En la parte superior del cuadro de diálogo, establezca **Lenguaje** en **C++** , establezca **Plataforma** en **Windows** y establezca **Tipo de proyecto** en **Biblioteca**.

1. En la lista filtrada de tipos de proyecto, seleccione **Asistente para escritorio de Windows** y, después, **Siguiente**.

1. En la página **Configure su nuevo proyecto**, escriba *MathLibrary* en el cuadro **Nombre del proyecto** para especificar un nombre para el proyecto. Escriba *StaticMath* en el cuadro  **Nombre de la solución**. Haga clic en el botón **Crear** para abrir el cuadro de diálogo **Proyecto de escritorio de Windows**.

1. En el cuadro de diálogo **Proyecto de escritorio de Windows**, en **Tipo de aplicación**, seleccione **Biblioteca estática (.lib)** .

1. En **Opciones adicionales**, desactive la casilla **Encabezado precompilado** si está activada. Active la casilla **Proyecto vacío**.

1. Seleccione **Aceptar** para crear el proyecto.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>Para crear un proyecto de biblioteca estática en Visual Studio 2017

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En el cuadro de diálogo **Nuevo proyecto**, seleccione **Instalado** > **Visual C++**  > **Escritorio de Windows**. En el panel central, seleccione **Asistente de Escritorio de Windows**.

1. Especifique un nombre para el proyecto; por ejemplo, *MathLibrary*, en el cuadro **Nombre**. Especifique un nombre para la solución, por ejemplo, *StaticMath*, en el cuadro **Nombre de la solución**. Elija el botón **Aceptar** .

1. En el cuadro de diálogo **Proyecto de escritorio de Windows**, en **Tipo de aplicación**, seleccione **Biblioteca estática (.lib)** .

1. En **Opciones adicionales**, desactive la casilla **Encabezado precompilado** si está activada. Active la casilla **Proyecto vacío**.

1. Seleccione **Aceptar** para crear el proyecto.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>Para crear un proyecto de biblioteca estática en Visual Studio 2015

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En el cuadro de diálogo **Nuevo proyecto**, seleccione **Instalado** > **Plantillas** > **Visual C++**  > **Win32**. En el panel central, seleccione **Aplicación de consola Win32**.

1. Especifique un nombre para el proyecto; por ejemplo, *MathLibrary*, en el cuadro **Nombre**. Especifique un nombre para la solución, por ejemplo, *StaticMath*, en el cuadro **Nombre de la solución**. Elija el botón **Aceptar** .

1. En el **Asistente para aplicaciones Win32**, elija **Siguiente**.

1. En la página **Configuración de la aplicación**, en **Tipo de aplicación**, seleccione **Biblioteca estática**. En **Opciones adicionales**, desactive la casilla **Encabezado precompilado**. Haga clic en **Finalizar** para crear el proyecto.

::: moniker-end

## <a name="add-a-class-to-the-static-library"></a><a name="AddClassToLib"></a> Adición de una clase a la biblioteca estática

### <a name="to-add-a-class-to-the-static-library"></a>Para agregar una clase a la biblioteca estática

1. Si quiere crear un archivo de encabezado para una nueva clase, haga clic con el botón derecho para abrir el menú contextual del proyecto **MathLibrary** en el **Explorador de soluciones** y, después, elija **Agregar** > **Nuevo elemento**.

1. En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **Visual C++**  > **Código**. En el panel central, seleccione **Archivo de encabezado (.h)** . Especifique un nombre para el encabezado de archivo, por ejemplo, *MathLibrary.h*, y después elija el botón **Agregar**. Se muestra un archivo de encabezado casi en blanco.

1. Agregue una declaración para una clase denominada `Arithmetic` para hacer operaciones matemáticas comunes, como sumas, restas, multiplicaciones y divisiones. El código debería ser similar al siguiente:

    ```cpp
    // MathLibrary.h
    #pragma once

    namespace MathLibrary
    {
        class Arithmetic
        {
        public:
            // Returns a + b
            static double Add(double a, double b);

            // Returns a - b
            static double Subtract(double a, double b);

            // Returns a * b
            static double Multiply(double a, double b);

            // Returns a / b
            static double Divide(double a, double b);
        };
    }
    ```

1. Para crear un archivo de código fuente para la nueva clase, abra el menú contextual para el proyecto **MathLibrary** en el **Explorador de soluciones** y, después, elija **Agregar** > **Nuevo elemento**.

1. En el cuadro de diálogo **Agregar nuevo elemento**, en el panel central, seleccione **Archivo C++ (.cpp)** . Especifique un nombre para el archivo de código fuente, por ejemplo, *MathLibrary.cpp*, y después elija el botón **Agregar**. Se muestra un archivo de código fuente en blanco.

1. Use este archivo de código fuente para implementar la funcionalidad de la clase `Arithmetic`. El código debería ser similar al siguiente:

    ```cpp
    // MathLibrary.cpp
    // compile with: cl /c /EHsc MathLibrary.cpp
    // post-build command: lib MathLibrary.obj

    #include "MathLibrary.h"

    namespace MathLibrary
    {
        double Arithmetic::Add(double a, double b)
        {
            return a + b;
        }

        double Arithmetic::Subtract(double a, double b)
        {
            return a - b;
        }

        double Arithmetic::Multiply(double a, double b)
        {
            return a * b;
        }

        double Arithmetic::Divide(double a, double b)
        {
            return a / b;
        }
    }
    ```

1. Para compilar la biblioteca estática, seleccione **Compilar** > **Compilar solución** en la barra de menús. La compilación crea una biblioteca estática, *MathLibrary.lib*, que pueden usar otros programas.

   > [!NOTE]
   > Cuando compile desde la línea de comandos de Visual Studio, debe compilar el programa en dos pasos. Primero, ejecute `cl /c /EHsc MathLibrary.cpp` para compilar el código y crear un archivo de objeto denominado *MathLibrary.obj*. (El comando `cl` invoca el compilador, Cl.exe y la opción `/c` especifica compilar sin vinculación. Para obtener más información, consulte el artículo [/c (Compilar sin vincular)](../build/reference/c-compile-without-linking.md). En segundo lugar, ejecute `lib MathLibrary.obj` para enlazar el código y crear la biblioteca estática *MathLibrary.lib*. (El comando `lib` invoca el Administrador de bibliotecas, Lib.exe. Para obtener más información, vea [LIB Reference](../build/reference/lib-reference.md)).

## <a name="create-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a> Creación de una aplicación de consola de C++ que haga referencia a la biblioteca estática

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>Para crear una aplicación de consola de C++ que haga referencia a la biblioteca estática en Visual Studio 2019

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo superior, **Solución "StaticMath"** , para abrir el menú contextual. Elija **Agregar** > **Nuevo proyecto** para abrir el cuadro de diálogo **Agregar un nuevo proyecto**.

1. En la parte superior del cuadro de diálogo, establezca el filtro **Tipo de proyecto** en **Consola**.

1. En la lista de plantillas de proyecto, seleccione **Aplicación de consola** y **Siguiente**. En la página siguiente, escriba *MathClient* en el cuadro **Nombre** para especificar un nombre para el proyecto.

1. Haga clic en el botón **Crear** para crear el proyecto de cliente.

1. Después de crear una aplicación de consola, se crea un programa vacío. El nombre del archivo de código fuente será el mismo que el elegido anteriormente. En este ejemplo, se denomina `MathClient.cpp`.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>Para crear una aplicación de consola de C++ que haga referencia a la biblioteca estática en Visual Studio 2017

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo superior, **Solución "StaticMath"** , para abrir el menú contextual. Elija **Agregar** > **Nuevo proyecto** para abrir el cuadro de diálogo **Agregar un nuevo proyecto**.

1. En el cuadro de diálogo **Agregar nuevo proyecto**, seleccione **Instalado** > **Visual C++**  > **Escritorio de Windows**. En el panel central, seleccione **Asistente de Escritorio de Windows**.

1. Especifique un nombre para el proyecto (por ejemplo, *MathClient*) en el cuadro **Nombre**. Elija el botón **Aceptar** .

1. En el cuadro de diálogo **Proyecto de escritorio de Windows**, en **Tipo de aplicación**, seleccione **Aplicación de consola (.exe)** .

1. En **Opciones adicionales**, desactive la casilla **Encabezado precompilado** si está activada.

1. Seleccione **Aceptar** para crear el proyecto.

1. Después de crear una aplicación de consola, se crea un programa vacío. El nombre del archivo de código fuente será el mismo que el elegido anteriormente. En este ejemplo, se denomina `MathClient.cpp`.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>Para crear una aplicación de consola de C++ que haga referencia a la biblioteca estática en Visual Studio 2015

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo superior, **Solución "StaticMath"** , para abrir el menú contextual. Elija **Agregar** > **Nuevo proyecto** para abrir el cuadro de diálogo **Agregar un nuevo proyecto**.

1. En el cuadro de diálogo **Agregar nuevo proyecto**, seleccione **Instalado** > **Visual C++**  > **Win32**. En el panel central, seleccione **Aplicación de consola Win32**.

1. Especifique un nombre para el proyecto (por ejemplo, *MathClient*) en el cuadro **Nombre**. Elija el botón **Aceptar** .

1. En el cuadro de diálogo **Asistente para aplicaciones Win32**, elija **Siguiente**.

1. En la página **Configuración de la aplicación**, en **Tipo de aplicación**, asegúrese de que la opción **Aplicación de consola** está seleccionada. En **Opciones adicionales**, desactive la casilla **Encabezado precompilado** y, a continuación, active la casilla **Proyecto vacío**. Haga clic en **Finalizar** para crear el proyecto.

1. Para agregar un archivo de código fuente al proyecto vacío, haga clic con el botón derecho para abrir el menú contextual del proyecto **MathClient** en el **Explorador de soluciones** y, después, elija **Agregar** > **Nuevo elemento**.

1. En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **Visual C++**  > **Código**. En el panel central, seleccione **Archivo de C++ (.cpp)** . Especifique un nombre para el archivo de código fuente, por ejemplo, *MathClient.cpp*, y después haga clic en el botón **Agregar**. Se muestra un archivo de código fuente en blanco.

::: moniker-end

## <a name="use-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a> Uso de la funcionalidad de la biblioteca estática en la aplicación

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Para utilizar la funcionalidad de la biblioteca estática en la aplicación

1. Para poder usar las rutinas de coincidencia de la biblioteca estática, debe hacer referencia a ella. Abra el menú contextual del proyecto **MathClient** en el **Explorador de soluciones** y, luego, elija **Agregar** > **Referencia**.

1. El cuadro de diálogo **Agregar referencia** muestra las bibliotecas a las que puede hacer referencia. La pestaña **Proyectos** enumera los proyectos de la solución actual y las bibliotecas a las que hacen referencia. En la pestaña **Proyectos**, active la casilla **MathLibrary** y, después, haga clic en el botón **Aceptar**.

1. Para hacer referencia al archivo de encabezado `MathLibrary.h`, debe modificar la ruta de acceso de los directorios de inclusión. En el **Explorador de soluciones**, haga clic con el botón derecho **MathClient** para abrir el menú contextual. Elija **Propiedades** para abrir el cuadro de diálogo **Páginas de propiedades de MathClient**.

1. En el cuadro de diálogo **Páginas de propiedades de MathClient**, establezca el valor de la lista desplegable **Configuración** en **Todas las configuraciones**. Establezca el valor de la lista desplegable **Plataforma** en **Todas las plataformas**.

1. Seleccione la página de propiedades **Propiedades de configuración** > **C/C++**  > **General**. En la propiedad **Directorios de inclusión adicionales**, especifique la ruta de acceso del directorio **MathLibrary** o búsquela.

   Para buscar la ruta de acceso del directorio:

   1. Abra la lista desplegable del valor de propiedad **Directorios de inclusión adicionales** y, a continuación, elija **Editar**.

   1. En el cuadro de diálogo **Directorios de inclusión adicionales** haga doble clic en la parte superior del cuadro de texto. A continuación, presione el botón de puntos suspensivos ( **…** ) al final de la línea.

   1. En el cuadro de diálogo **Seleccionar directorio**, desplácese a un nivel y, a continuación, seleccione el directorio **MathLibrary**. Después, haga clic en el botón **Seleccionar carpeta** para guardar su selección.

   1. En el cuadro de diálogo **Directorios de inclusión adicionales**, haga clic en el botón **Aceptar**.

   1. En el cuadro de diálogo **Páginas de propiedades**, elija el botón **Aceptar** para guardar los cambios en el proyecto.

1. Ahora puede usar la clase `Arithmetic` en esta aplicación incluyendo el encabezado `#include "MathLibrary.h"` en el código. Reemplace el contenido de `MathClient.cpp` por el código siguiente:

    ```cpp
    // MathClient.cpp
    // compile with: cl /EHsc MathClient.cpp /link MathLibrary.lib

    #include <iostream>
    #include "MathLibrary.h"

    int main()
    {
        double a = 7.4;
        int b = 99;

        std::cout << "a + b = " <<
            MathLibrary::Arithmetic::Add(a, b) << std::endl;
        std::cout << "a - b = " <<
            MathLibrary::Arithmetic::Subtract(a, b) << std::endl;
        std::cout << "a * b = " <<
            MathLibrary::Arithmetic::Multiply(a, b) << std::endl;
        std::cout << "a / b = " <<
            MathLibrary::Arithmetic::Divide(a, b) << std::endl;

        return 0;
    }
    ```

1. Para compilar el archivo ejecutable, elija **Compilación** > **Compilar solución** en la barra de menús.

## <a name="run-the-app"></a><a name="RunApp"></a> Ejecución de la aplicación

### <a name="to-run-the-app"></a>Para ejecutar la aplicación

1. Compruebe que **MathClient** está seleccionado como proyecto predeterminado. Para seleccionarlo, hacha clic con el botón derecho para abrir el menú contextual de **MathClient** en el **Explorador de soluciones** y, después, elija **Establecer como proyecto de inicio**.

1. Para ejecutar el proyecto, en la barra de menús, seleccione **Depurar** > **Iniciar sin depurar**. El resultado debería ser similar al siguiente:

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>Vea también

[Tutorial: Creación y uso de una biblioteca de vínculos dinámicos (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[Aplicaciones de escritorio (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
