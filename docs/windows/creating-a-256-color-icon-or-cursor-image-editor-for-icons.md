---
title: Crear un icono de 256 colores o el Cursor (Editor de imágenes para iconos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1d6e3af00bfe906a1954f7fc1d2b0af1ea52945e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415920"
---
# <a name="creating-a-256-color-icon-or-cursor-image-editor-for-icons"></a>Crear un nuevo icono o cursor de 256 colores (Editor de imágenes para iconos)

Mediante el **imagen** editor, iconos y cursores pueden ser de tamaño grande (64 x 64) con una paleta de 256 colores para elegir. Después de crear el recurso, se selecciona un estilo de imagen de dispositivo.

### <a name="to-create-a-256-color-icon-or-cursor"></a>Para crear un icono de 256 colores o cursor

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc y elija **Insertar recurso** en el menú contextual. (Si ya tiene un recurso de imagen existente en el archivo .rc, como un cursor, puede hacer simplemente clic en el **Cursor** carpeta y seleccione **insertar Cursor** en el menú contextual.)

   > [!NOTE] 
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. En el [cuadro de diálogo Insertar recurso](../windows/add-resource-dialog-box.md), seleccione **icono** o **Cursor** y haga clic en **New**.

3. En el **imagen** menú, haga clic en **nueva imagen de dispositivo**.

4. Seleccione el estilo de imagen de 256 colores que desee.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Uso de la paleta de 256 colores](../windows/using-the-256-color-palette-image-editor-for-icons.md)<br/>
[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Iconos y cursores: recursos de imagen para dispositivos de presentación](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)