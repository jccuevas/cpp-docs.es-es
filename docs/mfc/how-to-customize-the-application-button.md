---
title: 'Cómo: Personalizar el botón Aplicación'
ms.date: 09/07/2019
helpviewer_keywords:
- application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
ms.openlocfilehash: 9160e602848adf8dc95c840d702e0b1a1b2f9049
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620037"
---
# <a name="how-to-customize-the-application-button"></a>Cómo: Personalizar el botón Aplicación

Al hacer clic en el botón aplicación, se muestra un menú de comandos. Normalmente, el menú contiene comandos relacionados con archivos, como **abrir**, **Guardar**, **Imprimir**y **salir**.

![Botón de aplicación de cinta de opciones de MFC](../mfc/media/application_button.png "Botón de aplicación de cinta de opciones de MFC")

Para personalizar el botón aplicación, ábralo en la ventana **propiedades** (en **vista de recursos**), modifique sus propiedades y, a continuación, obtenga una vista previa del control de la cinta de opciones.

### <a name="to-open-the-application-button-in-the-properties-window"></a>Para abrir el botón aplicación en el ventana Propiedades

1. En Visual Studio, en el menú **Ver** , haga clic en **vista de recursos**.

1. En **vista de recursos**, haga doble clic en el recurso de la cinta de opciones para mostrarlo en la superficie de diseño.

1. En la superficie de diseño, haga clic con el botón secundario en el menú del botón de aplicación y después haga clic en **propiedades**.

## <a name="application-button-properties"></a>Propiedades de botón de aplicación

En la tabla siguiente se definen las propiedades del botón aplicación.

|Propiedad|Definición|
|--------------|----------------|
|**Botones**|Contiene la colección de hasta tres botones que aparecen en la esquina inferior derecha del menú de la aplicación.|
|**Caption**|Especifica el texto del control. A diferencia de otros elementos de la cinta de opciones, el botón aplicación no muestra el texto de la leyenda. En su lugar, el texto se utiliza para la accesibilidad.|
|**Imagen de HDPI**|Especifica el identificador del icono del botón de aplicación de puntos máximos por pulgada (HDPI). Cuando la aplicación se ejecuta en un monitor de PPP alto, se usa la **imagen HDPI** en lugar de la **imagen**.|
|**Imágenes grandes de HDPI**|Especifica el identificador de las imágenes grandes de PPP alto. Cuando la aplicación se ejecuta en un monitor de PPP alto, se utiliza **HDPI imágenes grandes** en lugar de **imágenes grandes**.|
|**HDPI imágenes pequeñas**|Especifica el identificador de las imágenes pequeñas de PPP altas. Cuando la aplicación se ejecuta en un monitor de PPP alto, se usa **HDPI pequeñas imágenes** en lugar de **imágenes pequeñas**.|
|**Id**|Especifica el identificador del control.|
|**Imagen**|Especifica el identificador del icono del botón de la aplicación. El icono es un mapa de bits 26x26 de 32 bits con transparencia alfa. Las partes transparentes del icono se resaltan cuando se hace clic o se mantiene el mouse sobre el botón de la aplicación.|
|**Claves**|Especifica la cadena que se muestra cuando está habilitada la navegación con sugerencias de teclas. La navegación con sugerencias de teclas está habilitada al presionar ALT.|
|**Imágenes grandes**|Especifica el identificador de la imagen que contiene una serie de iconos de 32x32. Los botones de la colección de elementos principales usan los iconos.|
|**Elementos principales**|Contiene una colección de elementos de menú que aparecen en el menú de la aplicación.|
|**Título MRU**|Especifica el texto que se muestra en el panel de lista reciente.|
|**Imágenes pequeñas**|Especifica el identificador de la imagen que contiene una serie de iconos 16x16. Los botones de la colección de botones usan los iconos.|
|**Uso**|Habilita o deshabilita el panel de lista reciente. El panel lista reciente aparece en el menú aplicación.|
|**Width**|Especifica el ancho en píxeles del panel de lista reciente.|

El menú aplicación no aparece en la superficie de diseño. Para verlo, debe obtener una vista previa de la cinta de opciones o ejecutar la aplicación.

#### <a name="to-preview-the-ribbon-control"></a>Para obtener una vista previa del control Ribbon

- En la **barra de herramientas del editor**de la cinta de opciones, haga clic en **probar cinta**.

## <a name="see-also"></a>Consulte también

[Diseñador de la cinta de opciones (MFC)](ribbon-designer-mfc.md)
