---
title: Impresión | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e03e750941be02385ac4d5b7463d5b6f32997b6a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373953"
---
# <a name="printing"></a>Impresión

Microsoft Windows implementa mostrar independientes del dispositivo. En MFC, esto significa que las mismas llamadas de dibujos, en el `OnDraw` función miembro de la clase de vista, son responsables del dibujo en la pantalla y en otros dispositivos, como las impresoras. Para la vista previa de impresión, el dispositivo de destino es una salida de impresora simulada a la pantalla.

##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a> Su rol en impresión frente a trabajo del marco de

La clase de vista tiene las siguientes responsabilidades:

- Informar al marco de trabajo de cuántas páginas se encuentran en el documento.

- Cuando se le pida para imprimir una página especificada, dibujar esa parte del documento.

- Asignar y desasignar cualquier fuente u otros recursos de interfaz (GDI) de dispositivo de gráficos necesarios para la impresión.

- Si es necesario, envía ninguno es necesarios para cambiar el modo de la impresora antes de imprimir una página determinada, por ejemplo, para cambiar la orientación de impresión en una función de la página de códigos de escape.

Responsabilidades del marco de trabajo son los siguientes:

- Mostrar el **impresión** cuadro de diálogo.

- Crear un [CDC](../mfc/reference/cdc-class.md) objeto para la impresora.

- Llame a la [StartDoc](../mfc/reference/cdc-class.md#startdoc) y [EndDoc](../mfc/reference/cdc-class.md#enddoc) funciones miembro de la `CDC` objeto.

- Llamar repetidamente a la [StartPage](../mfc/reference/cdc-class.md#startpage) función miembro de la `CDC` objeto, informar a la clase de vista de página que se debe imprimir y llame a la [EndPage](../mfc/reference/cdc-class.md#endpage) función miembro de la `CDC` objeto.

- Llamar a funciones que se puede invalidar en la vista en el momento adecuado.

Los siguientes artículos describen cómo el marco de trabajo es compatible con la impresión y vista previa:

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [¿Cómo se realiza la impresión predeterminada](../mfc/how-default-printing-is-done.md)

- [Documentos de varias páginas](../mfc/multipage-documents.md)

- [Encabezados y pies de página](../mfc/headers-and-footers.md)

- [Asignar recursos de GDI para imprimir](../mfc/allocating-gdi-resources.md)

- [Vista previa de impresión](../mfc/print-preview-architecture.md)

## <a name="see-also"></a>Vea también

[Impresión y vista previa de impresión](../mfc/printing-and-print-preview.md)

