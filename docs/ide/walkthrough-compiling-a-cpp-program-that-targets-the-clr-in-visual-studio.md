---
title: Compilación de un programa de C++ orientado a CLR
ms.date: 09/17/2018
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 51e8b234792dea8dd7d61e4ac4b97a55bd5ea4e9
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524636"
---
# <a name="walkthrough-compiling-a-c-program-that-targets-the-clr-in-visual-studio"></a>Tutorial: Compilar un programa de C++ orientado a CLR en Visual Studio

Se pueden crear programas de Visual C++ que usen clases de .NET y compilarlos con el entorno de desarrollo de Visual Studio.

Para realizar este procedimiento, puede escribir su propio programa de Visual C++ o usar uno de los programas de ejemplo. En el programa de ejemplo que se usa en este procedimiento se crea un archivo de texto denominado textfile.txt y se guarda en el directorio del proyecto.

## <a name="prerequisites"></a>Requisitos previos

En estos temas se da por supuesto que comprende los fundamentos del lenguaje C++.

### <a name="to-create-a-new-project-in-visual-studio-and-add-a-new-source-file"></a>Para crear un proyecto en Visual Studio y agregar un archivo de código fuente nuevo

1. Cree un nuevo proyecto. En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.

1. En los tipos de proyecto de Visual C++, haga clic en **CLR** y después en **Proyecto vacío de CLR**.

   > [!NOTE]
   > Si falta el tipo de **proyecto vacío de CLR** (solo Visual Studio 2017), seleccione **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**. Instale la opción que se encuentra en **Desarrollo para el escritorio con C++** en la sección de componentes **Opcional**, denominada **Compatibilidad con C++/CLI**.<br/>

1. Escriba un nombre de proyecto.

   De forma predeterminada, la solución que contiene el proyecto tiene el mismo nombre que el proyecto nuevo, pero puede escribir otro nombre. Si quiere, puede escribir otra ubicación para el proyecto.

   Haga clic en **Aceptar** para crear el proyecto nuevo.

1. Si el **Explorador de soluciones** no está visible, haga clic en **Explorador de soluciones** en el menú **Ver**.

1. Agregue un archivo de código fuente nuevo al proyecto:

   - Haga clic con el botón derecho en la carpeta **Archivos de código fuente** en el **Explorador de soluciones**, seleccione **Agregar** y haga clic en **Nuevo elemento**.

   - Haga clic en **Archivo C++ (.cpp)**, escriba un nombre de archivo y, después, haga clic en **Agregar**.

   El archivo **.cpp** aparece en la carpeta **Archivos de código fuente** en el **Explorador de soluciones** y se muestra una ventana con pestañas donde puede escribir el código que quiera en ese archivo.

1. Haga clic en la pestaña recién creada en Visual Studio y escriba un programa de Visual C++ válido, o copie y pegue uno de los programas de ejemplo.

   Por ejemplo, puede usar el programa de ejemplo [Cómo: Escribir un archivo de texto (C++/CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md) (en el nodo **Control y E/S de archivos** de la Guía de programación).

   Si usa el programa de ejemplo, observe que se usa la palabra clave `gcnew` en lugar de `new` al crear un objeto .NET y que `gcnew` devuelve un identificador (`^`) en lugar de un puntero (`*`):

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Para obtener más información sobre la nueva sintaxis de Visual C++, vea [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md).

1. En el menú **Compilar** , haga clic en **Compilar solución**.

   En la ventana **Salida** se muestra información sobre el progreso de la compilación, como la ubicación del registro de compilación y un mensaje que indica el estado de la compilación.

   Si realiza cambios y ejecuta el programa sin realizar una compilación, es posible que se indique que el proyecto no está actualizado en un cuadro de diálogo. Active la casilla de este cuadro de diálogo antes de hacer clic en **Aceptar** si quiere que Visual Studio use siempre las versiones actuales de los archivos en lugar de solicitárselo cada vez que se compile la aplicación.

1. En el menú **Depurar**, haga clic en **Iniciar sin depurar**.

1. Si usó el programa de ejemplo, al ejecutar el programa se muestra una ventana de comandos en la que se indica que se ha creado el archivo de texto.

   El archivo de texto **textfile.txt** se encuentra ahora en el directorio del proyecto. Puede abrir este archivo mediante el Bloc de notas.

   > [!NOTE]
   > Al elegir la plantilla de proyecto vacío de CLR se establece automáticamente la opción del compilador `/clr`. Para comprobarlo, haga clic con el botón derecho en el proyecto en el **Explorador de soluciones**, seleccione **Propiedades** y, después, active la opción **Compatible con Common Language Runtime** en el nodo  **General** de **Propiedades de configuración**.

## <a name="whats-next"></a>Pasos adicionales

**Anterior:** [Tutorial: Compilar un programa nativo de C++ en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
**Siguiente:** [Tutorial: Compilar un programa escrito en C en la línea de comandos](../build/walkthrough-compile-a-c-program-on-the-command-line.md)<br/>

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)<br/>
