---
title: "Agregar columnas al control (Vista de informe) | Microsoft Docs"
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
  - "CListCtrl (clase), agregar columnas"
  - "CListCtrl (clase), vista de informes"
  - "columnas [C++], agregar a CListCtrl"
  - "vista de informes en la clase CListCtrl"
  - "vistas, informe"
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar columnas al control (Vista de informe)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  El procedimiento siguiente se aplica a [CListView](../mfc/reference/clistview-class.md) o el objeto de [CListCtrl](../mfc/reference/clistctrl-class.md) .  
  
 Cuando un control de lista está en la vista de informe, las columnas se muestran, proporcionando un método de organizar varios subelementos de cada elemento del control de lista.  Implementan a esta organización con una correspondencia entre una columna del control de lista y el subelemento asociado del elemento del control de lista.  Para obtener más información sobre subelementos, vea [Agregar elementos al Control](../mfc/adding-items-to-the-control.md).  Un ejemplo de un control de vista de informe lo proporciona la vista detalles en Windows 95 y el Explorador de Windows 98.  Las primeras listas de columnas carpeta, iconos de archivo, y etiquetas.  El otro tamaño de archivo de lista de las columnas, tipo de archivo, Last modified date, y así sucesivamente.  
  
 Aunque las columnas se pueden agregar a un control de lista en cualquier momento, las columnas son visibles sólo cuando el control tiene el bit de estilo de `LVS_REPORT` activado.  
  
 Cada columna tiene un objeto asociado al elemento de encabezado \(vea [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)\) que las etiquetas la columna y permiten que los usuarios cambien el tamaño de la columna.  
  
 Si el control de lista admite una vista de informe, debe agregar una columna para cada subelemento posibles en un elemento de control list.  Agregue una columna preparar una estructura de [LV\_COLUMN](http://msdn.microsoft.com/library/windows/desktop/bb774743) y después mediante una llamada a [InsertColumn](../Topic/CListCtrl::InsertColumn.md).  Después de agregar las columnas necesarias \(denominadas a veces elementos de encabezado\), puede reordenarlos mediante las funciones miembro y diseñe pertenecer al control de encabezado incrustado.  Para obtener más información, vea [Ordenar elementos en el Control de encabezado](../mfc/ordering-items-in-the-header-control.md).  
  
> [!NOTE]
>  Si el control de lista se crea con el estilo de **LVS\_NOCOLUMNHEADER** , cualquier intento de insertar columnas se omitirá.  
  
## Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)