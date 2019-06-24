---
title: Implementación de CRT universal
ms.date: 05/11/2018
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
ms.openlocfilehash: 1f6e685cca65c4b31ac2e6147341c4b5a3fe8228
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344461"
---
# <a name="universal-crt-deployment"></a>Implementación de CRT universal

Desde Visual Studio .NET hasta Visual Studio 2013, en cada versión principal del compilador y las herramientas de C++ se ha incluido una versión nueva e independiente de la Biblioteca en tiempo de ejecución de C (CRT) de Microsoft. Estas versiones independientes de la biblioteca CRT eran independientes entre ellas y, a diferentes niveles, incompatibles. Por ejemplo, la biblioteca CRT que se usaba en Visual Studio 2012 era la versión 11, denominada msvcr110.dll, y la biblioteca CRT que se usaba en Visual Studio 2013 era la versión 12, denominada msvcr120.dll. A partir de Visual Studio 2015, ya no es el caso. En Visual Studio 2015 y versiones posteriores de Visual Studio se usa CRT universal.

CRT Universal es un componente de sistema operativo Microsoft Windows, incluido como parte del sistema operativo de Windows 10. Está disponible para los sistemas operativos anteriores, Windows Vista a través de Windows 8.1, mediante Windows Update. Se admite la implementación local de CRT Universal, con algunas restricciones.

## <a name="central-deployment"></a>Implementación central

El método preferido para instalar de forma centralizada CRT universal consiste en usar Microsoft Windows Update. CRT universal es una actualización recomendada para todos los sistemas operativos Microsoft Windows compatibles, por lo que de forma predeterminada, en la mayoría de los equipos se instala como parte del proceso de actualización habitual. La versión inicial de CRT Universal era [KB2999226](https://support.microsoft.com/kb/2999226). Se realizó una actualización posterior con varias correcciones de errores en [KB3118401](https://support.microsoft.com/kb/3118401), y ha habido actualizaciones adicionales con nuevas características y correcciones de errores más. Para obtener las actualizaciones más recientes, busque "tiempo de ejecución de C universal" o "CRT universal" en [support.microsoft.com](https://support.microsoft.com).

No en todos los equipos Microsoft Windows se instalan las actualizaciones periódicamente mediante Windows Update, y es posible que en algunos no se instalen todas las actualizaciones recomendadas. Para admitir el uso de aplicaciones integradas mediante el uso de Visual Studio 2015 y versiones posteriores C++ conjuntos de herramientas en esas máquinas, existen los archivos redistribuibles de CRT Universal para la distribución sin conexión. Desde uno de los vínculos KB anteriores se pueden descargar los archivos redistribuibles. El paquete redistribuible de CRT Universal requiere que la máquina se ha actualizado al service pack actual. Por tanto, por ejemplo, el paquete redistribuible para Windows 7 solo se instalará en Windows 7 SP1, no en Windows 7 RTM.

Dado que el CRT Universal es una dependencia fundamental de la C++ bibliotecas, el objeto Visual C++ (VCRedist) redistribuible instala la versión inicial de CRT Universal (versión 10.0.10240) en las máquinas que aún no tienen ninguno instalado. Esta versión es suficiente para satisfacer la C++ las dependencias de biblioteca. Si la aplicación depende de una versión más reciente de CRT Universal, debe usar Windows Update para poner el equipo completamente actualizado o instalan esa versión explícitamente. Es mejor instalar el tiempo de ejecución Universal C a través de Windows Update o un archivo MSU antes de instalar VCRedist, para evitar varios posibles necesarios se reinicia.

No todos los sistemas operativos son aptos para la más reciente Universal C Runtime a través de Windows Update. En Windows 10, la versión implementada de forma centralizada coincide con la versión del sistema operativo. Además, para actualizar el tiempo de ejecución de C Universal debe actualizar el sistema operativo. Para Windows Vista a través de Windows 8.1, la más reciente disponible Universal C Runtime actualmente se basa en la versión incluida en la actualización de aniversario de Windows 10, con correcciones adicionales (versión 10.0.14393).

## <a name="local-deployment"></a>Implementación local

Se admite la implementación local de aplicación de CRT universal, aunque no se recomienda por motivos de rendimiento y seguridad. Los archivos DLL para la implementación local se incluyen como parte de Windows SDK, en el subdirectorio Windows Kits\\10\\Redist\\ucrt\\DLLs, por cada arquitectura de equipo. Los archivos DLL necesarios incluyen ucrtbase.dll y un conjunto de archivos DLL de reenviador APISet denominado api-ms-win-\*.dll. Varía según el conjunto de archivos DLL necesarios en cada sistema operativo. Se recomienda incluir todos los archivos DLL cuando se implementa localmente.

En la implementación local hay que tener en cuenta dos restricciones:

- En Windows 10, siempre se usa CRT universal en el directorio del sistema, incluso si una aplicación incluye una copia local de la aplicación de CRT universal. Es cierto incluso cuando la copia local es más reciente, dado que el CRT Universal es un componente del sistema operativo core en Windows 10.

- En las versiones de Windows anteriores a Windows 8, CRT Universal no puede empaquetarse localmente con un complemento, si se encuentra en un directorio distinto de la aplicación principal ejecutable. En este caso, los archivos DLL de reenviador APISet no pueden resolver correctamente el archivo ucrtbase.dll. Algunas soluciones alternativas recomendadas son las siguientes:

  - Vincular CRT universal de forma estática,
  - Implementar CRT universal de forma centralizada, o bien
  - Colocar los archivos de CRT universal en el mismo directorio que la aplicación.

## <a name="deployment-on-microsoft-windows-xp"></a>Implementación en Microsoft Windows XP

En Visual Studio 2015 y Visual Studio 2017 se sigue admitiendo el desarrollo de software para su uso en Microsoft Windows XP. Para admitir este desarrollo, una versión de CRT Universal funciona en Microsoft Windows XP. El soporte técnico principal o ampliado para el sistema operativo Microsoft Windows XP ya ha finalizado, por lo que la implementación central de CRT universal en Microsoft Windows XP es diferente a la de otros sistemas operativos.

Cuando el objeto Visual C++ redistributable está instalado en Windows XP, instala directamente el CRT Universal y todas sus dependencias en el directorio del sistema. No instale ni dependen de cualquier actualización de Windows. Los módulos de combinación redistribuibles, los archivos Microsoft_VC*versión*_CRT_\*.msm, hacen lo mismo.

La implementación local de CRT universal en Windows XP es la misma que la de otros sistemas operativos compatibles.

## <a name="see-also"></a>Vea también

- [Implementación en Visual C++](deployment-in-visual-cpp.md)
