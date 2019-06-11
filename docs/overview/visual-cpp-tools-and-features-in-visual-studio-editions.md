---
title: Herramientas y características de C++ en las ediciones de Visual Studio
ms.date: 05/21/2019
helpviewer_keywords:
- tools and platforms [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: c5c0459888f8787fd8abba495395130d64a193e0
ms.sourcegitcommit: bde3279f70432f819018df74923a8bb895636f81
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182915"
---
# <a name="c-tools-and-features-in-visual-studio-editions"></a>Herramientas y características de C++ en las ediciones de Visual Studio


::: moniker range=">=vs-2019"


Las siguientes características de C++ están disponibles en Visual Studio 2019. A menos que se indique lo contrario, todas las características estarán disponibles en todas las ediciones: Visual Studio Community, Visual Studio Professional y Visual Studio Enterprise. Algunas características requieren determinadas cargas de trabajo o componentes opcionales, que se pueden instalar con el Instalador de Visual Studio.

## <a name="platforms"></a>Plataformas

- Escritorio de Windows
- Plataforma universal de Windows (tableta, PC, Xbox, IoT y HoloLens)
- Linux
- Android
- iOS

## <a name="compilers"></a>Compiladores

- Compilador de 32 bits de MSVC para x86, x64, ARM y ARM64
- Compilador de 64 bits de MSVC para x86, x64, ARM y ARM64
- Compilador cruzado de GCC de ARM
- Clang/LLVM
  - En Windows, Clang/LLVM 7.0 para x86 o x64 (solo compatibilidad con CMake). Otras versiones de Clang podrían funcionar, pero no se admiten oficialmente.
  - En Linux, cualquier instalación de Clang/LLVM compatible con la distribución.
 
## <a name="c-workloads"></a>Cargas de trabajo de C++

Visual Studio incluye las siguientes cargas de trabajo para el desarrollo de C++. Puede instalar una o todas ellas, así como otras cargas de trabajo, como el desarrollo de escritorio. NET, desarrollo de Python, desarrollo de Azure, desarrollo de extensiones de Visual Studio, etc.

### <a name="desktop-development-with-c"></a>Desarrollo para el escritorio con C++

Incluye:
- Características principales de escritorio para C++

Componentes opcionales:
- MSVC v142 - VS 2019 C++ x64/x86 Build Tools (v14.21)
- SDK de Windows 10 (10.0.17763.0)
- Depurador Just-In-Time
- Herramientas de generación de perfiles de C++
- Herramientas de CMake en C++ para Windows
- Herramientas de compilación de ATL de C++ para v142 (x86 y x64)
- Test Adapter para Boost.Test
- Test Adapter para Google Test
- Live Share
- IntelliCode
- IntelliTrace (solo Enterprise)
- Herramientas de compilación MFC de C++ para v142 (x86 y x64)
- Compatibilidad con C++/CLI para v142 Build Tools (14.21)
- Módulos de C++ para las herramientas de compilación de v142 (x64/x86: experimental)
- Compilador de Clang para Windows
- IncrediBuild: Aceleración de compilación
- SDK de Windows 10 (10.0.17134.0)
- SDK de Windows 10 (10.0.16299.0)
- MSVC v141 – VS 2017 C++ Build Tools para x64/x86 (v14.16)
- MSVC v140 - VS 2015 C++ Build Tools (v14.00)

### <a name="linux-development-with-c"></a>Desarrollo para Linux con C++

Incluye:
- Características principales de C++
- Entorno de tiempo de ejecución de C de Windows Universal
- C++ for Linux Development

Componentes opcionales:
- Herramientas de CMake en C++ para Linux
- Herramientas de desarrollo insertadas e IoT

### <a name="universal-windows-platform-development"></a>Desarrollo de la Plataforma universal de Windows

Incluye:
- Blend para Visual Studio
- .NET Native y .NET Standard
- Administrador de paquetes de NuGet
- Herramientas de la Plataforma universal de Windows
- SDK de Windows 10 (10.0.17763.0)

Componentes opcionales:
- IntelliCode
- IntelliTrace (solo Enterprise)
- Conectividad del dispositivo USB
- Herramientas de la Plataforma universal de Windows para C++ (v142)
- Herramientas de la Plataforma universal de Windows para C++ (v141)
- Depurador de gráficos y creador de perfiles GPU para DirectX
- SDK de Windows 10 (10.0.18362.0)
- SDK de Windows 10 (10.0.17134.0)
- SDK de Windows 10 (10.0.16299.0)
- Herramientas de arquitectura y análisis

### <a name="c-game-development"></a>Desarrollo de juegos de C++

Incluye:
- Características principales de C++
- Entorno de tiempo de ejecución de C de Windows Universal
- Actualización de C++ 2019 Redistributable
- MSVC v142 - VS 2019 C++ x64/x86 Build Tools (v14.21)

Componentes opcionales:
- Herramientas de generación de perfiles de C++
- SDK de Windows 10 (10.0.17763.0)
- IntelliCode
- IntelliTrace (solo Enterprise)
- SDK de Windows 10 (10.0.17134.0)
- SDK de Windows 10 (10.0.16299.0)
- IncrediBuild: Aceleración de compilación
- Cocos
- Instalador de Unreal Engine
- Compatibilidad con IDE de Android para Unreal Engine

### <a name="mobile-development-with-c"></a>Desarrollo móvil con C++

Incluye:
- Características principales de C++
- Programa de instalación de Android SDK (nivel de API 25) (instalación local para desarrollo móvil con C++)

Componentes opcionales:
- Android NDK (R16B)
- Apache Ant (1.9.3)
- Herramientas de desarrollo de Android en C ++
- IntelliCode
- Google Android Emulator (nivel de API 25) (instalación local)
- Intel Hardware Accelerated Execution Manager (HAXM) (instalación local)
- Android NDK (R16B) (32 bits)
- Herramientas de desarrollo de iOS en C++
- IncrediBuild: Aceleración de compilación


## <a name="individual-components"></a>Componentes individuales

Puede instalar estos componentes con independencia de cualquier carga de trabajo.

- Diagnósticos de JavaScript
- Live Share
- Entorno de ejecución de la Plataforma universal de Windows de C++ para las herramientas de compilación de v142
- Publicación de ClickOnce
- Proyectos del Instalador de Microsoft Visual Studio

## <a name="libraries-and-headers"></a>Encabezados y bibliotecas

- Bibliotecas y encabezados de Windows
- Entorno de tiempo de ejecución de C de Windows Universal (CRT)
- Biblioteca estándar de C++
- ATL
- MFC
- Biblioteca de clases de .NET Framework
- Biblioteca de compatibilidad de C++ para .NET
- OpenMP 2.0
- Más de 900 bibliotecas de código abierto a través del catálogo vcpkg

## <a name="build-and-project-systems"></a>Compilación y sistemas del proyecto

- CMake
- Cualquier sistema de compilación a través de Abrir carpeta
- Compilaciones de línea de comandos (msbuild.exe)
- Compatibilidad nativa con múltiples versiones
- Compatibilidad administrada con múltiples versiones
- Compilaciones en paralelo
- Compilar personalizaciones
- Extensibilidad de páginas de propiedades

## <a name="project-templates"></a>Plantillas de proyecto

Las siguientes plantillas de proyecto están disponibles dependiendo de las cargas de trabajo que haya instalado.

Escritorio de Windows:
- Proyecto vacío
- Aplicación de consola
- Asistente para escritorio de Windows
- Aplicación de escritorio de Windows
- Proyecto de elementos compartidos
- Aplicación de MFC
- Biblioteca de vínculos dinámicos
- Proyecto vacío de CLR
- Aplicación de consola CLR
- Biblioteca estática
- Proyecto de CMake
- Proyecto ATL
- Biblioteca de vínculos dinámicos MFC
- Biblioteca de clases CLR
- Proyecto de archivos Make (Windows)
- Control ActiveX MFC
- Proyecto de prueba unitaria de tipo nativo
- Google Test

Plataforma universal de Windows (C++/CX):
- Aplicación vacía
- Aplicación XAML y DirectX 11
- Aplicación de DirectX 11
- Aplicación de DirectX 12 
- Aplicación de pruebas unitarias 
- Archivo DLL 
- Componente de Windows en tiempo de ejecución 
- Biblioteca estática 
- Proyecto de paquete de aplicación de Windows

Linux:
- Aplicación de consola (Linux)
- Proyecto vacío (Linux)
- Blink para Raspberry Pi
- Proyecto de archivos Make (Linux)

## <a name="tools"></a>Herramientas

- Enlazador incremental (Link.exe)
- Utilidad de archivos Make de Microsoft (Nmake.exe)
- Generador de biblioteca (Lib.exe)
- Compilador de recursos de Windows (Rc.exe)
- Conversor de recurso a objeto de Windows (CvtRes.exe)
- Utilidad de mantenimiento de información de examen (BscMake.exe)
- C++ Name Undecorator (Undname.exe)
- Volcado COFF/PE (Dumpbin.exe)
- Editor de COFF/PE (Editbin.exe)
- MASM (Ml.exe)
- Spy++
- ErrLook
- AtlTrace
- Reglas de inferencia
- Optimizaciones guiadas por perfiles

## <a name="debugging-features"></a>Características de depuración

- Depuración nativa
- natvis (visualización de un tipo nativo)
- Depuración de gráficos
- Depuración administrada
- Uso de GPU
- Uso de memoria
- Remote Debugging
- Depuración de SQL
- Análisis de código estático

## <a name="designers-and-editors"></a>Diseñadores y editores

- XAML Designer
- Diseñador/Editor de estilo CSS
- Diseñador/Editor HTML
- Editor XML
- Editor de código fuente
- Características de productividad: refactorización, motor de IntelliSense EDG, formato de código de C++
- Diseñador de Windows Forms
- Diseñador de datos
- Editor de recursos nativos (archivos .rc)
- editores de recursos
- Editor de modelos
- Diseñador de sombras
- Validación de dependencias en vivo (solo Enterprise)
- Diagramas de capas arquitectónicas (solo Enterprise)
- Validación de arquitectura (solo Enterprise)
- Clon de código (solo Enterprise)

## <a name="data-features"></a>Características de datos

- Diseñador de datos
- Objetos de datos
- Servicios Web
- Explorador de servidores

## <a name="automation-and-extensibility"></a>Automation y extensibilidad

- Modelos de objetos de extensibilidad
- Modelo de código
- modelo de proyecto
- Modelo de editor de recursos
- Modelo de asistente
- Modelo de objetos del depurador

## <a name="application-lifecycle-management-tools"></a>Herramientas de administración del ciclo de vida de las aplicaciones

- Pruebas unitarias (C++ nativo de Microsoft, Boost.Test, Google Test, CTest)
- Mapa de código y gráficos de dependencias (Professional y Enterprise)
- Cobertura de código (solo Enterprise)
- Pruebas manuales (solo Enterprise)
- Pruebas exploratorias (solo Enterprise)
- Administración de casos de pruebas (solo Enterprise)
- Integración del depurador del mapa de código (solo Enterprise)
- Live Unit Testing (solo Enterprise)
- IntelliTrace (solo Enterprise)
- IntelliTest (solo Enterprise)
- Microsoft Fakes (aislamiento de prueba unitaria) (solo Enterprise)
- Cobertura de código (solo Enterprise)

## <a name="see-also"></a>Vea también

[Instalar Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Novedades de Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Tipos de proyectos de C++ en Visual Studio](../build/reference/visual-cpp-project-types.md)<br/>

::: moniker-end

::: moniker range="<=vs-2017"

En las siguientes tablas se muestran las características de Visual C++ que están disponibles en Visual Studio 2017. Una X en la celda indica que la característica está disponible y una celda vacía, que la característica no está disponible. Las notas entre paréntesis indican que una característica está disponible, pero con restricciones.

## <a name="platforms"></a>Plataformas

||||||
|-|-|-|-|-|
|Plataforma|Visual Studio Express para Windows 10|Visual Studio Express para escritorio de Windows|Visual Studio Community/Professional|Visual Studio Enterprise|
|Escritorio de Windows||X|X|X|
|Plataforma universal de Windows (teléfono, tableta, PC, Xbox, IoT y HoloLens)|X||X|X|
|Linux|X|X|
|Microsoft Store 8.1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>Compiladores

|Compilador|Visual Studio Express para Windows|Visual Studio Express para escritorio de Windows|Visual Studio Professional/Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Compilador de X86 de 32 bits de MSVC|X|X|X|X|
|Compilador cruzado de X86_arm|X||X|X|
|Compilador x64 de 64 bits de MSVC|||X|X|
|Compilador cruzado X86_ x64|X|X|X|X|

## <a name="libraries-and-headers"></a>Encabezados y bibliotecas

|Biblioteca o encabezado|Visual Studio Express para Windows|Visual Studio Express para escritorio de Windows|Visual Studio Professional/Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Encabezados y bibliotecas de Windows y biblioteca de CRT|(X)|X|X|X|
|Biblioteca estándar de C++|X|X|X|X|
|ATL|||X|X|
|MFC|||X|X|
|Biblioteca de clases de .NET Framework||X|X|X|
|Biblioteca de compatibilidad de C++ para .NET||X|X|X|
|OpenMP 2.0|X|X|X|X|

## <a name="project-templates"></a>Plantillas de proyecto

|Plantilla|Visual Studio Express para Windows|Visual Studio Express para escritorio de Windows|Visual Studio Professional/Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Plantillas XAML para UWP, Windows 8.1, Windows Phone 8.0|X||X|X|
|Aplicación Direct3D|X||X|X|
|DLL (Windows universal)|X||X|X|
|Biblioteca estática (Windows universal)|X||X|X|
|Componente de Windows en tiempo de ejecución|X||X|X|
|Aplicación de prueba unitaria (Windows universal)|X||X|X|
|Proyecto ATL|||X|X|
|Biblioteca de clases (CLR)||X|X|X|
|Aplicación de consola CLR||X|X|X|
|Proyecto vacío de CLR||X|X|X|
|Asistente personalizado|||X|X|
|Proyecto vacío||X|X|X|
|Proyecto de archivos Make||X|X|X|
|Control ActiveX MFC|||X|X|
|Aplicación MFC|||X|X|
|MFC DLL|||X|X|
|Proyecto de prueba|X|X|X|X|
|Aplicación de consola Win32||X|X|X|
|Proyecto Win32||X|X|X|

## <a name="tools"></a>Herramientas

|Herramienta|Visual Studio Express para Windows|Visual Studio Express para escritorio de Windows|Visual Studio Professional/Community|Visual Studio Enterprise|
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Enlazador incremental (Link.exe)|X|X|X|X|
|Utilidad de mantenimiento de programas (Nmake.exe)||X|X|X|
|Generador de biblioteca (Lib.exe)|X|X|X|X|
|Compilador de recursos de Windows (Rc.exe)|X|X|X|X|
|Conversor de recurso a objeto de Windows (CvtRes.exe)||X|X|X|
|Utilidad de mantenimiento de información de examen (BscMake.exe)|X|X|X|X|
|C++ Name Undecorator (Undname.exe)|X|X|X|X|
|Volcado COFF/PE (Dumpbin.exe)|X|X|X|X|
|Editor de COFF/PE (Editbin.exe)|X|X|X|X|
|MASM (Ml.exe)|||X|X|
|Spy++|||X|X|
|ErrLook|||X|X|
|AtlTrace|||X|X|
|Devenv.com|||X|X|
|Reglas de inferencia|||X|X|
|Actualizar proyectos .vcproj de VCBuild a MSBuild (VCUpgrade.exe)|X|X|X|X|
|Optimizaciones guiadas por perfiles|||X|X|

## <a name="debugging-features"></a>Características de depuración

|Característica de depuración|Visual Studio Express para Windows|Visual Studio Express para escritorio de Windows|Visual Studio Professional/Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Depuración nativa|X|X|X|X|
|natvis (visualización de un tipo nativo)|X|X|X|X|
|Depuración de gráficos|X||X|X|
|Depuración administrada||X|X|X|
|Uso de GPU|X||X|X|
|Uso de memoria|X||X|X|
|Remote Debugging|X|X|X|X|
|Depuración de SQL|||X|X|
|Análisis de código estático|Limitado|Limitado|X|X|

## <a name="designers-and-editors"></a>Diseñadores y editores

|Diseñador o editor|Visual Studio Express para Windows|Visual Studio Express para escritorio de Windows|Visual Studio Professional/Community|Visual Studio Enterprise|
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|XAML Designer|X||X|X|
|Diseñador/Editor de estilo CSS|X|X|X|X|
|Diseñador/Editor HTML|X|X|X|X|
|Editor XML|X|X|X|X|
|Editor de código fuente|X|X|X|X|
|Características de productividad: refactorización, IntelliSense, formato de código de C++|X|X|X|X|
|Diseñador de Windows Forms||X|X|X|
|Diseñador de datos|||X|X|
|Editor de recursos nativos (archivos .rc)|||X|X|
|editores de recursos|X|X|X|X|
|Editor de modelos|X||X|X|
|Diseñador de sombras|X||X|X|

## <a name="data-features"></a>Características de datos

|Característica de datos|Visual Studio Express para Windows|Visual Studio Express para escritorio de Windows|Visual Studio Professional/Community|Visual Studio Enterprise|
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Diseñador de datos|||X|X|
|Objetos de datos|||X|X|
|Servicios Web|||X|X|
|Explorador de servidores|||X|X|

## <a name="build-and-project-systems"></a>Compilación y sistemas del proyecto

|Compilación o característica de proyecto|Visual Studio Express para Windows|Visual Studio Express para escritorio de Windows|Visual Studio Professional/Community|Visual Studio Enterprise|
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Compilaciones de línea de comandos (msbuild.exe)|X|X|X|X|
|Compatibilidad nativa con múltiples versiones||X|X|X|
|Compatibilidad administrada con múltiples versiones||X|X|X|
|Compilaciones en paralelo|X|X|X|X|
|Compilar personalizaciones|X|X|X|X|
|Extensibilidad de páginas de propiedades|X|X|X|X|

## <a name="automation-and-extensibility"></a>Automation y extensibilidad

|Automation y extensibilidad|Visual Studio Express para Windows|Visual Studio Express para escritorio de Windows|Visual Studio Professional/Community|Visual Studio Enterprise|
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Modelos de objetos de extensibilidad|||X|X|
|Modelo de código|||X|X|
|modelo de proyecto|||X|X|
|Modelo de editor de recursos|||X|X|
|Modelo de asistente|||X|X|
|Modelo de objetos del depurador|||X|X|

## <a name="application-lifecycle-management-tools"></a>Herramientas de administración del ciclo de vida de las aplicaciones

||||||
|-|-|-|-|-|
|Herramienta|Visual Studio Express para Windows|Visual Studio Express para escritorio de Windows|Visual Studio Professional/Community|Visual Studio Enterprise|
|Pruebas unitarias (marco nativo)|X|X|X|X|
|Pruebas unitarias (marco administrado)||X|X|X|
|Cobertura de código||||X|
|Pruebas manuales||||X|
|Pruebas exploratorias||||X|
|Administración de casos de prueba||||X|
|Mapa de código y gráficos de dependencias|||solo lectura|X|
|Depuración de mapa de código||||X|

## <a name="see-also"></a>Vea también

[Instalar Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Novedades de Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Tipos de proyectos de C++ en Visual Studio](../build/reference/visual-cpp-project-types.md)<br/>

::: moniker-end
