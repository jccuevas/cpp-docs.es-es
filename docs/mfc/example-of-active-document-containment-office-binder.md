---
title: "Ejemplo de contenci&#243;n de documentos activos: Cuaderno de Office | Microsoft Docs"
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
  - "contenedores de documentos activos [C++], ejemplos"
  - "documentos activos [C++], contenedores"
  - "contenedores [C++], documento activo"
  - "ejemplos [C++], contención de documentos activos"
  - "MFC COM [C++], contención de documentos activos"
  - "Cuaderno de Office"
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ejemplo de contenci&#243;n de documentos activos: Cuaderno de Office
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft Office binder es un ejemplo de un contenedor de documento activo.  Un enlazador de Office incluye dos paneles principales, como los contenedores normalmente.  El panel izquierdo contiene iconos correspondientes a los documentos activos del enlazador.  Cada documento se denomina *una sección* dentro del enlazador.  Por ejemplo, un enlazador puede contener los documentos de Word, archivos de PowerPoint, hojas de cálculo de Excel, y así sucesivamente.  
  
 Hacer clic en un icono en el panel izquierdo provoca el documento activo correspondiente.  El panel derecho del enlazador después muestra el contenido del documento activo actualmente seleccionado.  
  
 Si abre y genera un documento de Word en un cuaderno, la barra de menús y barras de herramientas de word aparecen en la parte superior del cuadro de la vista, y puede modificar el contenido del documento utilizando cualquier comando de Word o herramienta.  Sin embargo, la barra de menús es una combinación de las barras de menús binder y word.  Porque el enlazador y word tienen menús de **Ay&uda** , el contenido de los menús respectivos se combinan.  Los contenedores del documento activo como Office binder proporcionan automáticamente la combinación de menús de **Ay&uda** ; para obtener más información, vea [Combinación del menú ayuda](../mfc/help-menu-merging.md).  
  
 Cuando selecciona un documento activo de otro tipo de aplicación, la interfaz binder para alojar el del tipo de aplicación del documento activo.  Por ejemplo, si un enlazador contiene una hoja de cálculo de Excel, observará que los menús del enlazador cambian cuando selecciona la sección de la hoja de cálculo de Excel.  
  
 Hay, por supuesto, otros posibles tipos de contenedores junto a los enlazadores.  El Explorador de archivos utiliza la interfaz típica de dual\- panel en el panel izquierdo utiliza un control de árbol para mostrar una lista jerárquica de directorios en una unidad o una red, mientras que el panel de la derecha muestra los archivos contenidos en el directorio seleccionado actualmente.  Un tipo de explorador internet de contenedor \(como Microsoft Internet Explorer\), en lugar de utilizar una interfaz de dual\- panel, tiene un solo cuadro y proporciona normalmente la navegación mediante hipervínculos.  
  
## Vea también  
 [Contención de documentos activos](../mfc/active-document-containment.md)