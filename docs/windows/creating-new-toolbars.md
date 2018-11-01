---
title: Crear nuevas barras de herramientas (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar
helpviewer_keywords:
- toolbars [C++], creating
- Toolbar editor [C++], creating new toolbars
- Insert Resource
ms.assetid: 1b28264b-0718-4df8-9f65-979805d2efef
ms.openlocfilehash: 3c36579560c78ff77a624e4827df9d6a9302ae57
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551312"
---
# <a name="creating-new-toolbars-c"></a>Crear nuevas barras de herramientas (C++)

### <a name="to-create-a-new-toolbar"></a>Para crear una nueva barra de herramientas

1. En **recursos** ver, haga clic en el archivo .rc y, a continuación, elija **Agregar recurso** en el menú contextual. (Si tiene una barra de herramientas existente en el archivo .rc, puede hacer simplemente clic en el **barra de herramientas** carpeta y seleccione **insertar Toolbar** en el menú contextual.)

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. En el **Agregar recurso** cuadro de diálogo, seleccione **barra de herramientas** en el **tipo de recurso** lista y, después, haga clic en **New**.

   Si un signo más (**+**) aparece junto a la **barra de herramientas** tipo de recurso, significa que están disponibles plantillas de barra de herramientas. Haga clic en el signo más para expandir la lista de plantillas, seleccione una plantilla y haga clic en **New**.

   \- o -

3. [Convertir un mapa de bits existente en una barra de herramientas](../windows/converting-bitmaps-to-toolbars.md).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

MFC o ATL

## <a name="see-also"></a>Vea también

[Editor de barras de herramientas](../windows/toolbar-editor.md)