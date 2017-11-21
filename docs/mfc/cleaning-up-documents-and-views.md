---
title: Limpiar documentos y vistas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f9bb1cbcb58e2693b33693b390a09d3826c77cfd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cleaning-up-documents-and-views"></a>Limpiar documentos y vistas
Cuando se cierra un documento, el marco de trabajo llama primero su [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) función miembro. Si ha asignado memoria en el montón en el transcurso de la operación del documento, `DeleteContents` es el mejor lugar para desasignarla.  
  
> [!NOTE]
>  No se deben cancelar la asignación de datos del documento en el destructor del documento. En el caso de una aplicación SDI, se puede reutilizar el objeto de documento.  
  
 Puede invalidar el destructor de una vista para desasignar la memoria asignada en el montón.  
  
## <a name="see-also"></a>Vea también  
 [Inicialización y limpieza de documentos y vistas](../mfc/initializing-and-cleaning-up-documents-and-views.md)

