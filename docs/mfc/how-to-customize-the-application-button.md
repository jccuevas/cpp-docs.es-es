---
title: 'Cómo: personalizar el botón aplicación | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 828886e6a5c4891e1fd7e1d820ee00542e052cc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351369"
---
# <a name="how-to-customize-the-application-button"></a>Cómo: Personalizar el botón Aplicación
Al hacer clic en el botón de la aplicación, se muestra un menú de comandos. Normalmente, el menú contiene comandos relacionados con el archivo como **abiertos**, **guardar**, **impresión**, y **Exit**.  
  
 ![Botón de aplicación de la cinta de opciones de MFC](../mfc/media/application_button.png "application_button")  
  
 Para personalizar el botón aplicación, abrirlo en el **propiedades** ventana, modificar sus propiedades y, a continuación, obtener una vista previa del control de la cinta de opciones.  
  
### <a name="to-open-the-application-button-in-the-properties-window"></a>Para abrir el botón de la aplicación en la ventana Propiedades  
  
1.  En Visual Studio, en el **vista** menú, haga clic en **vista de recursos**.  
  
2.  En **vista de recursos**, haga doble clic en el recurso de cinta de opciones para mostrarla en la superficie de diseño.  
  
3.  En la superficie de diseño, haga clic en el menú del botón de aplicación y, a continuación, haga clic en **propiedades**.  
  
## <a name="application-button-properties"></a>Propiedades de botón de la aplicación  
 En la tabla siguiente define las propiedades del botón de aplicación.  
  
|Property|de esquema JSON|  
|--------------|----------------|  
|**Botones**|Contiene la colección de hasta tres botones que aparecen en la esquina inferior derecha del menú de aplicación.|  
|**Título**|Especifica el texto del control. A diferencia de otros elementos de la cinta de opciones, el botón de la aplicación no muestra el texto del título. En su lugar, el texto se utiliza para mejorar la accesibilidad.|  
|**Imagen HDPI**|Especifica el identificador de la gran número de puntos por pulgada icono de botón de aplicación (HDPI). Cuando la aplicación se ejecuta en un monitor alta de PPP, **HDPI imagen** se utiliza en lugar de **imagen**.|  
|**Imágenes de gran tamaño HDPI**|Especifica el identificador de las imágenes de gran tamaño alta de PPP. Cuando la aplicación se ejecuta en un monitor alta de PPP, **HDPI Large Images** se utiliza en lugar de **Large Images**.|  
|**Imágenes pequeñas HDPI**|Especifica el identificador de las imágenes pequeños alta de PPP. Cuando la aplicación se ejecuta en un monitor alta de PPP, **imágenes pequeñas HDPI** se utiliza en lugar de **imágenes pequeñas**.|  
|**ID**|Especifica el identificador del control.|  
|**Image**|Especifica el identificador del icono de botón de aplicación. El icono es un mapa de bits de 26 x 26 de 32 bits con transparencia alfa. Las partes transparentes del icono se resaltan cuando se hace clic en o se mantiene el mouse sobre el botón de la aplicación.|  
|**Claves**|Especifica la cadena que se muestra cuando se habilita la exploración de la información de clave. Sugerencia de la clave de navegación está habilitada cuando se presiona la tecla ALT.|  
|**Imágenes de gran tamaño**|Especifica el identificador de la imagen que contiene una serie de iconos de 32 x 32. Los iconos se usan con los botones de la colección de elementos de la principal.|  
|**Elementos principales**|Contiene una colección de elementos de menú que aparecen en el menú de la aplicación.|  
|**Título MRU**|Especifica el texto que se muestra en el panel de lista de usados recientemente.|  
|**Imágenes pequeñas**|Especifica el identificador de la imagen que contiene una serie de iconos de 16 x 16. Los iconos son utilizados por los botones de la colección de botones.|  
|**Uso**|Habilita o deshabilita el panel de lista de usados recientemente. Aparecerá el panel de lista de usados recientemente en el menú de la aplicación.|  
|**Ancho**|Especifica el ancho en píxeles, del panel de lista de usados recientemente.|  
  
 El menú de la aplicación no aparece en la superficie de diseño. Para verlo, debe obtener una vista previa de la cinta de opciones o ejecutar la aplicación.  
  
#### <a name="to-preview-the-ribbon-control"></a>Para obtener una vista previa del control de la cinta de opciones  
  
-   En el **barra de herramientas del Editor de Ribbon**, haga clic en **Ribbon de prueba**.  
  
## <a name="see-also"></a>Vea también  
 [Diseñador de la cinta de opciones (MFC)](../mfc/ribbon-designer-mfc.md)

