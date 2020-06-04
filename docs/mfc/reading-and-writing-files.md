---
title: Leer y escribir en archivos
ms.date: 11/04/2016
helpviewer_keywords:
- CFile class [MFC], objects
- examples [MFC], reading files
- files [MFC], writing to
- examples [MFC], writing to files
- files [MFC], reading
- MFC, file operations
- CFile class [MFC], reading and writing CFile objects
- reading files
- writing to files [MFC]
ms.assetid: cac0c826-ba56-495f-99b3-ce6336f65763
ms.openlocfilehash: 6c4b2b21bbfa19fb73997f8475cfa9a4047dc0ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371799"
---
# <a name="reading-and-writing-files"></a>Leer y escribir en archivos

Si ha utilizado las funciones de control de archivos de biblioteca en tiempo de ejecución de C, las operaciones de lectura y escritura de MFC le resultarán familiares. En este artículo se describe la `CFile` lectura directamente de un objeto y escribirlo directamente. También puede realizar E/S de archivos almacenados en búfer con la clase [CArchive.](../mfc/reference/carchive-class.md)

#### <a name="to-read-from-and-write-to-the-file"></a>Para leer y escribir en el archivo

1. Utilice `Read` las `Write` funciones miembro y para leer y escribir datos en el archivo.

     o bien

1. La `Seek` función miembro también está disponible para pasar a un desplazamiento específico dentro del archivo.

`Read`toma un puntero a un búfer y el número de bytes para leer y devuelve el número real de bytes que se leyeron. Si no se pudo leer el número necesario de bytes porque se alcanza el final del archivo (EOF), se devuelve el número real de bytes leídos. Si se produce algún error de lectura, se produce una excepción. `Write`es similar `Read`a , pero no se devuelve el número de bytes escritos. Si se produce un error de escritura, incluido no escribir todos los bytes especificados, se produce una excepción. Si tiene un `CFile` objeto válido, puede leerlo o escribir en él como se muestra en el ejemplo siguiente:

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
> Normalmente debe llevar a cabo operaciones de entrada/salida dentro de un bloque de control de excepciones **try**/**catch.** Para obtener más información, vea [Control de excepciones (MFC)](../mfc/exception-handling-in-mfc.md).

## <a name="see-also"></a>Consulte también

[Archivos](../mfc/files-in-mfc.md)
