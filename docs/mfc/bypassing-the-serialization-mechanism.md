---
title: Omitir el mecanismo de serialización
ms.date: 11/04/2016
helpviewer_keywords:
- archive objects [MFC]
- bypassing serialization
- archives [MFC], serialization
- serialization [MFC], bypassing
- archives [MFC]
- serialization [MFC], role of framework
- serialization [MFC], overriding
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
ms.openlocfilehash: 1937098de30884be327c67a698dbb0023be248bb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345198"
---
# <a name="bypassing-the-serialization-mechanism"></a>Omitir el mecanismo de serialización

Tal como hemos visto, el marco proporciona una manera predeterminada para leer y escribir datos en y desde archivos. La serialización a través de un objeto de almacenamiento se adapte a las necesidades de una gran cantidad de aplicaciones. Este tipo de aplicación lee un archivo completamente en memoria, permite al usuario que actualice el archivo y, a continuación, escribe la versión actualizada en el disco nuevo.

Sin embargo, algunas aplicaciones funcionan en datos de forma muy diferente, y para estas aplicaciones no es adecuada la serialización a través de un archivo. Algunos ejemplos son programas de base de datos, los programas que edición solo partes de archivos grandes, los programas que escriben archivos de sólo texto y programas que comparten los archivos de datos.

En estos casos, puede invalidar el [Serialize](../mfc/reference/cobject-class.md#serialize) función de forma diferente para mediar en las acciones de archivo a través de un [CFile](../mfc/reference/cfile-class.md) objeto en lugar de un [CArchive](../mfc/reference/carchive-class.md) objeto.

Puede usar el `Open`, `Read`, `Write`, `Close`, y `Seek` funciones miembro de clase `CFile` para abrir un archivo, mueva el puntero de archivo (búsqueda) a un momento específico en el archivo, leer un registro (un número especificado de bytes ) en ese momento, dejar que el usuario actualice el registro, a continuación, buscar en el mismo punto nuevo y reescribir el registro en el archivo. El marco de trabajo abrirá el archivo por usted, y puede usar el `GetFile` función miembro de clase `CArchive` para obtener un puntero a la `CFile` objeto. Para su uso incluso más sofisticado y flexible, puede invalidar el [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) y [OnSaveDocument](../mfc/reference/cdocument-class.md#onsavedocument) funciones miembro de clase `CWinApp`. Para obtener más información, vea la clase [CFile](../mfc/reference/cfile-class.md) en el *referencia de MFC*.

En este escenario, su `Serialize` invalidación no hace nada, a menos que, por ejemplo, desea tener leer y escribir un encabezado de archivo para mantenerse al día cuando se cierra el documento.

## <a name="see-also"></a>Vea también

[Uso de documentos](../mfc/using-documents.md)
