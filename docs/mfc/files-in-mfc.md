---
title: Archivos en MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- serialization [MFC], MFC files
- I/O [MFC], MFC classes
- files [MFC], MFC
- files [MFC], serialization
- binary access, binary file operations in MFC
- file I/O classes [MFC]
- I/O [MFC]
- persistence [MFC]
- MFC, file operations
- files [MFC], manipulating
- binary access [MFC]
ms.assetid: ae25e2c5-2859-4679-ab97-438824e93ce1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bfc36a6b1610df07201833ed13a1c6ebd0ae6f7b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444497"
---
# <a name="files-in-mfc"></a>Archivos en MFC

En la biblioteca de clases de Microsoft Foundation (MFC), clase [CFile](../mfc/reference/cfile-class.md) controla las operaciones de E/S de archivos normales. Esta serie de artículos explica cómo abrir y cerrar archivos, así como leer y escribir datos en esos archivos. También describe las operaciones de estado de archivo. Para obtener una descripción de cómo usar las características de serialización basada en objetos de MFC como una manera alternativa de leer y escribir datos en archivos, consulte el artículo [serialización](../mfc/serialization-in-mfc.md).

> [!NOTE]
>  Cuando se usa MFC `CDocument` objetos, el marco de trabajo hace gran parte del trabajo de serialización por usted. En concreto, el marco de trabajo crea y usa el `CFile` objeto. Solo tiene que escribir código en el reemplazo del `Serialize` función miembro de clase `CDocument`.

La `CFile` clase proporciona una interfaz para las operaciones de archivos binarios de propósito general. El `CStdioFile` y `CMemFile` las clases derivadas de `CFile` y `CSharedFile` clase derivada de `CMemFile` proporcionar servicios de archivo más especializados.

Para obtener más información sobre las alternativas para la administración de archivos de MFC, vea [manejo de archivos](../c-runtime-library/file-handling.md) en el *referencia de la biblioteca de tiempo de ejecución*.

Para obtener información acerca de derivan `CFile` las clases, consulte el [gráfico de jerarquías MFC](../mfc/hierarchy-chart.md).

## <a name="what-do-you-want-to-do"></a>Qué quieres hacer

*Usar CFile*

- [Abrir un archivo con CFile](../mfc/opening-files.md)

- [Leer y escribir un archivo con CFile](../mfc/reading-and-writing-files.md)

- [Cerrar un archivo con CFile](../mfc/closing-files.md)

- [Estado de archivo de acceso con CFile](../mfc/accessing-file-status.md)

*Usar la serialización de MFC (persistencia de objeto)*

- [Crear una clase serializable](../mfc/serialization-making-a-serializable-class.md)

- [¿Serializar un objeto a través de un objeto CArchive?](../mfc/serialization-serializing-an-object.md)

- [¿Crear un objeto CArchive?](../mfc/two-ways-to-create-a-carchive-object.md)

- [Usar CArchive <\< y >> operadores](../mfc/using-the-carchive-output-and-input-operators.md)

- [Store y cargar CObjects y derivadas de CObject objetos a través de un archivo](../mfc/storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>Vea también

[Conceptos](../mfc/mfc-concepts.md)<br/>
[Temas generales de MFC](../mfc/general-mfc-topics.md)<br/>
[CArchive (clase)](../mfc/reference/carchive-class.md)<br/>
[CObject (clase)](../mfc/reference/cobject-class.md)
