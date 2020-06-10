---
title: Puntos de entrada de funciones exportadas de un archivo DLL
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [MFC], functions
- MFC, managing state data
- state management [MFC], exported DLLs
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
ms.openlocfilehash: c521cad666864c728fd871b460cf0c92b815e414
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622640"
---
# <a name="exported-dll-function-entry-points"></a>Puntos de entrada de funciones exportadas de un archivo DLL

En el caso de las funciones exportadas de un archivo DLL, utilice la macro [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) para mantener el estado global adecuado al cambiar del módulo DLL a la dll de la aplicación que realiza la llamada.

Cuando se llama, esta macro establece `pModuleState` un puntero a una `AFX_MODULE_STATE` estructura que contiene los datos globales del módulo, como el estado del módulo efectivo para el resto del ámbito contenedor de la función. Cuando se sale del ámbito que contiene la macro, el estado anterior del módulo efectivo se restaura automáticamente.

Este cambio se logra mediante la creación de una instancia de una `AFX_MODULE_STATE` clase en la pila. En su constructor, esta clase obtiene un puntero al estado actual del módulo y lo almacena en una variable miembro y, a continuación, establece `pModuleState` como el nuevo estado de módulo efectivo. En su Destructor, esta clase restaura el puntero almacenado en su variable miembro como el estado del módulo efectivo.

Si tiene una función exportada, como una que inicia un cuadro de diálogo en el archivo DLL, debe agregar el código siguiente al principio de la función:

[!code-cpp[NVC_MFCConnectionPoints#6](codesnippet/cpp/exported-dll-function-entry-points_1.cpp)]

Esto intercambia el estado actual del módulo con el estado devuelto desde [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) hasta el final del ámbito actual.

Los problemas con los recursos de los archivos DLL se producirán si `AFX_MANAGE_STATE` no se usa la macro. De forma predeterminada, MFC usa el identificador de recursos de la aplicación principal para cargar la plantilla de recursos. En realidad, esta plantilla se almacena en el archivo DLL. La causa principal es que la macro no ha cambiado la información de estado del módulo de MFC `AFX_MANAGE_STATE` . El identificador de recursos se recupera del estado del módulo de MFC. Si no se cambia el estado del módulo, se utiliza el identificador de recursos equivocado.

`AFX_MANAGE_STATE`no tiene que colocarse en todas las funciones del archivo DLL. Por ejemplo, `InitInstance` el código MFC de la aplicación puede llamar a este método sin `AFX_MANAGE_STATE` porque MFC desplaza automáticamente el estado del módulo antes `InitInstance` y, a continuación, lo vuelve a cambiar después de la `InitInstance` devolución. Lo mismo se aplica a todos los controladores de mapa de mensajes. Los archivos dll de MFC normales tienen realmente un procedimiento de ventana principal especial que cambia automáticamente el estado del módulo antes de enrutar cualquier mensaje.

## <a name="see-also"></a>Consulte también

[Administrar los datos de estado de los módulos MFC](managing-the-state-data-of-mfc-modules.md)
