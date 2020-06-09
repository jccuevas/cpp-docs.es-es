---
title: Cuadros de diálogo
ms.date: 11/04/2016
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
ms.openlocfilehash: da6a2eca7c2366e519b9bf2e809b042dc3ee2e50
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616867"
---
# <a name="dialog-boxes"></a>Cuadros de diálogo

Las aplicaciones para Windows se comunican con frecuencia con el usuario a través de cuadros de diálogo. La clase [CDialog](reference/cdialog-class.md) proporciona una interfaz para administrar cuadros de diálogo, el editor de cuadros de diálogo Visual C++ facilita el diseño de cuadros de diálogo y la creación de sus recursos de plantilla de cuadro de diálogo, y los asistentes para código simplifican el proceso de inicialización y validación de los controles en un cuadro de diálogo y de la recopilación de los valores especificados por el usuario.

Los cuadros de diálogo contienen controles, entre los que se incluyen:

- Controles comunes de Windows, como cuadros de edición, botones de control, cuadros de lista, cuadros combinados, controles de árbol, controles de lista e indicadores de progreso.

- Controles ActiveX.

- Controles dibujados por el propietario: controles que es responsable de dibujar en el cuadro de diálogo.

La mayoría de los cuadros de diálogo son modales, que requieren que el usuario cierre el cuadro de diálogo antes de usar cualquier otra parte del programa. Pero es posible crear cuadros de diálogo no modales, que permiten a los usuarios trabajar con otras ventanas mientras el cuadro de diálogo está abierto. MFC admite ambos tipos de cuadro de diálogo con la clase `CDialog` . Los controles se organizan y se administran mediante un recurso de plantilla de cuadro de diálogo, creado con el [Editor de cuadros de diálogo](../windows/dialog-editor.md).

Las [hojas de propiedades](property-sheets-mfc.md), también conocidas como cuadros de diálogo de pestaña, son cuadros de diálogo que contienen "páginas" de controles de cuadro de diálogo distintos. Cada página tiene una carpeta de archivos "pestaña" en la parte superior. Al hacer clic en una pestaña, la página se coloca en la parte frontal del cuadro de diálogo.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Ejemplo: Mostrar un cuadro de diálogo a través de un comando de menú](example-displaying-a-dialog-box-via-a-menu-command.md)

- [Componentes del cuadro de diálogo en el marco de trabajo](dialog-box-components-in-the-framework.md)

- [Cuadros de diálogo modales y no modales](modal-and-modeless-dialog-boxes.md)

- [Hojas de propiedades y páginas de propiedades](property-sheets-and-property-pages-mfc.md) en un cuadro de diálogo

- [Crear el recurso de cuadro de diálogo](creating-the-dialog-resource.md)

- [Crear una clase de cuadro de diálogo con los asistentes para código](creating-a-dialog-class-with-code-wizards.md)

- [Trabajar con cuadros de diálogo en MFC](life-cycle-of-a-dialog-box.md)

- [Intercambio de datos de cuadros de diálogo (DDX) y validación (DDV)](dialog-data-exchange-and-validation.md)

- [Acceso con seguridad de tipos a los controles de un cuadro de diálogo](type-safe-access-to-controls-in-a-dialog-box.md)

- [Asignación de mensajes de Windows a la clase](mapping-windows-messages-to-your-class.md)

- [Funciones miembro que se reemplazan con frecuencia](commonly-overridden-member-functions.md)

- [Funciones miembro que se agregan con frecuencia](commonly-added-member-functions.md)

- [Clases de cuadro de diálogo comunes](common-dialog-classes.md)

- [Cuadros de diálogo en OLE](dialog-boxes-in-ole.md)

- Crear una aplicación cuya interfaz de usuario sea un cuadro de diálogo: vea los programas de ejemplo [CMNCTRL1](../overview/visual-cpp-samples.md) o [CMNCTRL2](../overview/visual-cpp-samples.md) . El Asistente para aplicaciones también proporciona esta opción.

- [Muestras](dialog-sample-list.md)

## <a name="see-also"></a>Consulte también

[Elementos de la interfaz de usuario](user-interface-elements-mfc.md)
