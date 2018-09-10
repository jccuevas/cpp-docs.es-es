---
title: Creación de una información sobre herramientas para un botón de barra de herramientas (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [C++], adding to toolbar buttons
- "\nin tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor [C++], creating tool tips
ms.assetid: 0af65342-fd78-4e78-8d0d-dc68f7fc462e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5e5fef71d3fa2ad76192a06603ed9e22d52eef71
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317828"
---
# <a name="creating-a-tool-tip-for-a-toolbar-button-c"></a>Creación de una información sobre herramientas para un botón de barra de herramientas (C++)

### <a name="to-create-a-tool-tip"></a>Para crear una información sobre herramientas

1. Seleccione el botón de barra de herramientas.

2. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), en el **Prompt** campo de propiedad, agregue una descripción del botón de la barra de estado; después del mensaje, agregue `\n` y su nombre.

Un ejemplo común de una información sobre herramientas es el **impresión** botón **WordPad**:

1. Abra **WordPad**.

2. Mantenga el puntero del mouse sobre el **impresión** botón de barra de herramientas.

3. Tenga en cuenta que la palabra `Print` ahora está flotando en el puntero del mouse.

4. Examine la barra de estado (en la parte inferior de la **WordPad** ventana): tenga en cuenta que ahora muestra el texto `Prints the active document`.

El `Print` en **paso 3** es el nombre"herramienta sugerencia" y el `Prints the active document` desde **paso 4** es la "Descripción del botón de la barra de estado".

Si desea que este efecto mediante el **barra de herramientas** editor, establezca el **Prompt** propiedad `Prints the active document\nPrint`.

> [!NOTE]
> Puede editar el texto del mensaje utilizando el [ventana propiedades](/visualstudio/ide/reference/properties-window).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

MFC o ATL

## <a name="see-also"></a>Vea también

[Creación, migración y edición de botones de la barra de herramientas](../windows/creating-moving-and-editing-toolbar-buttons.md)  
[Editor de barras de herramientas](../windows/toolbar-editor.md)