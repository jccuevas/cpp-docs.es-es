---
title: Agregar valores a un Control de cuadro combinado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.combo
dev_langs:
- C++
helpviewer_keywords:
- combo boxes [C++], Data property
- controls [C++], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- Data property
- combo boxes [C++], testing values
ms.assetid: 22a78f98-fada-48b3-90d8-7fa0d8e4de51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 224f52ed9141f302568fe007e7cde4ef609d00ed
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317978"
---
# <a name="adding-values-to-a-combo-box-control"></a>Agregar valores a un control de cuadro combinado

Puede agregar valores a un control de cuadro combinado siempre que tenga el **diálogo** editor abierto.

> [!TIP]
> Es una buena idea agregar todos los valores al cuadro combinado *antes* tamaño en el cuadro de la **diálogo** editor, o se puede truncar el texto que debe aparecer en el control de cuadro combinado.

### <a name="to-enter-values-into-a-combo-box-control"></a>Para introducir valores en un control de cuadro combinado

1. Seleccione el control de cuadro combinado haciendo clic en él.

2. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), desplácese hacia abajo hasta la **datos** propiedad.

   > [!NOTE]
   > Si se muestran las propiedades agrupadas por tipo, **datos** aparece en el **Misc** propiedades.

3. Haga clic en el área de valores de la **datos** propiedad y escriba los valores de los datos, separados por punto y coma.

   > [!NOTE]
   > No incluya espacios entre los valores porque podrían afectar al orden alfabético de la lista desplegable.

4. Haga clic en **ENTRAR** cuando haya terminado de agregar valores.

Para obtener información sobre la ampliación de la parte desplegable de un cuadro combinado, vea [establecer el tamaño del cuadro combinado y su lista desplegable](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).

> [!NOTE]
> No se puede agregar valores a los proyectos de Win32 mediante este procedimiento (la **datos** propiedad está atenuada para los proyectos de Win32). Dado que los proyectos de Win32 no tienen bibliotecas que agregar esta funcionalidad, debe agregar valores mediante programación a un cuadro combinado con un proyecto de Win32.

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>Para probar la apariencia de los valores en un cuadro combinado

1. Después de escribir valores en el **datos** propiedad, haga clic en el **prueba** situado en la [barra de herramientas del Editor de cuadro de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

   Pruebe a desplazarse por la lista de valores todo. Los valores aparecen exactamente como se escriben en el **datos** propiedad en el **propiedades** ventana. Hay ningún ortografía ni la comprobación de mayúsculas y minúsculas.

   Presione **Esc** para volver a la **cuadro de diálogo** editor.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)  
[Controles](../mfc/controls-mfc.md)