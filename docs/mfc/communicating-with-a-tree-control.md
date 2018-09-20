---
title: Comunicación con un Control de árbol | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78bb6a6d6421a5336f8efbffc7d24a6121e208e6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432159"
---
# <a name="communicating-with-a-tree-control"></a>Comunicar con un control de árbol

Usar varios métodos para llamar a funciones miembro un [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objeto dependiendo de cómo se creó el objeto:

- Si el control de árbol está en un cuadro de diálogo, use una variable de miembro de tipo `CTreeCtrl` creados en la clase de cuadro de diálogo.

- Si el control de árbol es una ventana secundaria, use la `CTreeCtrl` objeto (o puntero) utilizado para construir el objeto.

- Si usas un `CTreeView` objeto, utilice la función [CTreeView:: GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) para obtener una referencia al control de árbol. Puede inicializar otra referencia con este valor o asignar la dirección de la referencia a un `CTreeCtrl` puntero.

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

