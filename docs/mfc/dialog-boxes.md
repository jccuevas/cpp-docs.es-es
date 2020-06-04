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
ms.openlocfilehash: 18b4c4d1386716a0a3282b88d6fdf5a701abce08
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685794"
---
# <a name="dialog-boxes"></a>Cuadros de diálogo

Las aplicaciones para Windows se comunican con frecuencia con el usuario a través de cuadros de diálogo. La clase [CDialog](../mfc/reference/cdialog-class.md) proporciona una interfaz para administrar los cuadros de diálogo C++ . el editor de cuadros de diálogo visual facilita el diseño de cuadros de diálogo y la creación de sus recursos de plantilla de cuadro de diálogo, y los asistentes de código simplifican el proceso de inicialización y validación del los controles de un cuadro de diálogo y de la recopilación de los valores especificados por el usuario.

Los cuadros de diálogo contienen controles, entre los que se incluyen:

- Controles comunes de Windows, como cuadros de edición, botones de control, cuadros de lista, cuadros combinados, controles de árbol, controles de lista e indicadores de progreso.

- Controles ActiveX.

- Controles dibujados por el propietario: controles que es responsable de dibujar en el cuadro de diálogo.

La mayoría de los cuadros de diálogo son modales, que requieren que el usuario cierre el cuadro de diálogo antes de usar cualquier otra parte del programa. Pero es posible crear cuadros de diálogo no modales, que permiten a los usuarios trabajar con otras ventanas mientras el cuadro de diálogo está abierto. MFC admite ambos tipos de cuadro de diálogo con la clase `CDialog`. Los controles se organizan y se administran mediante un recurso de plantilla de cuadro de diálogo, creado con el [Editor de cuadros de diálogo](../windows/dialog-editor.md).

Las [hojas de propiedades](../mfc/property-sheets-mfc.md), también conocidas como cuadros de diálogo de pestaña, son cuadros de diálogo que contienen "páginas" de controles de cuadro de diálogo distintos. Cada página tiene una carpeta de archivos "pestaña" en la parte superior. Al hacer clic en una pestaña, la página se coloca en la parte frontal del cuadro de diálogo.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Ejemplo: mostrar un cuadro de diálogo mediante un comando de menú](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)

- [Componentes del cuadro de diálogo en el marco de trabajo](../mfc/dialog-box-components-in-the-framework.md)

- [Cuadros de diálogo modales y no modales](../mfc/modal-and-modeless-dialog-boxes.md)

- [Hojas de propiedades y páginas de propiedades](../mfc/property-sheets-and-property-pages-mfc.md) en un cuadro de diálogo

- [Crear el recurso de cuadro de diálogo](../mfc/creating-the-dialog-resource.md)

- [Crear una clase de cuadro de diálogo con los asistentes para código](../mfc/creating-a-dialog-class-with-code-wizards.md)

- [Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)

- [Intercambio de datos de cuadros de diálogo (DDX) y validación (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [Acceso con seguridad de tipos a los controles de un cuadro de diálogo](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [Asignación de mensajes de Windows a la clase](../mfc/mapping-windows-messages-to-your-class.md)

- [Funciones miembro que se reemplazan con frecuencia](../mfc/commonly-overridden-member-functions.md)

- [Funciones miembro que se agregan con frecuencia](../mfc/commonly-added-member-functions.md)

- [Clases de cuadro de diálogo comunes](../mfc/common-dialog-classes.md)

- [Cuadros de diálogo en OLE](../mfc/dialog-boxes-in-ole.md)

- Crear una aplicación cuya interfaz de usuario sea un cuadro de diálogo: vea los programas de ejemplo [CMNCTRL1](../overview/visual-cpp-samples.md) o [CMNCTRL2](../overview/visual-cpp-samples.md) . El Asistente para aplicaciones también proporciona esta opción.

- [Muestras](../mfc/dialog-sample-list.md)

## <a name="see-also"></a>Vea también

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)
