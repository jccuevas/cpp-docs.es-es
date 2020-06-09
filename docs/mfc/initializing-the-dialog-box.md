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
ms.openlocfilehash: 1f8f8f7e40b1c873c4428542c628d02e250f14b4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626343"
---
# <a name="initializing-the-dialog-box"></a>Inicializar el cuadro de diálogo

Después de crear el cuadro de diálogo y todos sus controles pero justo antes de que el cuadro de diálogo (de cualquier tipo) aparezca en la pantalla, se llama a la función miembro [OnInitDialog](reference/cdialog-class.md#oninitdialog) del objeto de cuadro de diálogo. Para un cuadro de diálogo modal, esto se produce durante la `DoModal` llamada. En un cuadro de diálogo no modal, `OnInitDialog` se llama a cuando `Create` se llama a. Normalmente se invalida `OnInitDialog` para inicializar los controles del cuadro de diálogo, como establecer el texto inicial de un cuadro de edición. Debe llamar a la `OnInitDialog` función miembro de la clase base, `CDialog` , de la `OnInitDialog` invalidación.

Si desea establecer el color de fondo de un cuadro de diálogo (y el de todos los demás cuadros de diálogo de la aplicación), vea [establecer el color de fondo del cuadro de diálogo](setting-the-dialog-boxs-background-color.md).

## <a name="see-also"></a>Consulte también

[Trabajar con cuadros de diálogo en MFC](life-cycle-of-a-dialog-box.md)
