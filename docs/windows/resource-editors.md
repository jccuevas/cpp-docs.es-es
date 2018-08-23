---
title: Editores de recursos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vs.editors.resource
- vc.resvw.resource.editors
- vs.resvw.resource.editors
dev_langs:
- C++
helpviewer_keywords:
- editors [C++], resource
- editors [C++]
- resource editors
- Windows [C++], application resource editing
ms.assetid: e20a29ec-d6fb-4ead-98f3-431a0e23aaaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d05557b6f92fa5bce8506572fd1c651950d6aa23
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594298"
---
# <a name="resource-editors"></a>editores de recursos

Un **recursos** editor es un entorno especializado para la creación o modificación de los recursos que se incluyen en un proyecto de Visual Studio. Los editores de recursos de Visual Studio comparten técnicas e interfaces que ayudan a crear y modificar recursos de la aplicación de forma rápida y sencilla. Los editores de recursos permiten [ver y editar recursos en el editor adecuado](../windows/viewing-and-editing-resources-in-a-resource-editor.md) y [obtener una vista previa de los recursos](../windows/previewing-resources.md).

Al crear o abrir un recurso, se abre automáticamente el editor correspondiente.

**Nota** : dado que los proyectos administrados no usan archivos de script de recursos, los recursos deben abrirse desde el **Explorador de soluciones**. Se puede usar el [Editor de imágenes](../windows/image-editor-for-icons.md) y el [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

|Use...|Para editar...|
|----------------|----------------|
|[Editor de aceleradores](../windows/accelerator-editor.md)|Tablas de aceleradores en proyectos de Visual C++.|
|[Binary Editor](binary-editor.md)|Información de datos binarios y recursos personalizados en proyectos de Visual C++, Visual Basic o Visual C#.|
|[Editor de cuadros de diálogo](../windows/dialog-editor.md)|Cuadros de diálogo en proyectos de Visual C++.|
|[Image Editor](../windows/image-editor-for-icons.md)|Mapas de bits, iconos, cursores y otros archivos de imagen en proyectos de Visual C++, Visual Basic o Visual C#.|
|[Editor de menús](../windows/menu-editor.md)|Recursos de menús en proyectos de Visual C++.|
|[Editor de Ribbon](../mfc/ribbon-designer-mfc.md)|Recursos de cinta de opciones en proyectos de MFC.|
|[Editor de cadenas](../windows/string-editor.md)|Tablas de cadenas en proyectos de Visual C++.|
|[Editor de barras de herramientas](../windows/toolbar-editor.md)|Recursos de barras de herramientas en proyectos de Visual C++. El editor de barras de herramientas es parte del editor de imágenes.|
|[Editor de la información de versión](../windows/version-information-editor.md)|Información de versión en proyectos de Visual C++.|

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)  
[Archivos de recursos](../windows/resource-files-visual-studio.md)  
[Símbolos: Identificadores de recursos](../windows/symbols-resource-identifiers.md)  
[Menús y otros recursos](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)