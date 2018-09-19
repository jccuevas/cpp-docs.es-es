---
title: Editar partes de una imagen (Editor de imágenes para iconos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
ms.assetid: ff4f5fef-71a4-4fd8-825e-049399fed391
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0380fd6fc9b37c4d7458453398cfbd2ce6699234
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607838"
---
# <a name="editing-parts-of-an-image-image-editor-for-icons"></a>Editar partes de una imagen (Editor de imágenes para iconos)

Puede realizar las operaciones de edición estándares, cortar, copiar, borrar y mover, en un [selección](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), si la selección es la imagen completa o solamente una parte de ella. Dado que el **imagen** editor usa el **Portapapeles de Windows**, puede transferir imágenes entre el **imagen** editor y otras aplicaciones para Windows.

Además, puede cambiar la selección, si incluye toda la imagen o sólo una parte.

### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Para cortar la selección actual y colocarlo en el Portapapeles

1. Haga clic en **cortar** en el **editar** menú.

### <a name="to-copy-the-selection"></a>Para copiar la selección

1. Coloque el puntero dentro del borde de selección o en cualquier lugar en el mismo, excepto los controladores de tamaño.

2. Mantenga presionada la **Ctrl** mientras arrastra la selección a una nueva ubicación de la clave. No se modifica el área de la selección original.

3. Para copiar la selección en la imagen en su ubicación actual, haga clic fuera del cursor de selección.

### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Para pegar el contenido del Portapapeles en una imagen

1. Desde el **editar** menú, elija **pegar**.

   El contenido del Portapapeles, rodeado por el borde de selección, aparece en la esquina superior izquierda del panel.

2. Coloque el puntero en el borde de selección y arrástrela hasta la ubicación deseada en la imagen.

3. Para fijar la imagen en su nueva ubicación, haga clic fuera del borde de selección.

### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Para eliminar la selección actual sin moverlo en el Portapapeles

1. Desde el **editar** menú, elija **eliminar**.

   El área de la selección original se rellena con el color de fondo actual.

   > [!NOTE]
   > Puede tener acceso a la **cortar**, **copia**, **pegar**, y **eliminar** comandos, haga clic con el botón derecho en el **devistaderecursos** ventana.

### <a name="to-move-the-selection"></a>Para mover la selección

1. Coloque el puntero dentro del borde de selección o en cualquier lugar en el mismo, excepto los controladores de tamaño.

2. Arrastre la selección a su nueva ubicación.

3. Para fijar la selección en la imagen en su nueva ubicación, haga clic fuera del borde de selección.

Para obtener más información sobre cómo dibujar con una selección, consulte [crear un pincel personalizado](../windows/creating-a-custom-brush-image-editor-for-icons.md).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)  
[Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)