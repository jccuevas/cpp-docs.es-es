---
title: Limpiar documentos y vistas
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 1357a02379a848af23a6f78dee29e5b6adc1efcc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653903"
---
# <a name="cleaning-up-documents-and-views"></a>Limpiar documentos y vistas

Cuando se cierra un documento, el marco de trabajo llama primero su [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) función miembro. Si ha asignado memoria en el montón durante el transcurso de la operación del documento, `DeleteContents` es el mejor lugar para desasignarla.

> [!NOTE]
>  No debe desasignar datos del documento en el destructor del documento. En el caso de una aplicación SDI, se podría reutilizar el objeto de documento.

Puede invalidar el destructor de una vista para desasignar la memoria asignada en el montón.

## <a name="see-also"></a>Vea también

[Inicialización y limpieza de documentos y vistas](../mfc/initializing-and-cleaning-up-documents-and-views.md)

