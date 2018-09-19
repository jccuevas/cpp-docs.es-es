---
title: Conceptos de aplicaciones aisladas y ensamblados en paralelo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- side-by-side assemblies [C++]
- isolated assemblies [C++]
ms.assetid: 945a885f-cb3e-4c8a-a0b9-2c2e3e02cc50
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27ecefc5e448a1040e7eff3e45b94b0a31fbfc87
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710262"
---
# <a name="concepts-of-isolated-applications-and-side-by-side-assemblies"></a>Conceptos de aplicaciones aisladas y ensamblados simultáneos

Una aplicación se considera un [aplicación aislada](/windows/desktop/SbsCs/isolated-applications) si todos sus componentes son [ensamblados en paralelo](/windows/desktop/SbsCs/about-side-by-side-assemblies-). Un ensamblado simultáneo es una colección de recursos (un grupo de archivos DLL, clases de ventanas, servidores COM, bibliotecas de tipos o interfaces) que se implementan juntos y están disponibles para que una aplicación los use en tiempo de ejecución. Normalmente, un ensamblado simultáneo consta de uno o varios archivos DLL.

## <a name="shared-or-private"></a>Compartido o privado

Un ensamblado simultáneo puede ser compartido o privado. [Los ensamblados en paralelo compartidos](https://msdn.microsoft.com/library/aa375996.aspx) puede utilizarse en varias aplicaciones que se especifiquen en sus manifiestos una dependencia en el ensamblado. Puede haber varias versiones diferentes de un ensamblado en paralelo que se ejecuten al mismo tiempo en distintas aplicaciones. Un [ensamblado privado](/windows/desktop/SbsCs/about-private-assemblies-) es un ensamblado que se implementa junto con una aplicación para uso exclusivo de esa aplicación. Los ensamblados privados se instalan en la carpeta que contiene el archivo ejecutable de la aplicación o en una de sus subcarpetas.

## <a name="manifests-and-search-order"></a>Manifiestos y orden de búsqueda

Aplicaciones aisladas y ensamblados en paralelo se describen mediante [manifiestos](https://msdn.microsoft.com/library/aa375365). Un manifiesto es un documento XML que puede ser un archivo externo o que puede estar incrustado en una aplicación o un ensamblado como recurso. El archivo de manifiesto de una aplicación aislada se utiliza para administrar los nombres y las versiones de los ensamblados en paralelo compartidos con los que se debe enlazar la aplicación en tiempo de ejecución. El manifiesto de un ensamblado simultáneo especifica los nombres, versiones, recursos y ensamblados dependientes de los ensamblados en paralelo. En los ensamblados simultáneos compartidos, el manifiesto se instala en la carpeta %WINDIR%\WinSxS\Manifests\. En el caso de los ensamblados privados, es recomendable que incluya el manifiesto en el archivo DLL como recurso con el identificador 1. También puede asignar al ensamblado privado el nombre del archivo DLL. Para obtener más información, consulte [acerca de los ensamblados privados](/windows/desktop/SbsCs/about-private-assemblies-).

En tiempo de ejecución, Windows utiliza la información de ensamblado del manifiesto de la aplicación para buscar y cargar el ensamblado simultáneo correspondiente. Si una aplicación aislada especifica una dependencia de ensamblado, el sistema operativo buscará primero el ensamblado entre los ensamblados compartidos que se encuentran en la memoria caché de ensamblados en la carpeta %WINDIR%\WinSxS\ nativa. Si no se encuentra el ensamblado necesario, el sistema operativo buscará un ensamblado privado en una carpeta de la estructura de directorios de la aplicación. Para obtener más información, consulte [Assembly Searching Sequence](/windows/desktop/SbsCs/assembly-searching-sequence).

## <a name="changing-dependencies"></a>Cambiar las dependencias

Puede cambiar las dependencias de ensamblado en paralelo una vez implementada una aplicación mediante la modificación de la [archivos de configuración del publicador](/windows/desktop/SbsCs/publisher-configuration-files) y [los archivos de configuración de aplicación](/windows/desktop/SbsCs/application-configuration-files). Un archivo de configuración de publicador, también denominado archivo de directivas de editor, es un archivo XML que redirige las aplicaciones y ensamblados globalmente, pasando de una versión de un ensamblado simultáneo a otra versión del mismo ensamblado. Por ejemplo, puede cambiar una dependencia si se implementa una corrección de errores o una revisión de seguridad de un ensamblado simultáneo y desea redirigir todas las aplicaciones para que utilicen la versión establecida. Un archivo de configuración de aplicación es un archivo XML que redirige una aplicación específica de una versión de un ensamblado simultáneo a otra versión del mismo ensamblado. Puede utilizar un archivo de configuración de aplicación para redirigir una aplicación determinada de forma que utilice una versión de un ensamblado simultáneo diferente de la que se definió en el archivo de configuración del publicador. Para obtener más información, vea [Configuración](/windows/desktop/SbsCs/configuration).

## <a name="visual-c-libraries"></a>Bibliotecas de Visual C++

En Visual Studio 2005 y Visual Studio 2008, las bibliotecas redistribuibles, como ATL, MFC, CRT, C++ estándar, OpenMP y MSDIA, se implementaban como ensamblados en paralelo compartidos en la memoria caché de ensamblados nativa. En la versión actual, las bibliotecas redistribuibles utilizan la implementación central. De forma predeterminada, todas las aplicaciones compiladas con Visual C++ se compilan con el manifiesto incrustado en el archivo binario final y en el manifiesto se describen las dependencias de dicho archivo binario sobre las bibliotecas de Visual C++. Para entender la generación de manifiestos para las aplicaciones de Visual C++, vea [Understanding Manifest Generation for C/C++ Programs](../build/understanding-manifest-generation-for-c-cpp-programs.md). No se necesitan manifiestos en las aplicaciones que están vinculadas estáticamente a las bibliotecas que utilizan o que se usan en la implementación local. Para obtener más información sobre la implementación, vea [Deployment in Visual C++](../ide/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Vea también

[Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)