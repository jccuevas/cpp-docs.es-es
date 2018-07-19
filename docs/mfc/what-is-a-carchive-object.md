---
title: ¿Qué es un objeto CArchive? | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55b97843a8aeb2599d2bdf34458b362fc5899368
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383839"
---
# <a name="what-is-a-carchive-object"></a>¿Qué es un objeto CArchive?
A `CArchive` objeto proporciona un mecanismo de almacenamiento en búfer de seguridad de tipos para escribir o leer objetos serializables a o desde un `CFile` objeto. Normalmente el `CFile` objeto representa un archivo de disco; sin embargo, también puede ser un archivo de memoria (`CSharedFile` objeto), es posible que representa el Portapapeles.  
  
 A partir de `CArchive` ambos almacenes de objetos (escribe, serializa) datos o carga (lee, deserializa) datos, pero no ambos. La duración de un `CArchive` objeto se limita a pasar por leer objetos desde un archivo o escribir objetos en un archivo. Por lo tanto, dos consecutivamente creado `CArchive` objetos necesarios para serializar datos en un archivo y, a continuación, se deserializan desde el archivo.  
  
 Cuando un archivo almacena objetos en un archivo, el archivo se adjunta el `CRuntimeClass` nombre a los objetos. A continuación, cuando otro almacenamiento carga objetos de un archivo en la memoria, el `CObject`-objetos derivados se reconstruyen dinámicamente en función de la `CRuntimeClass` de los objetos. Un objeto determinado puede hacer referencia a más de una vez se escribe en el archivo al guardar el almacenamiento. El archivo de carga, sin embargo, reconstruir el objeto de una sola vez. Los detalles sobre cómo se asocia un archivo `CRuntimeClass` información para objetos y reconstruye, teniendo en cuenta posibles referencias múltiples, se describen en [Nota técnica 2](../mfc/tn002-persistent-object-data-format.md).  
  
 Cuando se serializan los datos en un archivo, el archivo acumula los datos hasta que su búfer está lleno. A continuación, el archivo escribe su búfer en el `CFile` objeto señalado por el `CArchive` objeto. De forma similar, cuando se leen datos desde un archivo, lee datos del archivo para su búfer y, a continuación, desde el búfer para el objeto deserializado. Este almacenamiento en búfer, reduce el número de veces que se lee físicamente un disco duro, mejorando así el rendimiento de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)

