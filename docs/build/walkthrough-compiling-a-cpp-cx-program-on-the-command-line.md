---
title: "Tutorial: Compilar un programa de C++/CX en la l&#237;nea de comandos | Microsoft Docs"
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
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Compilar un programa de C++/CX en la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede crear programas de Visual C\+\+ destinados a Windows en tiempo de ejecución y compilarlos en la línea de comandos.  Visual C\+\+ admite las extensiones de componentes de Visual C\+\+ \(C\+\+\/CX\), con tipos y operadores adicionales para tener como destino el modelo de programación de Windows en tiempo de ejecución.  Con C\+\+\/CX, puede crear aplicaciones para Windows Phone 8.1, la Tienda Windows y escritorio de Windows.  Para más información, consulte [Un recorrido por C\+\+\/CX](http://msdn.microsoft.com/magazine/dn166929.aspx) y [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md).  
  
 En este tutorial, utilizará un editor de texto para crear un programa básico de C\+\+\/CX y, a continuación, lo compilará en la línea de comandos.  \(Puede usar su propio programa de C\+\+\/CX en lugar de escribir el que se muestra o usar un código de ejemplo de C\+\+\/CX de otro artículo de ayuda.  Esta técnica es útil para compilar y probar módulos pequeños que no contienen ningún elemento de IU\).  
  
> [!NOTE]
>  También puede usar el IDE de Visual Studio para compilar programas de C\+\+\/CX.  Dado que el IDE incluye una compatibilidad con el diseño, la depuración, la emulación y la implementación que no está disponible en la línea de comandos, se recomienda utilizar el IDE para crear aplicaciones de la Tienda Windows.  Para obtener más información, vea [Create a basic C\+\+ Store app](http://msdn.microsoft.com/library/windows/apps/dn263168).  
  
## Requisitos previos  
 Debe entender los principios del lenguaje C\+\+.  
  
## Compilación de un programa de C\+\+\/CX  
 Para habilitar la compilación de C\+\+\/CX, debe usar la opción del compilador [\/ZW](../build/reference/zw-windows-runtime-compilation.md).  El compilador de Visual C\+\+ generará un archivo .exe destinado a Windows en tiempo de ejecución y vinculará las bibliotecas necesarias.  
  
#### Para compilar una aplicación de C\+\+\/CX en la línea de comandos  
  
1.  Abra una ventana de **Símbolo del sistema para desarrolladores**.  \(En la ventana **Inicio**, abra **Aplicaciones**.  Abra la carpeta **Visual Studio Tools** de su versión de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] y, luego, elija el acceso directo **Símbolo del sistema para desarrolladores**\). Para obtener más información acerca de cómo abrir una ventana de símbolo del sistema, consulte [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](../build/setting-the-path-and-environment-variables-for-command-line-builds.md).  
  
     Puede que se requieran credenciales de administrador para compilar el código correctamente, en función del sistema operativo y de la configuración del equipo.  Para ejecutar la ventana del símbolo del sistema como administrador, abra el menú contextual de **Símbolo del sistema para desarrolladores** y, luego, elija **Ejecutar como administrador**.  
  
2.  En el símbolo del sistema, escriba **notepad basiccx.cpp**.  
  
     Elija **Sí** cuando se le pida que cree un archivo.  
  
3.  En el Bloc de notas, escriba estas líneas:  
  
    ```cpp  
    using namespace Platform;  
  
    int main(Platform::Array<Platform::String^>^ args)  
    {  
        Platform::Details::Console::WriteLine("This is a C++/CX program.");  
    }  
  
    ```  
  
4.  En la barra de menús, elija **Archivo**, **Guardar**.  
  
     Acaba de crear un archivo de origen de Visual C\+\+ que utiliza el espacio de nombres [Espacio de nombres de plataforma](../Topic/Platform%20namespace%20\(C++-CX\).md) de Windows en tiempo de ejecución.  
  
5.  En el símbolo del sistema, escriba **cl \/EHsc \/ZW basiccx.cpp \/link \/SUBSYSTEM:CONSOLE**.  El compilador cl.exe compila el código fuente en un archivo .obj y, después, ejecuta el enlazador para generar un programa ejecutable llamado basiccx.exe.  \(La opción del compilador [\/EHsc](../build/reference/eh-exception-handling-model.md) especifica el modelo de control de excepciones de C\+\+ y la marca [\/link](../build/reference/link-pass-options-to-linker.md) especifica una aplicación de consola\).  
  
6.  Para ejecutar el programa basiccx.exe, en el símbolo del sistema, escriba **basiccx**.  
  
     El programa mostrará este texto y se cerrará:  
  
  **Lo que ve es un programa de C\+\+\/CX.**  
  
## Vea también  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/es-es/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Compilar programas de C\/C\+\+](../build/building-c-cpp-programs.md)   
 [Opciones del compilador](../build/reference/compiler-options.md)