---
title: Compilar aplicaciones aisladas de C/C++
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: fbb553e3514ac3c32ee1e1f276dcb3e43d3a192e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493343"
---
# <a name="building-cc-isolated-applications"></a>Compilar aplicaciones aisladas de C/C++

Una aplicación aislada depende solo de los ensamblados en paralelo y se enlaza a sus dependencias mediante un manifiesto. No es necesario que la aplicación esté totalmente aislada para ejecutarse correctamente en Windows. sin embargo, al invertir en la aplicación totalmente aislada, puede ahorrar tiempo si necesita dar servicio a la aplicación en el futuro. Para obtener más información sobre las ventajas de que la aplicación esté totalmente aislada, vea [aplicaciones aisladas](/windows/win32/SbsCs/isolated-applications).

Al compilar la aplicación CC++ /nativa con Visual Studio, de forma predeterminada el sistema de proyectos de Visual Studio genera un archivo de manifiesto que describe las dependencias de la aplicación en las bibliotecas de Visual Studio. Si estas son las únicas dependencias de la aplicación, se convierte en una aplicación aislada en cuanto se vuelve a generar con Visual Studio. Si la aplicación usa otras bibliotecas en tiempo de ejecución, puede que tenga que volver a compilar esas bibliotecas como ensamblados en paralelo siguiendo los pasos descritos en creación de ensamblados de [C/C++ simultáneos](building-c-cpp-side-by-side-assemblies.md).

## <a name="see-also"></a>Vea también

[Conceptos de aplicaciones aisladas y ensamblados simultáneos](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
