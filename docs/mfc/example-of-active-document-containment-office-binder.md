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
ms.openlocfilehash: fe9ccb5b78d9a60c5b8b2a19fe0818a8e1682f00
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623127"
---
# <a name="example-of-active-document-containment-office-binder"></a>Ejemplo de contención de documentos activos: Cuaderno de Office

El enlazador Microsoft Office es un ejemplo de un contenedor de documentos activo. Un enlazador de Office incluye dos paneles principales, como los contenedores normalmente. El panel izquierdo contiene iconos que corresponden a los documentos activos del enlazador. Cada documento se denomina *sección* dentro del enlazador. Por ejemplo, un enlazador puede contener documentos de Word, archivos de PowerPoint, hojas de cálculo de Excel, etc.

Al hacer clic en un icono del panel izquierdo, se activa el documento activo correspondiente. A continuación, el panel derecho del enlazador muestra el contenido del documento activo seleccionado actualmente.

Si abre y activa un documento de Word en un enlazador, la barra de menús y las barras de herramientas de Word aparecen en la parte superior del marco de la vista, y puede modificar el contenido del documento mediante cualquier comando o herramienta de Word. Sin embargo, la barra de menús es una combinación de las barras de menús del cuaderno y de la palabra. Dado que tanto el enlazador como Word tienen menús de **ayuda** , se combina el contenido de los menús respectivos. Los contenedores de documentos activos como el enlazador de Office proporcionan automáticamente la combinación de menús de **ayuda** ; para obtener más información, vea [combinación del menú Ayuda](help-menu-merging.md).

Al seleccionar un documento activo de otro tipo de aplicación, la interfaz del enlazador cambia para adaptarse al tipo de aplicación del documento activo. Por ejemplo, si un enlazador contiene una hoja de cálculo de Excel, observará que los menús del enlazador cambian al seleccionar la sección hoja de cálculo de Excel.

Por supuesto, hay otros tipos posibles de contenedores junto a los enlazadores. El explorador de archivos usa la interfaz típica de dos paneles en la que el panel izquierdo usa un control de árbol para mostrar una lista jerárquica de directorios de una unidad o red, mientras que el panel derecho muestra los archivos contenidos en el directorio seleccionado actualmente. Un explorador de Internet: tipo de contenedor (por ejemplo, Microsoft Internet Explorer), en lugar de usar una interfaz de dos paneles, normalmente tiene un único fotograma y permite la navegación mediante hipervínculos.

## <a name="see-also"></a>Consulte también

[Contención de documentos activos](active-document-containment.md)
