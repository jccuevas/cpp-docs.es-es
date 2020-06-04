---
title: Archivos en MFC
ms.date: 11/04/2016
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
ms.openlocfilehash: 3a99c4143bbd27ba765b0289b80be8870a940f63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365307"
---
# <a name="files-in-mfc"></a>Archivos en MFC

En la biblioteca Microsoft Foundation Class (MFC), la clase [CFile](../mfc/reference/cfile-class.md) controla las operaciones de E/S de archivos normales. Esta familia de artículos explica cómo abrir y cerrar archivos, así como leer y escribir datos en esos archivos. También se describen las operaciones de estado de los archivos. Para obtener una descripción de cómo utilizar las características de serialización basadas en objetos de MFC como una forma alternativa de leer y escribir datos en archivos, vea el artículo [Serialización](../mfc/serialization-in-mfc.md).

> [!NOTE]
> Cuando se `CDocument` usan objetos MFC, el marco de trabajo realiza gran parte del trabajo de serialización para usted. En particular, el marco `CFile` de trabajo crea y utiliza el objeto. Sólo tiene que escribir código en `Serialize` la invalidación de la función miembro de la clase `CDocument`.

La `CFile` clase proporciona una interfaz para operaciones de archivos binarios de propósito general. Las `CStdioFile` `CMemFile` clases y `CFile` derivadas `CSharedFile` de y `CMemFile` la clase derivada de proporcionan servicios de archivos más especializados.

Para obtener más información acerca de las alternativas al control de archivos MFC, vea [Control de](../c-runtime-library/file-handling.md) archivos en la Referencia de biblioteca en tiempo *de ejecución*.

Para obtener información `CFile` acerca de las clases derivadas, vea el gráfico de [jerarquía MFC](../mfc/hierarchy-chart.md).

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

*Usar CFile*

- [Abrir un archivo con CFile](../mfc/opening-files.md)

- [Leer y escribir un archivo con CFile](../mfc/reading-and-writing-files.md)

- [Cerrar un archivo con CFile](../mfc/closing-files.md)

- [Acceda al estado del archivo con CFile](../mfc/accessing-file-status.md)

*Usar serialización MFC (persistencia de objetos)*

- [Crear una clase serializable](../mfc/serialization-making-a-serializable-class.md)

- [Serializar un objeto a través de un cArchive objeto](../mfc/serialization-serializing-an-object.md)

- [Crear un objeto CArchive](../mfc/two-ways-to-create-a-carchive-object.md)

- [Utilice los \< operadores de <y >> de CArchive](../mfc/using-the-carchive-output-and-input-operators.md)

- [Almacenar y cargar CObjects y objetos derivados de CObject a través de un archivo](../mfc/storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>Consulte también

[Conceptos](../mfc/mfc-concepts.md)<br/>
[Temas generales de MFC](../mfc/general-mfc-topics.md)<br/>
[CArchive (clase)](../mfc/reference/carchive-class.md)<br/>
[Clase CObject](../mfc/reference/cobject-class.md)
