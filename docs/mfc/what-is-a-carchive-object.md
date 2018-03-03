---
title: "¿Qué es un objeto CArchive? | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CArchive
dev_langs:
- C++
helpviewer_keywords:
- archive objects [MFC]
- archives [MFC], for serialization
- buffers, serializable objects
- CArchive class [MFC], about CArchive class [MFC]
- buffering, serializable objects
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb9b0c3e24094deb0d4fd4ac20d673d9ffafca6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="what-is-a-carchive-object"></a>¿Qué es un objeto CArchive?
A `CArchive` objeto proporciona un mecanismo de almacenamiento en búfer de seguridad de tipos para escribir o leer objetos serializables a o desde un `CFile` objeto. Normalmente el `CFile` objeto representa un archivo de disco; sin embargo, también puede ser un archivo de memoria (`CSharedFile` objeto), es posible que representa el Portapapeles.  
  
 A partir de `CArchive` ambos almacenes de objetos (escribe, serializa) datos o carga (lee, deserializa) datos, pero no ambos. La duración de un `CArchive` objeto se limita a pasar por leer objetos desde un archivo o escribir objetos en un archivo. Por lo tanto, dos consecutivamente creado `CArchive` objetos necesarios para serializar datos en un archivo y, a continuación, se deserializan desde el archivo.  
  
 Cuando un archivo almacena objetos en un archivo, el archivo se adjunta el `CRuntimeClass` nombre a los objetos. A continuación, cuando otro almacenamiento carga objetos de un archivo en la memoria, el `CObject`-objetos derivados se reconstruyen dinámicamente en función de la `CRuntimeClass` de los objetos. Un objeto determinado puede hacer referencia a más de una vez se escribe en el archivo al guardar el almacenamiento. El archivo de carga, sin embargo, reconstruir el objeto de una sola vez. Los detalles sobre cómo se asocia un archivo `CRuntimeClass` información para objetos y reconstruye, teniendo en cuenta posibles referencias múltiples, se describen en [Nota técnica 2](../mfc/tn002-persistent-object-data-format.md).  
  
 Cuando se serializan los datos en un archivo, el archivo acumula los datos hasta que su búfer está lleno. A continuación, el archivo escribe su búfer en el `CFile` objeto señalado por el `CArchive` objeto. De forma similar, cuando se leen datos desde un archivo, lee datos del archivo para su búfer y, a continuación, desde el búfer para el objeto deserializado. Este almacenamiento en búfer, reduce el número de veces que se lee físicamente un disco duro, mejorando así el rendimiento de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)

