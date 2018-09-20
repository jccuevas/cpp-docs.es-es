---
title: Selección de controles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d6b322559777d10f3a53f7ed8adbc5d6a05a342
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379708"
---
# <a name="selecting-controls"></a>Seleccionar controles

Seleccione los controles de tamaño, alinear, mover, copiar, o eliminarlas y, a continuación, realizar la operación que desee. En la mayoría de los casos, deberá seleccionar más de un control para utilizar las herramientas de ajuste de tamaño y alineación de la [barra de herramientas del Editor de cuadro de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Cuando se selecciona un control, tiene un borde sombreado alrededor de ella con sólidos (activos) o "cuadros de tamaño" hueco (inactivo) pequeños cuadros que aparecen en el borde de selección. Cuando se seleccionan varios controles, el control dominante tiene controladores de tamaño sólido; todos los controles seleccionados tienen controladores de tamaño hueco.

Al cambiar el tamaño o alinear varios controles, el **diálogo** editor usa el "control dominante" para determinar cómo los otros controles o un tamaño alineados. De forma predeterminada, el control dominante es el primer control seleccionado.

- [Selección de varios controles](../windows/selecting-multiple-controls.md)

- [Especificación del control dominante](../windows/specifying-the-dominant-control.md)

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles](../mfc/controls-mfc.md)