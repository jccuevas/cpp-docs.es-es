---
title: Componentes de cuadro de diálogo en el marco
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
ms.openlocfilehash: b3290107337f60854e6abbd2f744aaa38af0b741
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616918"
---
# <a name="dialog-box-components-in-the-framework"></a>Componentes de cuadro de diálogo en el marco

En el marco de trabajo de MFC, un cuadro de diálogo tiene dos componentes:

- Un recurso de plantilla de cuadro de diálogo que especifica los controles del cuadro de diálogo y su ubicación.

   El recurso de cuadro de diálogo almacena una plantilla de cuadro de diálogo desde la que Windows crea la ventana de cuadro de diálogo y la muestra. La plantilla especifica las características del cuadro de diálogo, incluido su tamaño, ubicación, estilo y los tipos y posiciones de los controles del cuadro de diálogo. Normalmente, usará una plantilla de cuadro de diálogo almacenada como un recurso, pero también puede crear su propia plantilla en la memoria.

- Una clase de cuadro de diálogo, derivada de [CDialog](reference/cdialog-class.md), para proporcionar una interfaz de programación para administrar el cuadro de diálogo.

   Un cuadro de diálogo es una ventana y se adjunta a una ventana de Windows cuando está visible. Cuando se crea la ventana de cuadro de diálogo, el recurso de plantilla de cuadro de diálogo se utiliza como plantilla para crear controles de ventana secundarios para el cuadro de diálogo.

## <a name="see-also"></a>Consulte también

[Cuadros de diálogo](dialog-boxes.md)<br/>
[Trabajar con cuadros de diálogo en MFC](life-cycle-of-a-dialog-box.md)
