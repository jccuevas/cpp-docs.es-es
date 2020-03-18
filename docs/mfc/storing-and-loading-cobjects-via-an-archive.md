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
ms.openlocfilehash: 368421a86d6ff6fc70455edd0ea9a32e05645007
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446365"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Almacenar y cargar CObjects a través de un archivo

Almacenar y cargar `CObject`s a través de un archivo requiere una consideración adicional. En algunos casos, debe llamar a la función `Serialize` del objeto, donde el objeto `CArchive` es un parámetro de la llamada a `Serialize`, en lugar de usar el operador **<\<** o **>>** de la `CArchive`. Lo importante es tener en cuenta que el operador `CArchive` **>>** construye el `CObject` en memoria basándose en `CRuntimeClass` información escrita previamente en el archivo mediante el almacenamiento almacenado.

Por lo tanto, tanto si utiliza el `CArchive` **<\<** como los operadores **>>** , frente a la llamada a `Serialize`, depende de si *necesita* el archivo de carga para reconstruir dinámicamente el objeto basándose en la información de `CRuntimeClass` almacenada anteriormente. Utilice la función `Serialize` en los casos siguientes:

- Al deserializar el objeto, conoce la clase exacta del objeto con antelación.

- Al deserializar el objeto, ya tiene asignada una memoria.

> [!CAUTION]
>  Si carga el objeto con la función `Serialize`, también debe almacenar el objeto mediante la función `Serialize`. No almacene mediante el operador `CArchive` **<<** y, después, cargue con la función `Serialize`, o bien almacene con la función `Serialize` y, a continuación, cargue con el operador `CArchive >>`.

En el ejemplo siguiente se muestran los casos:

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

En Resumen, si la clase serializable define un `CObject` incrustado como miembro, *no* debe utilizar los operadores `CArchive` **<\<** y **>>** para ese objeto, sino que debe llamar a la función `Serialize` en su lugar. Además, si la clase serializable define un puntero a un `CObject` (o un objeto derivado de `CObject`) como miembro, pero construye este otro objeto en su propio constructor, también debe llamar a `Serialize`.

## <a name="see-also"></a>Consulte también

[Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)
