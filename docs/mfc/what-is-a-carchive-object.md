---
title: "&#191;Qu&#233; es un objeto CArchive? | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CArchive"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "objetos de archivo [C++]"
  - "archivos [C++], para la serialización"
  - "almacenamiento en búfer, objetos serializables"
  - "búferes, objetos serializables"
  - "CArchive (clase), acerca de la clase CArchive"
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# &#191;Qu&#233; es un objeto CArchive?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un objeto de `CArchive` proporciona un mecanismo tipo\- seguro de almacenamiento en búfer para escribir o leer objetos serializables a o desde un objeto de `CFile` .  El objeto de `CFile` representa normalmente un archivo de disco; sin embargo, también puede ser un archivo de memoria \(objeto de`CSharedFile` \), quizás representa el portapapeles.  
  
 Un objeto determinado de `CArchive` almacena \(las escrituras, serializan\) datos o carga \(lee, deserializar\) datos, pero no ambos.  La duración de un objeto de `CArchive` se limita a un paso a través de objetos de escribir en un archivo o de objetos de lectura de un archivo.  Así, dos objetos sucesivamente creados de `CArchive` se requieren para serializar datos en un archivo y después para deserializarlos posteriores del archivo.  
  
 Cuando un archivo almacena objetos en un archivo, el archivo asocia el nombre de `CRuntimeClass` a objetos.  A continuación, cuando otro archivo carga objetos de un archivo de mapa, `CObject`\- objetos derivados dinámicamente se vuelven a crear basándose en `CRuntimeClass` de los objetos.  Un objeto determinado puede hacer referencia a más de una vez mientras está escrito en el archivo por el archivo que almacena.  El archivo de carga, sin embargo, reconstruirá el objeto solo una vez.  Los detalles sobre cómo un archivo asocia la información de `CRuntimeClass` a objetos y vuelve a crear objetos, teniendo en cuenta varias referencias posibles, se describen en [Nota técnica 2](../mfc/tn002-persistent-object-data-format.md).  
  
 Mientras los datos se serializa en un archivo, el archivo acumula los datos hasta que el búfer esté completo.  El archivo escribe el búfer al objeto de `CFile` designado por el objeto de `CArchive` .  De igual forma, cuando lea los datos de un archivo, lee los datos del archivo en el búfer y después del búfer al objeto deserializado.  Este búfer reduce el número de veces que un disco duro se lee físicamente, lo mejora el rendimiento de la aplicación.  
  
## Vea también  
 [Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)