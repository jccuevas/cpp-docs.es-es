---
title: Compilar aplicaciones aisladas y ensamblados simultáneos de C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
ms.openlocfilehash: da8bd6d583d6f9d714853e545979d54ddcb79ce5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429176"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>Compilar aplicaciones aisladas y ensamblados simultáneos de C/C++

Visual C++ admite un modelo de implementación para aplicaciones cliente de Windows que se basa en la idea de las [aplicaciones aisladas](/windows/desktop/SbsCs/isolated-applications) y los [ensamblados en paralelo](/windows/desktop/SbsCs/about-side-by-side-assemblies-). De forma predeterminada, Visual C++ compila todas las aplicaciones nativas de C/C++ como aplicaciones aisladas que usan [manifiestos](https://msdn.microsoft.com/library/aa375365) para describir sus dependencias en las bibliotecas de Visual C++.

Compilar programas de C/C++ como aplicaciones aisladas presenta varias ventajas. Por ejemplo, a las aplicaciones aisladas no les afecta que otras aplicaciones de C/C++ instalen o desinstalen bibliotecas de Visual C++. Las bibliotecas de Visual C++ usadas por las aplicaciones aisladas, aun así, se pueden redistribuir en la carpeta local de la aplicación o instalándolas en la caché de ensamblados nativa (WinSxS). Sin embargo, el mantenimiento de las bibliotecas de Visual C++ para las aplicaciones ya implementadas se puede simplificar con un [archivo de configuración del publicador](/windows/desktop/SbsCs/publisher-configuration). Con el modelo de implementación de aplicaciones aisladas, es más fácil que las aplicaciones de C/C++ que se ejecutan en un equipo determinado usen la última versión de las bibliotecas de Visual C++ y, al mismo tiempo, se deja abierta la posibilidad de que los administradores del sistema y los autores de aplicaciones controlen el enlace explícito de versiones de las aplicaciones a las DLL dependientes.

En esta sección, se explica cómo compilar una aplicación de C/C++ como aplicación aislada y enlazarla a bibliotecas de Visual C++ con un manifiesto. La información de esta sección se aplica, principalmente, a las aplicaciones de Visual C++ nativas o no administradas. Para obtener información sobre la implementación de aplicaciones nativas compiladas con Visual C++, vea [Redistributing Visual C++ Files](../ide/redistributing-visual-cpp-files.md).

## <a name="in-this-section"></a>En esta sección

[Conceptos de aplicaciones aisladas y ensamblados simultáneos](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[Compilación de aplicaciones aisladas de C/C++](../build/building-c-cpp-isolated-applications.md)

[Compilación de ensamblados simultáneos de C/C++](../build/building-c-cpp-side-by-side-assemblies.md)

[Procedimiento para compilar componentes COM de registro gratuito](../build/how-to-build-registration-free-com-components.md)

[Procedimiento para compilar aplicaciones aisladas que empleen componentes COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)

[Introducción a la generación de manifiestos para los programas de C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)

[Solución de problemas de aplicaciones aisladas y ensamblados simultáneos de C/C++](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>Secciones relacionadas

[Aplicaciones aisladas y ensamblados en paralelo](/windows/desktop/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)