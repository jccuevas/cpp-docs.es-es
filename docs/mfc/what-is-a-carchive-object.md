---
title: ¿Qué es un objeto CArchive? | Microsoft Docs
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
ms.openlocfilehash: fe45b3e5444549001990f62db7028f9de6d49986
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409668"
---
# <a name="what-is-a-carchive-object"></a>¿Qué es un objeto CArchive?

Un `CArchive` objeto proporciona un mecanismo de almacenamiento en búfer de seguridad de tipos para escribir o leer objetos serializables a o desde un `CFile` objeto. Normalmente el `CFile` objeto representa un archivo de disco; sin embargo, también puede ser un archivo de memoria (`CSharedFile` objeto), quizás que representa el Portapapeles.

A partir de `CArchive` ambos almacenes de objetos (escribe, serializa) datos o cargas (lee, deserializa) datos, pero nunca ambas. La vida de un `CArchive` objeto está limitado a un paso a través de escribir objetos en un archivo o leer objetos desde un archivo. Por lo tanto, dos consecutivamente creado `CArchive` objetos son necesarios para serializar los datos en un archivo y, a continuación, deserializarlo desde el archivo.

Cuando un archivo almacena objetos en un archivo, el archivo se adjunta el `CRuntimeClass` nombre a los objetos. A continuación, cuando otro almacenamiento carga objetos desde un archivo a la memoria, el `CObject`-objetos derivados se reconstruyen dinámicamente según la `CRuntimeClass` de los objetos. Un objeto determinado puede hacer referencia a más de una vez se escribe en el archivo al guardar el almacenamiento. El almacenamiento de carga, sin embargo, reconstruir el objeto de una sola vez. Los detalles acerca de cómo se adjunta un archivo `CRuntimeClass` información para objetos y reconstruye, teniendo en cuenta posibles referencias múltiples, se describen en [Nota técnica 2](../mfc/tn002-persistent-object-data-format.md).

Cuando se serializan los datos en un archivo, se acumulan en los datos hasta que el búfer esté lleno. A continuación, el archivo escribe su búfer en el `CFile` objeto señalado por el `CArchive` objeto. De forma similar, cuando se leen datos desde un archivo, lee datos desde el archivo para su búfer y, a continuación, desde el búfer para el objeto deserializado. Este almacenamiento en búfer, reduce el número de veces que se lee físicamente un disco duro, mejorando así el rendimiento de la aplicación.

## <a name="see-also"></a>Vea también

[Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)

