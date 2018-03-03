---
title: Compilar un programa de C++ orientado a CLR | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eca6960d23c43fbe27d753ab4f79a27dea7bd7e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-compiling-a-c-program-that-targets-the-clr-in-visual-studio"></a>Tutorial: Compilar un programa de C++ orientado a CLR en Visual Studio
Puede crear programas de Visual C++ que utilizan las clases .NET y compilan con el entorno de desarrollo de Visual Studio.  
  
 Para realizar este procedimiento puede escribir su propio programa de Visual C++ o utilizar uno de los programas de ejemplo. El programa de ejemplo que utilizamos en este procedimiento crea un archivo de texto denominado textfile.txt y lo guarda en el directorio del proyecto.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Estos temas se asume que conoce los fundamentos del lenguaje C++.  
  
### <a name="to-create-a-new-project-in-visual-studio-and-add-a-new-source-file"></a>Para crear un nuevo proyecto en Visual Studio y agregue un nuevo archivo de origen  
  
1.  Cree un nuevo proyecto. En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.  
  
2.  En los tipos de proyecto de Visual C++, haga clic en **CLR**y, a continuación, haga clic en **proyecto vacío de CLR**.  
  
3.  Escriba un nombre de proyecto.  
  
     De forma predeterminada, la solución que contiene el proyecto tiene el mismo nombre que el nuevo proyecto, pero puede escribir un nombre diferente. Si desea que se puede escribir una ubicación diferente para el proyecto.  
  
     Haga clic en **Aceptar** para crear el nuevo proyecto.  
  
4.  Si el Explorador de soluciones no está visible, haga clic en **el Explorador de soluciones** en el **vista** menú.  
  
5.  Agregue un nuevo archivo de código fuente al proyecto:  
  
    -   Haga clic en el **archivos de código fuente** carpeta en el Explorador de soluciones, seleccione **agregar** y haga clic en **nuevo elemento**.  
  
    -   Haga clic en **archivo C++ (.cpp)** y escriba un nombre de archivo y, a continuación, haga clic en **agregar**.  
  
     El **.cpp** archivo aparece en la **archivos de código fuente** aparece de la carpeta en el Explorador de soluciones y una ventana con fichas donde escribe el código que desee en ese archivo.  
  
6.  Haga clic en la ficha recién creada en Visual Studio y escriba un programa de Visual C++ válido, o copie y pegue uno de los programas de ejemplo.  
  
     Por ejemplo, puede usar el [Cómo: escribir un archivo de texto (C++ / CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md) programa de ejemplo (en el **archivo de control y E/S** nodo de la Guía de programación).  
  
     Si utiliza el programa de ejemplo, observe que utilizar el `gcnew` palabra clave en lugar de `new` al crear un objeto. NET y que `gcnew` devuelve un identificador (`^`) en lugar de un puntero (`*`):  
  
     `StreamWriter^ sw = gcnew StreamWriter(fileName);`  
  
     Para obtener más información sobre la nueva sintaxis de Visual C++, vea [extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md).  
  
7.  En el menú **Compilar** , haga clic en **Compilar solución**.  
  
     El **salida** ventana muestra información sobre el progreso de la compilación, como la ubicación del registro de compilación y un mensaje que indica el estado de la compilación.  
  
     Si realiza cambios y ejecutar el programa sin tener que realizar una compilación, un cuadro de diálogo podría indicar que el proyecto no está actualizado. Seleccione la casilla de verificación en este cuadro de diálogo antes de hacer clic **Aceptar** si desea que Visual Studio utilice siempre las versiones actuales de archivos en lugar de pedir confirmación cada vez que compila la aplicación.  
  
8.  En el **depurar** menú, haga clic en **iniciar sin depurar**.  
  
9. Si utiliza el programa de ejemplo, al ejecutar el programa se muestra una ventana de comandos que indica que se ha creado el archivo de texto. Presione cualquier tecla para cerrar la ventana de comandos.  
  
     El **textfile.txt** ahora se encuentra el archivo de texto en el directorio del proyecto. Puede abrir este archivo mediante el Bloc de notas.  
  
    > [!NOTE]
    >  Elegir el CLR vacío plantilla de proyecto establece automáticamente el **/CLR** opción del compilador. Para comprobarlo, haga clic en el proyecto en **el Explorador de soluciones** y haga clic en **propiedades**y, a continuación, compruebe el **compatible con Common Language Runtime** opción en el  **General** nodo de **propiedades de configuración**.  
  
## <a name="whats-next"></a>Pasos adicionales  
 **Anterior:** [Tutorial: compilar un programa de C++ nativo en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md) &#124; **Siguiente:**[Tutorial: compilar un programa de C en la línea de comandos](../build/walkthrough-compile-a-c-program-on-the-command-line.md)  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Compilación de programas de C/C++](../build/building-c-cpp-programs.md)