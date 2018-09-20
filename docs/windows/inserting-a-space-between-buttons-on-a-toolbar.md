---
title: Insertar un espacio entre los botones de una barra de herramientas (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
ms.assetid: 4925ea6b-5d3a-4949-a920-bf371a37e529
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4c205d6f800682cb67749a73f57b1c35d03de61
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397460"
---
# <a name="inserting-a-space-between-buttons-on-a-toolbar-c"></a>Insertar un espacio entre los botones de una barra de herramientas (C++)

En general, para insertar un espacio entre los botones, sencillamente arrástrelos para separarlos entre sí en la barra de herramientas. Para quitar espacio, arrástrelos hacia entre sí.

### <a name="to-insert-a-space-before-a-button-that-is-not-followed-by-a-space"></a>Para insertar un espacio delante de un botón que no va seguido de un espacio

1. Arrastre el botón a la derecha o hacia abajo hasta que se superpone sobre el botón siguiente acerca de la mitad.

### <a name="to-insert-a-space-before-a-button-which-is-followed-by-a-space-and-to-retain-that-trailing-space"></a>Puede insertar un espacio delante de un botón que va seguido de un espacio y conservar espacio final

1. Arrastre el botón hasta que el borde derecho o inferior, simplemente es tocar el botón siguiente o se superpone a él.

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-close-up-that-following-space"></a>Para insertar un espacio delante de un botón que va seguido de un espacio y cerrar espacio siguiente

1. Arrastre el botón a la derecha o hacia abajo hasta que se superpone sobre el botón siguiente acerca de la mitad.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

MFC o ATL

## <a name="see-also"></a>Vea también

[Creación, migración y edición de botones de la barra de herramientas](../windows/creating-moving-and-editing-toolbar-buttons.md)<br/>
[Editor de barras de herramientas](../windows/toolbar-editor.md)