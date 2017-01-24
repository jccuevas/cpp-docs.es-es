---
title: "Serializaci&#243;n: Serializar un objeto | Microsoft Docs"
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
  - "objetos [C++], serializar"
  - "serialización [C++], objetos"
  - "serializar objetos [C++]"
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Serializaci&#243;n: Serializar un objeto
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El artículo [Serialización: Crear una clase Serializable](../mfc/serialization-making-a-serializable-class.md) muestra cómo crear una clase serializable.  Una vez que tiene una clase serializable, puede serializar objetos de esa clase en un archivo con un objeto de [CArchive](../mfc/reference/carchive-class.md) .  En este artículo se explica:  
  
-   [Es un qué objeto CArchive](../mfc/what-is-a-carchive-object.md).  
  
-   [Dos maneras de crear un CArchive](../mfc/two-ways-to-create-a-carchive-object.md).  
  
-   [Cómo utilizar el CArchive \<\< y \>\> operadores](../mfc/using-the-carchive-output-and-input-operators.md).  
  
-   [Almacenar y cargando CObjects mediante un archivo](../mfc/storing-and-loading-cobjects-via-an-archive.md).  
  
 Puede dejar el marco crear el archivo del documento serializable o crear explícitamente el objeto de `CArchive` personalmente.  Puede transferir datos entre un archivo y el objeto serializable mediante \<\< y \>\> operadores para `CArchive` o, en algunos casos, llamando a la función de `CObject`\- clase derivada de `Serialize` .  
  
## Vea también  
 [Serialización](../mfc/serialization-in-mfc.md)