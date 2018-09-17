---
title: MSBuild (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- MSBuild
dev_langs:
- C++
helpviewer_keywords:
- MSBuild
ms.assetid: 7a1be7ff-0312-4669-adf2-5f5bf507d560
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bdb48c71c244adc2df5beef9668e12ee47f2b48
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703955"
---
# <a name="msbuild-visual-c"></a>MSBuild (Visual C++)

Puede usar el **MSBuild** herramienta para crear una aplicación de Visual C++ desde el símbolo del sistema. El proceso de compilación se controla mediante la información en un archivo de proyecto (.vcxproj) que puede crear y editar. El archivo de proyecto especifica opciones de compilación basadas en fases, condiciones y eventos de compilación.

## <a name="in-this-section"></a>En esta sección

|Término|de esquema JSON|
|----------|----------------|
|[Información general sobre MSBuild (Visual C++)](../build/msbuild-visual-cpp-overview.md)|Describe cómo Visual C++ utiliza el **MSBuild** sistema.|
|[Cambios del sistema de compilación](../build/build-system-changes.md)|Se describen algunas de las diferencias entre el sistema de compilación actual y la versión anterior.|
|[Tutorial: Usar MSBuild para crear un proyecto de Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|Muestra cómo crear un proyecto de Visual C++ mediante **MSBuild**.|
|[Procedimiento para usar eventos de compilación en proyectos de MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)|Muestra cómo especificar una acción que se produce en una fase concreta de la compilación: antes de que empiece la compilación; antes de iniciar el paso de vínculo; o bien, una vez finalizada la compilación.|
|[Procedimiento para agregar un paso de compilación personalizado a proyectos de MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)|Muestra cómo agregar una fase definido por el usuario a la secuencia de compilación.|
|[Procedimiento para agregar herramientas de compilación personalizadas a proyectos de MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)|Muestra cómo asociar una herramienta de compilación con un archivo determinado.|
|[Procedimiento para integrar herramientas personalizadas en las propiedades del proyecto](../build/how-to-integrate-custom-tools-into-the-project-properties.md)|Muestra cómo agregar las opciones para una herramienta personalizada para las propiedades del proyecto.|
|[Procedimiento para modificar plataforma de destino y el conjunto de herramientas de la plataforma](../build/how-to-modify-the-target-framework-and-platform-toolset.md)|Muestra cómo compilar un proyecto para varios marcos de trabajo o conjuntos de herramientas.|

## <a name="see-also"></a>Vea también

[Compilación de código de C o C++ en la línea de comandos](../build/building-on-the-command-line.md)