---
title: "Tutorial: Compilar un C++ / CX programa en la línea de comandos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4e3ae72f5f8cd268bae88a0b5f0be74864317ad0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>Tutorial: Compilar un programa de C++/CX en la línea de comandos
Puede crear programas de Visual C++ destinados a Windows Runtime y compilarlos en la línea de comandos. Visual C++ admite las extensiones de componentes de Visual C++ (C++/CX), con tipos y operadores adicionales para tener como destino el modelo de programación de Windows en tiempo de ejecución. Con C++/CX, puede crear aplicaciones para Windows Phone 8.1, la Tienda Windows y escritorio de Windows. Para obtener más información, consulte [un paseo de c++ / CX](http://msdn.microsoft.com/magazine/dn166929.aspx) y [extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md).  
  
 En este tutorial, utilizará un editor de texto para crear un programa básico de C++/CX y, a continuación, lo compilará en la línea de comandos. (Puede usar su propio programa de C++/CX en lugar de escribir el que se muestra o usar un código de ejemplo de C++/CX de otro artículo de ayuda. Esta técnica es útil para compilar y probar módulos pequeños que no contienen ningún elemento de IU).  
  
> [!NOTE]
>  También puede usar el IDE de Visual Studio para compilar programas de C++/CX. Dado que el IDE incluye una compatibilidad con el diseño, la depuración, la emulación y la implementación que no está disponible en la línea de comandos, se recomienda utilizar el IDE para crear aplicaciones de la Tienda Windows. Para obtener más información, consulte [crear una aplicación básica de la tienda de C++](http://msdn.microsoft.com/library/windows/apps/dn263168).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Debe entender los principios del lenguaje C++.  
  
## <a name="compiling-a-ccx-program"></a>Compilación de un programa de C++/CX  
 Para habilitar la compilación de C++ / CX, debe utilizar el [/ZW](../build/reference/zw-windows-runtime-compilation.md) opción del compilador. El compilador de Visual C++ generará un archivo .exe destinado a Windows Runtime y vinculará las bibliotecas necesarias.  
  
#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>Para compilar una aplicación de C++/CX en la línea de comandos  
  
1.  Abra un **símbolo** ventana. (En el **iniciar** ventana, abra **aplicaciones**. Abra la **Visual Studio Tools** carpeta de su versión de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]y, a continuación, elija la **símbolo** acceso directo.) Para obtener más información sobre cómo abrir una ventana del símbolo del sistema para desarrolladores, consulte [de compilación de C/C ++ en la línea de comandos](../build/building-on-the-command-line.md).  
  
     Puede que se requieran credenciales de administrador para compilar el código correctamente,en función del sistema operativo y de la configuración del equipo. Para ejecutar la ventana de símbolo del sistema como administrador, abra el menú contextual de **símbolo** y, a continuación, elija **ejecutar como administrador**.  
  
2.  En el símbolo del sistema, escriba **basiccx.cpp el Bloc de notas**.  
  
     Elija **Sí** cuando le pedirá que cree un archivo.  
  
3.  En el Bloc de notas, escriba estas líneas:  
  
    ```cpp  
    using namespace Platform;  
  
    int main(Platform::Array<Platform::String^>^ args)  
    {  
        Platform::Details::Console::WriteLine("This is a C++/CX program.");  
    }  
  
    ```  
  
4.  En la barra de menús, elija **archivo**, **guardar**.  
  
     Ha creado un archivo de código fuente de Visual C++ que utiliza el tiempo de ejecución de Windows [espacio de nombres Platform](../cppcx/platform-namespace-c-cx.md) espacio de nombres.  
  
5.  En el símbolo del sistema, escriba **cl /EHsc/ZW basiccx.cpp /link /SUBSYSTEM:CONSOLE**. El compilador cl.exe compila el código fuente en un archivo .obj y, después, ejecuta el enlazador para generar un programa ejecutable llamado basiccx.exe. (El [/EHsc](../build/reference/eh-exception-handling-model.md) opción del compilador especifica el modelo de control de excepciones de C++ y la [/link](../build/reference/link-pass-options-to-linker.md) marca especifica una aplicación de consola.)  
  
6.  Para ejecutar el programa basiccx.exe, en el símbolo del sistema, escriba **basiccx**.  
  
     El programa mostrará este texto y se cerrará:  
  
    ```Output  
    This is a C++/CX program.  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Compilación de programas de C/C++](../build/building-c-cpp-programs.md)   
 [Opciones del compilador](../build/reference/compiler-options.md)