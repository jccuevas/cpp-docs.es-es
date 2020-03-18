---
title: The CCmdUI (Clase)
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
ms.openlocfilehash: 105aa7ad6c5cc6a5563dbde8145327a2b3d066a1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447142"
---
# <a name="the-ccmdui-class"></a>The CCmdUI (Clase)

Cuando enruta un comando de actualización a su controlador, el marco de trabajo pasa al controlador un puntero a un `CCmdUI` objeto (o a un objeto de una clase derivada de `CCmdUI`). Este objeto representa el elemento de menú o el botón de la barra de herramientas u otro objeto de la interfaz de usuario que generó el comando. El controlador de actualización llama a las funciones miembro de la estructura `CCmdUI` a través del puntero para actualizar el objeto de interfaz de usuario. Por ejemplo, este es un controlador de actualización para el elemento de menú borrar todo:

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

Este controlador llama a la función miembro `Enable` de un objeto con acceso al elemento de menú. `Enable` hace que el elemento esté disponible para su uso.

## <a name="see-also"></a>Consulte también

[Procedimiento para actualizar objetos de la interfaz de usuario](../mfc/how-to-update-user-interface-objects.md)
