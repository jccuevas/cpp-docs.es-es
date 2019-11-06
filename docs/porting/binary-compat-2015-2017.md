---
title: C++compatibilidad binaria entre Visual Studio 2015 y Visual Studio 2019
ms.date: 10/17/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: 761f6187a8b30ecb4214821c7f91d1b26e9c647c
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627022"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>C++compatibilidad binaria entre Visual Studio 2015 y Visual Studio 2019

En Visual Studio 2013 y versiones anteriores, no se garantizaba la compatibilidad binaria entre archivos objeto (OBJ), bibliotecas estáticas (LIB), bibliotecas dinámicas (DLL) y archivos ejecutables (EXE) compilados con versiones diferentes del conjunto de herramientas del compilador y las bibliotecas de tiempo de ejecución. 

En Visual Studio 2015 y versiones posteriores, el número principal del conjunto de herramientas de C++ es 14 (v140 en Visual Studio 2015, v141 en Visual Studio 2017 y v142 en Visual Studio 2019). Esto refleja el hecho de que las bibliotecas en tiempo de ejecución y las aplicaciones compiladas con cualquiera de estas versiones del compilador son compatibles con binarios. Esto significa que, si tiene una biblioteca de terceros compilada con Visual Studio 2015, no tendrá que volver a compilarla para consumirla desde una aplicación compilada con Visual Studio 2017 o con Visual Studio 2019.

La única excepción a esta regla es que las bibliotecas estáticas o los archivos objeto compilados con el modificador del compilador `/GL` no tienen compatibilidad binaria.

Cuando se mezclan archivos binarios compilados con diferentes versiones compatibles del conjunto de C++ herramientas de MSVC, el redistribuible visual en el que se ejecuta la aplicación no puede ser más antiguo que cualquiera de las versiones del conjunto de herramientas usadas para compilar la aplicación o las bibliotecas que consume.

## <a name="upgrade-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>Actualización de Microsoft C++ visual Redistributable desde visual Studio 2015 o 2017 a visual Studio 2019

Dado que se ha conservado la compatibilidad binaria y se ha conservado la versión principal ( C++ 14) del mismo para el paquete redistribuible de visual Studio 2015, 2017 y 2019 C++ , solo se puede instalar una versión del paquete redistribuible de visual en cualquier momento. Una versión más reciente sobrescribirá una versión anterior instalada. Si tiene el redistribuible visual C++ de visual Studio 2015 o 2017 y, posteriormente, instala 2019, la versión 2019 sobrescribirá una versión anterior. Dado que garantizamos que la última versión tendrá todas las características más recientes y correcciones de errores, incluidas las correcciones de seguridad, siempre recomendamos actualizar a la última versión disponible.

Del mismo modo, no se permite la instalación de una versión C++ anterior del paquete redistribuible de visual en un equipo en el que ya existe una versión más reciente. La instalación del C++ paquete redistribuible de visual Studio 2015 o 2017 en un equipo que ya tiene 2019 producirá un error de instalación. El error tendrá un aspecto similar al siguiente:

```
*0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.*.
```

Este error es así por diseño. Se recomienda mantener la última instalada.

## <a name="see-also"></a>Vea también

* [Historial de cambios en Visual C++](../porting/visual-cpp-change-history-2003-2015.md)
* [Las descargas más recientes C++ del paquete redistribuible de Visual](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 
