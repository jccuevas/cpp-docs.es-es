---
title: "Cómo: habilitar un herramientas de 64 bits Visual C++ en la línea de comandos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- x64 [C++]
- 64-bit compiler [C++], command line usage
- 64-bit compiler [C++], toolset enabling at command line
- command line [C++], 64-bit compiler
- Itanium [C++], command-line compiler
- IPF
- Itanium [C++]
- IPF, command-line compiler
- x64 [C++], command-line compiler
ms.assetid: 4da93a19-e20d-4778-902a-5eee9a6a90b5
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7712bcf73881d02b5d28c8a7645609be1df5e489
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-enable-a-64-bit-x64-hosted-visual-c-toolset-on-the-command-line"></a>Cómo: habilitar 64 bits, x64 hospeda el conjunto de herramientas de Visual C++ en la línea de comandos

Visual C++ incluye compiladores, vinculadores y otras herramientas que puede usar para crear versiones específicas de la plataforma de las aplicaciones que se pueden ejecutar en sistemas operativos Windows de 32 bits, 64 bits o basado en ARM. Otras cargas de trabajo opcionales de Visual Studio le permiten usar herramientas de C++ como destino otras plataformas, como iOS y Android, Linux. La arquitectura de compilación predeterminada usa herramientas de 32 bits, hospedados x86 para compilar el código de Windows de 32 bits, nativo x86. Sin embargo, probablemente tenga un equipo de 64 bits. Puede aprovechar las ventajas del procesador y espacio de memoria disponible para código de 64 bits usando el conjunto de herramientas de 64 bits, hospedados en x64 cuando se compila código de x86, x64 o procesadores ARM.
  
> [!NOTE]
>  Para obtener información acerca de las herramientas específicas que se incluyen con cada edición de Visual C++, vea [características en ediciones de Visual Studio y herramientas de Visual C++](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md).  
>   
>  Para obtener información acerca de cómo utilizar el IDE de Visual Studio para crear aplicaciones de 64 bits, consulte [Cómo: configurar proyectos de Microsoft Visual C++ a destino 64 bits, x64 plataformas](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).  
  
Cuando se instala una carga de trabajo de C++ en el instalador de Visual Studio, siempre se instala 32 bits, hospedados en x86, nativa y cruzada herramientas del compilador para compilar el código de x86 y x64. Si incluye la carga de trabajo de la plataforma Universal de Windows, también instala las herramientas de compilador cruzado hospedado x86 para compilar código ARM. Si instala estas cargas de trabajo en un x64 64 bits, procesador, también obtiene nativo de 64 bits y cross herramientas del compilador para compilar x86, x 64 y ARM de código. Las herramientas de 32 bits y 64 bits generan código idéntico, pero las herramientas de 64 bits admiten más memoria para los símbolos de encabezado precompilado y la optimización de todo el programa ([/GL](../build/reference/gl-whole-program-optimization.md) y [/LTCG](../build/reference/ltcg-link-time-code-generation.md)) opciones. Si se ejecuta con límites de memoria cuando se usan las herramientas de 32 bits, pruebe las herramientas de 64 bits.  

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>Utilice un método abreviado de símbolo del sistema de 64 bits hospedado developer
  
Cuando se instala Visual Studio en un sistema operativo de Windows de 64 bits, métodos abreviados de nativo de 64 bits, hospedados x64 y compiladores cruzados del símbolo de adicionales para los programadores están disponibles. Para obtener acceso a estos símbolos del sistema en Windows 10, en el **iniciar** menú, abra la carpeta para su versión de Visual Studio, por ejemplo **2017 de Visual Studio**y, a continuación, elija uno de los x64 nativo o entre herramientas símbolos del desarrollador. Para obtener acceso a estos símbolos del sistema en Windows 8, en la **iniciar** pantalla, abra **todas las aplicaciones**. En el encabezado de la versión instalada de Visual Studio, abra el **Visual Studio** carpeta (en versiones anteriores de Visual Studio, puede llamarse **Visual Studio Tools**). En versiones anteriores de Windows, elija **iniciar**, expanda **todos los programas**, la carpeta para su versión de **Visual Studio** (y en versiones anteriores de Visual Studio,  **Herramientas de Visual Studio**). Para obtener más información, consulte [métodos abreviados del símbolo de desarrollador](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts).  
  
## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>Utilizar Vcvarsall.bat para establecer una arquitectura de compilación hospedado de 64 bits
  
Cualquiera de nativo o entre herramientas del compilador configuraciones de compilación pueden usarse en la línea de comandos ejecutando el vcvarsall.bat archivo de comandos. Este archivo de comandos configura la ruta de acceso y las variables de entorno que habilitan una determinada arquitectura en una ventana de símbolo del sistema existente de compilación. Para obtener instrucciones específicas, consulte [archivos de comandos de desarrollador y ubicaciones](../build/building-on-the-command-line.md#developer_command_files) .  
  
## <a name="see-also"></a>Vea también  

[Configuración de Visual C++ en destinos de 64 bits, x64](../build/configuring-programs-for-64-bit-visual-cpp.md)