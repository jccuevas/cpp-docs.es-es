---
title: Seleccionar controles
ms.date: 11/04/2016
helpviewer_keywords:
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
- controls [C++], removing from groups
- Dialog Editor [C++], dominant control
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
ms.openlocfilehash: a0a21942f6e2c37b96a7a704fadbb9bacc4761c8
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149679"
---
# <a name="selecting-controls"></a>Seleccionar controles

Seleccione los controles de tamaño, alinear, mover, copiar, o eliminarlas y, a continuación, complete la operación que desee. En la mayoría de los casos, deberá seleccionar más de un control para utilizar las herramientas de ajuste de tamaño y alineación de la [barra de herramientas del Editor de cuadro de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Cuando se selecciona un control, tiene un borde sombreado alrededor de ella con sólidos (activos) o "cuadros de tamaño" hueco (inactivo) pequeños cuadros que aparecen en el borde de selección. Cuando se seleccionan varios controles, el control dominante tiene controladores de tamaño sólido y todos los controles seleccionados tienen controladores de tamaño hueco.

Al cambiar el tamaño o alinear varios controles, el **diálogo** editor usa el "control dominante" para determinar cómo los otros controles o un tamaño alineados. De forma predeterminada, el control dominante es el primer control seleccionado.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-select-multiple-controls"></a>Para seleccionar varios controles

1. En el [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox), seleccione el **puntero** herramienta.

1. Arrastre el puntero para dibujar un cuadro de selección alrededor de los controles que desea seleccionar en el cuadro de diálogo.

   Al soltar el botón del mouse, todos los controles internos y se selecciona el cuadro de selección de intersección.

   \- o -

   Mantenga presionada la **MAYÚS** clave y seleccione los controles que le gustaría incluir en la selección.

   \- o -

   Mantenga presionada la **Ctrl** clave y seleccione los controles que le gustaría incluir en la selección.

## <a name="to-remove-a-control-from-a-group-of-selected-controls-or-to-add-a-control-to-a-group-of-selected-controls"></a>Para quitar un control de un grupo de controles seleccionados o para agregar un control a un grupo de controles seleccionados

1. Con un grupo de controles seleccionados, mantenga presionada la **MAYÚS** clave y se selecciona el control que desea quitar o agregar a la selección existente.

   > [!NOTE]
   > Manteniendo presionada la tecla el **Ctrl** clave y seleccione un control dentro de una selección hará que controlan el control dominante en esa selección.

## <a name="to-specify-the-dominant-control"></a>Para especificar el control dominante

1. Mantenga presionada la **Ctrl** clave y haga clic en el control que desea usar para influir en el tamaño o la ubicación de otros controles *primera*.

> [!NOTE]
> Los controladores de tamaño del control dominante son sólidos, mientras que los de los controles subordinados serán huecos. Todos los aún más el cambio de tamaño o la alineación se basa en el control dominante.

## <a name="to-change-the-dominant-control"></a>Para cambiar el control dominante

1. Desactive la selección actual haciendo clic fuera de todos los controles seleccionados actualmente.

1. Repita el procedimiento anterior, seleccione primero un control diferente.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles](../mfc/controls-mfc.md)