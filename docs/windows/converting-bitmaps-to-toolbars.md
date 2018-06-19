---
title: Convertir mapas de bits en barras de herramientas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor, converting bitmaps
- toolbars [C++], converting bitmaps
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e80bee7ef9bfe52abf63ac959475c5d8dbcf0ece
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872632"
---
# <a name="converting-bitmaps-to-toolbars"></a>Convertir mapas de bits en barras de herramientas
Puede crear una nueva barra de herramientas mediante la conversión de un mapa de bits. El gráfico del mapa de bits se convierte a las imágenes de botón de una barra de herramientas. Normalmente, el mapa de bits contiene varias imágenes de botón en un mapa de bits única, con una imagen para cada botón. Las imágenes pueden tener cualquier tamaño; el valor predeterminado es 16 píxeles de ancho y el alto de la imagen. Puede especificar el tamaño de las imágenes de botón en el [cuadro de diálogo nuevo recurso de barra de herramientas](../windows/new-toolbar-resource-dialog-box.md) cuando se elige la barra de herramientas del Editor de la **imagen** menú mientras está en el editor de imágenes.  
  
### <a name="to-convert-bitmaps-to-a-toolbar"></a>Convertir mapas de bits a una barra de herramientas  
  
1.  Abrir un recurso de mapa de bits existente en el [editor de imágenes](../windows/image-editor-for-icons.md). (Si el mapa de bits no está ya en el archivo .rc, haga clic en el archivo .rc, elija **importación** en el menú contextual, navegue hasta el mapa de bits que se va a agregar al archivo .rc y, a continuación, haga clic en **abiertos**.)  
  
2.  Desde el **imagen** menú, elija **barra de herramientas del Editor**.  
  
     El [cuadro de diálogo nuevo recurso de barra de herramientas](../windows/new-toolbar-resource-dialog-box.md) aparece. Puede cambiar el ancho y alto de las imágenes de icono para que coincida con el mapa de bits. A continuación, se muestra la imagen de la barra de herramientas en el editor de la barra de herramientas.  
  
3.  Para finalizar la conversión, cambie el comando **identificador** del botón con el [ventana propiedades](/visualstudio/ide/reference/properties-window). Escriba el nuevo **identificador** o seleccione un **ID** en la lista desplegable.  
  
    > [!TIP]
    >  La ventana Propiedades contiene un botón de alfiler en la barra de título. Al hacer clic en este botón se habilita o deshabilita la opción Ocultar automáticamente de la ventana. Para desplazarse rápidamente por todas las propiedades de botón de barra de herramientas sin tener que volver a abrir la ventana de propiedad individual, desactive Ocultar automáticamente para que la ventana Propiedades permanecerá estacionaria.  
  
 También puede cambiar los identificadores de comando de los botones en la barra de herramientas mediante el [ventana propiedades](/visualstudio/ide/reference/properties-window). Para obtener información sobre cómo editar la nueva barra de herramientas, consulte [crear, mover y editar botones de la barra de herramientas](../windows/creating-moving-and-editing-toolbar-buttons.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Requisitos  
  
 MFC o ATL  
  
## <a name="see-also"></a>Vea también  
 [Crear nuevas barras de herramientas](../windows/creating-new-toolbars.md)   
 [Editor de barras de herramientas](../windows/toolbar-editor.md)

