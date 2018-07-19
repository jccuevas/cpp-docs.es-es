---
title: Cerrar archivos | Documentos de Microsoft
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
ms.openlocfilehash: 97bd910ae4cb514cda07dd319f37a05a32712909
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341031"
---
# <a name="closing-files"></a>Cerrar archivos
Como es habitual en las operaciones de E/S, una vez que termine con un archivo, se debe cerrar.  
  
#### <a name="to-close-a-file"></a>Para cerrar un archivo  
  
1.  Use la **cerrar** función miembro. Esta función cierra el archivo de sistema de archivos y vacía los búferes si es necesario.  
  
 Si ha asignado la [CFile](../mfc/reference/cfile-class.md) objeto en el marco (como en el ejemplo se muestra en [abrir archivos](../mfc/opening-files.md)), configurará automáticamente y el objeto se cierra y se destruyen cuando sale del ámbito. Tenga en cuenta que al eliminar el `CFile` objeto no elimina el archivo físico del sistema de archivos.  
  
## <a name="see-also"></a>Vea también  
 [Archivos](../mfc/files-in-mfc.md)

