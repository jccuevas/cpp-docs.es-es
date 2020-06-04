---
title: Compilar aplicaciones aisladas de C/C++
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: fbb553e3514ac3c32ee1e1f276dcb3e43d3a192e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493343"
---
# <a name="building-cc-isolated-applications"></a>Compilar aplicaciones aisladas de C/C++

Una aplicación aislada depende solo de ensamblados simultáneos y enlaza a sus dependencias mediante un manifiesto. No es necesario que la aplicación esté totalmente aislada para ejecutarse correctamente en Windows, pero si invierte en crear una aplicación totalmente aislada, ahorrará tiempo cuando necesite mantener la aplicación en el futuro. Para obtener más información sobre las ventajas de hacer que la aplicación esté totalmente aislada, vea [Aplicaciones aisladas](/windows/win32/SbsCs/isolated-applications).

Al compilar la aplicación nativa de C/C++ con Visual Studio, el sistema de proyectos de Visual Studio genera de forma predeterminada un archivo de manifiesto que describe las dependencias de la aplicación en bibliotecas de Visual Studio. Si estas son las únicas dependencias de la aplicación, se convertirá en una aplicación aislada en cuanto se vuelva a compilar con Visual Studio. Si la aplicación usa otras bibliotecas en tiempo de ejecución, puede que tenga que volver a compilar dichas bibliotecas como ensamblados simultáneos según los pasos descritos en [Compilar ensamblados simultáneos de C/C++](building-c-cpp-side-by-side-assemblies.md).

## <a name="see-also"></a>Vea también

[Conceptos de aplicaciones aisladas y ensamblados simultáneos](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
