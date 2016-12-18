---
title: "Tutorial: Compilar un programa de C++/CLI en la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
caps.latest.revision: 11
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Compilar un programa de C++/CLI en la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede crear programas de Visual C\+\+ destinados a Common Language Runtime \(CLR\) que usen .NET Framework y compilarlos en la línea de comandos.  Visual C\+\+ admite el lenguaje de programación C\+\+\/CLI, con tipos y operadores adicionales para tener como destino el modelo de programación .NET.  Para ver una introducción al lenguaje C\+\+\/CLI, consulte [Puro C\+\+: hola, C\+\+\/CLI](http://msdn.microsoft.com/magazine/cc163681.aspx).  Para obtener información general, consulte [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
 En este tutorial, utilizará un editor de texto para crear un programa básico de C\+\+\/CLI y, luego, lo compilará en la línea de comandos.  \(Puede usar su propio programa de C\+\+\/CLI en lugar de escribir el que se muestra, o usar un código de ejemplo de C\+\+\/CLI de otro artículo de ayuda.  Esta técnica es útil para compilar y probar módulos pequeños que no contienen ningún elemento de IU\).  
  
> [!NOTE]
>  También puede usar el IDE de Visual Studio para compilar programas de C\+\+\/CLI.  Para obtener más información, vea [Tutorial: Compilar un programa de C\+\+ orientado a CLR en Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md).  
  
## Requisitos previos  
 Debe entender los principios del lenguaje C\+\+.  
  
## Compilación de un programa de C\+\+\/CLI  
 En los pasos siguientes, se muestra cómo compilar una aplicación de consola de C\+\+\/CLI que utiliza clases de .NET Framework.  
  
 Para habilitar la compilación de C\+\+\/CLI, debe usar la opción del compilador [\/clr](../build/reference/clr-common-language-runtime-compilation.md).  El compilador de Visual C\+\+ genera un archivo .exe que contiene código MSIL \(o código nativo y MSIL combinado\) y que vincula a las bibliotecas .NET Framework necesarias.  
  
#### Para compilar una aplicación de C\+\+\/CLI en la línea de comandos  
  
1.  Abra una ventana de **Símbolo del sistema para desarrolladores**.  \(En la ventana **Inicio**, abra **Aplicaciones**.  Abra la carpeta **Visual Studio Tools** de su versión de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] y, luego, elija el acceso directo **Símbolo del sistema para desarrolladores**\). Para obtener más información sobre cómo abrir una ventana de símbolo del sistema, consulte [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](../build/setting-the-path-and-environment-variables-for-command-line-builds.md).  
  
     Puede que se requieran credenciales de administrador para compilar el código correctamente,en función del sistema operativo y de la configuración del equipo.  Para ejecutar la ventana del símbolo del sistema como administrador, abra el menú contextual de **Símbolo del sistema para desarrolladores** y, luego, elija **Ejecutar como administrador**.  
  
2.  En el símbolo del sistema, escriba **notepad basicclr.cpp**.  
  
     Elija **Sí** cuando se le pida que cree un archivo.  
  
3.  En el Bloc de notas, escriba estas líneas:  
  
    ```  
    int main()  
    {  
        System::Console::WriteLine("This is a C++/CLI program.");  
    }  
    ```  
  
4.  En la barra de menús, elija **Archivo**, **Guardar**.  
  
     Ha creado un archivo de código fuente de Visual C\+\+ que utiliza una clase .NET Framework \(<xref:System.Console>\) en el espacio de nombres <xref:System>.  
  
5.  En el símbolo del sistema, escriba **cl \/clr basicclr.cpp**.  El compilador cl.exe compila el código fuente en un archivo .obj que contiene código MSIL y, después, ejecuta el enlazador para generar un programa ejecutable llamado basicclr.exe.  
  
6.  Para ejecutar el programa basicclr.exe, en el símbolo del sistema, escriba **basicclr**.  
  
     El programa mostrará este texto y se cerrará:  
  
  **Lo que ve es un programa de C\+\+\/CLI.**  
  
## Vea también  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/es-es/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Compilar programas de C\/C\+\+](../build/building-c-cpp-programs.md)   
 [Opciones del compilador](../build/reference/compiler-options.md)