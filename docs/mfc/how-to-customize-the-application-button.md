---
title: "C&#243;mo: Personalizar el bot&#243;n Aplicaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "botón de aplicación, personalizar"
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Personalizar el bot&#243;n Aplicaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al hacer clic en el botón de la aplicación, un menú de comandos se muestra.  Normalmente, el menú contiene comandos archivo \(el archivo relacionados como **Abierta**, **Guardar**, **Impresión**, y **Salir**.  
  
 ![Botón de aplicación de cinta de opciones de MFC](../mfc/media/application_button.png "Application\_Button")  
  
 Para personalizar el botón de la aplicación, ábralo en la ventana de **Propiedades** , modifique sus propiedades, y después genere una vista previa del control de cinta.  
  
### Para abrir el botón de la aplicación en la ventana Propiedades  
  
1.  En Visual Studio, en el menú de **Visualización** , haga clic en **vista de recursos**.  
  
2.  En **vista de recursos**, haga doble clic en el recurso de la cinta de opciones para mostrarla en la superficie de diseño.  
  
3.  En la superficie de diseño, haga clic con el botón secundario en el menú del botón de la aplicación y haga clic en **Propiedades**.  
  
## Propiedades de los botones de la aplicación  
 La tabla siguiente define las propiedades de los botones de la aplicación.  
  
|Propiedad|Definición|  
|---------------|----------------|  
|**Botones**|Contiene la colección de hasta tres botones que aparecen en la esquina inferior derecha del menú de la aplicación.|  
|**Leyenda**|Especifica el texto del control.  A diferencia de otros elementos de cinta de opciones, el botón de la aplicación no muestra el texto de la leyenda.  En su lugar, el texto se utiliza para la accesibilidad.|  
|**Imagen de HDPI**|Especifica el identificador de alto icono de botón de la aplicación de \(HDPI\) de puntos por pulgada.  Cuando la aplicación se ejecuta en un alto PPP monitor, **Imagen de HDPI** se utiliza en lugar de **Proceso**.|  
|**Imágenes grandes de HDPI**|Especifica el identificador de las imágenes grandes height PPP.  Cuando la aplicación se ejecuta en un alto PPP monitor, **Imágenes grandes de HDPI** se utiliza en lugar de **Imágenes grandes**.|  
|**Pequeñas imágenes de HDPI**|Especifica el identificador de las pequeñas imágenes de alto PPP.  Cuando la aplicación se ejecuta en un alto PPP monitor, **Pequeñas imágenes de HDPI** se utiliza en lugar de **Pequeñas imágenes**.|  
|**ID**|Especifica el identificador del control.|  
|**Image**|Especifica el identificador del icono de botón de la aplicación.  El icono es un mapa de bits de 32 bits 26x26 que tiene transparencia alfa.  Resaltan partes transparentes de icono cuando el botón de la aplicación se hace clic o se mantiene el mouse sobre.|  
|**Claves**|Especifica la cadena que se muestra cuando se habilita la navegación de la tecla\- sugerencia.  Se habilita la navegación de la Tecla\- sugerencia al presionar ALT.|  
|**Imágenes grandes**|Especifica el identificador de la imagen que contiene una serie de los iconos 32x32.  Los iconos son utilizados por los botones en la colección elementos de Main.|  
|**Elementos primarios**|Contiene una colección de elementos de menú que aparecen en el menú de la aplicación.|  
|**Leyenda MRU**|Especifica el texto mostrado en el panel de lista más recientes de.|  
|**Pequeñas imágenes**|Especifica el identificador de la imagen que contiene una serie de los iconos 16x16.  Los iconos son utilizados por los botones en la colección de los botones.|  
|**Utilice**|Habilita o deshabilita el panel de lista más recientes de.  El panel de lista de Recientes aparece en el menú de la aplicación.|  
|**Ancho**|Especifica el ancho en píxeles del panel de lista más recientes de.|  
  
 El menú de la aplicación no aparece en la superficie de diseño.  Para verlo, debe obtener una vista previa de la cinta de opciones o ejecutar la aplicación.  
  
#### Para obtener una vista previa del control de la cinta de opciones  
  
-   En **Barra de herramientas del editor de la cinta de opciones**, haga clic en **Ribbon de prueba**.  
  
## Vea también  
 [Diseñador de la cinta de opciones \(MFC\)](../mfc/ribbon-designer-mfc.md)