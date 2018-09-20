---
title: Uso de la paleta de 256 colores (Editor de imágenes para iconos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 256-color palette
- colors [C++], icons and cursors
- cursors [C++], color
- color palettes, 256-color
- palettes, 256-color
- icons, color
ms.assetid: 1506ed00-669b-4a21-b1a4-39b6a84a78bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d9a8952ccdf4477f263a2fb960020e7abba19546
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418156"
---
# <a name="using-the-256-color-palette-image-editor-for-icons"></a>Utilizar la paleta de 256 colores (Editor de imágenes para iconos)

Para dibujar con una selección de la paleta de 256 colores, deberá seleccionar los colores de la **colores** paleta en la [ventana colores](../windows/colors-window-image-editor-for-icons.md).

### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Para elegir un color de la paleta de 256 colores para iconos grandes

1. Seleccione el icono o cursor grande o cree un nuevo icono o cursor grande.

2. Elija un color de los 256 colores mostrados en la **colores** paleta en la **colores** ventana.

   El color seleccionado se convertirá en el color actual en el **colores** paleta en la **colores** ventana.

   > [!NOTE]
   > La paleta inicial que se usa para imágenes de 256 colores coincide con la paleta devuelta por la `CreateHalftonePalette` API de Windows. Todos los iconos previstos para el shell de Windows deben usar esta paleta para impedir el parpadeo durante la realización de la paleta.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Crear un nuevo icono o cursor de 256 colores](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)<br/>
[Iconos y cursores: recursos de imagen para dispositivos de presentación](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)