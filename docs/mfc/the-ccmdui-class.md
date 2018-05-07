---
title: CCmdUI (clase) | Documentos de Microsoft
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
ms.openlocfilehash: dde8c31620f64e6201c59b7031c789caa16c4902
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="the-ccmdui-class"></a>The CCmdUI (Clase)
Cuando enruta un comando de actualización a su controlador, el marco de trabajo pasa al controlador de un puntero a un `CCmdUI` objeto (o a un objeto de un `CCmdUI`-clase derivada). Este objeto representa el botón de barra de herramientas o elemento de menú u otro objeto de interfaz de usuario que genera el comando. El controlador de actualización llama a funciones de miembro la `CCmdUI` estructura a través del puntero para actualizar el objeto de interfaz de usuario. Por ejemplo, aquí es un controlador de actualización para el elemento de menú Borrar todo:  
  
 [!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]  
  
 Llama a este controlador de la **habilitar** función miembro de un objeto con acceso al elemento de menú. **Habilitar** hace que el elemento estén disponibles para su uso.  
  
## <a name="see-also"></a>Vea también  
 [Procedimiento para actualizar objetos de la interfaz de usuario](../mfc/how-to-update-user-interface-objects.md)

