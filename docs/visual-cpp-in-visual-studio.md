---
title: Visual C++ en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- unmanaged code, C++
- development environment, Visual C++
- unmanaged code
- Visual C++
- Visual C++, reference
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6116a1b27595c6400edfcb79daafb362fb7aec5f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43684496"
---
# <a name="visual-c-in-visual-studio"></a>Visual C++ en Visual Studio

> [!NOTE]  
> Esta documentación para desarrolladores es aplicable a Visual Studio 2015 y Visual Studio 2017. 

> Si busca un paquete redistribuible de Visual C++ que le permita ejecutar un programa, vaya al [Centro de descarga de Microsoft](http://www.microsoft.com/en-us/download/) y escriba **Visual C++** en el cuadro de búsqueda.  
  

Microsoft Visual C++, con frecuencia abreviado como Visual C++ o MSVC, es el nombre de las herramientas y las bibliotecas de desarrollo de lenguaje ensamblador, C++ y C que están disponibles como parte de Visual Studio en Windows. Dichas herramientas y bibliotecas permiten crear aplicaciones de la Plataforma universal de Windows (UWP), aplicaciones nativas de servidor y escritorio de Windows, y aplicaciones y bibliotecas multiplataforma que se ejecuten en Windows, Linux, Android y iOS, así como aplicaciones y bibliotecas administradas que usen .NET Framework. Puede usar Visual C++ para escribir cualquier cosa, desde sencillas aplicaciones de consola hasta aplicaciones de lo más complejas y sofisticadas de escritorio de Windows, desde controladores de dispositivos y componentes del sistema operativo hasta juegos multiplataforma para dispositivos móviles, y desde dispositivos IoT de lo más simples hasta elementos multiservidor de informática de alto rendimiento en la nube de Azure.

## <a name="whats-new-and-conformance-history"></a>Historial de cumplimiento y novedades

[Novedades de C++ en Visual Studio 2017](what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
Descubra las novedades de Visual Studio 2017.

[Novedades de C++ desde Visual Studio 2003 hasta 2015](porting/visual-cpp-what-s-new-2003-through-2015.md)<br/>
Descubra las novedades de C++ para cada versión de Visual Studio desde 2003 hasta 2015.

[Mejoras de conformidad de C++ en Visual Studio 2017](cpp-conformance-improvements-2017.md)<br/>
Obtenga más información sobre las mejoras de conformidad de C++ en Visual Studio 2017.

[Conformidad del lenguaje Visual C++](visual-cpp-language-conformance.md)<br/>
Lista de estados de conformidad por característica del Compilador de Microsoft Visual C++.

[Historial de cambios en Visual C++ 2003-2015](porting/visual-cpp-change-history-2003-2015.md)<br/>
Obtenga información sobre los cambios importantes de versiones anteriores.

## <a name="install-visual-studio-and-upgrade-from-earlier-versions"></a>Instalación de Visual Studio y actualización de versiones anteriores

[Instalación de la compatibilidad con C++ en Visual Studio](build/vscpp-step-0-installation.md)<br/>
Descargue Visual Studio 2015 o Visual Studio 2017 e instale el conjunto de herramientas de Visual C++.

[Guía de migración y actualización de Visual C++](porting/visual-cpp-porting-and-upgrading-guide.md)<br/>
Guía para migrar el código y actualizar proyectos a Visual Studio 2015 o Visual Studio 2017, incluida la migración del código de C++ a Windows 10 y a la Plataforma universal de Windows.

[Herramientas y características de Visual C++ en las ediciones de Visual Studio](ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)<br/>
Obtenga información sobre diferentes ediciones de Visual Studio.

[Plataformas compatibles](supported-platforms-visual-cpp.md)<br/>
Compruebe cuáles son las plataformas admitidas.

## <a name="learn-c"></a>Aprender C++

[Aquí está otra vez C++](cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
Obtenga más información sobre técnicas de programación modernas de C++ basadas en C++11 y C++14 que le permiten escribir código seguro y rápido, y evite muchos de los problemas de programación de estilo C.

[Standard C++](http://isocpp.org/)<br/>
Obtenga información sobre C++, obtenga información general sobre Modern C++, así como vínculos a libros, artículos, conferencias y eventos

[Aprender Visual C++](build/vscpp-step-1-create.md)<br/>
Comience el aprendizaje de C++.

[Ejemplos de Visual C++](visual-cpp-samples.md)<br/>
Información acerca de los ejemplos.

## <a name="c-development-tools"></a>Herramientas de desarrollo de C++

[IDE y herramientas de desarrollo](ide/ide-and-tools-for-visual-cpp-development.md).
Cómo usar el IDE de Visual Studio para crear proyectos, trabajar con archivos de código fuente, vincular a bibliotecas, compilar, depurar, crear pruebas unitarias, realizar análisis estáticos, implementar y mucho más.

[Compiladores y herramientas de creación](build/building-c-cpp-programs.md) Opciones del vinculador y compilador de Microsoft C++, mensajes de error, ejemplos de línea de comandos, configuración para diferentes plataformas y temas de referencia de compilación. 

## <a name="write-applications-in-c"></a>Escritura de aplicaciones en C++

[Aplicaciones Windows universales](windows/universal-windows-apps-cpp.md)<br/>
Encuentre guías y contenido de referencia en el Centro de desarrollo de Windows. Para obtener información sobre cómo desarrollar aplicaciones para la Plataforma universal de Windows, vea [Introducción a la plataforma Universal de Windows](/windows/uwp/get-started/universal-application-platform-guide) y [Create your first UWP app using C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp) (Creación de la primera aplicación para la Plataforma universal de Windows con C++).

[Aplicaciones de escritorio (C++)](windows/desktop-applications-visual-cpp.md)<br/>
Aprenda a crear aplicaciones tradicionales de escritorio de C++ nativas para Windows.

[Programación de .NET con C++/CLI](dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md) Aprenda a crear DLL que permitan la interoperabilidad entre programas de C++ y .NET nativos escritos en lenguajes como C# o Visual Basic.

[Programación de Linux](linux/index.md) Use el IDE de Visual Studio para programar e implementar una máquina Linux remota para compilar con GCC.

[Archivos DLL en Visual C++](build/dlls-in-visual-cpp.md)<br/>
Descubra cómo utilizar Win32, ATL y MFC para crear archivos DLL de escritorio de Windows, e información sobre cómo compilar y registrar un archivo DLL.

[Programación en paralelo](parallel/parallel-programming-in-visual-cpp.md)<br/>
Obtenga información sobre el uso de la Biblioteca de patrones de procesamiento paralelo, C++ AMP, OpenMP y otras características relacionadas con multithreading en Windows.

[Procedimientos recomendados para la seguridad](security/security-best-practices-for-cpp.md)<br/>
Obtenga información sobre cómo proteger las aplicaciones del código malintencionado y el uso no autorizado.

[Programación web y para la nube](cloud/cloud-and-web-programming-in-visual-cpp.md)<br/>
En C++, existen varias opciones para conectarse a la Web y a la nube.

[Acceso a datos](data/data-access-in-cpp.md)<br/>
Conectarse a bases de datos mediante ODBC y otras tecnologías de acceso a bases de datos.

[Texto y cadenas](text/text-and-strings-in-visual-cpp.md)<br/>
Obtenga información sobre cómo trabajar con diferentes codificaciones y formatos de texto y cadenas para el desarrollo local e internacional.

## <a name="c-language-reference"></a>Referencia del lenguaje C++

Para obtener información sobre el lenguaje C++, vea [C++ Language Reference](cpp/cpp-language-reference.md).

Para obtener información sobre el preprocesador de C++, vea [C/C++ Preprocessor Reference](preprocessor/c-cpp-preprocessor-reference.md).

## <a name="c-libraries-in-visual-studio"></a>Bibliotecas de C++ en Visual Studio

En las secciones siguientes se proporciona información sobre las distintas bibliotecas de C y C++ que se incluyen en Visual Studio.

[Referencia de la biblioteca en tiempo de ejecución de C](c-runtime-library/c-run-time-library-reference.md)<br/>
Incluye alternativas de seguridad mejoradas a las funciones que tienen problemas de seguridad conocidos.

[Biblioteca estándar de C++](standard-library/cpp-standard-library-reference.md)<br/>
La biblioteca estándar de C++.

[Biblioteca de plantillas activas (ATL)](atl/atl-com-desktop-components.md)<br/>
Compatibilidad con aplicaciones y componentes COM.

[Bibliotecas de Microsoft Foundation Class (MFC)](mfc/mfc-desktop-applications.md)<br/>
Compatibilidad para la creación de aplicaciones de escritorio que tienen interfaces de usuario tradicionales o del estilo de Office.

[Biblioteca de patrones de procesamiento paralelo (PPL)](parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Algoritmos asincrónicos y paralelos que se ejecutan en la CPU.

[C++ AMP (C++ Accelerated Massive Parallelism)](parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
Algoritmos con gran paralelismo que se ejecutan en la GPU.

[Biblioteca de plantillas de Windows Runtime (WRL)](windows/windows-runtime-cpp-template-library-wrl.md)<br/>
Aplicaciones y componentes de la Plataforma universal de Windows (UWP).

[Programación de .NET con C++/CLI](dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
Programación para Common Language Runtime (CLR).

## <a name="third-party-open-source-c-libraries"></a>Bibliotecas de C++ de código abierto de terceros

La herramienta de línea de comandos **vcpkg** multiplataforma simplifica mucho la detección e instalación de más de 900 bibliotecas de código abierto de C++. Para obtener más información, consulte [Vcpkg: Administrador de paquetes de C++ para Windows](vcpkg.md).

## <a name="feedback-and-community"></a>Comentarios y comunidad

[Cómo notificar un problema con el conjunto de herramientas de Visual C++](how-to-report-a-problem-with-the-visual-cpp-toolset.md)<br/>
Aprenda a crear informes de error eficaces en el conjunto de herramientas de Visual C++ (compilador, enlazador y otras herramientas) y las formas de enviar el informe.

[Blog del equipo de Visual C++](http://blogs.msdn.com/b/vcblog/)<br/>
Obtenga más información acerca de las nuevas características y la información más reciente de los desarrolladores de [!INCLUDE[vcprvc](build/includes/vcprvc_md.md)].

[Comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/)<br/>
Descubra cómo obtener ayuda, errores de archivo y hacer sugerencias para Visual Studio.

## <a name="see-also"></a>Vea también

- [Referencia del lenguaje C](c-language/c-language-reference.md)
- [Referencia de la biblioteca en tiempo de ejecución de C](c-runtime-library/c-run-time-library-reference.md)
- [Intrínsecos del compilador y lenguaje ensamblador](intrinsics/compiler-intrinsics-and-assembly-language.md)
