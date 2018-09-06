---
title: Herramientas y características de Visual C++ en las ediciones de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- versions [C++]
- Visual C++, versions
- editions [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 79814d96bac185e73cc1c42a98be6d7b35e9a75d
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42578285"
---
# <a name="visual-c-tools-and-features-in-visual-studio-editions"></a>Herramientas y características de Visual C++ en las ediciones de Visual Studio

En las siguientes tablas se muestran las características de Visual C++ que están disponibles en Visual Studio. Una X en la celda indica que la característica está disponible y una celda vacía, que la característica no está disponible. Las notas entre paréntesis indican que una característica está disponible, pero con restricciones.

## <a name="platforms"></a>Plataformas

||||||
|-|-|-|-|-|
|Plataforma|Visual Studio Express para Windows 10|Visual Studio Express para escritorio de Windows|Visual Studio Community/Professional|Visual Studio Enterprise|
|Escritorio de Windows||X|X|X|
|Plataforma universal de Windows (teléfono, tableta, PC, Xbox, IoT y HoloLens)|X||X|X|
|Microsoft Store 8.1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>Compiladores

|Compilador|Visual Studio Express para Windows|Visual Studio Express para escritorio de Windows|Visual Studio Professional/Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Compilador de X86 de 32 bits|X|X|X|X|
|Compilador cruzado de X86_arm|X||X|X|
|Compilador x64 de 64 bits|||X|X|
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
|OpenMP|X|X|X|X|

## <a name="project-templates"></a>Plantillas de proyecto

|Plantilla|Visual Studio Express para Windows|Visual Studio Express para escritorio de Windows|Visual Studio Professional/Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Plantillas XAML para UWP, Windows 8.1, Windows Phone 8.0|X||X|X|
|Aplicación Direct3D|X||X|X|
|DLL (Windows universal)|X||X|X|
|Biblioteca estática (Windows universal)|X||X|X|
|Componente de Windows Runtime|X||X|X|
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
|Depuración remota|X|X|X|X|
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

## <a name="automation-and-extensibility"></a>Automatización y extensibilidad

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
|prueba exploratoria||||X|
|Administración de casos de prueba||||X|
|Mapa de código y gráficos de dependencias|||solo lectura|X|
|Depuración de mapa de código||||X|

## <a name="see-also"></a>Vea también

[Instalar Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Novedades de Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Tipos de proyecto de Visual C++](../ide/visual-cpp-project-types.md)<br/>
[SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686)<br/>
