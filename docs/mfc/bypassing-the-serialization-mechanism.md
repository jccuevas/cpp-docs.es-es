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
ms.openlocfilehash: f47cac34f6cdbdae01af98ec28be5af17edf0e25
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620965"
---
# <a name="bypassing-the-serialization-mechanism"></a>Omitir el mecanismo de serialización

Como ha podido observar, el marco de trabajo proporciona una manera predeterminada de leer y escribir datos en archivos. La serialización a través de un objeto de archivo se adapta a las necesidades de una gran cantidad de aplicaciones. Este tipo de aplicación Lee un archivo completamente en la memoria, permite al usuario actualizar el archivo y, a continuación, vuelve a escribir la versión actualizada en el disco.

Sin embargo, algunas aplicaciones operan en los datos de forma muy distinta, y para la serialización de estas aplicaciones a través de un archivo no es adecuado. Entre los ejemplos se incluyen programas de base de datos, programas que solo editan partes de archivos grandes, programas que escriben archivos de solo texto y programas que comparten archivos de datos.

En estos casos, puede invalidar la función [Serialize](reference/cobject-class.md#serialize) de una manera diferente para mediar acciones de archivo a través de un objeto [CFile](reference/cfile-class.md) en lugar de un objeto [CArchive](reference/carchive-class.md) .

Puede usar las `Open` `Read` `Write` funciones miembro,,, `Close` y `Seek` de la clase `CFile` para abrir un archivo, pasar el puntero de archivo (buscar) a un punto específico del archivo, leer un registro (un número especificado de bytes) en ese momento, dejar que el usuario actualice el registro y, a continuación, volver a realizar el mismo punto y volver a escribir el registro en el archivo. El marco de trabajo abrirá el archivo automáticamente y podrá usar la `GetFile` función miembro de clase `CArchive` para obtener un puntero al `CFile` objeto. Para un uso aún más sofisticado y flexible, puede invalidar las funciones miembro [OnOpenDocument](reference/cdocument-class.md#onopendocument) y [OnSaveDocument](reference/cdocument-class.md#onsavedocument) de la clase `CWinApp` . Para obtener más información, vea la clase [CFile](reference/cfile-class.md) en la *referencia de MFC*.

En este escenario, la `Serialize` invalidación no realiza ninguna acción, a menos que, por ejemplo, desee que lea y escriba un encabezado de archivo para mantenerlo actualizado cuando se cierre el documento.

## <a name="see-also"></a>Consulte también

[Usar documentos](using-documents.md)
