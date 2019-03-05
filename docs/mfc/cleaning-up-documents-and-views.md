---
title: Limpiar documentos y vistas
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 940c768823d26950d9710fb1d1a52e6a1955fead
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258819"
---
# <a name="cleaning-up-documents-and-views"></a>Limpiar documentos y vistas

Cuando se cierra un documento, el marco de trabajo llama primero su [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) función miembro. Si ha asignado memoria en el montón durante el transcurso de la operación del documento, `DeleteContents` es el mejor lugar para desasignarla.

> [!NOTE]
>  No debe desasignar datos del documento en el destructor del documento. En el caso de una aplicación SDI, se podría reutilizar el objeto de documento.

Puede invalidar el destructor de una vista para desasignar la memoria asignada en el montón.

## <a name="see-also"></a>Vea también

[Inicialización y limpieza de documentos y vistas](../mfc/initializing-and-cleaning-up-documents-and-views.md)
