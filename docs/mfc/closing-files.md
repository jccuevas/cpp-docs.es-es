---
title: "Cerrar archivos | Microsoft Docs"
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
  - "archivos [C++], cerrar"
  - "MFC [C++], operaciones en archivo"
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Cerrar archivos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Como de costumbre en operaciones de E\/S, una vez que termine con un archivo, debe cerrarlo.  
  
#### Para cerrar un archivo  
  
1.  Utilice la función miembro de **cerrar** .  Esta función cierra el archivo del sistema de archivos y los búferes de los rubores en caso necesario.  
  
 Si se haya asignado el objeto de [Archivo C](../mfc/reference/cfile-class.md) en el cuadro \(como en el ejemplo mostrado en [Abrir archivos](../mfc/opening-files.md)\), el objeto automáticamente se cierra y se destruirá cuando salga del ámbito.  Observe que elimina el objeto de `CFile` no elimina el archivo físico en el sistema de archivos.  
  
## Vea también  
 [Archivos](../mfc/files-in-mfc.md)