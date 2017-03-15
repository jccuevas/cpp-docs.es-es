---
title: "Tutorial: Compilar un programa de C++ orientado a CLR en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones de línea de comandos [C++], código administrado"
  - "compilar programas [C++]"
  - "código administrado [C++]"
  - "Visual C++, código administrado"
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
caps.latest.revision: 40
caps.handback.revision: 40
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Compilar un programa de C++ orientado a CLR en Visual Studio
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede crear programas de Visual C\+\+ que utilicen clases .NET y compilarlos con el entorno de desarrollo de Visual Studio.  
  
 Para realizar este procedimiento, puede escribir su propio programa de Visual C\+\+ o utilizar uno de los programas de ejemplo.  El programa de ejemplo que utilizamos en este procedimiento crea un archivo de texto denominado textfile.txt y lo guarda en el directorio del proyecto.  
  
## Requisitos previos  
 En estos temas se asume que conoce los fundamentos del lenguaje C\+\+.  
  
### Para crear un nuevo proyecto en Visual Studio y agregar un nuevo archivo de código fuente  
  
1.  Cree un nuevo proyecto.  En el menú **Archivo**, seleccione **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
2.  En los tipos de proyecto de Visual C\+\+, haga clic en **CLR** y, a continuación, en **Proyecto vacío de CLR**.  
  
3.  Escriba un nombre de proyecto.  
  
     De forma predeterminada, la solución que contiene el proyecto tiene el mismo nombre que el nuevo proyecto, pero puede escribir un nombre diferente.  Puede escribir una ubicación diferente para el proyecto si lo desea.  
  
     Haga clic en **Aceptar** para crear el nuevo proyecto.  
  
4.  Si el Explorador de soluciones no está visible, haga clic en **Explorador de soluciones** en el menú **Ver**.  
  
5.  Agregue un nuevo archivo de código fuente al proyecto:  
  
    -   Haga clic con el botón secundario del mouse en la carpeta **Archivos de código fuente** en el Explorador de soluciones, seleccione **Agregar** y haga clic en **Nuevo elemento...**.  
  
    -   Haga clic en **Archivo C\+\+ \(.cpp\)** y escriba un nombre de archivo; a continuación, haga clic en **en Agregar**.  
  
     El archivo **.cpp** se muestra en la carpeta **Archivos de código fuente** en el Explorador de soluciones y aparece una ventana con fichas donde escribe el código que desea para el archivo.  
  
6.  Haga clic en la ficha recién creada en Visual Studio y escriba un programa de Visual C\+\+ válido o copie y pegue uno de los programas de ejemplo.  
  
     Por ejemplo, puede utilizar el programa de ejemplo [Cómo: Escribir un archivo de texto](../dotnet/how-to-write-a-text-file-cpp-cli.md) \(en el nodo **E\/S y control de archivos** de la Guía de programación\).  
  
     Si usa el programa de ejemplo, observe que se emplea la palabra clave `gcnew` ``  en lugar de `new` al crear un objeto de .NET, y que `gcnew` devuelve un identificador \(`^`\) en lugar de un puntero \(`*`\):  
  
     `StreamWriter^ sw = gcnew StreamWriter(fileName);`  
  
     Para obtener más información acerca de la nueva sintaxis de Visual C\+\+, vea [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md).  
  
7.  En el menú **Compilar**, haga clic en **Compilar solución**.  
  
     La ventana **Resultado** muestra información sobre el progreso de la compilación, como la ubicación del registro de compilación y un mensaje que indica el estado de la compilación.  
  
     Si realiza cambios y ejecuta el programa sin hacer una compilación, puede aparecer un cuadro de diálogo en el que se indica que el proyecto no está actualizado.  Active la casilla en este cuadro de diálogo antes de hacer clic en **Aceptar** si desea que Visual Studio utilice siempre las versiones actuales de los archivos en lugar de preguntarle cada vez que compila la aplicación.  
  
8.  En el menú **Depurar**, haga clic en **Iniciar sin depurar**.  
  
9. Si ha utilizado el programa de ejemplo, al ejecutarlo aparecerá una ventana de comandos que indica que se ha creado el archivo de texto.  Presione cualquier tecla para cerrar la ventana de comandos.  
  
     El archivo de texto **textfile.txt** se encuentra ahora en el directorio del proyecto.  Puede abrir este archivo con el Bloc de notas.  
  
    > [!NOTE]
    >  La elección de la plantilla de proyecto de CLR vacía establece automáticamente la opción del compilador **\/clr**.  Puede comprobarlo haciendo clic con el botón secundario del mouse sobre el proyecto en el **Explorador de soluciones**, haciendo clic en **Propiedades** y seleccionando la opción **Compatibilidad con Common Language Runtime** que se encuentra en el nodo **General** de **Propiedades de configuración**.  
  
## Pasos adicionales  
 **Anterior:** [Tutorial: Compilar un programa nativo de C\+\+ en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md) &#124; **Siguiente:** [Tutorial: Compilar un programa escrito en C en la línea de comandos](../Topic/Walkthrough:%20Compiling%20a%20C%20Program%20on%20the%20Command%20Line.md)  
  
## Vea también  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/es-es/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Compilar programas de C\/C\+\+](../build/building-c-cpp-programs.md)