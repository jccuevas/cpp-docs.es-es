---
title: The CCmdUI (Clase)
ms.date: 11/04/2016
f1_keywords:
- CCmdUI
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
ms.openlocfilehash: 8e0af0703924d6fae626d3753b8523efe0c56652
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326637"
---
# <a name="the-ccmdui-class"></a>The CCmdUI (Clase)

Cuando enruta un comando de actualización a su controlador, el marco de trabajo pasa al controlador de un puntero a un `CCmdUI` objeto (o a un objeto de un `CCmdUI`-clase derivada). Este objeto representa el botón de barra de herramientas o elemento de menú u otro objeto de interfaz de usuario que genera el comando. El controlador de actualización llama a funciones de miembro el `CCmdUI` estructura a través del puntero para actualizar el objeto de interfaz de usuario. Por ejemplo, aquí es un controlador de actualización para el elemento de menú Borrar todo:

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

Llama este controlador de la `Enable` función miembro de un objeto con acceso al elemento de menú. `Enable` Convierte el elemento disponibles para su uso.

## <a name="see-also"></a>Vea también

[Cómo: Actualizar los objetos de interfaz de usuario](../mfc/how-to-update-user-interface-objects.md)
