---
title: "Usar hojas de propiedades en una aplicaci&#243;n | Microsoft Docs"
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
  - "AddPage (método)"
  - "CPropertyPage (clase), estilos"
  - "Create (método) [C++], hojas de propiedades"
  - "recursos de cuadro de diálogo"
  - "plantillas de cuadro de diálogo, hojas de propiedades"
  - "hojas de propiedades del método DoModal"
  - "páginas de propiedades, hojas de propiedades"
  - "hojas de propiedades, acerca de las hojas de propiedades"
ms.assetid: 240654d4-152b-4e3f-af7b-44234339206e
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar hojas de propiedades en una aplicaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para utilizar una hoja de propiedades de la aplicación, realice los pasos siguientes:  
  
1.  Cree un recurso de plantilla de cuadro de diálogo para cada página de propiedades.  Tenga en cuenta que el usuario puede pasar de una página a otra, por lo que muestran cada página tan siempre posible.  
  
     Las plantillas de cuadro de diálogo para todas las páginas no tienen que ser del mismo tamaño.  El marco de trabajo usa el tamaño de la página mayor para determinar cuánto espacio se asignan en la hoja de propiedades para las páginas de propiedades.  
  
     Al crear el recurso de plantilla de cuadro de diálogo para una página de propiedades, debe especificar los estilos siguientes en la hoja de propiedades de las propiedades de diálogo:  
  
    -   Establezca el cuadro de edición de **caption** en la página de **General** al texto que desea que aparezca en la pestaña para esta página.  
  
    -   Establezca el cuadro de lista de **Estilo** en la página de **Estilos** a **Child**.  
  
    -   Establezca el cuadro de lista de **Borde** en la página de **Estilos** a **Thin**.  
  
    -   Asegúrese de que la casilla de **barra de título** en la página de **Estilos** está seleccionada.  
  
    -   Asegúrese de que la casilla de **Deshabilitado** en la página de **Más estilos** está seleccionada.  
  
2.  Cree [CPropertyPage](../mfc/reference/cpropertypage-class.md)\- clase derivada correspondiente a cada plantilla de diálogo página de propiedades.  Vea [Agregar una clase](../ide/adding-a-class-visual-cpp.md).  Elija `CPropertyPage` como clase base.  
  
3.  Cree las variables miembro para contener los valores de esta página de propiedades.  El proceso para agregar a variables miembros a una página de propiedades es exactamente igual que variables agregar miembros a un cuadro de diálogo, porque una página de propiedades es un cuadro de diálogo especializado.  Para obtener más información, vea [Definición de las variables miembro para Controles de cuadro de diálogo](../mfc/defining-member-variables-for-dialog-controls.md).  
  
4.  Crea un objeto de [CPropertySheet](../mfc/reference/cpropertysheet-class.md) en el código fuente.  Normalmente, se construye el objeto de `CPropertySheet` en el controlador del comando que muestra la hoja de propiedades.  Este objeto representa la hoja de propiedades completa.  Si crea una hoja de propiedades modal con la función de [DoModal](../Topic/CPropertySheet::DoModal.md) , el marco proporciona tres botones de comando de manera predeterminada: OK, delete, y se aplica.  El marco no crea ningún botón de comando para las hojas de propiedades no modal creadas con la función de [crear](../Topic/CPropertySheet::Create.md) .  No necesita derivar una clase de `CPropertySheet` a menos que desee a agregar otros controles \(como una ventana de vista previa\) o mostrar una hoja de propiedades no modal.  Este paso es necesario para las hojas de propiedades no modal porque no contienen ningún control predeterminada que se podrían utilizar para cerrar la hoja de propiedades.  
  
5.  Para cada página que se agregue a la hoja de propiedades, haga lo siguiente:  
  
    -   Construye un objeto para cada `CPropertyPage`\- clase derivada que creó anteriormente en este proceso.  
  
    -   Llamada [CPropertySheet::AddPage](../Topic/CPropertySheet::AddPage.md) para cada página.  
  
     Normalmente, el objeto que crea `CPropertySheet` también crea objetos de `CPropertyPage` en este paso.  Sin embargo, si implementa `CPropertySheet`\- clase derivada, puede insertar los objetos de `CPropertyPage` en el objeto de `CPropertySheet` y llamar a `AddPage` para cada página de `CPropertySheet`\(constructor de clase derivada.  `AddPage` agrega el objeto de `CPropertyPage` a la lista de hojas de propiedades de páginas pero no realiza realmente la ventana para esa página.  Por consiguiente, no es necesario esperar a la creación de la ventana de la hoja de propiedades para llamar a `AddPage`; puede llamar a `AddPage` de constructor de la hoja de propiedades.  
  
     De forma predeterminada, si una hoja de propiedades tiene más pestañas que caben en una sola fila de la hoja de propiedades, fichas pila en varias filas.  Para deshabilitar el apilado, llame a [CPropertySheet::EnableStackedTabs](../Topic/CPropertySheet::EnableStackedTabs.md) con el parámetro establecido en **FALSE**.  Debe llamar a `EnableStackedTabs` cuando crea la hoja de propiedades.  
  
6.  Llame a [CPropertySheet::DoModal](../Topic/CPropertySheet::DoModal.md) o [crear](../Topic/CPropertySheet::Create.md) para mostrar la hoja de propiedades.  Llame a `DoModal` para crear una hoja de propiedades como cuadro de diálogo modal.  Llame a **crear** para crear la hoja de propiedades como cuadro de diálogo no modal.  
  
7.  Intercambiar datos entre las páginas de propiedades y el propietario de la hoja de propiedades.  Esto se explica en el caso [Cambiar datos](../mfc/exchanging-data.md).  
  
 Para obtener un ejemplo de cómo utilizar las hojas de propiedades, vea el ejemplo [PROPDLG](../top/visual-cpp-samples.md)MFC General.  
  
## Vea también  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md)