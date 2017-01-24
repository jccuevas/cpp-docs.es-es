---
title: "Tutorial: Compilar un programa nativo de C++ en la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones de línea de comandos [C++], nativas"
  - "compilar programas [C++]"
  - "código nativo [C++]"
  - "Visual C++, código nativo"
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
caps.latest.revision: 63
caps.handback.revision: 57
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Compilar un programa nativo de C++ en la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ incluye un compilador de C\+\+ de línea de comandos que puede usar para crear desde aplicaciones de consola básicas hasta aplicaciones universales de Windows, pasando por aplicaciones de la Tienda Windows y componentes .NET.  
  
 En este tutorial, creará un programa de consola básico en Visual C\+\+ con un editor de texto y, luego, lo compilará en la línea de comandos.  
  
> [!NOTE]
>  También puede usar el entorno de desarrollo integrado \(IDE\) de Visual Studio para compilar programas de Visual C\+\+. Para obtener más información, consulta [Tutorial: Trabajar con proyectos y soluciones \(C\+\+\)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md).  
  
 En este tutorial, puede usar su propio programa de Visual C\+\+ en lugar de escribir el que se muestra o usar un código de ejemplo de Visual C\+\+ de otro artículo de ayuda.  
  
## Requisitos previos  
 Para completar este tutorial, debe tener una versión de Visual Studio que incluya los componentes de Visual C\+\+. Es recomendable conocer los principios del lenguaje C\+\+. En estas instrucciones se supone que está utilizando Windows 10 y Visual Studio 2015, pero las instrucciones para otros entornos y versiones son similares.  
  
### Para crear un archivo de código fuente de Visual C\+\+ y compilarlo en la línea de comandos  
  
1.  Primero, abra un **Símbolo del sistema para desarrolladores**. El compilador de Visual C\+\+ necesita un entorno de comandos especial para ejecutarse, por lo que no puede utilizar un símbolo del sistema normal para este tutorial.  
  
     En el menú **Inicio** de Windows, abra **Todas las aplicaciones**. Desplácese hacia abajo, busque y abra la carpeta **Visual Studio** para su versión de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] y, luego, elija el acceso directo **Símbolo del sistema para desarrolladores**.  
  
2.  Cree un nuevo directorio para albergar el programa. En la ventana **Símbolo del sistema para desarrolladores**, escriba un comando `cd \` para cambiar el directorio a la raíz de la unidad. Escriba un comando `md examples` para crear un directorio para el código de ejemplo. Después, escriba un comando `cd examples` para convertirlo en el directorio de trabajo actual. Aquí será donde irá el primer programa.  
  
3.  En el símbolo del sistema, escriba **notepad hello.cpp**.  
  
     Elija **Sí** cuando se le pida que cree un archivo. Se abrirá una ventana del Bloc de notas en blanco, lista para que escriba el código.  
  
4.  En el Bloc de notas, escriba estas líneas:  
  
    ```cpp  
    #include <iostream> using namespace std; void main() { cout << "Hello, world, from Visual C++!" << endl; }  
    ```  
  
     Se trata de un programa muy sencillo que escribirá una línea de texto en la pantalla y, después, saldrá. Para minimizar los errores, copie este código y péguelo en el Bloc de notas.  
  
5.  No olvide guardar su trabajo. En el Bloc de notas, en el menú **Archivo**, elija **Guardar**.  
  
     Ha creado un archivo de código fuente de Visual C\+\+.  
  
6.  En el símbolo del sistema, escriba `cl /EHsc hello.cpp` para compilar el programa.  
  
     El compilador cl.exe genera un archivo .obj que contiene el código compilado y, luego, ejecuta el enlazador para crear un programa ejecutable llamado hello.exe. Este nombre aparece en las líneas de información de salida que muestra el compilador. La salida del compilador debe tener un aspecto similar al siguiente:  
  
    ```Output  
    Microsoft (R) C/C++ Optimizing Compiler Version 19.00.23504 for x86 Copyright (C) Microsoft Corporation.  All rights reserved. hello.cpp Microsoft (R) Incremental Linker Version 14.00.23504.0 Copyright (C) Microsoft Corporation.  All rights reserved. /out:hello.exe hello.obj  
    ```  
  
     Si hay errores, compruebe el código en el Bloc de notas para asegurarse de que coincida con el ejemplo. Ejecute el comando del compilador de nuevo después de guardar los cambios.  Si no se encuentra el comando cl, compruebe que está utilizando el Símbolo del sistema para desarrolladores y no una ventana de comandos normal. Si aún no está instalado, es posible que también deba instalar el componente de Visual C\+\+ en la instalación de Visual Studio.  
  
7.  Para ejecutar el programa hello.exe, en el símbolo del sistema, escriba `hello`.  
  
     El programa mostrará este texto y se cerrará:  
  
    ```Output  
    Hello, world, from Visual C++!  
    ```  
  
     Enhorabuena, ha creado y compilado un programa con las herramientas de línea de comandos.  
  
## Pasos siguientes  
 Para más información sobre cómo abrir una ventana del Símbolo del sistema para desarrolladores a fin de usar las herramientas de línea de comandos, consulte [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](../build/setting-the-path-and-environment-variables-for-command-line-builds.md).  
  
 Puede que se requieran credenciales de administrador para compilar el código de este tutorial correctamente, dependiendo del sistema operativo y de la configuración del equipo. Para ejecutar la ventana del Símbolo del sistema para desarrolladores como administrador, haga clic con el botón derecho para abrir el menú contextual del **Símbolo del sistema para desarrolladores** y, luego, elija **Ejecutar como administrador**.  
  
 La opción de la línea de comandos **\/EHsc** le indica al compilador que habilite el control de excepciones de C\+\+. Para obtener más información, consulta [\/EH \(Modelo de control de excepciones\)](../build/reference/eh-exception-handling-model.md).  
  
## Vea también  
 [Paseo guiado de Visual C\+\+](http://msdn.microsoft.com/es-es/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Compilar programas de C\/C\+\+](../build/building-c-cpp-programs.md)   
 [Opciones del compilador](../build/reference/compiler-options.md)