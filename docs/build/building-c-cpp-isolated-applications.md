---
title: Compilar aplicaciones aisladas de C/C++
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: 42192ad9388a8e69b70947c20c6fa7ee428a2bb9
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220962"
---
# <a name="building-cc-isolated-applications"></a>Compilar aplicaciones aisladas de C/C++

Una aplicación aislada sólo depende de los ensamblados en paralelo y se enlaza a sus dependencias mediante un manifiesto. No es necesario para la aplicación sea totalmente aisladas para ejecutar correctamente en Windows; Sin embargo, al invertir en aislar totalmente su aplicación, puede ahorrar tiempo si necesita mantener la aplicación en el futuro. Para obtener más información sobre las ventajas de aislar totalmente su aplicación, consulte [aplicaciones aisladas](/windows/desktop/SbsCs/isolated-applications).

Al compilar la C nativa /C++ aplicación mediante Visual Studio, de forma predeterminada, el sistema del proyecto de Visual Studio genera un archivo de manifiesto que describe las dependencias de la aplicación en las bibliotecas de Visual Studio. Si se trata de las dependencias sola tiene la aplicación, se convertirá en una aplicación aislada en cuanto se vuelve a generar con Visual Studio. Si la aplicación utiliza otras bibliotecas en tiempo de ejecución, es posible que deba volver a generar las bibliotecas como ensamblados en paralelo siguiendo los pasos descritos en [creación de ensamblados de C o C++ por en paralelo](building-c-cpp-side-by-side-assemblies.md).

## <a name="see-also"></a>Vea también

[Conceptos de aplicaciones aisladas y ensamblados simultáneos](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
