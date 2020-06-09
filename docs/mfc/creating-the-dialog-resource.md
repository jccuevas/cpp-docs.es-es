---
title: Crear el recurso de cuadro de diálogo
ms.date: 11/04/2016
helpviewer_keywords:
- dialog resources
- MFC dialog boxes [MFC], creating
- dialog templates [MFC], creating dialog resource
- templates [MFC], creating
- resources [MFC], creating dialog boxes
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 0b83bd33-14d3-4611-8129-fccdae18053e
ms.openlocfilehash: efaef11cfdc036a201ced3357ca81b37a5dc29db
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619625"
---
# <a name="creating-the-dialog-resource"></a>Crear el recurso de cuadro de diálogo

Para diseñar el [cuadro de diálogo](dialog-boxes.md) y crear el recurso de diálogo, use el [Editor de cuadros de diálogo](../windows/dialog-editor.md). En el editor de cuadros de diálogo, puede:

- Ajuste el tamaño y la ubicación que tendrá el cuadro de diálogo cuando aparezca.

- Arrastre varios tipos de controles desde una paleta de controles y colóquelos donde desee en el cuadro de diálogo.

- Coloque los controles con botones de alineación en la barra de herramientas.

- Pruebe el cuadro de diálogo mediante la simulación de la apariencia y el comportamiento que tendrá en el programa. En el modo de prueba, puede manipular los controles del cuadro de diálogo escribiendo texto en cuadros de texto, haciendo clic en pulsadores, etc.

Cuando termine, el recurso de plantilla de cuadro de diálogo se almacena en el archivo de script de recursos de la aplicación. Puede editarlo más adelante si es necesario. Para obtener una descripción completa de cómo crear y editar recursos de cuadro de diálogo, vea los temas del [Editor de cuadros de diálogo](../windows/dialog-editor.md) . Esta técnica también se usa para crear los recursos de plantilla de cuadro de diálogo para las clases [CFormView](reference/cformview-class.md) y [CRecordView](reference/crecordview-class.md) .

Cuando la apariencia del cuadro de diálogo le convenga, cree una clase de diálogo y asigne sus mensajes, como se describe en [crear una clase de diálogo con los asistentes para código](creating-a-dialog-class-with-code-wizards.md).

## <a name="see-also"></a>Consulte también

[Cuadros de diálogo](dialog-boxes.md)<br/>
[Trabajar con cuadros de diálogo en MFC](life-cycle-of-a-dialog-box.md)
