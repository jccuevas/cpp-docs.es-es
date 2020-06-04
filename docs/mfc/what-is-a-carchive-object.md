---
title: ¿Qué es un objeto CArchive?
ms.date: 11/04/2016
helpviewer_keywords:
- archive objects [MFC]
- archives [MFC], for serialization
- buffers, serializable objects
- CArchive class [MFC], about CArchive class [MFC]
- buffering, serializable objects
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
ms.openlocfilehash: 0a78385c81c43a4b0c925bbe89ccd3937873ee8b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446018"
---
# <a name="what-is-a-carchive-object"></a>¿Qué es un objeto CArchive?

Un objeto `CArchive` proporciona un mecanismo de almacenamiento en búfer con seguridad de tipos para escribir o leer objetos serializables hacia o desde un objeto `CFile`. Normalmente, el objeto `CFile` representa un archivo de disco; sin embargo, también puede ser un archivo de memoria (`CSharedFile` objeto), que quizás represente el portapapeles.

Un objeto `CArchive` determinado almacena (escribe, serializa) datos o carga (Lee, deserializa) datos, pero nunca ambos. La duración de un objeto `CArchive` está limitada a un paso a través de la escritura de objetos en un archivo o la lectura de objetos de un archivo. Por lo tanto, se requieren dos objetos `CArchive` creados sucesivamente para serializar los datos en un archivo y, a continuación, deserializarlos de nuevo desde el archivo.

Cuando un archivo almacena objetos en un archivo, el archivo adjunta el nombre del `CRuntimeClass` a los objetos. A continuación, cuando otro archivo carga objetos de un archivo en la memoria, los objetos derivados de `CObject`se reconstruyen dinámicamente basándose en el `CRuntimeClass` de los objetos. Se puede hacer referencia a un objeto dado más de una vez, ya que lo escribe en el archivo mediante el almacenamiento almacenado. El archivo de carga, sin embargo, reconstruirá el objeto solo una vez. Los detalles sobre cómo un archivo adjunta información `CRuntimeClass` a objetos y reconstruye objetos, teniendo en cuenta posibles referencias múltiples, se describen en la [Nota técnica 2](../mfc/tn002-persistent-object-data-format.md).

A medida que los datos se serializan en un archivo, el archivo acumula los datos hasta que el búfer está lleno. Después, el archivo escribe su búfer en el `CFile` objeto al que apunta el objeto `CArchive`. Del mismo modo, a medida que se leen los datos de un archivo, Lee los datos del archivo en su búfer y, a continuación, desde el búfer hasta el objeto deserializado. Este almacenamiento en búfer reduce el número de veces que se lee físicamente un disco duro, con lo que se mejora el rendimiento de la aplicación.

## <a name="see-also"></a>Consulte también

[Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)
