---
title: Asignar recursos de GDI
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: 149aefeade6f99c294b12bfb294cdf1addb9e5e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370851"
---
# <a name="allocating-gdi-resources"></a>Asignar recursos de GDI

En este artículo se explica cómo asignar y desasignar los objetos de la Interfaz de dispositivo gráfico (GDI) de Windows necesarios para la impresión.

> [!NOTE]
> Para obtener más información, consulte la documentación del SDK de [GDI+GDI+.](/windows/win32/gdiplus/-gdiplus-gdi-start)

Supongamos que necesita usar determinadas fuentes, lápices u otros objetos GDI para imprimir, pero no para la visualización en pantalla. Debido a la memoria que necesitan, no resulta eficiente asignar estos objetos cuando se inicia la aplicación. Cuando la aplicación no está imprimiendo un documento, esa memoria puede ser necesaria para otros fines. Es mejor asignarlos cuando comienza la impresión y, después, eliminarlos cuando la impresión haya terminado.

Para asignar estos objetos GDI, reemplace el [OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting) función miembro. Esta función es adecuada para este propósito por dos razones: el marco de trabajo llama a esta función una vez al principio de cada trabajo de impresión y, a diferencia de [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting), esta función tiene acceso al objeto [CDC](../mfc/reference/cdc-class.md) que representa el controlador del dispositivo de impresora. Puede almacenar estos objetos para su uso durante el trabajo de impresión definiendo variables `CFont *` miembro en la clase de vista que apunten a objetos GDI (por ejemplo, miembros, etc.).

Para utilizar los objetos GDI que ha creado, selecciónelos en el contexto del dispositivo de impresora en la función miembro [OnPrint.](../mfc/reference/cview-class.md#onprint) Si necesita diferentes objetos GDI para diferentes páginas `m_nCurPage` del documento, puede examinar el miembro de la [CPrintInfo](../mfc/reference/cprintinfo-structure.md) estructura y seleccionar el objeto GDI en consecuencia. Si necesita un objeto GDI para varias páginas consecutivas, Windows necesita que lo seleccione en el contexto de dispositivo cada vez que se llame a `OnPrint`.

Para desasignar estos objetos GDI, reemplace la [OnEndPrinting](../mfc/reference/cview-class.md#onendprinting) función miembro. El marco llama a esta función al final de cada trabajo de impresión, lo que le ofrece la oportunidad de desasignar objetos GDI específicos de impresión antes de que la aplicación vuelva a otras tareas.

## <a name="see-also"></a>Consulte también

[Impresión](../mfc/printing.md)<br/>
[Cómo se realiza la impresión predeterminada](../mfc/how-default-printing-is-done.md)
