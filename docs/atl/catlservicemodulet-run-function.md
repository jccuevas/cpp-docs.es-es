---
title: 'Función CAtlServiceModuleT:: Run'
ms.date: 11/04/2016
f1_keywords:
- CServiceModule::Run
- CServiceModule.Run
- CSecurityDescriptor
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
ms.openlocfilehash: 91b6465dd975a1e3227d1416f2b78a8abbd441ad
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694328"
---
# <a name="catlservicemoduletrun-function"></a>Función CAtlServiceModuleT:: Run

`Run` contiene las llamadas a `PreMessageLoop`, `RunMessageLoop`, y `PostMessageLoop`. Después de que se llama, `PreMessageLoop` almacena primero el identificador de subproceso. del servicio El servicio utilizará este identificador para cerrarse enviando un mensaje WM_QUIT mediante la función de la API de Win32, [PostThreadMessage](/windows/desktop/api/winuser/nf-winuser-postthreadmessagea).

`PreMessageLoop` a continuación, llama a `InitializeSecurity`. De forma predeterminada, `InitializeSecurity` llamadas [CoInitializeSecurity](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializesecurity) con el descriptor de seguridad establecido en NULL, lo que significa que los usuarios tengan acceso al objeto.

Si no desea que el servicio para especificar su propia seguridad, invalidar `PreMessageLoop` y no llame a `InitializeSecurity`, y COM, a continuación, va a determinar la configuración de seguridad del registro. Es una manera cómoda de configuración del registro con el [DCOMCNFG](../atl/dcomcnfg.md) utilidad descrita más adelante en esta sección.

Una vez que se especifica la seguridad, el objeto está registrado con COM para que los nuevos clientes pueden conectarse al programa. Por último, el programa indica al administrador de control de servicios (SCM) que se está ejecutando y el programa entra en un bucle de mensajes. El programa sigue ejecutándose hasta que envía un mensaje quit al cerrar el servicio.

## <a name="see-also"></a>Vea también

[Servicios](../atl/atl-services.md)<br/>
[CSecurityDesc (clase)](../atl/reference/csecuritydesc-class.md)<br/>
[CSid (clase)](../atl/reference/csid-class.md)<br/>
[CDacl (clase)](../atl/reference/cdacl-class.md)<br/>
[CAtlServiceModuleT:: Run](../atl/reference/catlservicemodulet-class.md#run)

