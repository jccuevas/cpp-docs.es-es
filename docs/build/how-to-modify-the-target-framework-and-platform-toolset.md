---
title: 'Cómo: modificar plataforma de destino y el conjunto de herramientas de plataforma | Microsoft Docs'
ms.custom: conceptual
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.modifytargetframeworkandplatformtoolset
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: modify target framework and platform toolset'
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60fa9bd3d6db9d90e5d7f3bc94e7686e5cf9481e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708453"
---
# <a name="how-to-modify-the-target-framework-and-platform-toolset"></a>Cómo: Modificar plataforma de destino y el conjunto de herramientas de la plataforma

Puede cambiar la configuración del proyecto de Visual C++ a distintas versiones de .NET Framework de destino y utilizar conjuntos de herramientas de plataforma diferente. De forma predeterminada, el sistema de proyectos utiliza la versión de .NET Framework y la versión del conjunto de herramientas que corresponden a la versión de Visual Studio que se utiliza para crear el proyecto. Puede cambiar el conjunto de herramientas de la plataforma de destino modificando las propiedades del proyecto. Puede cambiar la versión de .Net Framework de destino modificando el archivo de proyecto (.vcxproj). No tiene que mantener una base de código independiente para cada destino de compilación.

> [!IMPORTANT]
>  Es posible que algunas ediciones no admitan versiones de .NET Framework de destino o conjuntos de herramientas de plataformas modificados. Para obtener información de compatibilidad, vea [portar, migrar y actualizar proyectos de Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects).

Cuando se cambia la versión de .Net Framework de destino, también cambia el conjunto de herramientas de la plataforma a una versión que admite la versión de .Net Framework de destino. Por ejemplo, para definir como destino .NET Framework 4.5, debe utilizar un conjunto de herramientas de plataforma compatible, tal como Visual Studio 2015 (v140), Visual Studio 2013 (v120) o Visual Studio 2012 (v110). Puede utilizar el conjunto de herramientas de la plataforma **Windows7.1SDK** para las plataformas .NET Framework 2.0, 3.0, 3.5 y 4, así como x86, Itanium y x64.

> [!NOTE]
>  Para cambiar el conjunto de herramientas de la plataforma de destino, debe tener la versión asociada de Visual Studio o Windows Platform SDK instalado. Por ejemplo, para definir como destino la plataforma Itanium con el conjunto de herramientas de la plataforma de **Windows7.1SDK** , debe tener instalado [Microsoft Windows SDK para Windows 7 y .NET Framework 4 SP1](http://www.microsoft.com/download/details.aspx?id=8279) ; sin embargo, podría utilizar otra versión compatible de Visual Studio para realizar el trabajo de desarrollo, siempre que el destino sea el conjunto de herramientas correcto de versión y plataforma de .NET Framework.

Puede extender la plataforma de destino aún más creando un conjunto de herramientas personalizado de la plataforma. Para obtener más información, consulte [C++ Native Multi-Targeting](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) en el blog de Visual C++.

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

### <a name="to-change-the-project-toolset"></a>Para cambiar el conjunto de herramientas del proyecto

1. En Visual Studio, en el **Explorador de soluciones**, abra el menú contextual del proyecto (no de la solución) y, luego, elija **Propiedades** para abrir el cuadro de diálogo **Páginas de propiedades** del proyecto.

1. En el cuadro de diálogo **Páginas de propiedades** , abra la lista desplegable **Configuración** y seleccione **Todas las configuraciones**.

1. En el panel de la izquierda del cuadro de diálogo, expanda **Propiedades de configuración** y, a continuación, seleccione **General**.

1. En el panel de la derecha, seleccione **Conjunto de herramientas de la plataforma** y, a continuación, seleccione el conjunto de herramientas que desee en la lista desplegable. Por ejemplo, si ha instalado el conjunto de herramientas de Visual Studio 2010, seleccione **Visual Studio 2010 (v100)** se usa para el proyecto.

1. Elija el botón **Aceptar** .

## <a name="see-also"></a>Vea también

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)