---
title: Cerrar archivos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 27b1c59c952b022c7382db7d6b2dcb660cca2e9a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="closing-files"></a>Cerrar archivos
Como es habitual en las operaciones de E/S, una vez que termine con un archivo, se debe cerrar.  
  
#### <a name="to-close-a-file"></a>Para cerrar un archivo  
  
1.  Use la **cerrar** función miembro. Esta función cierra el archivo de sistema de archivos y vacía los búferes si es necesario.  
  
 Si ha asignado la [CFile](../mfc/reference/cfile-class.md) objeto en el marco (como en el ejemplo se muestra en [abrir archivos](../mfc/opening-files.md)), configurará automáticamente y el objeto se cierra y se destruyen cuando sale del ámbito. Tenga en cuenta que al eliminar el `CFile` objeto no elimina el archivo físico del sistema de archivos.  
  
## <a name="see-also"></a>Vea también  
 [Archivos](../mfc/files-in-mfc.md)

