---
title: Componentes de cuadro de diálogo en el marco de trabajo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6936a48d1a3e1845d56c73524c84800d9d605155
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065517"
---
# <a name="dialog-box-components-in-the-framework"></a>Componentes de cuadro de diálogo en el marco

En el marco de trabajo MFC, un cuadro de diálogo tiene dos componentes:

- Un recurso de plantilla de cuadro de diálogo que especifica los controles del cuadro de diálogo y su ubicación.

   El recurso de cuadro de diálogo almacena una plantilla de cuadro de diálogo desde el que Windows crea la ventana de cuadro de diálogo y lo muestran. La plantilla especifica las características del cuadro de diálogo, incluidos su tamaño, ubicación, estilo y los tipos y posiciones de los controles del cuadro de diálogo. Normalmente, usará una plantilla de cuadro de diálogo almacenada como un recurso, pero también puede crear su propia plantilla en la memoria.

- Deriva una clase de cuadro de diálogo, [CDialog](../mfc/reference/cdialog-class.md), para proporcionar una interfaz de programación para administrar el cuadro de diálogo.

   Un cuadro de diálogo es una ventana y se adjuntará a una ventana de Windows cuando está visible. Cuando se crea la ventana de cuadro de diálogo, el recurso de plantilla de cuadro de diálogo se usa como plantilla para crear controles de ventana del cuadro de diálogo de secundarios.

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)<br/>
[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)

