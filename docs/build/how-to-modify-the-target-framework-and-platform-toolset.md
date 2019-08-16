---
title: Procedimiento Modificar la plataforma de destino y el conjunto de herramientas de la plataforma
ms.custom: conceptual
ms.date: 07/24/2019
helpviewer_keywords:
- 'msbuild (c++), howto: modify target framework and platform toolset'
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
ms.openlocfilehash: 6af7a4eb47c1d3f8b9c52eec39795c9307ca9d8e
ms.sourcegitcommit: ce3393846c86e7905ff0c86e4cd6610476809585
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2019
ms.locfileid: "68492234"
---
# <a name="how-to-modify-the-target-framework-and-platform-toolset"></a>Procedimiento Modificar la plataforma de destino y el conjunto de herramientas de la plataforma

Puede editar un archivo de proyecto C++ de Visual Studio para tener como destino distintas C++ versiones del conjunto de herramientas de la plataforma,C++la Windows SDK y el .NET Framework (solo en proyectos/CLI). De forma predeterminada, el sistema de proyectos utiliza la versión de .NET Framework y la versión del conjunto de herramientas que corresponden a la versión de Visual Studio que se utiliza para crear el proyecto. Puede modificar todos estos valores en el archivo. vcxproj para que pueda usar la misma base de código para cada destino de compilación.

## <a name="platform-toolset"></a>Conjunto de herramientas de la plataforma

El conjunto de herramientas de la C++ plataforma consta del compilador (cl. exe) y del vinculador (link. exe)C++ , junto con las bibliotecas de C/estándar. Desde Visual Studio 2015, la versión principal del conjunto de herramientas ha permanecido en 14, lo que significa que los proyectos compilados con Visual Studio 2019 o Visual Studio 2017 son compatibles con las versiones anteriores de ABI con los proyectos compilados con Visual Studio 2015. La versión secundaria se ha actualizado en 1 para cada versión desde Visual Studio 2015:

- Visual Studio 2015: V140
- Visual Studio 2017: v141
- Visual Studio 2019: v142

Estos conjuntos de herramientas admiten .NET Framework 4,5 y versiones posteriores.

Visual Studio también admite la compatibilidad con múltiples C++ versiones para los proyectos. Puede usar el IDE de Visual Studio para editar y compilar proyectos que se crearon con versiones anteriores de Visual Studio, sin actualizarlos para usar una nueva versión del conjunto de herramientas. Debe tener instalados en el equipo los conjuntos de herramientas anteriores. Para obtener más información, consulte [uso de la compatibilidad nativa con múltiples versiones en Visual Studio](../porting/use-native-multi-targeting.md). Por ejemplo, en Visual Studio 2015, puede tener *como destino* .NET Framework 2,0, pero debe usar un conjunto de herramientas anterior que lo admita.

## <a name="target-framework-ccli-project-only"></a>Plataforma de destinoC++(solo para el proyecto/CLI)

Cuando se cambia la versión de .Net Framework de destino, también cambia el conjunto de herramientas de la plataforma a una versión que admite la versión de .Net Framework de destino. Por ejemplo, para definir como destino .NET Framework 4.5, debe utilizar un conjunto de herramientas de plataforma compatible, tal como Visual Studio 2015 (v140), Visual Studio 2013 (v120) o Visual Studio 2012 (v110). Puede usar el conjunto de herramientas de la plataforma [Windows 7,1 SDK](https://www.microsoft.com/en-us/download/details.aspx?id=8279) para tener como destino los .NET Framework 2,0, 3,0, 3,5 y 4, y las plataformas x86/x64.

Puede extender la plataforma de destino aún más creando un conjunto de herramientas personalizado de la plataforma. Para obtener más información, vea [C++ Native Multi-Targeting](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) en el blog de Visual C++.

### <a name="to-change-the-target-framework"></a>Para cambiar la versión de .NET Framework de destino

1. En Visual Studio, en el **Explorador de soluciones**, seleccione el proyecto. En la barra de menús, abra el menú **Proyecto** y elija **Descargar el proyecto**. Esto descarga el archivo de proyecto (.vcxproj) para el proyecto.

   > [!NOTE]
   >  Un proyecto de C++ no se puede cargar mientras el archivo de proyecto se está modificando en Visual Studio. Sin embargo, puede utilizar otro editor como Bloc de notas para modificar el archivo de proyecto mientras se carga el proyecto en Visual Studio. Visual Studio detecta que el archivo de proyecto ha cambiado y pide que se recargue el proyecto.

1. En la barra de menús, seleccione **Archivo**, **Abrir**, **Archivo**. En el cuadro de diálogo **Abrir archivo** , navegue a la carpeta de proyecto y vuelva a abrir el archivo de proyecto (.vcxproj).

1. En el archivo de proyecto, busque la entrada para la versión de .Net Framework de destino. Por ejemplo, si se ha diseñado el proyecto para usar .NET Framework 4.5, busque `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` en el elemento `<PropertyGroup Label="Globals">` del elemento `<Project>` . Si el elemento `<TargetFrameworkVersion>` no está presente, el proyecto no usa .NET Framework y no se requiere ningún cambio.

1. Cambie el valor a la versión de Framework que desee, como v3.5 o v4.6.

1. Guarde los cambios y cierre el editor.

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Volver a cargar el proyecto**.

1. Para comprobar el cambio, en el **Explorador de soluciones**, haga clic con el botón derecho para abrir el menú contextual del proyecto (no de la solución) y, luego, elija **Propiedades** para abrir el cuadro de diálogo **Páginas de propiedades** del proyecto. En el panel de la izquierda del cuadro de diálogo, expanda **Propiedades de configuración** y, a continuación, seleccione **General**. Compruebe que **Versión de .NET Target Framework** muestre la nueva versión de Framework.

### <a name="to-change-the-platform-toolset"></a>Para cambiar el conjunto de herramientas de la plataforma

1. En Visual Studio, en el **Explorador de soluciones**, abra el menú contextual del proyecto (no de la solución) y, luego, elija **Propiedades** para abrir el cuadro de diálogo **Páginas de propiedades** del proyecto.

1. En el cuadro de diálogo **Páginas de propiedades** , abra la lista desplegable **Configuración** y seleccione **Todas las configuraciones**.

1. En el panel de la izquierda del cuadro de diálogo, expanda **Propiedades de configuración** y, a continuación, seleccione **General**.

1. En el panel de la derecha, seleccione **Conjunto de herramientas de la plataforma** y, a continuación, seleccione el conjunto de herramientas que desee en la lista desplegable. Por ejemplo, si ha instalado el conjunto de herramientas de Visual Studio 2010, seleccione **visual studio 2010 (V100)** para usarlo en el proyecto.

1. Elija el botón **Aceptar** .

## <a name="see-also"></a>Vea también

[MSBuild en la línea de comandos - C++](msbuild-visual-cpp.md)
