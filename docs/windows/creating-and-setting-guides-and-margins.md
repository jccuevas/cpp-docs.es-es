---
title: Creación y configuración, guías y márgenes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- guides, clearing
- guides
- Dialog Editor [C++], guides and margins
- dialog box controls [C++], placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
ms.assetid: fafa4545-8f00-436f-b590-300e76601156
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0083affb850f35941ca18709785c9bd5e4fc35e8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378259"
---
# <a name="creating-and-setting-guides-and-margins"></a>Crear y establecer las guías y los márgenes

Si va a mover controles, agregar controles o reorganizar un diseño actual, las guías pueden ayudarle a alinear los controles con precisión dentro de un cuadro de diálogo. Las guías aparecen en azul las líneas de puntos en el cuadro de diálogo que aparece en el editor y flechas correspondientes en las reglas (en la parte superior y en el lado izquierdo de la **diálogo** editor).

Cuando se crea un cuadro de diálogo, se proporcionan cuatro márgenes. Los márgenes son guías modificadas, que aparecen como líneas de puntos azules.

### <a name="to-create-a-guide"></a>Para crear una guía

1. Dentro de la regla, haga clic una vez para crear a una guía. (Un solo clic, crea un nuevo guía; hacer doble clic en los lanzamientos de la [cuadro de diálogo de configuración de guía](../windows/guide-settings-dialog-box.md) en el que puede especificar la configuración de la guía.)

### <a name="to-set-a-guide"></a>Para establecer una guía

1. En el cuadro de diálogo, haga clic en la guía y arrástrelo a una nueva posición. (También puede hacer clic en la flecha de la regla para arrastrar a la guía asociada.)

   Las coordenadas de la guía se muestran en la barra de estado en la parte inferior de la ventana y en la regla. Mueva el puntero sobre la flecha de la regla para mostrar la posición exacta de la guía.

### <a name="to-delete-a-guide"></a>Para eliminar una guía

1. Arrastre a la guía fuera del cuadro de diálogo.

\- o -

- Arrastre la flecha correspondiente fuera de la regla.

### <a name="to-move-margins"></a>Para mover los márgenes

1. Arrastre el margen a la nueva posición.

   Para que desaparezca un margen, mueva el margen a una posición cero. Para recuperar el margen, coloque el puntero sobre el margen de la posición cero y mueva el margen a posición.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Estados del Editor de cuadros de diálogo (guías y cuadrículas)](../windows/dialog-editor-states-guides-and-grids.md)<br/>
[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)