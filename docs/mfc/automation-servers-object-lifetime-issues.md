---
title: 'Servidores de automatización: Problemas de duración de objetos'
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
ms.openlocfilehash: f9dbc6e4f321ba10fdffa013c158d53b84331e30
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392900"
---
# <a name="automation-servers-object-lifetime-issues"></a>Servidores de automatización: Problemas de duración de objetos

Cuando un cliente de automatización se crea o activa un elemento OLE, el servidor pasa al cliente un puntero a ese objeto. El cliente establece una referencia al objeto mediante una llamada a la función OLE [IUnknown:: AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref). Esta referencia está en vigor hasta que el cliente llama a [IUnknown:: Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release). (Las aplicaciones cliente escritas con clases de la biblioteca Microsoft Foundation Class OLE no necesitan realizar estas llamadas; lo hace el marco de trabajo). El sistema OLE y el propio servidor pueden establecer referencias al objeto. Un servidor debe destruir un objeto siempre y cuando las referencias externas al objeto siguen en vigor.

El marco de trabajo mantiene un recuento interno del número de referencias a cualquier objeto de servidor que se deriva de [CCmdTarget](../mfc/reference/ccmdtarget-class.md). Este recuento se actualiza cuando un cliente de automatización o en otra entidad se agrega o libera una referencia al objeto.

Cuando el recuento de referencias se convierte en 0, el marco llama a la función virtual [CCmdTarget:: OnFinalRelease](../mfc/reference/ccmdtarget-class.md#onfinalrelease). La implementación predeterminada de esta función llama a la **eliminar** operador para eliminar este objeto.

La biblioteca Microsoft Foundation Class proporciona funciones adicionales para controlar el comportamiento de la aplicación cuando los clientes externos tienen referencias a objetos de la aplicación. Además de mantener un recuento de referencias a cada objeto, los servidores mantienen un recuento global de objetos activos. Las funciones globales [AfxOleLockApp](../mfc/reference/application-control.md#afxolelockapp) y [AfxOleUnlockApp](../mfc/reference/application-control.md#afxoleunlockapp) actualizan el recuento de objetos activos de la aplicación. Si este número es distinto de cero, la aplicación no finaliza cuando el usuario elige cerrar en el menú de sistema o la salida en el menú archivo. En su lugar, ventana principal de la aplicación está oculta (pero no se destruye) hasta que todas las pendientes se hayan completado las solicitudes de cliente. Por lo general, `AfxOleLockApp` y `AfxOleUnlockApp` se llaman en los constructores y destructores, respectivamente, de clases que admiten la automatización.

A veces circunstancias forzar al servidor para finalizar mientras un cliente tiene una referencia a un objeto. Por ejemplo, un recurso que depende el servidor no esté disponible, hacer que el servidor se produzca un error. El usuario también puede cerrar un documento de servidor que contiene los objetos a los que otras aplicaciones tienen referencias.

En el SDK de Windows, consulte `IUnknown::AddRef` y `IUnknown::Release`.

## <a name="see-also"></a>Vea también

[Servidores de automatización](../mfc/automation-servers.md)<br/>
[AfxOleCanExitApp](../mfc/reference/application-control.md#afxolecanexitapp)
