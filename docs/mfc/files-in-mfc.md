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
ms.openlocfilehash: 8b8859e188e42f4419ca7ee7f683cc31de0c75b3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625875"
---
# <a name="files-in-mfc"></a>Archivos en MFC

En el biblioteca MFC (MFC), la clase [CFile](reference/cfile-class.md) controla las operaciones normales de e/s de archivos. Esta familia de artículos explica cómo abrir y cerrar archivos, así como leer y escribir datos en esos archivos. También se describen las operaciones de estado de archivo. Para obtener una descripción de cómo usar las características de serialización basadas en objetos de MFC como una forma alternativa de leer y escribir datos en archivos, vea el artículo sobre [serialización](serialization-in-mfc.md).

> [!NOTE]
> Cuando se usan `CDocument` objetos MFC, el marco de trabajo realiza gran parte de las tareas de serialización. En concreto, el marco de trabajo crea y usa el `CFile` objeto. Solo tiene que escribir código en la invalidación de la `Serialize` función miembro de clase `CDocument` .

La `CFile` clase proporciona una interfaz para las operaciones de archivos binarios de uso general. Las `CStdioFile` `CMemFile` clases y derivadas de `CFile` y la `CSharedFile` clase derivada de `CMemFile` proporcionan servicios de archivo más especializados.

Para obtener más información sobre las alternativas al control de archivos de MFC, vea [control de archivos](../c-runtime-library/file-handling.md) en la referencia de la biblioteca en *tiempo de ejecución*.

Para obtener información acerca de `CFile` las clases derivadas, vea el [gráfico de jerarquías de MFC](hierarchy-chart.md).

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

*Usar CFile*

- [Abrir un archivo con CFile](opening-files.md)

- [Leer y escribir un archivo con CFile](reading-and-writing-files.md)

- [Cerrar un archivo con CFile](closing-files.md)

- [Acceder al estado del archivo con CFile](accessing-file-status.md)

*Usar la serialización de MFC (persistencia de objetos)*

- [Crear una clase serializable](serialization-making-a-serializable-class.md)

- [Serializar un objeto a través de un objeto CArchive](serialization-serializing-an-object.md)

- [Crear un objeto CArchive](two-ways-to-create-a-carchive-object.md)

- [Usar los operadores de> de <CArchive \< and >](using-the-carchive-output-and-input-operators.md)

- [Almacenar y cargar objetos derivados de CObjects y CObject a través de un archivo](storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>Consulte también

[Conceptos](mfc-concepts.md)<br/>
[Temas generales de MFC](general-mfc-topics.md)<br/>
[CArchive (clase)](reference/carchive-class.md)<br/>
[CObject (clase)](reference/cobject-class.md)
