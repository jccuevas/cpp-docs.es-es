---
title: Actualizar código a CRT universal
ms.date: 03/31/2017
ms.assetid: eaf34c1b-da98-4058-a059-a10db693a5ce
ms.openlocfilehash: bdf1615d47361654e9690977520d01c332098438
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58898770"
---
# <a name="upgrade-your-code-to-the-universal-crt"></a>Actualizar código a CRT universal

En Visual Studio 2015, se ha refactorizado la Biblioteca en tiempo de ejecución de C (CRT) de Microsoft. La biblioteca estándar de C, las extensiones POSIX y las funciones, las macros y las variables globales específicas de Microsoft se han movido a una nueva biblioteca: la biblioteca en tiempo de ejecución de C universal (CRT universal o UCRT). Los componentes específicos del compilador de CRT se han movido a una nueva biblioteca de vcruntime.

El UCRT ahora es un componente de Windows y se incluye en Windows 10. UCRT admite un ABI estable basado en convenciones de llamada de C y se ajusta al estándar ISO C99, con solo unas pocas excepciones. Ya no está vinculada a una versión concreta del compilador. UCRT se puede usar en cualquier versión de Windows compatible con Visual Studio 2015 o Visual Studio 2017. La ventaja es que ya no es necesario actualizar las compilaciones destinadas a una nueva versión de CRT con cada actualización de Visual Studio.

Con esta refactorización se han cambiado los nombres o las ubicaciones de muchos archivos de encabezado de CRT, archivos de biblioteca y redistribuibles, así como los métodos de implementación necesarios para el código. Además, muchas funciones y macros de UCRT se han agregado o cambiado para mejorar la conformidad con los estándares. Para aprovechar estos cambios, se deben actualizar el código existente y los sistemas de compilación de proyectos.

## <a name="where-to-find-the-universal-crt-files"></a>Dónde encontrar los archivos de CRT universal

Como componente de Windows, los encabezados y los archivos de biblioteca UCRT ahora forman parte del kit de desarrollo de software (SDK) de Windows. Cuando se instala Visual Studio, también se instalan los elementos del SDK de Windows necesarios para usar UCRT. El instalador de Visual Studio agrega las ubicaciones de los encabezados UCRT, las bibliotecas y los archivos DLL a las rutas de acceso predeterminadas empleadas por el sistema de compilación de proyectos de Visual Studio. Al actualizar los proyectos de Visual C++, si usan la configuración de proyecto predeterminada, el IDE busca automáticamente las nuevas ubicaciones de los archivos de encabezado y el vinculador usa automáticamente las nuevas bibliotecas predeterminadas UCRT y vcruntime. De forma similar, si usa un símbolo del sistema para desarrolladores para las compilaciones de línea de comandos, las variables de entorno que contienen rutas de acceso para encabezados y bibliotecas se actualizan y además funcionan automáticamente.

Los archivos de encabezado de la biblioteca estándar de C ahora se encuentran en el SDK de Windows en una carpeta de inclusión en un directorio específico de la versión del SDK. Una ubicación típica de los archivos de encabezado es el directorio Archivos de programa o Archivos de programa (x86) en Windows Kits\\10\\Include\\_sdk-version_\\ucrt, donde _sdk-version_ corresponde a una versión o actualización de Windows, por ejemplo, 10.0.14393.0 para la Actualización de aniversario de Windows 10.

Las bibliotecas estáticas de UCRT y las bibliotecas de vínculos dinámicos de código auxiliar se encuentran en el directorio Archivos de programa o Archivos de programa (x86) en Windows Kits\\10\\Lib\\_sdk-version_\\ucrt\\_architecture_, donde _architecture_ es ARM, x86 o X64. Las bibliotecas estáticas comercial y de depuración son libucrt.lib y libucrtd.lib, y las bibliotecas para los archivos DLL de UCRT son ucrt.lib y ucrtd.lib.

Los archivos DLL UCRT comerciales y de depuración se encuentran en ubicaciones independientes. Los archivos DLL comerciales son redistribuibles y pueden encontrarse en el directorio Archivos de programa o Archivos de programa (x86) en Kits de Windows \\10\\Redist\\ucrt\\DLLs\\_arquitectura_\. Las bibliotecas UCRT de depuración no son redistribuibles y pueden encontrarse en el directorio Archivos de programa o Archivos de programa (x86) en Kits de Windows \\10\\bin\\_arquitectura_\\carpeta ucrt.

La biblioteca de compatibilidad en tiempo de ejecución específica del compilador de C y C++, **vcruntime**, contiene el código necesario para admitir el inicio del programa y características como el control de excepciones y los valores intrínsecos. La biblioteca y sus archivos de encabezado todavía se encuentran en la carpeta de Microsoft Visual Studio específica de la versión del directorio Archivos de programa o Archivos de programa (x86). En Visual Studio 2017, los encabezados se encuentran en Microsoft Visual Studio\\2017\\_edition_\\VC\\Tools\\MSVC\\_lib-version_\\include y las bibliotecas de vínculos se encuentran en Microsoft Visual Studio\\2017\\_edition_\\VC\\Tools\\MSVC\\_lib-version_\\lib\\_architecture_, donde _edition_ es la edición de Visual Studio instalada, _lib-version_ es la versión de las bibliotecas y _architecture_ es la arquitectura del procesador. Las bibliotecas de vínculos para OneCore y la tienda también se encuentran en la carpeta de bibliotecas. Las versiones comercial y de depuración de la biblioteca estática son libvcruntime.lib y libvcruntimed.lib. Las bibliotecas de vínculos dinámicos de código auxiliar comercial y de depuración son vcruntime.lib y vcruntimed.lib, respectivamente.

Al actualizar los proyectos de Visual C++, si ha establecido la propiedad del **Enlazador** del proyecto **Omitir todas las bibliotecas predeterminadas** en **Sí** o si usa la opción `/NODEFAULTLIB` del enlazador en la línea de comandos, debe actualizar la lista de bibliotecas para incluir las nuevas bibliotecas refactorizadas. Reemplace la biblioteca CRT anterior, por ejemplo, libcmt.lib, libcmtd.lib, msvcrt.lib o msvcrtd.lib, por las bibliotecas refactorizadas equivalentes. Para más información sobre las bibliotecas concretas que se van a usar, vea [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md).

## <a name="deployment-and-redistribution-of-the-universal-crt"></a>Implementación y redistribución de CRT universal

Dado que UCRT ahora es un componente del sistema operativo Microsoft Windows, se incluye como parte del sistema operativo en Windows 10 y está disponible a través de Windows Update para sistemas operativos anteriores, de Windows Vista a Windows 8.1. Hay una versión redistribuible disponible para Windows XP. Como componente del sistema operativo, Windows Update administra las actualizaciones y el mantenimiento de UCRT independientemente de las versiones de Visual Studio y el Compilador de Microsoft Visual C++. Puesto que UCRT es un componente de Windows, por motivos de seguridad y de facilidad de las actualizaciones, así como por el menor tamaño de imagen, se recomienda encarecidamente la implementación central de UCRT para la aplicación.

UCRT se puede usar en cualquier versión de Windows compatible con Visual Studio 2015 o Visual Studio 2017. Se puede redistribuir mediante un paquete vcredist para versiones compatibles de Windows que no sean Windows 10. Los paquetes vcredist incluyen los componentes de UCRT y los instalan automáticamente en los sistemas operativos Windows que no los tienen instalados de forma predeterminada. Para obtener más información, consulte [Redistribuir archivos de Visual C++](../windows/redistributing-visual-cpp-files.md).

Se admite la implementación local de aplicación de UCRT, aunque no se recomienda por motivos de rendimiento y seguridad. Los archivos DLL para la implementación local de aplicación se incluyen como parte del SDK de Windows, en el subdirectorio **redist**. Los archivos DLL necesarios incluyen ucrtbase.dll y un conjunto de archivos DLL **reenviador APISet** denominado api-ms-win-_subset_.dll. El conjunto de archivos DLL necesario en cada sistema operativo varía, por lo que se recomienda incluir todos los archivos DLL cuando se use la implementación local de aplicación. Para obtener detalles adicionales y advertencias sobre la implementación local de aplicación, vea [Implementación en Visual C++](../windows/deployment-in-visual-cpp.md).

## <a name="changes-to-the-universal-crt-functions-and-macros"></a>Cambios en las funciones y macros de CRT universal

En UCRT se han agregado o actualizado muchas funciones para mejorar la conformidad con ISO C99 y para resolver problemas de calidad y seguridad del código. En algunos casos, esto ha exigido cambios importantes en la biblioteca. Si el código se compilaba correctamente al usar una versión anterior de CRT pero se rompe al compilar con UCRT, debe cambiar el código para aprovechar estas actualizaciones y características. Para obtener una lista detallada de los cambios y actualizaciones importantes en CRT realizados en CRT universal, vea la sección [Biblioteca de C en tiempo de ejecución (CRT)](visual-cpp-change-history-2003-2015.md#BK_CRT) del historial de cambios de Visual C++. Incluye una lista de encabezados afectados y funciones que puede usar para identificar los cambios necesarios en el código.

## <a name="see-also"></a>Vea también

[Guía de migración y actualización de Visual C++](visual-cpp-porting-and-upgrading-guide.md)<br/>
[Información general sobre posibles problemas de actualización (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Actualizar proyectos desde versiones anteriores de Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Historial de cambios en Visual C++ 2003-2015](visual-cpp-change-history-2003-2015.md)<br/>
[Mejoras de conformidad de C++ en Visual Studio](../overview/cpp-conformance-improvements.md)
