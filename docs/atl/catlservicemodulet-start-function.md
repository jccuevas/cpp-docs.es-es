---
title: 'CAtlServiceModuleT:: Start (función)'
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: e6de15f40e89bfffba504db04ee7a16b2a68cac9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491664"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT:: Start (función)

Cuando se ejecuta el servicio, `_tWinMain` llama `CAtlServiceModuleT::WinMain`a, que a su `CAtlServiceModuleT::Start`vez llama a.

`CAtlServiceModuleT::Start`configura una matriz de `SERVICE_TABLE_ENTRY` estructuras que asignan cada servicio a su función de inicio. A continuación, esta matriz se pasa a la función de la API de Win32, [StartServiceCtrlDispatcher](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw). En teoría, un archivo exe podría controlar varios servicios y la matriz podría tener `SERVICE_TABLE_ENTRY` varias estructuras. En la actualidad, sin embargo, un servicio generado por ATL solo admite un servicio por cada archivo. Por lo tanto, la matriz tiene una sola entrada que contiene el nombre `_ServiceMain` del servicio y como la función de inicio. `_ServiceMain`es una función miembro estática de `CAtlServiceModuleT` que llama a la función miembro no estática, `ServiceMain`.

> [!NOTE]
>  Un error `StartServiceCtrlDispatcher` de para conectarse al administrador de control de servicios (SCM) probablemente significa que el programa no se está ejecutando como servicio. En este caso, el programa llama `CAtlServiceModuleT::Run` directamente a para que el programa se pueda ejecutar como un servidor local. Para obtener más información sobre cómo ejecutar el programa como un servidor local, vea [sugerencias](../atl/debugging-tips.md)para la depuración.

## <a name="see-also"></a>Vea también

[Servicios](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)
