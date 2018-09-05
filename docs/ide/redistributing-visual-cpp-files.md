---
title: Redistribuir archivos de Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09d65a19ecf573cc11d71fe49cdb40c1a748aafa
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681922"
---
# <a name="redistributing-visual-c-files"></a>Redistribuir archivos de Visual C++

> [!NOTE]
> ¿Está buscando una descarga de uno de los archivos del tiempo de ejecución de Visual C++? Vaya al sitio web de [Microsoft](http://www.microsoft.com/) y escriba **Visual C++ redistribuible** en el cuadro de búsqueda. Descargue e instale el paquete redistribuible para la arquitectura del equipo (por ejemplo, x64 si está ejecutando Windows de 64 bits) y la versión de Visual C++ (por ejemplo, 2015) que necesite.

Al implementar una aplicación, también debe implementar los archivos necesarios para asistirla. Si alguno de estos archivos los proporciona Microsoft, compruebe si está permitida su redistribución. Para revisar los términos de licencia de Visual Studio, vea el vínculo Términos de licencia en el cuadro de diálogo Acerca de Microsoft Visual Studio en el IDE o descargue el archivo [Términos de la licencia de software de Microsoft](https://visualstudio.microsoft.com/license-terms/mlt687465/). Para ver la "lista REDIST" a la que se hace referencia en la sección "Código distribuible" de los Términos de la licencia de software de Microsoft para determinadas ediciones de Visual Studio, vea [Código distribuible para Microsoft Visual Studio 2017 (incluye utilidades, extensibilidad y archivos BuildServer)](/visualstudio/productinfo/2017-redistribution-vs), o bien para Visual Studio 2015, vea [Código distribuible para Microsoft Visual Studio 2015 y Microsoft Visual Studio 2015 SDK (incluye utilidades y archivos BuildServer)](/visualstudio/productinfo/2015-redistribution-vs). Para obtener más información sobre los archivos redistribuibles, vea [Determinar qué archivos DLL se redistribuirán](../ide/determining-which-dlls-to-redistribute.md) y [Ejemplos de implementación](../ide/deployment-examples.md).

Para implementar los archivos redistribuibles de Visual C++, puede usar los paquetes redistribuibles de Visual C++ (VCRedist\_x86.exe, VCRedist\_x64.exe o VCRedist\_arm.exe) que se incluyen en Visual Studio. En Visual Studio 2017, estos archivos se pueden encontrar en la carpeta Archivos de programa [(x86)]\\Microsoft Visual Studio\\2017\\_edición_\\VC\\Redist\\MSVC\\_versión_bib_, donde _edición_ es la edición de Visual Studio instalada, y _versión_bib_ es la versión de las bibliotecas que se van a redistribuir. En Visual Studio 2015, estos archivos se pueden encontrar en el directorio de instalación de Visual Studio en Archivos de programa [(x86)]\Microsoft Visual Studio *versión*\VC\redist\\*configuración_regional*\\. Otra opción consiste en usar módulos de combinación redistribuibles (archivos .msm), que en Visual Studio 2017 se pueden encontrar en la carpeta Archivos de programa [(x86)]\\Microsoft Visual Studio\\2017\\_edición_\\VC\\Redist\\MSVC\\_versión_bib_\\MergeModules\\. En Visual Studio 2015 se pueden encontrar en programa Archivos de programa [(x86)]\Common Files\Merge Modules\\. También es posible instalar directamente los archivos DLL redistribuibles de Visual C++ en la *carpeta local de la aplicación*, que es la que contiene el archivo ejecutable de la aplicación. Por razones del servicio, se recomienda no usar esta ubicación para la instalación.

Los paquetes redistribuibles de Visual C++ instalan y registran todas las bibliotecas de Visual C++. Si usa alguno, debe configurarlo para que se ejecute en el sistema de destino como un requisito previo para la instalación de la aplicación. Se recomienda usar estos paquetes para las implementaciones, ya que habilitan la actualización automática de las bibliotecas de Visual C++. Para obtener un ejemplo sobre cómo usar estos paquetes, vea [Tutorial: Implementar una aplicación de Visual C++ mediante el paquete redistribuible de Visual C++](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

Cada paquete redistribuible de Visual C++ comprueba si existe una versión más reciente en el equipo. Si se encuentra una versión más reciente, el paquete no se instala. A partir de Visual Studio 2015, los paquetes redistribuibles muestran un mensaje de error que indica que la instalación no se pudo realizar. Si se ejecuta un paquete mediante la marca **/quiet**, no se mostrará ningún mensaje de error. En cualquier caso, Microsoft Installer registrará un error y devolverá un resultado de error al llamador. A partir de los paquetes de Visual Studio 2015, este error se puede evitar si se comprueba el Registro para averiguar si hay instalada una versión más reciente. La versión instalada actualmente se almacena en la clave HKEY_LOCAL_MACHINE\SOFTWARE[\Wow6432Node]\Microsoft\VisualStudio\\_versión_VS_\VC\Runtimes\\{x86|x64|ARM}, donde _versión_VS_ es el número de versión para Visual Studio (14.0 para Visual Studio 2015 y Visual Studio 2017, porque el paquete redistribuible de 2017 actualizado es binario compatible con la versión 2015), y donde la clave es ARM, x86 o x64 según las versiones de vcredist instaladas para la plataforma. (No es necesario comprobar bajo la subclave Wow6432Node a menos que se use RegEdit para ver la versión del paquete x86 instalada en una plataforma x64). El número de versión se almacena en el valor de cadena REG_SZ **Version** y también en el conjunto de valores de REG_DWORD **Major**, **Minor**, **Bld** y **Rbld**. Para evitar un error durante la instalación, debe omitir la instalación del paquete redistribuible si la versión instalada actualmente es más reciente.

Si usa un módulo de fusión mediante combinación que contenga un archivo DLL de Visual C++, debe incluirlo en el paquete de Windows Installer (o paquete de instalación similar) que esté usando para implementar la aplicación. Para obtener más información, vea [Redistribuir mediante módulos de combinación](../ide/redistributing-components-by-using-merge-modules.md). Para obtener un ejemplo, vea [Tutorial: Implementar una aplicación de Visual C++ mediante un proyecto de instalación](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md), donde también se muestra cómo usar InstallShield Limited Edition para crear un paquete de instalación.

## <a name="potential-run-time-errors"></a>Posibles errores en tiempo de ejecución

Si Windows no puede encontrar uno de los archivos DLL de biblioteca redistribuibles necesarios para la aplicación, puede aparecer un mensaje similar al siguiente: "No se pudo iniciar la aplicación porque no se encontró *biblioteca*.dll. La reinstalación de la aplicación puede solucionar el problema".

Para resolver este tipo de errores, debe asegurarse de que el instalador de la aplicación se compila correctamente y de que las bibliotecas redistribuibles se implementan correctamente en el sistema de destino. Para obtener más información, vea [Descripción de las dependencias de una aplicación de Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Redistribuir mediante módulos de combinación](../ide/redistributing-components-by-using-merge-modules.md)|Se describe cómo usar los módulos de combinación redistribuibles de Visual C++ para instalar las bibliotecas en tiempo de ejecución de Visual C++ como archivos DLL compartidos en la carpeta %windir%\system32\.|
|[Redistribuir controles ActiveX de Visual C++](../ide/redistributing-visual-cpp-activex-controls.md)|Describe cómo redistribuir una aplicación que utiliza controles ActiveX.|
|[Redistribuir la biblioteca MFC](../ide/redistributing-the-mfc-library.md)|Describe cómo redistribuir una aplicación que utiliza MFC.|
|[Redistribuir una aplicación ATL](../ide/redistributing-an-atl-application.md)|Describe cómo redistribuir una aplicación que usa ATL. A partir de Visual Studio 2012, no es necesaria ninguna biblioteca redistribuible para ATL.|
|[Ejemplos de implementación](../ide/deployment-examples.md)|Vínculos a ejemplos que muestran cómo implementar aplicaciones de Visual C++.|
|[Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)|Presenta los conceptos y las tecnologías de implementación de Visual C++.|