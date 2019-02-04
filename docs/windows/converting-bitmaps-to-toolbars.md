---
title: Convertir mapas de bits en barras de herramientas (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.newtoolbarresource
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
ms.openlocfilehash: 31b684ff72e970a6b09748b3925564b0b372d339
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702705"
---
# <a name="converting-bitmaps-to-toolbars-c"></a>Convertir mapas de bits en barras de herramientas (C++)

Puede crear una nueva barra de herramientas en un proyecto de C++ mediante la conversión de un mapa de bits. El gráfico de mapa de bits se convierte a las imágenes de botón para una barra de herramientas. Normalmente, el mapa de bits contiene varias imágenes de botón en un mapa de bits única, con una imagen para cada botón. Las imágenes pueden tener cualquier tamaño; el valor predeterminado es 16 píxeles de ancho y el alto de la imagen. Puede especificar el tamaño de las imágenes de botón en el **nuevo recurso de barra de herramientas** cuadro de diálogo cuando se elige **barra de herramientas del Editor** desde el **imagen** menú mientras está en el editor de imágenes.

El **nuevo recurso de barra de herramientas** cuadro de diálogo permite especificar el ancho y alto de los botones que se va a agregar a un recurso de barra de herramientas en un proyecto de C++. El valor predeterminado es 16 x 15 píxeles.

Un mapa de bits que se usa para crear una barra de herramientas tiene un ancho máximo de 2048. Por tanto, si establece la **ancho del botón** en 512, solo puede tener cuatro botones. Si establece el ancho en 513, solo puede tener tres botones.

El cuadro de diálogo tiene las siguientes propiedades:

|Property|Descripción|
|---|---|
|**Ancho del botón**|Proporciona un espacio para escribir el ancho de los botones de barra de herramientas que está convirtiendo de un recurso de mapa de bits a un recurso de barra de herramientas. Las imágenes se recortan al ancho y alto especificados, y se ajustan los colores para utilizar colores de la barra de herramientas estándar (16 colores).|
|**Alto de botón**|Proporciona un espacio para escribir el alto de los botones de barra de herramientas que está convirtiendo de un recurso de mapa de bits a un recurso de barra de herramientas. Las imágenes se recortan al ancho y alto especificados, y se ajustan los colores para utilizar colores de la barra de herramientas estándar (16 colores).|

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-convert-bitmaps-to-a-toolbar"></a>Convertir mapas de bits a una barra de herramientas

1. Abrir un recurso de mapa de bits existente en el [editor de imágenes](../windows/image-editor-for-icons.md). (Si el mapa de bits no está en el archivo .rc, haga clic en el archivo .rc, elija **importación** en el menú contextual, navegue hasta el mapa de bits que se va a agregar al archivo .rc y luego seleccione **abierto**.)

1. Desde el **imagen** menú, elija **barra de herramientas del Editor**.

   El **nuevo recurso de barra de herramientas** aparece el cuadro de diálogo. Puede cambiar el ancho y alto de las imágenes de icono para que coincida con el mapa de bits. La imagen de la barra de herramientas, a continuación, se muestra en el editor de la barra de herramientas.

1. Para finalizar la conversión, cambie el comando **ID** del botón con el [ventana propiedades](/visualstudio/ide/reference/properties-window). Escriba el nuevo **ID** o seleccione un **ID** en la lista desplegable.

   > [!TIP]
   > El **propiedades** ventana contiene un botón de alfiler en la barra de título. Al seleccionar este botón habilita o deshabilita **Ocultar automáticamente** para la ventana. Para recorrer rápidamente todas las propiedades del botón de barra de herramientas sin tener que volver a abrir las ventanas de propiedades individuales, activar **Ocultar automáticamente** desactivar por lo que la **propiedades** ventana permanece estacionario.

También puede cambiar los identificadores de comando de los botones de la barra de herramientas nueva mediante el [ventana propiedades](/visualstudio/ide/reference/properties-window). Para obtener información sobre cómo editar la nueva barra de herramientas, consulte [crear, mover y editar botones de la barra de herramientas](../windows/creating-moving-and-editing-toolbar-buttons.md).

## <a name="requirements"></a>Requisitos

MFC o ATL

## <a name="see-also"></a>Vea también

[Creación de nuevas barras de herramientas](../windows/creating-new-toolbars.md)<br/>
[Editor de barras de herramientas](../windows/toolbar-editor.md)<br/>
[Propiedades de los botones de la barra de herramientas](../windows/toolbar-button-properties.md)<br/>
