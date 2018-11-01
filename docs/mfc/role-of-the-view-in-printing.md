---
title: Rol de la vista en la impresión | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], printing
- OnDraw method [MFC], and printing
- printing [MFC], OnDraw method [MFC]
- printing [MFC], views
- CView class [MFC], role in printing
- printing views [MFC]
ms.assetid: 8d4a3c8e-1fce-4edc-b608-94cb5f3e487e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c78756ea84df66b77f71d8f8ad8d0b9dfa1a6c9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377531"
---
# <a name="role-of-the-view-in-printing"></a>Rol de la vista en la impresión

La vista también desempeña dos funciones importantes al imprimir el documento asociado.

La vista:

- Usa el mismo [OnDraw](../mfc/reference/cview-class.md#ondraw) código para dibujar en la impresora que para dibujar en la pantalla.

- Administra la división del documento en páginas para imprimir.

Para obtener más información sobre cómo imprimir y rol de la vista en la impresión, consulte [impresión y vista previa de impresión](../mfc/printing-and-print-preview.md).

## <a name="see-also"></a>Vea también

[Uso de vistas](../mfc/using-views.md)

