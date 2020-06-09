---
title: Cerrar archivos
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
ms.openlocfilehash: 51e51c88260a51ec44f11ecb5c2a88e645194f4e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617230"
---
# <a name="closing-files"></a>Cerrar archivos

Como de costumbre en operaciones de e/s, una vez que haya terminado con un archivo, debe cerrarlo.

#### <a name="to-close-a-file"></a>Para cerrar un archivo

1. Utilice la función miembro **Close** . Esta función cierra el archivo del sistema de archivos y vacía los búferes si es necesario.

Si ha asignado el objeto [CFile](reference/cfile-class.md) en el marco (como en el ejemplo que se muestra en [abrir archivos](opening-files.md)), el objeto se cerrará automáticamente y se destruirá cuando salga del ámbito. Tenga en cuenta que al eliminar el objeto no se `CFile` elimina el archivo físico en el sistema de archivos.

## <a name="see-also"></a>Consulte también

[Archivos](files-in-mfc.md)
