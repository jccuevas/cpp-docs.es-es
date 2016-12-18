---
title: "Tutorial: Crear un programa de consola Win32 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "vcfirstapp"
  - "vccreatefirst"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones de línea de comandos [C++], estándar"
  - "aplicaciones estándar [C++]"
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
caps.latest.revision: 36
caps.handback.revision: 36
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Crear un programa de consola Win32 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede usar Visual C\+\+ en el entorno de desarrollo integrado \(IDE\) de Visual Studio para crear programas en C\+\+ estándar.  Si sigue los pasos de este tutorial, puede crear un proyecto, agregar un nuevo archivo al proyecto, modificar el archivo para agregar código de C\+\+ y, finalmente, compilar y ejecutar el programa con [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
 Puede escribir su propio programa de C\+\+ o utilizar uno de los programas de ejemplo.  El programa de ejemplo de este tutorial es una aplicación de consola.  Esta aplicación usa el contenedor `set` de la Biblioteca de plantillas estándar \(STL\).  
  
 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] cumple la norma de 2003 C\+\+ excepto en estos casos: búsquedas de nombres en dos fases, especificaciones de excepciones y exportaciones.  Además, [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] admite varias características de C\+\+0x, como lambda, auto, static\_assert, referencias rvalue y plantillas extern.  
  
> [!NOTE]
>  Si se requiere cumplimiento normativo, use la opción del compilador **\/Za** para deshabilitar las extensiones de Microsoft para la norma.  Para obtener más información, vea [\/Za, \/Ze \(Deshabilitar extensiones de lenguaje\)](../build/reference/za-ze-disable-language-extensions.md).  
  
## Requisitos previos  
 Para completar este tutorial, debe comprender los conceptos básicos del lenguaje C\+\+.  
  
### Para crear un proyecto y agregar un archivo de origen  
  
1.  Para crear un nuevo proyecto, en el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
2.  En el panel de tipos de proyecto de **Visual C\+\+**, haga clic en **Win32** y, a continuación, en **Aplicación de consola Win32**.  
  
3.  Escriba un nombre para el proyecto.  
  
     De forma predeterminada, la solución que contiene el proyecto tiene el mismo nombre que el proyecto, pero puede escribir un nombre diferente.  También puede escribir una ubicación diferente para el proyecto.  
  
     Haga clic en **Aceptar** para crear el proyecto.  
  
4.  En el **Asistente para aplicaciones Win32**, haga clic en **Siguiente**, seleccione **Proyecto vacío** y,, a continuación, haga clic en **Finalizar**.  
  
5.  Si no aparece el **Explorador de soluciones**, en el menú **Ver**, haga clic en **Explorador de soluciones**.  
  
6.  Agregue un nuevo archivo de origen al proyecto como se indica a continuación.  
  
    1.  En el **Explorador de soluciones**, haga clic con el botón secundario en la carpeta **Archivos de origen**, elija **Agregar** y, a continuación, seleccione **Nuevo elemento**.  
  
    2.  En el nodo **Código**, haga clic en **Archivo C\+\+ \(.cpp\)**, escriba un nombre para el archivo y, a continuación, haga clic en **Agregar**.  
  
     El archivo .cpp aparece en la carpeta de archivos de origen del **Explorador de soluciones** y el archivo se abre en el editor de Visual Studio.  
  
7.  En el archivo del editor, escriba un programa de C\+\+ válido que use la Biblioteca estándar de C\+\+ o copie uno de los programas de ejemplo y péguelo en el archivo.  
  
     Por ejemplo, puede usar el programa [set::find](../misc/set-find-stl-samples.md), que es uno de los ejemplos de Biblioteca de plantillas estándar incluidos en la Ayuda.  
  
     Si usa el programa de ejemplo, observe la directiva `using namespace std;`.  Esta directiva permite al programa usar `cout` y `endl` sin requerir nombres completos \(`std::cout` y `std::endl`\).  
  
8.  Guarde el archivo.  
  
9. En el menú **Compilar**, haga clic en **Compilar solución**.  
  
     La **Ventana de salida** muestra información sobre el progreso de compilación; por ejemplo, la ubicación del registro de compilación y un mensaje que indica el estado de la misma.  
  
10. En el menú **Depurar**, haga clic en **Iniciar sin depurar**.  
  
     Si usó el programa de ejemplo, aparece una ventana de comandos que indica si hay determinados enteros en el conjunto.  
  
## Pasos siguientes  
 **Anterior:** [Creating Command\-Line Applications \(C\+\+\)](http://msdn.microsoft.com/es-es/2505d9ed-aca4-426a-9071-078a2d707254).  **Siguiente:** [Tutorial: Compilar un programa nativo de C\+\+ en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).  
  
## Vea también  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/es-es/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C\+\+](../standard-library/cpp-standard-library-reference.md)