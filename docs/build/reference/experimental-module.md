---
title: '/experimental: módulo (habilitar la compatibilidad con módulos)'
description: 'Use la opción del compilador/experimental: Module para habilitar la compatibilidad experimental del compilador con los módulos.'
ms.date: 09/03/2019
f1_keywords:
- module
- /experimental:module
helpviewer_keywords:
- module
- /experimental:module
- Enable module support
ms.openlocfilehash: 82cce127ad5a2f87d11e4a653035bd80ea9f5001
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294462"
---
# <a name="experimentalmodule-enable-module-support"></a>/experimental: módulo (habilitar la compatibilidad con módulos)

Habilita la compatibilidad experimental del compilador con los módulos, tal y como especifica el estándar de borrador de C++ 20.

## <a name="syntax"></a>Sintaxis

> **/experimental: módulo** [ **-** ]

## <a name="remarks"></a>Comentarios

Puede habilitar la compatibilidad con módulos experimentales mediante el uso de la opción del compilador **/experimental: module** junto con la opción [/STD: c + + latest](std-specify-language-standard-version.md) . Puede usar **/experimental: module** para deshabilitar la compatibilidad de módulos explícitamente.

Esta opción está disponible a partir de Visual Studio 2015 Update 1. A partir de la versión 16,2 de Visual Studio 2019, los módulos de borrador de C++ 20 estándar C++ no están totalmente implementados en el compilador de Microsoft. Puede usar la característica módulos para crear módulos de una sola partición e importar los módulos de la biblioteca estándar que proporciona Microsoft. Un módulo y el código que lo consume deben compilarse con las mismas opciones del compilador.

Para obtener más información sobre los módulos y cómo usarlos y crearlos, vea [información general C++sobre los módulos de ](../../cpp/modules-cpp.md).

Este es un ejemplo de las opciones de línea de comandos del compilador que se usan para crear un módulo de exportación a partir del archivo de código fuente *ModuleName. IXX*:

```cmd
cl /EHsc /MD /experimental:module /module:export /module:name ModuleName /module:wrapper C:\Output\path\ModuleName.h /module:output C:\Output\path\ModuleName.ifc -c ModuleName.ixx
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Establezca la lista desplegable **configuración** en **todas las configuraciones**.

1. Seleccione la **Página propiedades** > de configuración**C/C++**  > idioma.

1. Modifique la **propiedad C++ habilitar módulos (experimental)** y, después, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](zc-conformance.md)
