---
title: Compilar aplicaciones aisladas y ensamblados simultáneos de C/C++
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
ms.openlocfilehash: 8164ede1379e573b08f699cd55c199f6fa228823
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220976"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>Compilar aplicaciones aisladas y ensamblados simultáneos de C/C++

Visual Studio admite un modelo de implementación para aplicaciones de cliente de Windows basadas en la idea de [aplicaciones aisladas](/windows/desktop/SbsCs/isolated-applications) y [ensamblados en paralelo](/windows/desktop/SbsCs/about-side-by-side-assemblies-). De forma predeterminada, Visual Studio compila C todos nativo /C++ aplicaciones como aplicaciones aisladas que usan [manifiestos](/windows/desktop/sbscs/manifests) para describir sus dependencias en Visual C++ bibliotecas.

Compilar programas de C/C++ como aplicaciones aisladas presenta varias ventajas. Por ejemplo, a las aplicaciones aisladas no les afecta que otras aplicaciones de C/C++ instalen o desinstalen bibliotecas de Visual C++. Las bibliotecas de Visual C++ usadas por las aplicaciones aisladas, aun así, se pueden redistribuir en la carpeta local de la aplicación o instalándolas en la caché de ensamblados nativa (WinSxS). Sin embargo, el mantenimiento de las bibliotecas de Visual C++ para las aplicaciones ya implementadas se puede simplificar con un [archivo de configuración del publicador](/windows/desktop/SbsCs/publisher-configuration). Con el modelo de implementación de aplicaciones aisladas, es más fácil que las aplicaciones de C/C++ que se ejecutan en un equipo determinado usen la última versión de las bibliotecas de Visual C++ y, al mismo tiempo, se deja abierta la posibilidad de que los administradores del sistema y los autores de aplicaciones controlen el enlace explícito de versiones de las aplicaciones a las DLL dependientes.

En esta sección, se explica cómo compilar una aplicación de C/C++ como aplicación aislada y enlazarla a bibliotecas de Visual C++ con un manifiesto. La información de esta sección se aplica principalmente a nativo o administrado, C++ aplicaciones. Para obtener información acerca de la implementación nativa C++ las aplicaciones compiladas con Visual Studio, consulte [Redistribuir Visual C++ archivos](../windows/redistributing-visual-cpp-files.md).

## <a name="in-this-section"></a>En esta sección

[Conceptos de aplicaciones aisladas y ensamblados simultáneos](concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[Compilación de aplicaciones aisladas de C/C++](building-c-cpp-isolated-applications.md)

[Compilación de ensamblados simultáneos de C/C++](building-c-cpp-side-by-side-assemblies.md)

[Cómo: Compilar componentes COM de registro gratuito](how-to-build-registration-free-com-components.md)

[Cómo: Compilar aplicaciones aisladas que empleen componentes COM](how-to-build-isolated-applications-to-consume-com-components.md)

[Introducción a la generación de manifiestos para los programas de C/C++](understanding-manifest-generation-for-c-cpp-programs.md)

[Solución de problemas de aplicaciones aisladas y ensamblados simultáneos de C/C++](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>Secciones relacionadas

[Aplicaciones aisladas y ensamblados en paralelo](/windows/desktop/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[Implementar aplicaciones de escritorio](../windows/deploying-native-desktop-applications-visual-cpp.md)