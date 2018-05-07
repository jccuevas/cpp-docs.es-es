---
title: 'Servidores de automatización: Problemas de duración de objetos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e27812c20a64f5472c29a66298bcdec30bf4ef2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="automation-servers-object-lifetime-issues"></a>Servidores de Automation: Problemas de duración de objetos
Cuando un cliente de automatización crea o activa un elemento OLE, el servidor transfiere al cliente un puntero a ese objeto. El cliente establece una referencia al objeto mediante una llamada a la función OLE [IUnknown:: AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379). Esta referencia no está en vigor hasta que el cliente llama [IUnknown:: Release](http://msdn.microsoft.com/library/windows/desktop/ms682317). (Las aplicaciones cliente escritas con clases de la biblioteca Microsoft Foundation Class OLE no necesitan realizar estas llamadas; lo hace el marco de trabajo). El sistema OLE y el propio servidor pueden establecer referencias al objeto. Un servidor no debe destruir un objeto mientras las referencias externas al objeto siguen en vigor.  
  
 El marco de trabajo mantiene un recuento interno del número de referencias a cualquier objeto de servidor derivado de [CCmdTarget](../mfc/reference/ccmdtarget-class.md). Este recuento se actualiza cuando un cliente de automatización u otra entidad agrega o libera una referencia al objeto.  
  
 Cuando el recuento de referencias se convierte en 0, el marco de trabajo llama a la función virtual [CCmdTarget:: OnFinalRelease](../mfc/reference/ccmdtarget-class.md#onfinalrelease). La implementación predeterminada de esta función llama el **eliminar** operador que se va a eliminar este objeto.  
  
 La biblioteca Microsoft Foundation Class proporciona funciones adicionales para controlar el comportamiento de la aplicación cuando los clientes externos tienen referencias a objetos de la aplicación. Además de mantener un recuento de referencias a cada objeto, servidores de mantienen un recuento de objetos activos global. Las funciones globales [AfxOleLockApp](../mfc/reference/application-control.md#afxolelockapp) y [AfxOleUnlockApp](../mfc/reference/application-control.md#afxoleunlockapp) actualizan el recuento de objetos activos de la aplicación. Si este número es distinto de cero, la aplicación no finaliza cuando el usuario elige cerrar en el menú de sistema o la salida en el menú archivo. En su lugar, ventana principal de la aplicación se oculta, pero no destruye hasta que todas las pendientes se hayan completado las solicitudes de cliente. Por lo general, `AfxOleLockApp` y `AfxOleUnlockApp` se llaman en los constructores y destructores, respectivamente, de clases que admiten la automatización.  
  
 A veces circunstancias forzar al servidor para terminar mientras un cliente todavía tiene una referencia a un objeto. Por ejemplo, un recurso del que depende el servidor podrían no estar disponible, lo que obliga a que se produzca un error. El usuario también puede cerrar un documento del servidor que contiene objetos a los que otras aplicaciones tienen referencias.  
  
 En el SDK de Windows, vea `IUnknown::AddRef` y `IUnknown::Release`.  
  
## <a name="see-also"></a>Vea también  
 [Servidores de automatización](../mfc/automation-servers.md)   
 [AfxOleCanExitApp](../mfc/reference/application-control.md#afxolecanexitapp)

