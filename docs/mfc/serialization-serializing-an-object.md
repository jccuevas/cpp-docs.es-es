---
title: 'Serialización: Serializar un objeto'
ms.date: 11/04/2016
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
ms.openlocfilehash: 10a7c52e6187f4db8345e1eadb88faeefa50b419
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588531"
---
# <a name="serialization-serializing-an-object"></a>Serialización: Serializar un objeto

El artículo [serialización: crear una clase Serializable](../mfc/serialization-making-a-serializable-class.md) se muestra cómo hacer que una clase sea serializable. Una vez que una clase serializable, se puede serializar objetos de esa clase a y desde un archivo a través de un [CArchive](../mfc/reference/carchive-class.md) objeto. En este artículo se explica:

- [Es lo que un objeto CArchive](../mfc/what-is-a-carchive-object.md).

- [Dos maneras de crear un objeto CArchive](../mfc/two-ways-to-create-a-carchive-object.md).

- [Cómo usar CArchive <\< y >> operadores](../mfc/using-the-carchive-output-and-input-operators.md).

- [Almacenar y cargar CObjects a través de un archivo](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Puede permitir que el marco de crear el contenedor de un documento serializable o bien crear explícitamente la `CArchive` objeto usted mismo. Puede transferir datos entre un archivo y el objeto serializable mediante el <\< y >> operadores para `CArchive` o, en algunos casos, mediante una llamada a la `Serialize` función de un `CObject`-clase derivada.

## <a name="see-also"></a>Vea también

[Serialización](../mfc/serialization-in-mfc.md)

