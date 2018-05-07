---
title: Obtener acceso al estado de archivo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- files [MFC], status information
- examples [MFC], file status
- files [MFC], accessing
- file status [MFC]
- status of files [MFC]
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d424502e991ea355a6e31bba8fedccb6d5ad2fcf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-file-status"></a>Acceso al estado del archivo
`CFile` También permite obtener estado de archivo, incluso si el archivo existe, las fechas de creación y modificación y veces, el tamaño lógico y ruta de acceso.  
  
### <a name="to-get-file-status"></a>Para obtener el estado de archivo  
  
1.  Use la [CFile](../mfc/reference/cfile-class.md) clase para obtener y establecer información acerca de un archivo. Una aplicación útil consiste en utilizar el `CFile` función miembro estática **GetStatus** para determinar si existe un archivo. **GetStatus** devuelve 0 si el archivo especificado no existe.  
  
 Por lo tanto, podría utilizar el resultado de **GetStatus** para determinar si se debe usar el **CFile:: modeCreate** marca al abrir un archivo, como se muestra en el ejemplo siguiente:  
  
 [!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]  
  
 Para obtener información relacionada, consulte [serialización](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [Archivos](../mfc/files-in-mfc.md)

