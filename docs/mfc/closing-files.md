---
title: Cerrar archivos
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
ms.openlocfilehash: 04e5084615b1f1cf85d9f41e2c4dcc84910b9d05
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636272"
---
# <a name="closing-files"></a>Cerrar archivos

Como es habitual en las operaciones de E/S, cuando haya terminado con un archivo, debe cerrarlo.

#### <a name="to-close-a-file"></a>Para cerrar un archivo

1. Use la **cerrar** función miembro. Esta función cierra el archivo de sistema de archivos y vacía los búferes si es necesario.

Si ha asignado la [CFile](../mfc/reference/cfile-class.md) objeto en el marco (como en el ejemplo se muestra en [abrir archivos](../mfc/opening-files.md)), automáticamente se cerrará y, a continuación, se destruye cuando sale del ámbito. Tenga en cuenta que al eliminar el `CFile` objeto no elimina el archivo físico en el sistema de archivos.

## <a name="see-also"></a>Vea también

[Archivos](../mfc/files-in-mfc.md)

