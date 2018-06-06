---
title: 'Cómo: crear proyectos de C++ comprobables (C++ / CLI) | Documentos de Microsoft'
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
ms.openlocfilehash: 36e7ee85d97639df6298a346ae83bb090e81bf87
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704768"
---
# <a name="how-to-create-verifiable-c-projects-ccli"></a>Cómo: crear proyectos de C++ comprobables (C++ / CLI)

Asistentes para aplicaciones de visuales C++ no crean proyectos comprobables.

> [!IMPORTANT]
> Visual Studio 2015 en desuso y 2017 de Visual Studio no admite la **/CLR: pure** y **/CLR: safe** creación de proyectos comprobables. Si necesita código comprobable, se recomienda que trasladar el código C#.

Sin embargo, si está utilizando una versión anterior del conjunto de herramientas de compilador de Visual C++ admiten **/CLR: pure** y **/CLR: safe**, proyectos se pueden convertir para que sea comprobable. En este tema se describe cómo establecer propiedades del proyecto y modificar archivos de código fuente del proyecto para transformar los proyectos de Visual C++ para generar aplicaciones comprobables.

## <a name="compiler-and-linker-settings"></a>Configuración del compilador y el vinculador

 De forma predeterminada, los proyectos de .NET use la marca de compilador /clr y configuran al vinculador para hardware de destino x86. Para código comprobable, debe usar el indicador/clr: safe e indicar al vinculador que genere MSIL en lugar de instrucciones máquina nativas.

### <a name="to-change-the-compiler-and-linker-settings"></a>Para cambiar la configuración de compilador y el vinculador

1. Mostrar la página de propiedades del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).

1. En el **General** página en el **propiedades de configuración** de conjunto de nodos, el **soporte de Common Language Runtime** propiedad a **seguro MSIL Common Language Compatibilidad en tiempo de ejecución (/ CLR: safe)**.

1. En el **avanzadas** página en el **vinculador** de conjunto de nodos, el **tipo de imagen CLR** propiedad **Forzar imagen de IL segura (/ CLRIMAGETYPE: safe)**.

## <a name="removing-native-data-types"></a>Quitar tipos de datos nativos

Dado que los tipos de datos nativos no son comprobables, incluso si no se usan realmente, debe quitar todos los archivos de encabezado que contiene los tipos nativos.

> [!NOTE]
> El siguiente procedimiento se aplica a los proyectos de aplicación de Windows Forms (. NET) y aplicación de consola (. NET).

### <a name="to-remove-references-to-native-data-types"></a>Para quitar las referencias a tipos de datos nativos

1. Marque como comentario todo el archivo Stdafx.h.

## <a name="configuring-an-entry-point"></a>Configurar un punto de entrada

Dado que las aplicaciones comprobables no pueden usar las bibliotecas de tiempo de ejecución de C (CRT), no pueden depender de CRT para llamar a la función principal como punto de entrada estándar. Esto significa que debe proporcionar explícitamente el nombre de la función llamar inicialmente al vinculador. (En este caso, Main() se utiliza en lugar de main() o _tmain () para indicar un punto de entrada de CRT no, pero dado que el punto de entrada debe especificarse explícitamente, este nombre es arbitrario.)

> [!NOTE]
> Los procedimientos siguientes se aplican a los proyectos de aplicación de consola (. NET).

#### <a name="to-configure-an-entry-point"></a>Para configurar un punto de entrada

1. Cambie _tmain () por Main() en el archivo del proyecto .cpp principal.

1. Mostrar la página de propiedades del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).

1. En el **avanzadas** página en el **vinculador** nodo, escriba `Main` como el **punto de entrada** valor de propiedad.

## <a name="see-also"></a>Vea también

- [Código puro y comprobable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
