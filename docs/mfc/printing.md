---
title: Impresión
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: a46096592c9983d04d2122bfabb56ece9346c4bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371204"
---
# <a name="printing"></a>Impresión

Microsoft Windows implementa la visualización independiente del dispositivo. En MFC, esto significa que las `OnDraw` mismas llamadas de dibujo, en la función miembro de la clase de vista, son responsables de dibujar en la pantalla y en otros dispositivos, como impresoras. Para la vista previa de impresión, el dispositivo de destino es una salida de impresora simulada a la pantalla.

## <a name="your-role-in-printing-vs-the-frameworks-role"></a><a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a>Su rol en la impresión frente al rol del marco de trabajo

La clase de vista tiene las siguientes responsabilidades:

- Informe al marco de trabajo cuántas páginas hay en el documento.

- Cuando se le pida que imprima una página especificada, dibuje esa parte del documento.

- Asigne y desasigna las fuentes u otros recursos de interfaz de dispositivo gráfico (GDI) necesarios para la impresión.

- Si es necesario, envíe los códigos de escape necesarios para cambiar el modo de impresora antes de imprimir una página determinada, por ejemplo, para cambiar la orientación de impresión por página.

Las responsabilidades del marco son las siguientes:

- Visualice el cuadro de diálogo **Imprimir.**

- Cree un objeto [CDC](../mfc/reference/cdc-class.md) para la impresora.

- Llame a las funciones miembro `CDC` [StartDoc](../mfc/reference/cdc-class.md#startdoc) y [EndDoc](../mfc/reference/cdc-class.md#enddoc) del objeto.

- Llame repetidamente a la [StartPage](../mfc/reference/cdc-class.md#startpage) función miembro del `CDC` objeto, informar a la clase de vista qué página se debe imprimir y llame a la [EndPage](../mfc/reference/cdc-class.md#endpage) función miembro del `CDC` objeto.

- Llame a funciones reemplazables en la vista en los momentos adecuados.

En los artículos siguientes se explica cómo el marco de trabajo admite la impresión y la vista previa de impresión:

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Cómo se realiza la impresión predeterminada](../mfc/how-default-printing-is-done.md)

- [Documentos de varias páginas](../mfc/multipage-documents.md)

- [Encabezados y pies de página](../mfc/headers-and-footers.md)

- [Asignación de recursos De GDI para la impresión](../mfc/allocating-gdi-resources.md)

- [Vista previa de impresión](../mfc/print-preview-architecture.md)

## <a name="see-also"></a>Consulte también

[Impresión y vista previa de impresión](../mfc/printing-and-print-preview.md)
