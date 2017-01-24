---
title: "Almacenar y cargar CObjects a trav&#233;s de un archivo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchive (clase), almacenar y cargar objetos"
  - "CObject (clase), CArchive (objetos)"
  - "CObjects"
  - "CObjects, cargar a través de archivos"
  - "Serialize (método), frente a operadores CArchive"
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Almacenar y cargar CObjects a trav&#233;s de un archivo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Almacenar y cargar s para `CObject`mediante un archivo requiere la consideración adicional.  En algunos casos, debe llamar a la función de `Serialize` de objeto, donde es un parámetro el objeto de `CArchive` de llamada de `Serialize` , en comparación con el operador de **\<\<** o de **\>\>** de `CArchive`.  El hecho importante a tener en cuenta es que el operador de `CArchive`**\>\>** construye `CObject` en memoria basándose en la información de `CRuntimeClass` escrita anteriormente al archivo por el archivo que almacena.  
  
 Por consiguiente, si utiliza `CArchive` **\<\<** y operadores de **\>\>** , para llamar a `Serialize`, depende de si *necesita* el archivo de carga volver a crear dinámicamente el objeto basándose en la información anteriormente almacenada de `CRuntimeClass` .  Utilice la función de `Serialize` en los casos siguientes:  
  
-   Al deserializar el objeto, conoce la clase exacta del objeto de antemano.  
  
-   Al deserializar el objeto, ya tiene la memoria asignada para él.  
  
> [!CAUTION]
>  Si carga el objeto mediante la función de `Serialize` , también debe almacenar el objeto mediante la función de `Serialize` .  No almacene mediante el operador de `CArchive`**\<\<** y no cargue utilizando la función de `Serialize` , o el almacén mediante la función de `Serialize` y no cargue utilizando el operador de **CArchive \>\>** .  
  
 El ejemplo siguiente se muestran los casos:  
  
 [!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/CPP/storing-and-loading-cobjects-via-an-archive_1.h)]  
  
 [!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/CPP/storing-and-loading-cobjects-via-an-archive_2.cpp)]  
  
 En resumen, si la clase serializable define t incrustada de **CObjec**como miembro, no debe utilizar `CArchive` **\<\<** y operadores de **\>\>** para ese objeto, pero debe llamar a la función de `Serialize` en su lugar.  Además, si la clase serializable define un puntero a `CObject` \(o a un objeto derivado de `CObject`\) como miembro, pero construye este otro objeto en un constructor, también debe llamar a `Serialize`.  
  
## Vea también  
 [Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)