---
title: Función CAtlServiceModuleT::Start
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: 50054bbb34bcc31a1d11dd8bfab797f98e4e82f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317277"
---
# <a name="catlservicemoduletstart-function"></a>Función CAtlServiceModuleT::Start

Cuando se ejecuta `_tWinMain` el `CAtlServiceModuleT::WinMain`servicio, llama `CAtlServiceModuleT::Start`, que a su vez llama .

`CAtlServiceModuleT::Start`configura una matriz `SERVICE_TABLE_ENTRY` de estructuras que asignan cada servicio a su función de inicio. A continuación, esta matriz se pasa a la función de API de Win32, [StartServiceCtrlDispatcher](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw). En teoría, un EXE podría controlar varios `SERVICE_TABLE_ENTRY` servicios y la matriz podría tener varias estructuras. Actualmente, sin embargo, un servicio generado por ATL solo admite un servicio por EXE. Por lo tanto, la matriz tiene una `_ServiceMain` sola entrada que contiene el nombre del servicio y como la función de inicio. `_ServiceMain`es una función `CAtlServiceModuleT` miembro estática de que `ServiceMain`llama a la función miembro no estática, .

> [!NOTE]
> `StartServiceCtrlDispatcher` Si no se conecta al administrador de control de servicios (SCM), es probable que el programa no se esté ejecutando como un servicio. En este caso, `CAtlServiceModuleT::Run` el programa llama directamente para que el programa se pueda ejecutar como un servidor local. Para obtener más información sobre cómo ejecutar el programa como un servidor local, vea [Sugerencias de depuración](../atl/debugging-tips.md).

## <a name="see-also"></a>Consulte también

[Servicios](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)
