---
title: 'Cómo: crear proyectos de C++ comprobables (C++ / c++ / CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], creating
- conversions, C++ projects
- Visual C++ projects
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a84fcd660f8cc7ef5686fe0e03f9b520d1251bc4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408939"
---
# <a name="how-to-create-verifiable-c-projects-ccli"></a>Cómo: crear proyectos de C++ comprobables (C++ / c++ / CLI)

Asistentes para aplicaciones de visuales C++ no crean proyectos comprobables.

> [!IMPORTANT]
> En desuso de Visual Studio 2015 y Visual Studio 2017 no admite la **/CLR: pure** y **/CLR: safe** creación de proyectos que se pueda comprobar. Si necesita código comprobable, se recomienda que trasladar el código en C#.

Sin embargo, si usa una versión anterior del conjunto de herramientas del compilador de Visual C++ que admite **/CLR: pure** y **/CLR: safe**, se pueden convertir los proyectos para que sea comprobable. Este tema describe cómo establecer las propiedades del proyecto y modificar archivos de código fuente del proyecto para transformar los proyectos de Visual C++ para generar aplicaciones comprobables.

## <a name="compiler-and-linker-settings"></a>Configuración de compilador y vinculador

De forma predeterminada, los proyectos de .NET use la marca de compilador/CLR y configuran al vinculador para hardware x86. Para código comprobable, debe usar el indicador/clr: safe e indicar al vinculador que genere MSIL en lugar de instrucciones máquina nativas.

### <a name="to-change-the-compiler-and-linker-settings"></a>Para cambiar la configuración del compilador y vinculador

1. Mostrar la página de propiedades del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../ide/working-with-project-properties.md).

1. En el **General** página en el **propiedades de configuración** de conjunto de nodos, el **compatible con tiempo de ejecución de Common Language** propiedad **seguro MSIL Common Language Compatibilidad en tiempo de ejecución (/ CLR: safe)**.

1. En el **avanzadas** página en el **vinculador** de conjunto de nodos, el **tipo de imagen CLR** propiedad **Forzar imagen de IL segura (/ CLRIMAGETYPE: safe)**.

## <a name="removing-native-data-types"></a>Quitar tipos de datos nativos

Dado que los tipos de datos nativos son que no es comprobable, incluso si no se usan realmente, debe quitar todos los archivos de encabezado que contiene los tipos nativos.

> [!NOTE]
> El siguiente procedimiento se aplica a los proyectos de aplicación de Windows Forms (. NET) y aplicación de consola (. NET).

### <a name="to-remove-references-to-native-data-types"></a>Para quitar las referencias a tipos de datos nativos

1. Marque como comentario todo el archivo Stdafx.h.

## <a name="configuring-an-entry-point"></a>Configurar un punto de entrada

Dado que las aplicaciones comprobables no pueden usar las bibliotecas de tiempo de ejecución de C (CRT), no puede depender de CRT para llamar a la función principal como punto de entrada estándar. Esto significa que debe proporcionar explícitamente el nombre de la llamada a función inicialmente al vinculador. (En este caso, Main() se utiliza en lugar de main() o _tmain () para indicar un punto de entrada que no son CRT, pero dado que el punto de entrada se debe especificar explícitamente, este nombre es arbitrario).

> [!NOTE]
> Los procedimientos siguientes se aplican a los proyectos de aplicación de consola (. NET).

#### <a name="to-configure-an-entry-point"></a>Para configurar un punto de entrada

1. Cambiar _tmain () por Main() en el archivo del proyecto .cpp principal.

1. Mostrar la página de propiedades del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../ide/working-with-project-properties.md).

1. En el **avanzadas** página bajo la **vinculador** nodo, escriba `Main` como el **punto de entrada** valor de propiedad.

## <a name="see-also"></a>Vea también

- [Código puro y comprobable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
