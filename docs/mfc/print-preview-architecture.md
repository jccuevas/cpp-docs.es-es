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
ms.openlocfilehash: 1956313d4e904255ba59e79690fe3d7144669a29
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623935"
---
# <a name="print-preview-architecture"></a>Arquitectura de la vista previa de impresión

En este artículo se explica cómo el marco de trabajo de MFC implementa la funcionalidad de vista previa de impresión. Temas cubiertos:

- [Proceso de vista previa de impresión](#_core_the_print_preview_process)

- [Modificar la vista previa de impresión](#_core_modifying_print_preview)

La vista previa de impresión es algo diferente de la presentación en pantalla y la impresión porque, en lugar de dibujar directamente una imagen en un dispositivo, la aplicación debe simular la impresora mediante la pantalla. Para dar cabida a esto, el biblioteca MFC define una clase especial (no documentada) derivada de la [clase CDC](reference/cdc-class.md), denominada `CPreviewDC` . Todos los `CDC` objetos contienen dos contextos de dispositivo, pero normalmente son idénticos. En un `CPreviewDC` objeto, son diferentes: el primero representa la impresora que se está simulando y la segunda representa la pantalla en la que se muestra realmente la salida.

## <a name="the-print-preview-process"></a><a name="_core_the_print_preview_process"></a>Proceso de vista previa de impresión

Cuando el usuario selecciona el comando vista previa de impresión en el menú **archivo** , el marco de trabajo crea un `CPreviewDC` objeto. Cada vez que la aplicación realiza una operación que establece una característica del contexto del dispositivo de impresora, el marco también realiza una operación similar en el contexto de dispositivo de pantalla. Por ejemplo, si la aplicación selecciona una fuente para imprimirla, el marco de trabajo selecciona una fuente para la presentación en pantalla que simula la fuente de la impresora. Siempre que la aplicación envíe la salida a la impresora, el marco de trabajo envía la salida a la pantalla.

La vista previa de impresión también difiere de la impresión en el orden en que cada uno dibuja las páginas de un documento. Durante la impresión, el marco continúa un bucle de impresión hasta que se ha representado un determinado intervalo de páginas. Durante la vista previa de impresión, se muestran una o dos páginas en cualquier momento y, a continuación, la aplicación espera; no se muestran más páginas hasta que el usuario responde. Durante la vista previa de impresión, la aplicación también debe responder a WM_PAINT mensajes, tal como lo hace durante la presentación de pantalla normal.

Se llama a la función [CView:: OnPreparePrinting](reference/cview-class.md#onprepareprinting) cuando se invoca el modo de vista previa, tal como está al principio de un trabajo de impresión. La estructura de [estructura CPrintInfo](reference/cprintinfo-structure.md) pasada a la función contiene varios miembros cuyos valores se pueden establecer para ajustar ciertas características de la operación de vista previa de impresión. Por ejemplo, puede establecer el miembro *m_nNumPreviewPages* para especificar si desea obtener una vista previa del documento en modo de una o dos páginas.

## <a name="modifying-print-preview"></a><a name="_core_modifying_print_preview"></a>Modificar la vista previa de impresión

Puede modificar el comportamiento y la apariencia de la vista previa de impresión de varias maneras. Por ejemplo, puede, entre otras cosas:

- Hacer que la ventana de vista previa de impresión muestre una barra de desplazamiento para facilitar el acceso a cualquier página del documento.

- Hacer que la vista previa de impresión mantenga la posición del usuario en el documento empezando su presentación en la página actual.

- Hace que se realice una inicialización diferente para la impresión y la vista previa de impresión.

- Hacer que la vista previa de impresión muestre los números de página en sus propios formatos.

Si sabe cuánto tiempo es el documento y llama a `SetMaxPage` con el valor adecuado, el marco de trabajo puede utilizar esta información en el modo de vista previa, así como durante la impresión. Una vez que el marco de trabajo conoce la longitud del documento, puede proporcionar la ventana de vista previa con una barra de desplazamiento, lo que permite al usuario avanzar y retroceder por el documento en el modo de vista previa. Si no ha establecido la longitud del documento, el marco de trabajo no puede colocar el cuadro de desplazamiento para indicar la posición actual, por lo que el marco no agrega una barra de desplazamiento. En este caso, el usuario debe usar los botones página siguiente y página anterior de la barra de control de la ventana de vista previa para desplazarse por el documento.

En la vista previa de impresión, puede que le resulte útil asignar un valor al miembro *m_nCurPage* de `CPrintInfo` , aunque nunca lo haría para la impresión normal. Durante la impresión normal, este miembro transporta información del marco de trabajo a la clase de vista. Así es como el marco de trabajo indica a la vista qué página se debe imprimir.

Por el contrario, cuando se inicia el modo de vista previa de impresión, el miembro de *m_nCurPage* incluye información en la dirección opuesta: desde la vista hasta el marco de trabajo. El marco de trabajo usa el valor de este miembro para determinar la página en la que se debe obtener una vista previa en primer lugar. El valor predeterminado de este miembro es 1, por lo que la primera página del documento se muestra inicialmente. Puede invalidar `OnPreparePrinting` para establecer este miembro en el número de la página que se está viendo en el momento en que se invocó el comando de vista previa de impresión. De esta manera, la aplicación mantiene la posición actual del usuario al pasar del modo de presentación normal al modo de vista previa de impresión.

En ocasiones, es posible que desee `OnPreparePrinting` realizar una inicialización diferente en función de si se llama para un trabajo de impresión o para la vista previa de impresión. Puede determinarlo examinando la variable miembro de *m_bPreview* en la `CPrintInfo` estructura. Este miembro se establece en **true** cuando se invoca la vista previa de impresión.

La `CPrintInfo` estructura también contiene un miembro denominado *m_strPageDesc*, que se usa para dar formato a las cadenas que se muestran en la parte inferior de la pantalla en los modos de una página y de varias páginas. De forma predeterminada, estas cadenas tienen el formato "página *n*" y "páginas *n*  -  *m*", pero puede modificar *m_strPageDesc* desde `OnPreparePrinting` y establecer las cadenas en algo más elaborado. Vea [CPrintInfo (estructura](reference/cprintinfo-structure.md) ) en la *referencia de MFC* para obtener más información.

## <a name="see-also"></a>Consulte también

[Impresión y vista previa de impresión](printing-and-print-preview.md)<br/>
[Impresión](printing.md)<br/>
[CView (clase)](reference/cview-class.md)<br/>
[CDC (clase)](reference/cdc-class.md)
