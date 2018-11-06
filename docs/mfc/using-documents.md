---
title: Usar documentos
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], C++ applications
- data [MFC], reading
- documents [MFC]
- files [MFC], writing to
- data [MFC], documents
- files [MFC]
- views [MFC], C++ applications
- document/view architecture [MFC], documents
- reading data [MFC], documents and views
- printing [MFC], documents
- writing to files [MFC]
ms.assetid: f390d6d8-d0e1-4497-9b6a-435f7ce0776c
ms.openlocfilehash: 1fcdd365bd3744e1a09b768f56c1044696686c73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589740"
---
# <a name="using-documents"></a>Usar documentos

Trabajar juntos, documentos y vistas:

- Contener, administrar y mostrar específica de su aplicación [datos](../mfc/managing-data-with-document-data-variables.md).

- Proporcionan una interfaz que consta de [variables de datos de documentos](../mfc/managing-data-with-document-data-variables.md) para manipular los datos.

- Participar en [escribir y leer archivos](../mfc/serializing-data-to-and-from-files.md).

- Participar en [impresión](../mfc/role-of-the-view-in-printing.md).

- [Controlar](../mfc/handling-commands-in-the-document.md) la mayoría de los comandos y mensajes de la aplicación.

El documento está especialmente implicado en la administración de datos. Store los datos, normalmente, en variables de miembro de clase de documento. La vista usa estas variables para tener acceso a los datos para mostrar y actualizar. Mecanismo de serialización predeterminado del documento administra leer y escribir los datos hacia y desde archivos. Documentos también pueden controlar comandos (pero no los mensajes de Windows que no sea de WM_COMMAND).

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Derivar una clase de documento de CDocument](../mfc/deriving-a-document-class-from-cdocument.md)

- [Administración de datos con variables de datos del documento](../mfc/managing-data-with-document-data-variables.md)

- [Serializar datos hacia y desde archivos](../mfc/serializing-data-to-and-from-files.md)

- [Omitir el mecanismo de serialización](../mfc/bypassing-the-serialization-mechanism.md)

- [Controlar comandos en el documento](../mfc/handling-commands-in-the-document.md)

- [Función miembro OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument)

- [Función miembro DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)

## <a name="see-also"></a>Vea también

[Arquitectura documento/vista](../mfc/document-view-architecture.md)

