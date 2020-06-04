---
title: Almacenar y cargar CObjects a través de un archivo
ms.date: 11/04/2016
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
ms.openlocfilehash: f1b59516d5bba13b6f5e006f91d8ebd560543b05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372147"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Almacenar y cargar CObjects a través de un archivo

Almacenar y `CObject`cargar s a través de un archivo requiere una consideración adicional. En algunos casos, debe `Serialize` llamar a la `CArchive` función del objeto, donde el objeto es un parámetro de la `Serialize` llamada, en lugar de utilizar el ** < ** operador or **>>** del `CArchive`archivo . El hecho importante a tener `CArchive` **>>** en cuenta `CObject` es que `CRuntimeClass` el operador construye el en la memoria en función de la información previamente escrita en el archivo por el archivo de almacenamiento.

Por lo tanto, `CArchive` ** < ** si se utilizan `Serialize`los operadores y, **>>** frente a la llamada, depende de `CRuntimeClass` si *necesita* el archivo de carga para reconstruir dinámicamente el objeto en función de la información almacenada anteriormente. Utilice `Serialize` la función en los siguientes casos:

- Al deserializar el objeto, conoce la clase exacta del objeto de antemano.

- Al deserializar el objeto, ya tiene memoria asignada para él.

> [!CAUTION]
> Si carga el objeto `Serialize` utilizando la función, `Serialize` también debe almacenar el objeto mediante la función. No almacene con `CArchive` **<<** el operador y, `Serialize` a continuación, `Serialize` cargue con la `CArchive >>` función, o almacene mediante la función y, a continuación, cargue con el operador using.

En el ejemplo siguiente se ilustran los casos:

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

En resumen, si la clase serializable define una incrustada `CObject` como miembro, *no* debe usar los `CArchive` ** < ** operadores y **>>** para ese objeto, sino que debe llamar a la `Serialize` función en su lugar. Además, si la clase serializable define un puntero a un `CObject` (o un objeto derivado de `CObject`) como `Serialize`un miembro, pero construye este otro objeto en su propio constructor, también debe llamar a .

## <a name="see-also"></a>Consulte también

[Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)
