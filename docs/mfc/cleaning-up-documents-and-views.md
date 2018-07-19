---
title: Limpiar documentos y vistas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2dfe54c13db6f44bc70289380ae5f50d99c3722b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341331"
---
# <a name="cleaning-up-documents-and-views"></a>Limpiar documentos y vistas
Cuando se cierra un documento, el marco de trabajo llama primero su [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) función miembro. Si ha asignado memoria en el montón en el transcurso de la operación del documento, `DeleteContents` es el mejor lugar para desasignarla.  
  
> [!NOTE]
>  No se deben cancelar la asignación de datos del documento en el destructor del documento. En el caso de una aplicación SDI, se puede reutilizar el objeto de documento.  
  
 Puede invalidar el destructor de una vista para desasignar la memoria asignada en el montón.  
  
## <a name="see-also"></a>Vea también  
 [Inicialización y limpieza de documentos y vistas](../mfc/initializing-and-cleaning-up-documents-and-views.md)

