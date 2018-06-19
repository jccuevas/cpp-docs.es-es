---
title: 'Ejemplo de contención de documentos activos: Cuaderno de Office | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- examples [MFC], active document containment
- containers [MFC], active document
- active document containers [MFC], examples
- Office Binder [MFC]
- MFC COM, active document containment
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7e4f82840a4c5620762ad57b5b9fa8dd7e62d0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345966"
---
# <a name="example-of-active-document-containment-office-binder"></a>Ejemplo de contención de documentos activos: Cuaderno de Office
Cuaderno de Microsoft Office es un ejemplo de un contenedor de documento activo. Un cuaderno de Office incluye dos paneles principales, como contenedores normalmente lo hacen. El panel izquierdo contiene iconos que corresponden a documentos activos en el enlazador. Cada documento se denomina un *sección* en el enlazador. Por ejemplo, puede contener un enlazador de documentos de Word, archivos de PowerPoint, hojas de cálculo de Excel y así sucesivamente.  
  
 Al hacer clic en el panel izquierdo, activa el documento activo correspondiente. El panel derecho del enlazador, a continuación, muestra el contenido del documento activo actualmente seleccionado.  
  
 Si se abre y activa un documento de Word en un enlazador, la barra de menús de Word y las barras de herramientas aparecen en la parte superior del marco de la vista y se puede editar el contenido del documento con cualquier comando de Word o la herramienta. Sin embargo, la barra de menús es una combinación de las barras de menús del cuaderno y de Word. Porque cuaderno y Word tienen **ayuda** se combinan los menús, el contenido de los menús respectivos. Contenedores de documentos activos como cuaderno de Office proporcionan automáticamente **ayuda** menú Combinar; para obtener más información, consulte [combinar el menú Ayuda](../mfc/help-menu-merging.md).  
  
 Cuando se selecciona un documento activo de otro tipo de aplicación, los cambios en la interfaz del enlazador para dar cabida a del tipo de aplicación del documento activo. Por ejemplo, si un cuaderno contiene una hoja de cálculo de Excel, observará que los menús del cuaderno cambian cuando se selecciona la sección de la hoja de cálculo de Excel.  
  
 Por supuesto, hay otros posibles tipos de contenedores además de enlazadores. Explorador de archivos utiliza la interfaz de dos paneles típica en el que el panel izquierdo utiliza un control de árbol para mostrar una lista jerárquica de directorios en una unidad o red, mientras que el panel derecho muestra los archivos contenidos en el directorio seleccionado actualmente. Un tipo de explorador Internet de contenedor (por ejemplo, Microsoft Internet Explorer), en lugar de utilizar una interfaz de dos paneles, normalmente tiene un solo fotograma y permite la navegación mediante hipervínculos.  
  
## <a name="see-also"></a>Vea también  
 [Contención de documentos activos](../mfc/active-document-containment.md)

