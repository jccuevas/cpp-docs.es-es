---
title: Arquitectura de la vista previa de impresión
ms.date: 11/04/2016
helpviewer_keywords:
- print preview [MFC], process
- previewing printing
- print preview [MFC], architecture
- printing [MFC], print preview
- print preview [MFC], modifications to MFC
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
ms.openlocfilehash: 5943edc22cd48ed10d152f72624467ff87104b96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375945"
---
# <a name="print-preview-architecture"></a>Arquitectura de la vista previa de impresión

En este artículo se explica cómo el marco mfc implementa la funcionalidad de vista previa de impresión. Temas cubiertos:

- [Proceso de vista previa de impresión](#_core_the_print_preview_process)

- [Modificación de la vista previa de impresión](#_core_modifying_print_preview)

La vista previa de impresión es algo diferente de la visualización de la pantalla y la impresión porque, en lugar de dibujar directamente una imagen en un dispositivo, la aplicación debe simular la impresora utilizando la pantalla. Para dar cabida a esto, la biblioteca Microsoft Foundation Class define `CPreviewDC`una clase especial (no documentada) derivada de CDC [Class](../mfc/reference/cdc-class.md), denominada . Todos `CDC` los objetos contienen dos contextos de dispositivo, pero normalmente son idénticos. En `CPreviewDC` un objeto, son diferentes: el primero representa la impresora que se está simulando y el segundo representa la pantalla en la que se muestra realmente la salida.

## <a name="the-print-preview-process"></a><a name="_core_the_print_preview_process"></a>El proceso de vista previa de impresión

Cuando el usuario selecciona el comando Vista previa de `CPreviewDC` impresión del menú **Archivo,** el marco de trabajo crea un objeto. Cada vez que la aplicación realiza una operación que establece una característica del contexto del dispositivo de impresora, el marco de trabajo también realiza una operación similar en el contexto del dispositivo de pantalla. Por ejemplo, si la aplicación selecciona una fuente para imprimir, el marco de trabajo selecciona una fuente para la visualización de pantalla que simula la fuente de la impresora. Cada vez que la aplicación enviaría la salida a la impresora, el marco de trabajo en su lugar envía la salida a la pantalla.

La vista previa de impresión también difiere de la impresión en el orden en que cada uno dibuja las páginas de un documento. Durante la impresión, el marco de trabajo continúa un bucle de impresión hasta que se ha representado un cierto rango de páginas. Durante la vista previa de impresión, se muestran una o dos páginas en cualquier momento y, a continuación, la aplicación espera; no se mostrarán más páginas hasta que el usuario responda. Durante la vista previa de impresión, la aplicación también debe responder a WM_PAINT mensajes, tal como lo hace durante la visualización de pantalla ordinaria.

Se llama a la función [CView::OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) cuando se invoca el modo de vista previa, al igual que al principio de un trabajo de impresión. La estructura [de estructura CPrintInfo](../mfc/reference/cprintinfo-structure.md) pasada a la función contiene varios miembros cuyos valores se pueden establecer para ajustar ciertas características de la operación de vista previa de impresión. Por ejemplo, puede establecer el *miembro m_nNumPreviewPages* para especificar si desea obtener una vista previa del documento en modo de una o dos páginas.

## <a name="modifying-print-preview"></a><a name="_core_modifying_print_preview"></a>Modificación de la vista previa de impresión

Puede modificar el comportamiento y la apariencia de la vista previa de impresión de varias maneras con bastante facilidad. Por ejemplo, puede, entre otras cosas:

- Haga que la ventana de vista previa de impresión muestre una barra de desplazamiento para facilitar el acceso a cualquier página del documento.

- Haga que la vista previa de impresión mantenga la posición del usuario en el documento iniciando su visualización en la página actual.

- Haga que se realice una inicialización diferente para la vista previa de impresión y la impresión.

- Haga que la vista previa de impresión muestre los números de página en sus propios formatos.

Si sabe cuánto tiempo es `SetMaxPage` el documento y llama con el valor adecuado, el marco de trabajo puede usar esta información en modo de vista previa, así como durante la impresión. Una vez que el marco de trabajo conoce la longitud del documento, puede proporcionar la ventana de vista previa con una barra de desplazamiento, lo que permite al usuario paginar hacia adelante y hacia atrás a través del documento en modo de vista previa. Si no ha establecido la longitud del documento, el marco de trabajo no puede colocar el cuadro de desplazamiento para indicar la posición actual, por lo que el marco de trabajo no agrega una barra de desplazamiento. En este caso, el usuario debe usar los botones Página siguiente y Página anterior de la barra de control de la ventana de vista previa para paginar el documento.

Para la vista previa de impresión, puede resultarle `CPrintInfo`útil asignar un valor al miembro *m_nCurPage* de , aunque nunca lo haría para la impresión normal. Durante la impresión normal, este miembro lleva información del marco de trabajo a la clase de vista. Así es como el marco de trabajo indica a la vista qué página se debe imprimir.

Por el contrario, cuando se inicia el modo de vista previa de impresión, el miembro *m_nCurPage* lleva información en la dirección opuesta: desde la vista hasta el marco de trabajo. El marco de trabajo usa el valor de este miembro para determinar qué página se debe obtener primero la vista previa. El valor predeterminado de este miembro es 1, por lo que la primera página del documento se muestra inicialmente. Puede invalidar `OnPreparePrinting` para establecer este miembro en el número de la página que se está viendo en el momento en que se invocó el comando Vista previa de impresión. De esta manera, la aplicación mantiene la posición actual del usuario al pasar del modo de visualización normal al modo de vista previa de impresión.

A veces `OnPreparePrinting` es posible que desee realizar una inicialización diferente dependiendo de si se llama para un trabajo de impresión o para la vista previa de impresión. Puede determinar esto examinando la *variable* `CPrintInfo` miembro m_bPreview en la estructura. Este miembro se establece en **TRUE** cuando se invoca la vista previa de impresión.

La `CPrintInfo` estructura también contiene un miembro denominado *m_strPageDesc*, que se utiliza para dar formato a las cadenas que se muestran en la parte inferior de la pantalla en los modos de una sola página y de varias páginas. De forma predeterminada, estas cadenas tienen el formato "Página *n"* y "Páginas *n* - *m*", pero puede modificar *m_strPageDesc* desde dentro `OnPreparePrinting` y establecer las cadenas en algo más elaborado. Consulte [CPrintInfo Structure](../mfc/reference/cprintinfo-structure.md) en la *referencia de MFC* para obtener más información.

## <a name="see-also"></a>Consulte también

[Impresión y vista previa de impresión](../mfc/printing-and-print-preview.md)<br/>
[Impresión](../mfc/printing.md)<br/>
[CView (clase)](../mfc/reference/cview-class.md)<br/>
[Clase CDC](../mfc/reference/cdc-class.md)
