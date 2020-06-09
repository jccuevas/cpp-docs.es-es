---
title: Impresión
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: 3d2ef494be66171cbcbf2b8b9e19c29c8bdc5c2f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619803"
---
# <a name="printing"></a>Impresión

Microsoft Windows implementa la presentación independiente del dispositivo. En MFC, esto significa que las mismas llamadas de dibujo, en la `OnDraw` función miembro de la clase de vista, son responsables del dibujo en la pantalla y en otros dispositivos, como las impresoras. En la vista previa de impresión, el dispositivo de destino es una salida de impresora simulada en la pantalla.

## <a name="your-role-in-printing-vs-the-frameworks-role"></a><a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a>Su rol en la impresión frente al rol del marco de trabajo

La clase de vista tiene las siguientes responsabilidades:

- Informe al marco del número de páginas del documento.

- Cuando se le pida que imprima una página especificada, dibuje esa parte del documento.

- Asigne y Desasigne las fuentes u otros recursos de la interfaz de dispositivo gráfico (GDI) necesarios para la impresión.

- Si es necesario, envíe los códigos de escape necesarios para cambiar el modo de impresión antes de imprimir una página determinada, por ejemplo, para cambiar la orientación de impresión por página.

Las responsabilidades del marco son las siguientes:

- Mostrar el cuadro de diálogo **Imprimir** .

- Cree un objeto [CDC](reference/cdc-class.md) para la impresora.

- Llame a las funciones miembro [StartDoc](reference/cdc-class.md#startdoc) y [EndDoc](reference/cdc-class.md#enddoc) del `CDC` objeto.

- Llame repetidamente a la función miembro [StartPage](reference/cdc-class.md#startpage) del `CDC` objeto, informe a la clase de vista de la página que se debe imprimir y llame a la función miembro [EndPage](reference/cdc-class.md#endpage) del `CDC` objeto.

- Llame a las funciones que se van a reemplazar en la vista en los momentos adecuados.

En los siguientes artículos se describe cómo el marco de trabajo admite la impresión y la vista previa de impresión:

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Cómo se realiza la impresión predeterminada](how-default-printing-is-done.md)

- [Documentos de páginas multipágina](multipage-documents.md)

- [Encabezados y pies de página](headers-and-footers.md)

- [Asignar recursos GDI para imprimir](allocating-gdi-resources.md)

- [Vista previa de impresión](print-preview-architecture.md)

## <a name="see-also"></a>Consulte también

[Impresión y vista previa de impresión](printing-and-print-preview.md)
