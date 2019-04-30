---
title: 'Ejemplo de contención de documentos activos: Cuaderno de Office'
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- examples [MFC], active document containment
- containers [MFC], active document
- active document containers [MFC], examples
- Office Binder [MFC]
- MFC COM, active document containment
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
ms.openlocfilehash: b06bc0f22ee71c8afbbc8feadca68895fc24a50b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358869"
---
# <a name="example-of-active-document-containment-office-binder"></a>Ejemplo de contención de documentos activos: Cuaderno de Office

El cuaderno de Office de Microsoft es un ejemplo de un contenedor de documentos activos. Un cuaderno de Office incluye dos paneles principales, como haría normalmente los contenedores. El panel izquierdo contiene iconos que corresponden a los documentos activos en el cuaderno. Se llama a cada documento un *sección* dentro del cuaderno. Por ejemplo, un cuaderno puede contener archivos de PowerPoint, documentos de Word, hojas de cálculo de Excel y así sucesivamente.

Al hacer clic en el panel izquierdo, activa el documento activo correspondiente. El panel derecho del enlazador, a continuación, muestra el contenido del documento activo actualmente seleccionado.

Si abre y activar un documento de Word en un cuaderno, la barra de menús de Word y barras de herramientas aparecen en la parte superior del marco de vista, y puede editar el contenido del documento mediante cualquier comando de Word o la herramienta. Sin embargo, la barra de menús es una combinación de las barras de menús del cuaderno y de Word. Porque el cuaderno y Word tienen **ayuda** se combinan los menús, el contenido de los menús correspondientes. Contenedores de documentos activos como el cuaderno de Office proporcionan automáticamente **ayuda** menú combinación; para obtener más información, consulte [ayudan a la combinación de menús](../mfc/help-menu-merging.md).

Cuando selecciona un documento activo de otro tipo de aplicación, los cambios en la interfaz del enlazador para dar cabida a la del tipo de aplicación del documento activo. Por ejemplo, si un cuaderno contiene una hoja de cálculo de Excel, observará que los menús del cuaderno cambian cuando se selecciona la sección de la hoja de cálculo de Excel.

Por supuesto, hay otros tipos de contenedores, además de los cuadernos. Explorador de archivos utiliza la interfaz de dos paneles típica en el que el panel izquierdo utiliza un control de árbol para mostrar una lista jerárquica de los directorios en una unidad o la red, mientras que el panel derecho muestra los archivos contenidos en el directorio seleccionado actualmente. Un tipo de explorador de Internet de contenedor (por ejemplo, Microsoft Internet Explorer), en lugar de utilizar una interfaz dual panel, normalmente tiene un solo fotograma y proporciona navegación mediante hipervínculos.

## <a name="see-also"></a>Vea también

[Contención de documentos activos](../mfc/active-document-containment.md)
