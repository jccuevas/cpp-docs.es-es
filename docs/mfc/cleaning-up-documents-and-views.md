---
title: Limpiar documentos y vistas
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 8cb6e9337b69daf78286f57898c9badf513c7921
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626524"
---
# <a name="cleaning-up-documents-and-views"></a>Limpiar documentos y vistas

Cuando se cierra un documento, el marco llama primero a su función miembro [DeleteContents](reference/cdocument-class.md#deletecontents) . Si asignó memoria en el montón durante el transcurso de la operación del documento, `DeleteContents` es el mejor lugar para desasignarla.

> [!NOTE]
> No debe desasignar datos de documento en el destructor del documento. En el caso de una aplicación SDI, es posible que se reutilice el objeto de documento.

Puede invalidar el destructor de una vista para desasignar cualquier memoria asignada en el montón.

## <a name="see-also"></a>Consulte también

[Inicialización y limpieza de documentos y vistas](initializing-and-cleaning-up-documents-and-views.md)
