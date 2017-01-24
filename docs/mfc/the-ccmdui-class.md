---
title: "The CCmdUI (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CCmdUI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCmdUI (clase), actualización del menú"
  - "barras de herramientas [C++], actualizar"
  - "controladores de actualización"
  - "actualizar objetos de la interfaz de usuario"
  - "objetos de interfaz de usuario, actualizar"
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# The CCmdUI (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando distribuye un comando de actualización al controlador, el marco de trabajo pasa al controlador un puntero a un objeto de `CCmdUI` \(o a un objeto de `CCmdUI`\- clase derivada\).  Este objeto representa el elemento de menú o en el botón de la barra de herramientas u otro objeto de la interfaz de usuario que generó el comando.  El controlador de actualización llama a las funciones miembro de la estructura de `CCmdUI` a través del puntero para actualizar el objeto de la interfaz de usuario.  Por ejemplo, aquí tiene un controlador de actualización para el elemento de menú claro Todo:  
  
 [!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/CPP/the-ccmdui-class_1.cpp)]  
  
 Este controlador llama a la función miembro de **Habilitar** de un objeto con acceso al elemento de menú.  **Habilitar** hace que el elemento disponibles para su uso.  
  
## Vea también  
 [Cómo: Actualizar objetos de la interfaz de usuario](../mfc/how-to-update-user-interface-objects.md)