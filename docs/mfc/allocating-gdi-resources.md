---
title: Asignar recursos de GDI
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: f0cadac5320a8c6e91eb3b1989d1fb3c0c701eb0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623235"
---
# <a name="allocating-gdi-resources"></a>Asignar recursos de GDI

En este artículo se explica cómo asignar y desasignar los objetos de la Interfaz de dispositivo gráfico (GDI) de Windows necesarios para la impresión.

> [!NOTE]
> Para obtener más información, vea la [documentación del SDK de GDI+](/windows/win32/gdiplus/-gdiplus-gdi-start).

Supongamos que necesita usar determinadas fuentes, lápices u otros objetos GDI para imprimir, pero no para la visualización en pantalla. Debido a la memoria que necesitan, no resulta eficiente asignar estos objetos cuando se inicia la aplicación. Cuando la aplicación no está imprimiendo un documento, esa memoria puede ser necesaria para otros fines. Es mejor asignarlos cuando comienza la impresión y, después, eliminarlos cuando la impresión haya terminado.

Para asignar estos objetos GDI, reemplace la función miembro [OnBeginPrinting](reference/cview-class.md#onbeginprinting) . Esta función es muy adecuada para este propósito por dos motivos: el marco llama a esta función una vez al principio de cada trabajo de impresión y, a diferencia de [OnPreparePrinting](reference/cview-class.md#onprepareprinting), esta función tiene acceso al objeto [CDC](reference/cdc-class.md) que representa el controlador de dispositivo de impresora. Puede almacenar estos objetos para su uso durante el trabajo de impresión definiendo variables de miembro en la clase de vista que señalen a objetos GDI (por ejemplo, `CFont *` miembros, etc.).

Para usar los objetos GDI que ha creado, selecciónelos en el contexto de dispositivo de impresora de la función miembro [OnPrint](reference/cview-class.md#onprint) . Si necesita objetos GDI diferentes para diferentes páginas del documento, puede examinar el `m_nCurPage` miembro de la estructura [CPrintInfo](reference/cprintinfo-structure.md) y seleccionar el objeto GDI en consecuencia. Si necesita un objeto GDI para varias páginas consecutivas, Windows necesita que lo seleccione en el contexto de dispositivo cada vez que se llame a `OnPrint`.

Para desasignar estos objetos GDI, reemplace la función miembro [OnBeginPrinting](reference/cview-class.md#onendprinting) . El marco llama a esta función al final de cada trabajo de impresión, lo que le ofrece la oportunidad de desasignar objetos GDI específicos de impresión antes de que la aplicación vuelva a otras tareas.

## <a name="see-also"></a>Consulte también

[Impresión](printing.md)<br/>
[Cómo se realiza la impresión predeterminada](how-default-printing-is-done.md)
