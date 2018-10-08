---
title: Tipos asociados a objetos de interfaz de usuario de mensajes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.uiobject.msgs
dev_langs:
- C++
helpviewer_keywords:
- message types and user interface objects [MFC]
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd89f19547eef8ade9d23a6176ea74cb49586857
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860295"
---
# <a name="message-types-associated-with-user-interface-objects"></a>Tipos de mensajes asociados a objetos de la interfaz de usuario

En la tabla siguiente se muestra los tipos de objetos con las que trabaja y los tipos de mensajes asociados con ellos.

### <a name="user-interface-objects-and-associated-messages"></a>Objetos de la interfaz de usuario y los mensajes asociados

|Id. de objeto|Mensajes|
|---------------|--------------|
|Nombre de clase, que representa la ventana contenedora|Mensajes de Windows apropiados para una [CWnd](../../mfc/reference/cwnd-class.md)-clase derivada: un cuadro de diálogo, ventanas, ventana secundaria, ventana secundaria MDI o marco de nivel superior.|
|Identificador de menú o tecla aceleradora|-Mensaje de comando (ejecuta la función del programa).<br />-Mensaje UPDATE_COMMAND_UI (actualiza dinámicamente el elemento de menú).|
|Identificador de control|Controlar mensajes de notificación para el tipo de control seleccionado.|

## <a name="see-also"></a>Vea también

[Asignación de mensajes a funciones](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Reemplazar una función Virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navegar por la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)
