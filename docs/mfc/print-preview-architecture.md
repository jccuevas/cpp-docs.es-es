---
title: Arquitectura de vista previa de impresión | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- print preview [MFC], process
- previewing printing
- print preview [MFC], architecture
- printing [MFC], print preview
- print preview [MFC], modifications to MFC
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e89349811b2d340357e003ad31394cea13eb36b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417597"
---
# <a name="print-preview-architecture"></a>Arquitectura de la vista previa de impresión

En este artículo se explica cómo el marco de trabajo MFC implementa la funcionalidad de vista previa de impresión. Los temas tratados se incluyen:

- [Proceso de vista previa de impresión](#_core_the_print_preview_process)

- [Modificar la vista previa de impresión](#_core_modifying_print_preview)

Vista previa de impresión es un poco diferente de impresión y presentación en pantalla porque, en lugar de dibujar directamente una imagen en un dispositivo, la aplicación debe simular la impresora por medio de la pantalla. Para dar cabida a esto, la biblioteca Microsoft Foundation Class define una clase especial de (sin documentar) derivada de [CDC (clase)](../mfc/reference/cdc-class.md), llamado `CPreviewDC`. Todos los `CDC` objetos contienen dos contextos de dispositivo, pero normalmente son idénticos. En un `CPreviewDC` de objeto, que son diferentes: el primero representa la impresora simulada y el segundo representa la pantalla en el que realmente se muestra la salida.

##  <a name="_core_the_print_preview_process"></a> El proceso de vista previa de impresión

Cuando el usuario selecciona el comando Vista previa de impresión desde el **archivo** menú, el marco crea un `CPreviewDC` objeto. Cada vez que la aplicación realiza una operación que establece una característica del contexto de dispositivo de impresora, el marco de trabajo también realiza una operación similar en el contexto de dispositivo de pantalla. Por ejemplo, si la aplicación selecciona una fuente para imprimir, el marco de trabajo selecciona una fuente de pantalla que simula la fuente de impresora. Cada vez que la aplicación envía resultados a la impresora, el marco de trabajo en su lugar envía el resultado a la pantalla.

Vista previa de impresión también difiere de impresión en el orden en que cada una dibuja las páginas de un documento. Durante la impresión, el marco de trabajo sigue un bucle de impresión hasta que se ha representado un determinado intervalo de páginas. Durante la vista previa de impresión, se muestran una o dos páginas en cualquier momento y, a continuación, espera a que la aplicación; No hay más páginas se muestran hasta que el usuario responde. Durante la vista previa de impresión, la aplicación también debe responder a mensajes WM_PAINT, al igual que durante la presentación en pantalla ordinaria.

El [CView:: OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) función se llama cuando se invoca al modo de vista previa, igual que al principio de un trabajo de impresión. El [CPrintInfo (estructura)](../mfc/reference/cprintinfo-structure.md) estructura pasada a la función contiene varios miembros cuyos valores se pueden establecer para ajustar ciertas características de la operación de vista previa de impresión. Por ejemplo, puede establecer el *m_nNumPreviewPages* miembro para especificar si desea obtener una vista previa del documento en modo de uno o dos páginas.

##  <a name="_core_modifying_print_preview"></a> Modificar la vista previa de impresión

Puede modificar el comportamiento y apariencia de la vista previa de impresión de varias maneras con bastante facilidad. Por ejemplo, puede, entre otras cosas:

- Hace que la ventana de vista previa de impresión mostrar una barra de desplazamiento para facilitar el acceso a cualquier página del documento.

- Hacer que la vista preliminar para mantener la posición del usuario en el documento comenzando la presentación en la página actual.

- Provocar una inicialización distinta a realizarse para la impresión y vista previa de impresión.

- Hacer que la vista preliminar para mostrar los números de página en sus propios formatos.

Si sabe cuánto tiempo es el documento y llamar a `SetMaxPage` con el valor adecuado, el marco de trabajo puede usar esta información en modo de vista previa, así como durante la impresión. Una vez que el marco de trabajo conoce la longitud del documento, puede proporcionar la ventana Vista previa con una barra de desplazamiento, que permite al usuario desplazarse hacia delante y hacia atrás por el documento en modo de vista previa. Si no ha establecido la longitud del documento, el marco de trabajo no puede colocar el cuadro de desplazamiento para indicar la posición actual, por lo que el marco de trabajo no agrega una barra de desplazamiento. En este caso, el usuario debe usar los botones de página anterior y siguiente página en la barra de control de la ventana de vista previa a la página a través del documento.

Para la vista previa de impresión, le resultará útil para asignar un valor para el *m_nCurPage* miembro de `CPrintInfo`, aunque nunca lo haría para la impresión normal. Durante la impresión normal, este miembro transporta información desde el marco de trabajo a la clase de vista. Se trata cómo el marco de trabajo indica a la vista a qué página debe imprimirse.

Por el contrario, cuando se inicia el modo de vista previa de impresión, el *m_nCurPage* miembro transporta información en la dirección opuesta: desde la vista para el marco de trabajo. El marco de trabajo usa el valor de este miembro para determinar qué página se debe mostrar en primer lugar. El valor predeterminado de este miembro es 1, por lo que se muestra inicialmente la primera página del documento. Puede invalidar `OnPreparePrinting` para establecer este miembro en el número de página que aparece en el momento en que se invocó el comando Vista previa de impresión. De este modo, la aplicación mantiene la posición del usuario actual al pasar de modo de presentación normal a modo de vista previa de impresión.

En ocasiones, es posible que desee `OnPreparePrinting` para realizar la inicialización diferente dependiendo de si se llama para un trabajo de impresión o de vista previa de impresión. Puede determinar examinando el *m_bPreview* variable miembro en el `CPrintInfo` estructura. Este miembro está establecido en **TRUE** cuando se invoca la vista previa de impresión.

El `CPrintInfo` estructura también contiene un miembro denominado *m_strPageDesc*, que se usa para dar formato a las cadenas que se muestran en la parte inferior de la pantalla en los modos de página única y varias páginas. De forma predeterminada, estas cadenas son la forma "página *n*" y "páginas *n* - *m*," pero se puede modificar *m_strPageDesc* desde dentro de `OnPreparePrinting` y establecer las cadenas en algo más elaborados. Consulte [CPrintInfo (estructura)](../mfc/reference/cprintinfo-structure.md) en el *referencia de MFC* para obtener más información.

## <a name="see-also"></a>Vea también

[Impresión y vista previa de impresión](../mfc/printing-and-print-preview.md)<br/>
[Impresión](../mfc/printing.md)<br/>
[CView (clase)](../mfc/reference/cview-class.md)<br/>
[CDC (clase)](../mfc/reference/cdc-class.md)
