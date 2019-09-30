---
title: Inicializar el cuadro de diálogo
ms.date: 11/04/2016
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
ms.openlocfilehash: 14cdf94bef79f254b4aaa2c1c0dfba6c88b7498b
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685620"
---
# <a name="initializing-the-dialog-box"></a>Inicializar el cuadro de diálogo

Después de crear el cuadro de diálogo y todos sus controles pero justo antes de que el cuadro de diálogo (de cualquier tipo) aparezca en la pantalla, se llama a la función miembro [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) del objeto de cuadro de diálogo. En un cuadro de diálogo modal, esto ocurre durante la llamada a `DoModal`. En un cuadro de diálogo no modal, se llama a `OnInitDialog` cuando se llama a `Create`. Normalmente, se invalida `OnInitDialog` para inicializar los controles del cuadro de diálogo, como establecer el texto inicial de un cuadro de edición. Debe llamar a la función miembro `OnInitDialog` de la clase base, `CDialog`, de la invalidación `OnInitDialog`.

Si desea establecer el color de fondo de un cuadro de diálogo (y el de todos los demás cuadros de diálogo de la aplicación), vea [establecer el color de fondo del cuadro de diálogo](../mfc/setting-the-dialog-boxs-background-color.md).

## <a name="see-also"></a>Vea también

[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)
