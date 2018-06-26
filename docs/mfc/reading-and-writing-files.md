---
title: Leer y escribir archivos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e30ee5b326833b45365c422238ecfcd4f82c556d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930916"
---
# <a name="reading-and-writing-files"></a>Leer y escribir en archivos
Si ha usado las funciones de control de archivos de biblioteca en tiempo de ejecución de C, lectura y escritura de las operaciones de MFC le resultarán familiar. Este artículo describe directamente leer y escribir directamente a un `CFile` objeto. También puede búfer E/S de archivos con la [CArchive](../mfc/reference/carchive-class.md) clase.  
  
#### <a name="to-read-from-and-write-to-the-file"></a>Para leer y escribir en el archivo  
  
1.  Use la `Read` y `Write` funciones de miembro para leer y escribir datos en el archivo.  
  
     O bien  
  
2.  El `Seek` función miembro también está disponible para mover a un desplazamiento específico dentro del archivo.  
  
 `Read` toma un puntero a un búfer y el número de bytes que se va a leer y devuelve el número real de bytes leídos. Si el número necesario de bytes no se pudo leer porque final de archivo (EOF) se alcanza, se devuelve el número real de bytes leídos. Si se produce un error de lectura, se produce una excepción. `Write` es similar a `Read`, pero no se devuelve el número de bytes escritos. Si se produce un error de escritura, incluida la no escritura todos los bytes especificados, se produce una excepción. Si tienes un válido `CFile` de objeto, puede leer o escribir en él, tal como se muestra en el ejemplo siguiente:  
  
 [!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]  
  
> [!NOTE]
>  Se debe normalmente llevar a cabo operaciones de entrada/salida dentro de un **intente**/**catch** bloque de control de excepciones. Para obtener más información, consulte [de control de excepciones (MFC)](../mfc/exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [Archivos](../mfc/files-in-mfc.md)

