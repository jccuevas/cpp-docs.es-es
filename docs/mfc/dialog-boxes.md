---
title: Cuadros de diálogo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f26f5cad47815c25602eba836a482e6f6cecc85d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424942"
---
# <a name="dialog-boxes"></a>Cuadros de diálogo

Con frecuencia, las aplicaciones para Windows comunican con el usuario a través de cuadros de diálogo. Clase [CDialog](../mfc/reference/cdialog-class.md) proporciona una interfaz para administrar los cuadros de diálogo, el editor de cuadro de diálogo de Visual C++ facilita la tarea diseñar los cuadros de diálogo y crear sus recursos de plantilla de cuadro de diálogo y asistentes para código simplifican el proceso de inicialización y validación de los controles en un cuadro de diálogo y de recopilación de los valores especificados por el usuario.

Cuadros de diálogo contienen controles, incluidos:

- Controles comunes de Windows, como edición cuadros, botones de comando, cuadros de lista, cuadros combinados, los controles de árbol, los controles de lista e indicadores de progreso.

- Controles ActiveX.

- Controles dibujados por el propietario: controles que usted es responsable de dibujar en el cuadro de diálogo.

La mayoría de los cuadros de diálogo son modales, que requieren que el usuario cerrar el cuadro de diálogo antes de usar cualquier otra parte del programa. Pero es posible crear cuadros de diálogo no modal, que permiten a los usuarios trabajar con otras ventanas mientras está abierto el cuadro de diálogo. MFC es compatible con ambos tipos de cuadro de diálogo con la clase `CDialog`. Los controles se organizan y administran mediante un recurso de plantilla de cuadro de diálogo, creado con la [editor de cuadro de diálogo](../windows/dialog-editor.md).

[Hojas de propiedades](../mfc/property-sheets-mfc.md), también conocido como cuadros de diálogo de pestaña, son cuadros de diálogo que contienen "páginas" de los controles de cuadro de diálogo distintos. Cada página tiene una carpeta de archivos "tab" en la parte superior. Al hacer clic en una ficha, esa página se coloca al principio del cuadro de diálogo.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Ejemplo: Mostrar un cuadro de diálogo a través de un comando de menú](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)

- [Componentes de cuadro de diálogo en el marco de trabajo](../mfc/dialog-box-components-in-the-framework.md)

- [Cuadros de diálogo modales y no modales](../mfc/modal-and-modeless-dialog-boxes.md)

- [Hojas de propiedades y páginas de propiedades](../mfc/property-sheets-and-property-pages-mfc.md) en un cuadro de diálogo

- [Crear el recurso de cuadro de diálogo](../mfc/creating-the-dialog-resource.md)

- [Crear una clase de cuadro de diálogo con los asistentes para código](../mfc/creating-a-dialog-class-with-code-wizards.md)

- [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)

- [Intercambio de datos de cuadro de diálogo (DDX) y la validación (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [Acceso de seguridad de tipos a los controles en un cuadro de diálogo](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [Asignación de mensajes de Windows a la clase](../mfc/mapping-windows-messages-to-your-class.md)

- [Funciones miembro que se reemplazan con frecuencia](../mfc/commonly-overridden-member-functions.md)

- [Funciones miembro que se agregan con frecuencia](../mfc/commonly-added-member-functions.md)

- [Clases de cuadro de diálogo comunes](../mfc/common-dialog-classes.md)

- [Cuadros de diálogo en OLE](../mfc/dialog-boxes-in-ole.md)

- Crear una aplicación cuya interfaz de usuario es un cuadro de diálogo: vea la [CMNCTRL1](../visual-cpp-samples.md) o [CMNCTRL2](../visual-cpp-samples.md) programas de ejemplo. El Asistente para aplicaciones proporciona esta opción también.

- [Ejemplos](../mfc/dialog-sample-list.md)

## <a name="see-also"></a>Vea también

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)
