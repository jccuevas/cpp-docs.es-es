---
title: "Objetos de datos y or&#237;genes de datos (OLE) | Microsoft Docs"
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
  - "objetos de datos [C++], definición"
  - "orígenes de datos [C++], definición"
  - "transferencia de datos [C++]"
  - "transferencia de datos [C++], definición"
  - "OLE [C++], objetos de datos"
  - "OLE [C++], orígenes de datos"
  - "OLE [C++], transferencia de datos"
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Objetos de datos y or&#237;genes de datos (OLE)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al realizar una transferencia de datos, utilizar el portapapeles o la operación de arrastrar y colocar, los datos tiene un origen y un destino.  Una aplicación proporciona los datos para copiar y otra aplicación lo acepta para pegar.  Cada lado de transferencia necesita realizar diversas operaciones en los mismos datos para que la transferencia sea correcta.  La biblioteca de \(MFC\) de la clase de la base de Microsoft proporciona dos clases que representan cada lado de esta transferencia:  
  
-   Los orígenes de datos \(implementados por los objetos de `COleDataSource` \) representan el lado del origen de la transferencia de datos.  Son creados por la aplicación origen cuando los datos se debe copiar en el portapapeles, o cuando los datos se proporciona para una operación de arrastrar y colocar.  
  
-   Los objetos de datos \(implementados por los objetos de `COleDataObject` \) representan el lado de destino de la transferencia de datos.  Se crean cuando la aplicación destino tiene datos colocados en ella, o cuando se solicita que realizar una operación de pegar desde el portapapeles.  
  
 Los artículos siguientes explican cómo utilizar objetos de datos y orígenes de datos en las aplicaciones.  Esta información se aplica al contenedor y aplicaciones de servidor, ya que ambos se pueden llamar para copiar y datos pegar.  
  
-   [Objetos de datos y orígenes de datos: Creación y Destruction](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [Objetos de datos y orígenes de datos: Manipulación](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## En esta sección  
 [Arrastrar y colocar](../mfc/drag-and-drop-ole.md)  
  
 [Portapapeles](../mfc/clipboard.md)  
  
## Vea también  
 [OLE](../mfc/ole-in-mfc.md)   
 [COleDataObject Class](../mfc/reference/coledataobject-class.md)   
 [COleDataSource Class](../mfc/reference/coledatasource-class.md)