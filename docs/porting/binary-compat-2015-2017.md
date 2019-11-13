---
title: C++compatibilidad binaria entre Visual Studio 2015, 2017 y 2019
description: Describe cómo funciona la compatibilidad binaria C++ entre archivos compilados en Visual Studio 2015, 2017 y 2019. Un paquete redistribuible de Microsoft Visual C++ funciona para las tres versiones.
ms.date: 11/11/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: 118ad0a32d5dc8c344967f9a67f2d5b05aa806c0
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965565"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-2017-and-2019"></a>C++compatibilidad binaria entre Visual Studio 2015, 2017 y 2019

Los conjuntos C++ de herramientas del compilador de Microsoft (MSVC) en Visual Studio 2013 y versiones anteriores no garantizan la compatibilidad binaria entre versiones. No se pueden vincular archivos objeto, bibliotecas estáticas, bibliotecas dinámicas y ejecutables compilados por versiones diferentes. Los Abi, los formatos de objetos y las bibliotecas en tiempo de ejecución no son compatibles.

Hemos cambiado este comportamiento en Visual Studio 2015, 2017 y 2019. Las bibliotecas en tiempo de ejecución y las aplicaciones compiladas por cualquiera de estas versiones del compilador son compatibles con archivos binarios. Se refleja en el C++ número principal del conjunto de herramientas, que es 14 para las tres versiones. (La versión del conjunto de herramientas es V140 para Visual Studio 2015, v141 para 2017 y v142 para 2019). Supongamos que tiene bibliotecas de terceros compiladas por Visual Studio 2015. Todavía puede usarlos en una aplicación compilada con Visual Studio 2017 o 2019. No es necesario volver a compilar con un conjunto de herramientas coincidente. La versión más reciente del paquete redistribuible de Microsoft Visual C++ (el redistribuible) funciona para todos ellos.

Hay una excepción a esta regla: las bibliotecas estáticas o los archivos de objeto compilados con el `/GL` conmutador del compilador *no son* compatibles con binarios en las versiones.

El redistribuible que usa la aplicación tiene una restricción importante de compatibilidad binaria. Se aplica cuando se mezclan archivos binarios compilados con diferentes versiones compatibles del conjunto de herramientas. La versión redistribuible debe ser al menos tan nueva como el conjunto de herramientas más reciente usado por cualquier componente de la aplicación.

## <a name="upgrade-the-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>Actualización de Microsoft Visual C++ Redistributable desde visual Studio 2015 o 2017 a visual Studio 2019

Hemos mantenido el mismo número de C++ versión principal de Microsoft Visual Redistributable para Visual Studio 2015, 2017 y 2019. Esto significa que solo se puede instalar una instancia del paquete redistribuible a la vez. Una versión más reciente sobrescribe cualquier versión anterior que ya esté instalada. Por ejemplo, una aplicación puede instalar el paquete redistribuible de Visual Studio 2015. Después, otra aplicación instala el paquete redistribuible desde Visual Studio 2019. La versión 2019 sobrescribe la versión anterior, pero dado que son compatibles con el formato binario, la aplicación anterior sigue funcionando bien. Nos aseguramos de que la versión más reciente del paquete redistribuible tiene todas las características más recientes, las actualizaciones de seguridad y las correcciones de errores. Esta es la razón por la que siempre se recomienda actualizar a la última versión disponible.

Del mismo modo, no se puede instalar un paquete redistribuible más antiguo cuando ya está instalada una versión más reciente. El instalador informa de un error si lo intenta. Verá un error similar al siguiente si instala el paquete redistribuible 2015 o 2017 en un equipo que ya tiene la versión 2019:

```Output
0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.
```

Este error es así por diseño. Se recomienda mantener instalada la versión más reciente. Asegúrese de que el instalador puede recuperarse de este error de forma silenciosa.

## <a name="see-also"></a>Vea también

[Historial C++ de cambios visuales](../porting/visual-cpp-change-history-2003-2015.md)\
[Las descargas más recientes C++ del paquete redistribuible de Visual](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)
