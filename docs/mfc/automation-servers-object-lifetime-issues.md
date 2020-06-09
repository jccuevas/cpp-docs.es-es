---
title: 'Servidores de Automation: Problemas de duración de objetos'
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
ms.openlocfilehash: 6e8c4189e8c895cf41323528c70d9277645d8f9d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619068"
---
# <a name="automation-servers-object-lifetime-issues"></a>Servidores de Automation: Problemas de duración de objetos

Cuando un cliente de automatización crea o activa un elemento OLE, el servidor pasa al cliente un puntero a ese objeto. El cliente establece una referencia al objeto a través de una llamada a la función OLE [IUnknown:: AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref). Esta referencia está en vigor hasta que el cliente llame a [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release). (Las aplicaciones cliente escritas con las clases OLE del biblioteca MFC no necesitan realizar estas llamadas; el marco lo hace). El sistema OLE y el propio servidor pueden establecer referencias al objeto. Un servidor no debe destruir un objeto siempre y cuando permanezcan en vigor las referencias externas al objeto.

El marco de trabajo mantiene un recuento interno del número de referencias a cualquier objeto de servidor derivado de [CCmdTarget](reference/ccmdtarget-class.md). Este recuento se actualiza cuando un cliente de automatización u otra entidad agrega o libera una referencia al objeto.

Cuando el recuento de referencias se convierte en 0, el marco de trabajo llama a la función virtual [CCmdTarget:: OnFinalRelease](reference/ccmdtarget-class.md#onfinalrelease). La implementación predeterminada de esta función llama al operador **Delete** para eliminar este objeto.

El biblioteca MFC proporciona funciones adicionales para controlar el comportamiento de la aplicación cuando los clientes externos tienen referencias a los objetos de la aplicación. Además de mantener un recuento de referencias a cada objeto, los servidores mantienen un recuento global de objetos activos. Las funciones globales [AfxOleLockApp](reference/application-control.md#afxolelockapp) y [AfxOleUnlockApp](reference/application-control.md#afxoleunlockapp) actualizan el número de objetos activos de la aplicación. Si este recuento es distinto de cero, la aplicación no finaliza cuando el usuario elige cerrar en el menú del sistema o salir del menú archivo. En su lugar, la ventana principal de la aplicación está oculta (pero no se destruye) hasta que se hayan completado todas las solicitudes de cliente pendientes. Normalmente, `AfxOleLockApp` `AfxOleUnlockApp` se llama a y en los constructores y destructores, respectivamente, de las clases que admiten la automatización.

A veces, las circunstancias obligan al servidor a terminar mientras un cliente todavía tiene una referencia a un objeto. Por ejemplo, un recurso del que depende el servidor puede dejar de estar disponible, lo que hace que el servidor encuentre un error. El usuario también puede cerrar un documento de servidor que contiene objetos a los que otras aplicaciones tienen referencias.

En el Windows SDK, vea `IUnknown::AddRef` y `IUnknown::Release` .

## <a name="see-also"></a>Consulte también

[Servidores de automatización](automation-servers.md)<br/>
[AfxOleCanExitApp](reference/application-control.md#afxolecanexitapp)
