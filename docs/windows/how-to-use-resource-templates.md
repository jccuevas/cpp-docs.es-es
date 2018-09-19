---
title: 'Cómo: usar plantillas de recursos (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- language-specific template files [C++]
- resource templates
- resources [C++], creating
- rct files [C++]
- templates, resource templates
- resources [C++], templates
- .rct files [C++]
ms.assetid: bdfe7060-f98e-4859-8285-9c8570360e9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 90c94e87693929c2ae33d65fe3f3a4b2dd55d48b
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313980"
---
# <a name="how-to-use-resource-templates-c"></a>Cómo: usar plantillas de recursos (C++)

Una plantilla de recursos es un recurso personalizado que ha guardado como un archivo .rct. Por lo tanto, una plantilla de recursos puede servir como punto de partida para crear otros recursos. Las plantillas de recursos ahorran tiempo en el desarrollo de recursos adicionales o grupos de recursos que comparten características, como los controles estándar y otros elementos repetidos. Por ejemplo, debe incluir un botón de ayuda y el icono del logotipo de una empresa en varios cuadros de diálogo. Para hacerlo de una forma rápida, cree una nueva plantilla de cuadro de diálogo y personalícela con el logotipo y el botón de ayuda.

Una vez que ha personalizado la plantilla de recursos, debe guardar los cambios en la carpeta de plantillas (o en cualquier ubicación especificada en la ruta de acceso de inclusión) para que aparezca bajo su tipo de recurso en el [cuadro de diálogo Agregar recurso](../windows/add-resource-dialog-box.md). A continuación, podrá utilizar la nueva plantilla de recursos tantas veces como sea necesario.

> [!NOTE]
> Puede colocar los archivos de plantilla específicos del idioma en los subdirectorios del directorio principal de plantillas. Por ejemplo, puede colocar archivos de plantilla solo en inglés en \\< directorio de plantillas de recursos\>\1033.

### <a name="to-create-a-template-for-resources"></a>Para crear una plantilla para los recursos

1. En **el Explorador de soluciones**, haga clic en el proyecto.

2. En el menú contextual, elija **agregar**, a continuación, haga clic en **Agregar nuevo elemento**.

3. En el **Agregar nuevo elemento** cuadro de diálogo el **plantillas:** panel, elija **el archivo de plantilla de recursos (.rct)**.

4. Proporcione un nombre y ubicación para el nuevo archivo .rct y haga clic en **abierto**.

5. El nuevo archivo .rct se agregará al proyecto y aparece en **el Explorador de soluciones** bajo el **recursos** carpeta.

   Ahora puede haga doble clic en el archivo .rct para abrirlo en una ventana de documento y luego agregar recursos a él (haga clic en el archivo en la ventana de documento y elija **Agregar recurso** en el menú contextual). A continuación, puede personalizar estos recursos y guardar el archivo .rct.

   > [!NOTE]
   > Cuando se crea un archivo RCT nuevo, Visual Studio lo buscará en \Program Files\Microsoft Visual Studio 9.0\VC\VCResourceTemplates, en \Program Files\Microsoft Visual Studio 9.0\VC\VCResourceTemplates\\*LCID* () Por ejemplo, 1033 para inglés), *o* en cualquier parte de la [incluir ruta de acceso](../windows/how-to-specify-include-directories-for-resources.md). Si prefiere guardar los archivos RCT en otra carpeta de archivo, por ejemplo \Mis documentos, solo tendrá que agregar esta carpeta a la ruta de inclusión y Visual Studio encontrará su archivo RCT.

### <a name="to-convert-an-existing-rc-file-to-an-rct-file"></a>Para convertir un archivo .rc existente en un archivo .rct

1. [Abra el archivo .rc como un archivo independiente](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

2. En el **archivo** menú, haga clic en **guardar \< *su nombre de archivo*> como**.

3. Especifique una ubicación y haga clic en **Aceptar**.

### <a name="to-create-a-new-resource-from-a-template"></a>Para crear un nuevo recurso a partir de una plantilla

1. En el [vista de recursos](../windows/resource-view-window.md) panel, haga clic el archivo .rc y elija **Agregar recurso** en el menú contextual.

2. En el **Agregar recurso** diálogo cuadro, haga clic en el signo más (**+**) junto a un recurso para expandir el nodo de recursos y ver todas las plantillas disponibles para ese recurso.

3. Haga doble clic en la plantilla que desea editar.

4. Modifique el recurso agregado en su editor de recursos según sea necesario.

   El editor de recursos proporciona automáticamente un identificador de recurso único. Puede revisar el [propiedades del recurso](../windows/changing-the-properties-of-a-resource.md) según sea necesario.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Archivos de recursos](../windows/resource-files-visual-studio.md)  
[Editores de recursos](../windows/resource-editors.md)