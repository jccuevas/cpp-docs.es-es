---
title: 'CAtlServiceModuleT:: ServiceMain (función)'
ms.date: 11/04/2016
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: b79767d4c1696174f90a325ea152ccc7939ed9fe
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491721"
---
# <a name="catlservicemoduletservicemain-function"></a>CAtlServiceModuleT:: ServiceMain (función)

El administrador de control de servicios (SCM `ServiceMain` ) llama al abrir la aplicación de panel de control de servicios, seleccione el servicio y haga clic en **iniciar**.

Una vez que el `ServiceMain`SCM llama a, un servicio debe proporcionar al SCM una función de controlador. Esta función permite al SCM obtener el estado del servicio y pasar instrucciones específicas (como pausar o detener). El SCM obtiene esta función cuando el servicio pasa `_Handler` a la función de la API de Win32, [RegisterServiceCtrlHandler](/windows/win32/api/winsvc/nf-winsvc-registerservicectrlhandlerw). (`_Handler` es una función miembro estática que llama al [controlador](../atl/reference/catlservicemodulet-class.md#handler)de la función miembro no estática).

En el inicio, un servicio también debe informar al SCM de su estado actual. Para ello, pasa SERVICE_START_PENDING a la función de la API de Win32, [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus).

`ServiceMain`a continuación `CAtlExeModuleT::InitializeCom`, llama a, que llama a la función de la API de Win32 [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex). De forma predeterminada `InitializeCom` , pasa la marca COINIT_MULTITHREADED a la función. Esta marca indica que el programa va a ser un servidor de subprocesamiento libre.

Ahora, `CAtlServiceModuleT::Run` se llama a para realizar el trabajo principal del servicio. `Run`continúa ejecutándose hasta que se detiene el servicio.

## <a name="see-also"></a>Vea también

[Servicios](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)
