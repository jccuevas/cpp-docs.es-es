---
title: Implementación de CRT universal | Documentos de Microsoft
ms.custom: ''
ms.date: 05/11/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20006118d4bf27c379b78b84dc8807a4fd6c5e6c
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="universal-crt-deployment"></a>Implementación de CRT universal

Desde Visual Studio .NET a través de Visual Studio 2013, cada versión principal de las herramientas y el compilador de C++ incluye una nueva versión independiente de la biblioteca en tiempo de ejecución de C de Microsoft (CRT). Estas versiones independientes de CRT eran independientes from y to diferentes grados, incompatibles entre ellos. Por ejemplo, la biblioteca de CRT que se usa en Visual Studio 2012 estaba msvcr110.dll 11, con nombre de versión y CRT utilizado por Visual Studio 2013 era la versión 12, con nombre msvcr120.dll. A partir de Visual Studio 2015, esto no es el caso. Visual Studio 2015 y versiones posteriores de Visual Studio todos los usan CRT Universal.

CRT Universal es un componente del sistema operativo Microsoft Windows. Se incluye como parte del sistema operativo en Windows 10 y está disponible para los sistemas operativos anteriores, Windows Vista a través de Windows 8.1, mediante Windows Update. Además, se admite la implementación local de CRT Universal, con algunas restricciones.

## <a name="central-deployment"></a>Implementación central

El método preferido para instalar de forma centralizada el CRT Universal consiste en utilizar Microsoft Windows Update. CRT Universal es que una actualización recomendado para todos los admite sistemas operativos Microsoft Windows, de forma que predeterminada, la mayoría de las máquinas instalación como parte del proceso de actualización regular. La versión inicial de la biblioteca CRT Universal fue [KB2999226](https://support.microsoft.com/en-us/kb/2999226); se realizó una actualización posterior con varias correcciones de errores en [KB3118401](https://support.microsoft.com/en-us/kb/3118401), y ha habido actualizaciones adicionales con nuevas características y correcciones de errores adicional. Para las actualizaciones más recientes, busque [support.microsoft.com](https://support.microsoft.com) para Universal en tiempo de ejecución de C o CRT Universal.

No todos los equipos de Microsoft Windows con regularidad instalan actualizaciones mediante el uso de Windows Update y algunos no pueden instalar todas las actualizaciones recomendadas. Para admitir el uso de las aplicaciones compiladas con la Visual Studio 2015 y posterior conjuntos de herramientas de C++ en esos equipos, hay paquetes redistribuibles de CRT Universal disponibles para la distribución sin conexión. Los archivos redistribuibles se pueden descargar desde uno de los vínculos KB anteriores. Tenga en cuenta que los archivos redistribuibles de CRT Universal requieren que el equipo se ha actualizado con el service pack actual. Por lo tanto, por ejemplo, el paquete redistribuible para Windows 7 solo se instalará en Windows 7 SP1, no Windows 7 RTM.

Dado que el CRT Universal es una dependencia fundamental de las bibliotecas de C++, el Visual C++ redistributable (VCRedist) instala una versión de base de CRT Universal en equipos que no tienen una versión ya instalada, suficiente para satisfacer la biblioteca de C++ dependencias. Si la aplicación depende de una versión más reciente de CRT Universal, debe instalar explícitamente que la versión más reciente. Es mejor instalarlos antes de instalar VCRedist, para evitar posibles múltiples necesarios se reinicia.

## <a name="local-deployment"></a>Implementación local

La implementación local de CRT Universal se admite, pero no se recomienda para los motivos de rendimiento y seguridad.  Los archivos DLL para la implementación local se incluyen como parte del SDK de Windows, en los Kits de Windows\\10\\Redist\\ucrt\\subdirectorio de archivos DLL, arquitectura de equipo. Los archivos DLL necesarios incluyen ucrtbase.dll y un conjunto de reenviador APISet dll denominadas api-ms-win -\*.dll. Varía según el conjunto de archivos DLL necesarios en cada sistema operativo, por lo que se recomienda encarecidamente que incluya todos los archivos DLL cuando se implementa localmente.

Hay dos restricciones en una implementación local para tener en cuenta:

- En Windows 10, CRT Universal en el directorio del sistema se utiliza siempre, incluso si una aplicación incluye una copia local de la aplicación de la biblioteca CRT Universal. Esto ocurre incluso si la copia local de CRT Universal es más reciente. Esto es porque el CRT Universal es un componente del sistema operativo core en Windows 10.

- En las versiones de Windows anteriores a Windows 8, CRT Universal no se pueden empaquetar localmente con un complemento que se encuentra en un directorio distinto al directorio que contiene el archivo ejecutable principal de la aplicación. El reenviador de APISet archivos DLL son no se puede resolver el ucrtbase.dll correctamente en este caso. Algunas soluciones alternativas recomendadas son:

  - Las funciones de CRT Universal, se vinculan estáticamente
  - Implementar de forma centralizada las funciones de CRT Universal, o
  - Coloque los archivos CRT Universal en el mismo directorio que la aplicación.

## <a name="deployment-on-microsoft-windows-xp"></a>Implementación en Microsoft Windows XP

Visual Studio 2015 y Visual Studio de 2017 continuarán sustentar el desarrollo de software para su uso en Microsoft Windows XP. Para ello, una versión de CRT Universal funciona en Microsoft Windows XP. El sistema operativo Microsoft Windows XP ya no es en soporte estándar o extendida, por lo que la implementación central de CRT Universal en Microsoft Windows XP es diferente de otros sistemas operativos.

Cuando se instala el paquete redistribuible de Visual C++ en Windows XP, directamente instala el CRT Universal y todas sus dependencias en el directorio del sistema, sin necesidad de instalar o según una actualización de Windows. Los módulos de combinación redistribuibles, el Microsoft_VC*versión*_CRT_\*archivos .msm, haga lo mismo.

La implementación local de CRT Universal en Windows XP es igual que en otros sistemas operativos compatibles.

## <a name="see-also"></a>Vea también

- [Implementación en Visual C++](deployment-in-visual-cpp.md)
