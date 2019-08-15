---
title: 'CAtlServiceModuleT:: Run (función)'
ms.date: 11/04/2016
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
ms.openlocfilehash: 0c35020996852731a8f22c15860d4cceb7a8bdb6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491516"
---
# <a name="catlservicemoduletrun-function"></a>CAtlServiceModuleT:: Run (función)

`Run`contiene llamadas a `PreMessageLoop`, `RunMessageLoop`y `PostMessageLoop`. Después de llamar a `PreMessageLoop` , primero almacena el identificador de subproceso del servicio. El servicio usará este identificador para cerrarse mediante el envío de un mensaje de WM_QUIT mediante la función de la API de Win32, [PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew).

`PreMessageLoop`a continuación `InitializeSecurity`, llama a. De forma predeterminada `InitializeSecurity` , llama a [CoInitializeSecurity](/windows/win32/api/combaseapi/nf-combaseapi-coinitializesecurity) con el descriptor de seguridad establecido en null, lo que significa que cualquier usuario tiene acceso al objeto.

Si no desea que el servicio especifique su propia seguridad, invalide `PreMessageLoop` y no llame `InitializeSecurity`a, y com determinará la configuración de seguridad del registro. Una manera cómoda de configurar los valores del registro es con la utilidad [dcomcnfg](../atl/dcomcnfg.md) que se describe más adelante en esta sección.

Una vez especificada la seguridad, el objeto se registra con COM para que los nuevos clientes puedan conectarse al programa. Por último, el programa indica al administrador de control de servicios (SCM) que se está ejecutando y el programa entra en un bucle de mensajes. El programa permanece en ejecución hasta que envía un mensaje de cierre tras el cierre del servicio.

## <a name="see-also"></a>Vea también

[Servicios](../atl/atl-services.md)<br/>
[CSecurityDesc (clase)](../atl/reference/csecuritydesc-class.md)<br/>
[CSid (clase)](../atl/reference/csid-class.md)<br/>
[CDacl (clase)](../atl/reference/cdacl-class.md)<br/>
[CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)
