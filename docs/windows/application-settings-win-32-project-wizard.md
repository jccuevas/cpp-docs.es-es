---
title: Configuración de la aplicación, Asistente para proyecto de Win32 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.appwiz.win32.appset
dev_langs:
- C++
helpviewer_keywords:
- application settings [C++]
- Win32 Project Wizard, application settings
ms.assetid: d6b818f0-9b23-4793-a6c5-df1c8c594bad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2be9b63ddf6e93c6e0db2645634a4f7bd7ecf3b8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591666"
---
# <a name="application-settings-win-32-project-wizard"></a>Configuración de la aplicación, Asistente para proyectos Win32

Utilice esta página del asistente para establecer las opciones en el proyecto Win32.

## <a name="application-type"></a>Tipo de aplicación

Crea el tipo de aplicación especificado.

|Opción|Descripción|
|------------|-----------------|
|**Aplicación de consola**|Crea una aplicación de consola. Programas de consola se desarrollan con [consola funciones](https://msdn.microsoft.com/library/ms813137.aspx), que proporcionan compatibilidad con modo de carácter en ventanas de consola. Visual C++ [bibliotecas en tiempo de ejecución](../c-runtime-library/c-run-time-library-reference.md) también proporcionan entrada y salida de ventanas de consola con funciones estándar de E/S, tales como `printf_s()` y `scanf_s()`. Las aplicaciones de consola no tienen interfaz gráfica de usuario. Al compilarse producen un archivo .exe que se puede ejecutar como una aplicación independiente desde la línea de comandos.<br /><br /> Puede agregar compatibilidad con MFC y ATL a las aplicaciones de consola.|
|**Aplicación de Windows**|Crea un programa Win32. Un programa Win32 es una aplicación ejecutable (EXE) escrita en C o C++, que utiliza llamadas a la API de Win32 para crear una interfaz gráfica de usuario.<br /><br /> No se puede agregar compatibilidad con MFC y ATL a una aplicación Windows.|
|**ARCHIVO DLL**|Crea una biblioteca de vínculos dinámicos (DLL) de Win32. Una DLL de Win32 es un archivo binario, escrito en C o C++, que utiliza llamadas a la API de Win32 en lugar de llamadas a clases MFC y que actúa como una biblioteca compartida de funciones que múltiples aplicaciones pueden utilizar simultáneamente.<br /><br /> No puede agregar compatibilidad con MFC y ATL a una aplicación de DLL. Puede indicar que la DLL exporta símbolos.|
|**Biblioteca estática**|Crea una biblioteca estática. Una biblioteca estática es un archivo que contiene objetos y sus funciones, así como datos que vincula al programa cuando se compila el archivo ejecutable. En este tema se explica cómo crear los archivos de inicio y [las propiedades del proyecto](../ide/property-pages-visual-cpp.md) para una biblioteca estática. Un archivo de biblioteca estática proporciona las siguientes ventajas:<br /><br /> -Una biblioteca estática Win32 resulta útil si la aplicación que está trabajando realiza llamadas a la API de Win32 en lugar de a clases MFC.<br />-El proceso de vinculación es el mismo si el resto de la aplicación de Windows se escribe en C o C++.<br />-Puede vincular una biblioteca estática a un programa basado en MFC o a un programa no basados en MFC.|

## <a name="additional-options"></a>Opciones adicionales

Permite definir las compatibilidades y las opciones de la aplicación, en función de su tipo.

|Opción|Descripción|
|------------|-----------------|
|**Proyecto vacío**|Especifica que los archivos de proyecto están en blanco. Si tiene un conjunto de archivos de código fuente (como archivos .cpp, archivos de encabezado, iconos, barras de herramientas, cuadros de diálogo, etc.) y desea crear un proyecto en el entorno de desarrollo de Visual C++, primero deberá crear un archivo de proyecto en blanco y después agregar los archivos al proyecto.<br /><br /> Esta selección no está disponible para los proyectos de biblioteca estática.|
|**Exportar símbolos**|Especifica que el proyecto DLL exporta símbolos.|
|**Encabezado precompilado**|Especifica que el proyecto de biblioteca estática utiliza un encabezado precompilado.|
|Comprobaciones del ciclo de vida de desarrollo de seguridad (SDL)|Para obtener más información sobre SDL, vea [Guía de procesos de ciclo de vida de desarrollo de seguridad (SDL) de Microsoft](../build/reference/sdl-enable-additional-security-checks.md)|

## <a name="add-support-for"></a>Agregar compatibilidad para

Permite agregar compatibilidad con una de las bibliotecas suministradas en Visual C++.

|Opción|Descripción|
|------------|-----------------|
|**ATL**|Compila en el proyecto compatibilidad con las clases ATL (Active Template Library). Solo para aplicaciones de consola Win32.<br /><br /> **Tenga en cuenta** esta opción no indica compatibilidad para agregar objetos ATL mediante la biblioteca ATL de asistentes para código. Solo puede agregar objetos ATL a proyectos ATL o a proyectos MFC con compatibilidad ATL.|
|**MFC**|Compila en el proyecto compatibilidad con la biblioteca MFC (Microsoft Foundation Class). Solo para aplicaciones de consola Win32 y bibliotecas estáticas.|

## <a name="see-also"></a>Vea también

[Asistente para aplicaciones Win32](../windows/win32-application-wizard.md)  