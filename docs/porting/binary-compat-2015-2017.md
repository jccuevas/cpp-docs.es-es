---
title: C++compatibilidad binaria entre Visual Studio 2015 y Visual Studio 2019
description: Describe cómo funciona la compatibilidad binaria C++ entre archivos compilados en Visual Studio 2015, 2017 y 2019. Un paquete redistribuible de Microsoft Visual C++ funciona para las tres versiones.
ms.date: 11/07/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: e41c34abe25deefe100f525044faeac0b0c3054a
ms.sourcegitcommit: eb254b4462a58d219376ff501bf768bd1adc07ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2019
ms.locfileid: "73912878"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>C++compatibilidad binaria entre Visual Studio 2015 y Visual Studio 2019

En Microsoft Visual Studio 2013 y versiones anteriores, no se garantiza la compatibilidad binaria entre los archivos objeto (obj), las bibliotecas estáticas (bibliotecas), las bibliotecas de vínculos dinámicos (dll) y los ejecutables (exe) compilados con las diferentes versiones del conjunto de herramientas del compilador. y bibliotecas en tiempo de ejecución.

En Visual Studio 2015 y versiones posteriores, el número principal del conjunto de herramientas de C++ es 14 (v140 en Visual Studio 2015, v141 en Visual Studio 2017 y v142 en Visual Studio 2019). Esta numeración refleja el hecho de que las bibliotecas en tiempo de ejecución y las aplicaciones compiladas con cualquiera de estas versiones del compilador son compatibles con binario. Por lo tanto, si tiene una biblioteca de terceros que se compiló con Visual Studio 2015, no tiene que volver a compilarla para usarla desde una aplicación que se compiló con Visual Studio 2017 o Visual Studio 2019.

La única excepción a esta regla es que las bibliotecas estáticas o los archivos objeto compilados con el `/GL` modificador del compilador *no* son compatibles con binario.

Cuando se mezclan archivos binarios compilados con diferentes versiones C++ compatibles del conjunto de herramientas de Microsoft C++ (MSVC), el paquete redistribuible de visual en el que se ejecuta la aplicación no puede ser más antiguo que cualquiera de las versiones del conjunto de herramientas usadas para compilar la aplicación o las bibliotecas que consume.

## <a name="upgrade-the-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>Actualización de Microsoft Visual C++ Redistributable desde visual Studio 2015 o 2017 a visual Studio 2019

Dado que se ha conservado la compatibilidad binaria y se ha mantenido la versión principal (14) C++ la misma en Microsoft Visual Redistributable para visual Studio 2015, 2017 y 2019, solo se puede C++ instalar una versión del paquete redistribuible de visual en cualquier momento. Una versión más reciente sobrescribe una versión anterior que ya está instalada. Si tiene el redistribuible visual C++ de visual Studio 2015 o 2017 y, posteriormente, instala visual Studio 2019, la versión de 2019 sobrescribe la versión anterior. Dado que nos aseguramos de que la última versión tiene todas las características más recientes y correcciones de errores (incluidas las correcciones de seguridad), siempre recomendamos que actualice a la última versión disponible.

Del mismo modo, no se le permite instalar una versión anterior del C++ paquete redistribuible de visual en una máquina en la que ya esté instalada una versión más reciente. La instalación del C++ paquete redistribuible de visual Studio 2015 o 2017 en un equipo que ya tiene la versión 2019 desencadena un error de instalación. El error es similar al siguiente:

```Output
0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.
```

Este error es así por diseño. Se recomienda mantener instalada la versión más reciente.

## <a name="see-also"></a>Vea también

* [Historial de cambios en Visual C++](../porting/visual-cpp-change-history-2003-2015.md)
* [Las descargas más recientes C++ del paquete redistribuible de Visual](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 
