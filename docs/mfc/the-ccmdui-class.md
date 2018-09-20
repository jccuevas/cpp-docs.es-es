---
title: CCmdUI (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CCmdUI
dev_langs:
- C++
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18b5675aff2d10f224238a1ba6d3b919e1b285a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374587"
---
# <a name="the-ccmdui-class"></a>The CCmdUI (Clase)

Cuando enruta un comando de actualización a su controlador, el marco de trabajo pasa al controlador de un puntero a un `CCmdUI` objeto (o a un objeto de un `CCmdUI`-clase derivada). Este objeto representa el botón de barra de herramientas o elemento de menú u otro objeto de interfaz de usuario que genera el comando. El controlador de actualización llama a funciones de miembro el `CCmdUI` estructura a través del puntero para actualizar el objeto de interfaz de usuario. Por ejemplo, aquí es un controlador de actualización para el elemento de menú Borrar todo:

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

Llama este controlador de la `Enable` función miembro de un objeto con acceso al elemento de menú. `Enable` Convierte el elemento disponibles para su uso.

## <a name="see-also"></a>Vea también

[Procedimiento para actualizar objetos de la interfaz de usuario](../mfc/how-to-update-user-interface-objects.md)

