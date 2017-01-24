---
title: "C&#243;mo: Personalizar la barra de herramientas de acceso r&#225;pido | Microsoft Docs"
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
  - "barra de herramientas de acceso rápido, personalización"
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Personalizar la barra de herramientas de acceso r&#225;pido
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La barra de herramientas de acceso rápido \(QAT\) es una barra de herramientas personalizable que contiene un conjunto de comandos que se muestran junto al botón de la aplicación o en las pestañas de la categoría.  La ilustración siguiente se muestra una barra de herramientas de acceso rápido típica.  
  
 ![Barra de herramientas de acceso rápido de la cinta de opciones de MFC](../mfc/media/quick_access_toolbar.png "Quick\_Access\_Toolbar")  
  
 Para personalizar la barra de herramientas de acceso rápido, ábralo en la ventana de **Propiedades** , modifique los comandos, y después genere una vista previa del control de cinta.  
  
### Para abrir la barra de herramientas de acceso rápido en la ventana Propiedades  
  
1.  En Visual Studio, en el menú de **Visualización** , haga clic en **vista de recursos**.  
  
2.  En **vista de recursos**, haga doble clic en el recurso de la cinta de opciones para mostrarla en la superficie de diseño.  
  
3.  En la superficie de diseño, haga clic con el botón secundario en el menú de la barra de herramientas de acceso rápido y haga clic en **Propiedades**.  
  
## Propiedades de la barra de herramientas de acceso rápido  
 La tabla siguiente define las propiedades de la barra de herramientas de acceso rápido.  
  
|Propiedad|Definición|  
|---------------|----------------|  
|Posición de QAT|Especifica la posición de la barra de herramientas de acceso rápido cuando se inicia la aplicación.  La posición puede ser **Por encima** o **Por debajo** el control de cinta.|  
|Elementos de QAT|Especifica los comandos que están disponibles para la barra de herramientas de acceso rápido.|  
  
#### Para agregar o quitar comandos en la barra de herramientas de acceso rápido  
  
1.  En la ventana de **Propiedades** , el tecleo **Elementos de QAT**, y haga clic en los puntos suspensivos **\(...\)**.  
  
2.  En el cuadro de diálogo de **Editor de elementos de QAT** , utilice los botones de **Add** y de **Quitar** para modificar la lista de comandos de la barra de herramientas de acceso rápido.  
  
3.  Si desea un comando aparezca en la barra de herramientas de acceso rápido y el menú de la barra de herramientas de acceso rápido, seleccione el cuadro situado junto al comando.  Si desea que el comando aparezca únicamente en el menú, desactive la casilla.  
  
## Obtener una vista previa de la cinta de opciones  
 Los comandos de la barra de herramientas de acceso rápido no aparecen en la superficie de diseño.  Para verlos, debe obtener una vista previa de la cinta de opciones o ejecutar la aplicación.  
  
#### Para obtener una vista previa del control de la cinta de opciones  
  
-   En **Barra de herramientas del editor de la cinta de opciones**, haga clic en **Ribbon de prueba**.  
  
## Vea también  
 [Diseñador de la cinta de opciones \(MFC\)](../mfc/ribbon-designer-mfc.md)