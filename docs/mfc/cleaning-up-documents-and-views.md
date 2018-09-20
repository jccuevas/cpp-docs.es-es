---
title: Limpiar documentos y vistas | Microsoft Docs
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
ms.openlocfilehash: f4325b0de10861fc76ee9ab816376f40ba0ba587
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437422"
---
# <a name="cleaning-up-documents-and-views"></a>Limpiar documentos y vistas

Cuando se cierra un documento, el marco de trabajo llama primero su [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) función miembro. Si ha asignado memoria en el montón durante el transcurso de la operación del documento, `DeleteContents` es el mejor lugar para desasignarla.

> [!NOTE]
>  No debe desasignar datos del documento en el destructor del documento. En el caso de una aplicación SDI, se podría reutilizar el objeto de documento.

Puede invalidar el destructor de una vista para desasignar la memoria asignada en el montón.

## <a name="see-also"></a>Vea también

[Inicialización y limpieza de documentos y vistas](../mfc/initializing-and-cleaning-up-documents-and-views.md)

