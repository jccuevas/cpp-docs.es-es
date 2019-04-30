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
ms.openlocfilehash: ab1ddc58ec6cc2b67e5843f46afbead3ead54eba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324264"
---
# <a name="reading-and-writing-files"></a>Leer y escribir en archivos

Si ha usado las funciones de administración de archivos de biblioteca en tiempo de ejecución de C, MFC, leer y escribir operaciones le resultarán familiar. En este artículo se describe directamente de lectura y escritura directamente a un `CFile` objeto. Se pueden también almacenar en búfer de E/S de archivos con la [CArchive](../mfc/reference/carchive-class.md) clase.

#### <a name="to-read-from-and-write-to-the-file"></a>Para leer y escribir en el archivo

1. Use la `Read` y `Write` las funciones miembro para leer y escribir datos en el archivo.

     -o bien-

1. El `Seek` también está disponible para mover a un desplazamiento específico dentro del archivo de la función miembro.

`Read` toma un puntero a un búfer y el número de bytes que se leen y devuelve el número real de bytes leídos. Si el número necesario de bytes no se puede leer porque final de archivo (EOF) se alcanza, se devuelve el número real de bytes leídos. Si se produce cualquier error de lectura, se produce una excepción. `Write` es similar a `Read`, pero no se devuelve el número de bytes escritos. Si se produce un error de escritura, incluidas no escribir todos los bytes especificados, se produce una excepción. Si tiene un válido `CFile` de objeto, puede leer o escribir en él, tal como se muestra en el ejemplo siguiente:

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
>  Normalmente debe llevar a cabo operaciones de entrada/salida dentro de un **intente**/**catch** bloque de control de excepciones. Para obtener más información, consulte [de control de excepciones (MFC)](../mfc/exception-handling-in-mfc.md).

## <a name="see-also"></a>Vea también

[Archivos](../mfc/files-in-mfc.md)
