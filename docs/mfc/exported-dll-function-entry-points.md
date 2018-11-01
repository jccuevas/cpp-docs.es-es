---
title: Puntos de entrada de funciones exportadas de un archivo DLL
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [MFC], functions
- MFC, managing state data
- state management [MFC], exported DLLs
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
ms.openlocfilehash: 8b84209833fee42ec8ebdd1fdea7a9229decad9d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463331"
---
# <a name="exported-dll-function-entry-points"></a>Puntos de entrada de funciones exportadas de un archivo DLL

Para las funciones exportadas de un archivo DLL, utilice el [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) macro para mantener el estado global adecuado al cambiar del módulo DLL al archivo DLL de la aplicación que realiza la llamada.

Cuando se llama, esta macro establece `pModuleState`, un puntero a un `AFX_MODULE_STATE` estructura que contiene los datos globales del módulo, como el estado efectivo del módulo para el resto del ámbito de la función contenedora. Al salir del ámbito que contiene la macro, el estado efectivo del módulo anterior se restaura automáticamente.

Este cambio se logra mediante la creación de una instancia de un `AFX_MODULE_STATE` clase en la pila. En su constructor, esta clase obtiene un puntero al estado actual del módulo y lo almacena en una variable de miembro y, a continuación, establece `pModuleState` como el nuevo estado efectivo del módulo. En su destructor, esta clase restaura el puntero almacenado en su variable de miembro como el estado efectivo del módulo.

Si tiene una función exportada, como el que se abre un cuadro de diálogo en el archivo DLL, deberá agregar el código siguiente al principio de la función:

[!code-cpp[NVC_MFCConnectionPoints#6](../mfc/codesnippet/cpp/exported-dll-function-entry-points_1.cpp)]

Esto cambia el estado actual del módulo con el estado devuelto desde [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) hasta el final del ámbito actual.

Problemas con los recursos en archivos DLL se producirán si la `AFX_MANAGE_STATE` macro no se usa. De forma predeterminada, MFC utiliza el identificador de recurso de la aplicación principal para cargar la plantilla de recursos. Esta plantilla se almacena realmente en el archivo DLL. La causa es que no ha cambiado la información de estado del módulo de MFC mediante el `AFX_MANAGE_STATE` macro. El identificador de recurso se recuperó de estado del módulo de MFC. Si no se cambia el estado del módulo hace que el identificador de recurso incorrecto que se usará.

`AFX_MANAGE_STATE` no es necesario que se colocará en todas las funciones en el archivo DLL. Por ejemplo, `InitInstance` pueden llamarse mediante el código de MFC en la aplicación sin `AFX_MANAGE_STATE` porque MFC cambia automáticamente el estado del módulo antes de `InitInstance` y, a continuación, vuelve a cambiar el lo después `InitInstance` devuelve. Lo mismo puede decirse de todos los controladores de mapa de mensajes. Archivos DLL de MFC estándar tiene realmente un procedimiento de ventana maestro que cambia automáticamente el estado del módulo antes de enrutar cualquier mensaje.

## <a name="see-also"></a>Vea también

[Administración de los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

