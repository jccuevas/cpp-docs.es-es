---
title: Limpiar documentos y vistas
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 06ff60a2cf6245f64e80d899c13a8444558fcf0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374620"
---
# <a name="cleaning-up-documents-and-views"></a>Limpiar documentos y vistas

Cuando se cierra un documento, el marco de trabajo llama primero a su [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) función miembro. Si ha asignado memoria en el montón durante el `DeleteContents` transcurso de la operación del documento, es el mejor lugar para desasignarlo.

> [!NOTE]
> No debe desasignar datos de documento en el destructor del documento. En el caso de una aplicación SDI, el objeto de documento podría reutilizarse.

Puede invalidar el destructor de una vista para desasignar cualquier memoria asignada en el montón.

## <a name="see-also"></a>Consulte también

[Inicialización y limpieza de documentos y vistas](../mfc/initializing-and-cleaning-up-documents-and-views.md)
