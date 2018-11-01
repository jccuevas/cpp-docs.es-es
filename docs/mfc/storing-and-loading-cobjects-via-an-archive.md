---
title: Almacenar y cargar CObjects a través de un archivo
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
ms.openlocfilehash: 370e8202d1bd1cda04edbdbd12bd936bdf5ef7b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493696"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Almacenar y cargar CObjects a través de un archivo

Almacenar y cargar `CObject`s a través de un archivo requiere una consideración adicional. En algunos casos, debe llamar a la `Serialize` función del objeto, donde el `CArchive` objeto es un parámetro de la `Serialize` llamada, en lugar de usar el **< \<** o **>>** operador de la `CArchive`. Los hechos importantes a tener en cuenta es que el `CArchive` **>>** operador construcciones el `CObject` en memoria en función de `CRuntimeClass` escrita anteriormente en el archivo al guardar el almacenamiento de información.

Por lo tanto, si usa el `CArchive` **< \<** y **>>** operadores, en lugar de llamar a `Serialize`, depende de si se *necesita* el almacenamiento de carga para reconstruir el objeto de forma dinámica según almacenadas previamente `CRuntimeClass` información. Use el `Serialize` función en los casos siguientes:

- Cuando se deserializa el objeto, saber con antelación la clase exacta del objeto.

- Cuando se deserializa el objeto, ya dispone de memoria asignada para él.

> [!CAUTION]
>  Si carga el objeto mediante el `Serialize` función, también se debe almacenar el objeto con el `Serialize` función. No almacene con el `CArchive` **<<** operador y, a continuación, carga mediante el `Serialize` función, o bien almacenar mediante la `Serialize` función y, a continuación, cargar mediante `CArchive >>` operador.

El ejemplo siguiente muestra los casos:

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

En resumen, si una clase serializable define incrustada `CObject` como un miembro, debe *no* utilizar el `CArchive` **< \<** y **>>** operadores para ese objeto, pero debe llamar a la `Serialize` funcione en su lugar. Además, si una clase serializable define un puntero a un `CObject` (o un objeto derivado de `CObject`) como un miembro, pero construcciones el otro objeto en su propio constructor, también deberá llamar `Serialize`.

## <a name="see-also"></a>Vea también

[Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)

