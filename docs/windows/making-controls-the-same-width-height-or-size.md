---
title: Hacer que los controles del mismo ancho, alto o tamaño | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Make Same Size command
- controls [C++], sizing
ms.assetid: 94b50613-67e2-497b-a2b6-6d98dccfd345
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fe7831c12a9ea68525334a55aec5a1fa2ecb847d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405117"
---
# <a name="making-controls-the-same-width-height-or-size"></a>Hacer que los controles tengan el mismo ancho, el mismo alto o el mismo tamaño

Puede cambiar el tamaño de un grupo de controles en función del tamaño del control principal. También puede [cambiar el tamaño de un control según las dimensiones del texto del título](../windows/sizing-individual-controls.md).

### <a name="to-make-controls-the-same-width-height-or-size"></a>Para hacer que controla el mismo ancho, alto o tamaño

1. [Seleccione los controles](../windows/selecting-multiple-controls.md) que desea cambiar el tamaño.

   El control seleccionado en primer lugar de la serie es el control dominante. El tamaño final de los controles en el grupo depende del tamaño del control principal. Para obtener más información sobre cómo seleccionar el control dominante, vea [especificar el Control dominante](../windows/specifying-the-dominant-control.md).

2. Desde el **formato** menú, elija **Igualar tamaño**, a continuación, elija uno de los siguientes comandos:

   - **Ambos**

   - **Alto**

   - **Ancho**

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles](../mfc/controls-mfc.md)