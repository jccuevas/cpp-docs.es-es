---
title: Establecer un Cursor&#39;s punto crucial (Editor de imágenes para iconos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], hot spots
- hot spots
ms.assetid: a610388a-45c8-43cd-98a2-fd31f29238b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9246d7a26c9764e31cca9c861ec0a15d4792c115
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389103"
---
# <a name="setting-a-cursor39s-hot-spot-image-editor-for-icons"></a>Establecer un Cursor&#39;s punto crucial (Editor de imágenes para iconos)

La zona activa de una [cursor](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md) es el punto en que Windows hace referencia en el seguimiento de la posición del cursor. De forma predeterminada, la zona activa se establece en la esquina superior izquierda del cursor (coordenadas 0,0). El **Hotspot** propiedad en el [ventana propiedades](/visualstudio/ide/reference/properties-window) muestra las coordenadas de la zona activa.

### <a name="to-set-a-cursors-hot-spot"></a>Establecer zona activa del cursor

1. En el [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md), haga clic en el **establecer zona activa** herramienta.

2. Haga clic en el píxel que desee designar como zona activa del cursor.

   El **Hotspot** propiedad en el **propiedades** ventana muestra las nuevas coordenadas.

   > [!TIP]
   > Información sobre herramientas aparece cuando desplaza el cursor sobre un botón de barra de herramientas. Estas sugerencias pueden ayudarle a identificar la función de cada botón.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Iconos y cursores: recursos de imagen para dispositivos de presentación](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)