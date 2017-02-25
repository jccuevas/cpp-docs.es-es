---
title: "Acceso al estado del archivo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ejemplos [MFC], estado del archivo"
  - "estado del archivo [C++]"
  - "archivos [C++], obtener acceso"
  - "archivos [C++], información de estado"
  - "estado de archivos"
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Acceso al estado del archivo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CFile` también permite obtener el estado del archivo, incluir si existe el archivo, fechas y horas de creación y modificar, el tamaño lógico, y la ruta de acceso.  
  
### Para obtener el estado del archivo  
  
1.  Utilice la clase de [Archivo C](../mfc/reference/cfile-class.md) para obtener y establecer información sobre un archivo.  Una aplicación útil es utilizar la función estática **GetStatus** miembro de `CFile` para determinar si existe un archivo.  **GetStatus** devuelve 0 si el archivo especificado no existe.  
  
 Así, puede utilizar el resultado de **GetStatus** para determinar si utilizar la marca de **CFile::modeCreate** al abrir un archivo, como se muestra en el ejemplo siguiente:  
  
 [!code-cpp[NVC_MFCFiles#3](../mfc/codesnippet/CPP/accessing-file-status_1.cpp)]  
  
 Para obtener información relacionada, vea [Serialización](../mfc/serialization-in-mfc.md).  
  
## Vea también  
 [Archivos](../mfc/files-in-mfc.md)