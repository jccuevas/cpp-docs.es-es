---
title: 'Cómo: Personalizar el botón Aplicación'
ms.date: 11/19/2018
helpviewer_keywords:
- application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
ms.openlocfilehash: ba29e9ad65e0bb1d2163e4051c7c7b53664d8817
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175332"
---
# <a name="how-to-customize-the-application-button"></a>Cómo: Personalizar el botón Aplicación

Al hacer clic en el botón de la aplicación, se muestra un menú de comandos. Normalmente, el menú contiene comandos relacionados con el archivo como **abierto**, **guardar**, **impresión**, y **Exit**.

![Botón de aplicación de cinta de opciones MFC](../mfc/media/application_button.png "botón de aplicación de cinta de opciones MFC")

Para personalizar el botón de la aplicación, ábralo en el **propiedades** , modificar sus propiedades y, a continuación, obtener una vista previa del control de la cinta de opciones.

### <a name="to-open-the-application-button-in-the-properties-window"></a>Para abrir el botón de la aplicación en la ventana Propiedades

1. En Visual Studio, en el **vista** menú, haga clic en **vista de recursos**.

1. En **vista de recursos**, haga doble clic en el recurso de cinta para que se muestre en la superficie de diseño.

1. En la superficie de diseño, haga clic en el menú del botón de aplicación y, a continuación, haga clic en **propiedades**.

## <a name="application-button-properties"></a>Propiedades del botón aplicación

En la tabla siguiente define las propiedades del botón aplicación.

|Property|de esquema JSON|
|--------------|----------------|
|**Botones**|Contiene la colección de hasta tres botones que aparecen en la esquina inferior derecha del menú de aplicación.|
|**Título**|Especifica el texto del control. A diferencia de otros elementos de la cinta de opciones, el botón de la aplicación no muestra el texto del título. En su lugar, el texto se utiliza para mejorar la accesibilidad.|
|**HDPI Image**|Especifica el identificador de los muchos puntos por pulgada icono de botón de la aplicación (HDPI). Cuando la aplicación se ejecuta en un monitor alta de PPP, **HDPI Image** se utiliza en lugar de **imagen**.|
|**HDPI Large Images**|Especifica el identificador de las imágenes de gran tamaño de PPP alta. Cuando la aplicación se ejecuta en un monitor alta de PPP, **HDPI Large Images** se utiliza en lugar de **Large Images**.|
|**HDPI Small Images**|Especifica el identificador de las imágenes pequeñas de PPP alta. Cuando la aplicación se ejecuta en un monitor alta de PPP, **HDPI Small Images** se utiliza en lugar de **imágenes pequeñas**.|
|**ID**|Especifica el identificador del control.|
|**Image**|Especifica el identificador del icono de botón de aplicación. El icono es un mapa de bits de 26 x 26 de 32 bits que tenga transparencia alfa. Cuando se hace clic o al mantener el mouse sobre el botón de la aplicación, se resaltan las partes transparentes del icono.|
|**Claves**|Especifica la cadena que se muestra cuando se habilita la navegación de clave de sugerencia. Sugerencia de la clave de navegación está habilitada cuando se presiona ALT.|
|**Imágenes de gran tamaño**|Especifica el identificador de la imagen que contiene una serie de iconos de 32 x 32. Los iconos se usan por los botones en la colección de elementos de la principal.|
|**Elementos principales**|Contiene una colección de elementos de menú que aparece en el menú de la aplicación.|
|**Título MRU**|Especifica el texto que se muestra en el panel de lista de elementos recientes.|
|**Imágenes pequeñas**|Especifica el identificador de la imagen que contiene una serie de iconos de 16 x 16. Los iconos se usan con los botones de la colección de botones.|
|**Use**|Habilita o deshabilita el panel de lista de elementos recientes. El panel de lista de elementos recientes aparece en el menú de la aplicación.|
|**Ancho**|Especifica el ancho en píxeles, del panel de lista de elementos recientes.|

El menú de la aplicación no aparece en la superficie de diseño. Para verlo, debe obtener una vista previa de la cinta de opciones o ejecutar la aplicación.

#### <a name="to-preview-the-ribbon-control"></a>Para obtener una vista previa del control de la cinta de opciones

- En el **barra de herramientas del Editor de Ribbon**, haga clic en **Ribbon de prueba**.

## <a name="see-also"></a>Vea también

[Diseñador de la cinta de opciones (MFC)](../mfc/ribbon-designer-mfc.md)
