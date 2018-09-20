---
title: Cerrar archivos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c392ef728e1d796a02cfa32edc2c3e8c74d083b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426242"
---
# <a name="closing-files"></a>Cerrar archivos

Como es habitual en las operaciones de E/S, cuando haya terminado con un archivo, debe cerrarlo.

#### <a name="to-close-a-file"></a>Para cerrar un archivo

1. Use la **cerrar** función miembro. Esta función cierra el archivo de sistema de archivos y vacía los búferes si es necesario.

Si ha asignado la [CFile](../mfc/reference/cfile-class.md) objeto en el marco (como en el ejemplo se muestra en [abrir archivos](../mfc/opening-files.md)), automáticamente se cerrará y, a continuación, se destruye cuando sale del ámbito. Tenga en cuenta que al eliminar el `CFile` objeto no elimina el archivo físico en el sistema de archivos.

## <a name="see-also"></a>Vea también

[Archivos](../mfc/files-in-mfc.md)

