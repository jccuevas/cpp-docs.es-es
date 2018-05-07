---
title: Almacenar y cargar CObjects a través de un archivo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe5cc426e3494117bff98577f02178709a2588f3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Almacenar y cargar CObjects a través de un archivo
Almacenar y cargar `CObject`s a través de un archivo requiere una consideración adicional. En algunos casos, debe llamar a la `Serialize` función del objeto, donde la `CArchive` objeto es un parámetro de la `Serialize` llamada, en lugar de utilizar el **< \<** o **>>** operador de la `CArchive`. El hecho importante a tener en cuenta es que la `CArchive` **>>** construcciones de operador la `CObject` en la memoria en función de `CRuntimeClass` información escrita anteriormente en el archivo al guardar el almacenamiento.  
  
 Por lo tanto, si utiliza la `CArchive` **< \<** y **>>** operadores, en lugar de llamar a `Serialize`, depende de si se *necesita* el archivo de carga para reconstruir el objeto de forma dinámica según previamente almacenado `CRuntimeClass` información. Use la `Serialize` función en los casos siguientes:  
  
-   Al deserializar el objeto, se conoce la clase exacta del objeto de antemano.  
  
-   Cuando se deserializa el objeto, ya dispone de memoria asignada para él.  
  
> [!CAUTION]
>  Si carga el objeto mediante la `Serialize` función, también se debe almacenar el objeto utilizando el `Serialize` función. No lo guarde con el `CArchive` **<<** operador y, a continuación, carga utilizando el `Serialize` de función o almacenar mediante la `Serialize` función y, a continuación, cargue con **CArchive >>** operador.  
  
 En el ejemplo siguiente se ilustra los casos:  
  
 [!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]  
  
 [!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]  
  
 En resumen, si una clase serializable define incrustada **objeto CObject**t como miembro, debe *no* usar la `CArchive` **< \<** y **>>** operadores para ese objeto, pero debe llamar a la `Serialize` funcione en su lugar. Además, si una clase serializable define un puntero a un `CObject` (o un objeto derivado de `CObject`) como un miembro, pero las construcciones este otro objeto en su propio constructor, también debe llamar a `Serialize`.  
  
## <a name="see-also"></a>Vea también  
 [Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)

