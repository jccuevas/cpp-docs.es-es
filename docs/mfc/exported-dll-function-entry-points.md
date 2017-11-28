---
title: "Puntos de entrada de función DLL exportados | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exporting DLLs [MFC], functions
- MFC, managing state data
- state management [MFC], exported DLLs
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8959c30a5c1b65687d51e127781b82cccf0cce5c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="exported-dll-function-entry-points"></a>Puntos de entrada de funciones exportadas de un archivo DLL
Para las funciones exportadas de un archivo DLL, utilice la [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) macro para mantener el estado global adecuado al cambiar del módulo DLL al archivo DLL de la aplicación que realiza la llamada.  
  
 Cuando se llama, esta macro establece `pModuleState`, un puntero a un `AFX_MODULE_STATE` estructura que contiene datos globales del módulo, como el estado efectivo del módulo para el resto del ámbito contenedor de la función. Al salir del ámbito que contiene la macro, se restaura automáticamente el estado efectivo del módulo anterior.  
  
 Este cambio se logra mediante la creación de una instancia de un **AFX_MODULE_STATE** clase en la pila. En su constructor, esta clase obtiene un puntero al estado actual del módulo y lo almacena en una variable de miembro y, a continuación, establece `pModuleState` como el nuevo estado efectivo del módulo. En su destructor, esta clase restaura el puntero almacenado en su variable miembro como estado efectivo del módulo.  
  
 Si tiene una función exportada, como uno que se abre un cuadro de diálogo en el archivo DLL, debe agregar el código siguiente al principio de la función:  
  
 [!code-cpp[NVC_MFCConnectionPoints#6](../mfc/codesnippet/cpp/exported-dll-function-entry-points_1.cpp)]  
  
 Con ello intercambia el estado actual del módulo con el estado devuelto desde [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) hasta el final del ámbito actual.  
  
 Problemas con los recursos en archivos DLL se producen si la `AFX_MANAGE_STATE` no se utiliza la macro. De forma predeterminada, MFC usa el identificador de recurso de la aplicación principal para cargar la plantilla de recursos. Esta plantilla se almacena realmente en el archivo DLL. La causa es que la información de estado de módulo de MFC no se ha cambiado, por el `AFX_MANAGE_STATE` macro. El identificador de recurso se recupera del estado del módulo de MFC. Si no se cambia el estado del módulo hace que el identificador de recursos incorrecto para usarse.  
  
 `AFX_MANAGE_STATE`no es necesario para ponerla en cada función del archivo DLL. Por ejemplo, `InitInstance` puede llamarse mediante el código MFC de la aplicación sin `AFX_MANAGE_STATE` porque MFC cambia automáticamente el estado del módulo antes de `InitInstance` y, a continuación, los conmutadores de nuevo después de `InitInstance` devuelve. Lo mismo puede decirse de todos los controladores de mapa de mensajes. Archivos DLL de MFC estándar tiene en realidad un procedimiento de ventana maestro que cambia automáticamente el estado del módulo antes de enrutar cualquier mensaje.  
  
## <a name="see-also"></a>Vea también  
 [Administración de los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)
