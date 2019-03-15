---
title: 'Función CAtlServiceModuleT:: Start'
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: 204d02a1122ee78b38850bedae5f98b1f338ab1d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816287"
---
# <a name="catlservicemoduletstart-function"></a>Función CAtlServiceModuleT:: Start

Cuando se ejecuta el servicio, `_tWinMain` llamadas `CAtlServiceModuleT::WinMain`, que a su vez llama a `CAtlServiceModuleT::Start`.

`CAtlServiceModuleT::Start` establece una matriz de `SERVICE_TABLE_ENTRY` estructuras que se asignan cada servicio a su función de inicio. Esta matriz, a continuación, se pasa a la función de la API de Win32, [StartServiceCtrlDispatcher](/windows/desktop/api/winsvc/nf-winsvc-startservicectrldispatchera). En teoría, un archivo EXE puede controlar varios servicios y la matriz puede tener varias `SERVICE_TABLE_ENTRY` estructuras. Actualmente, sin embargo, un servicio generado con ATL sólo admite un servicio por archivo EXE. Por lo tanto, la matriz tiene una sola entrada que contiene el nombre del servicio y `_ServiceMain` como función de inicio. `_ServiceMain` es una función miembro estática de `CAtlServiceModuleT` que llama a la función miembro no estático, `ServiceMain`.

> [!NOTE]
>  Error de `StartServiceCtrlDispatcher` para conectar con el control de service manager (SCM) probablemente significa que el programa no se está ejecutando como servicio. En este caso, el programa llama a `CAtlServiceModuleT::Run` directamente para que el programa puede ejecutarse como un servidor local. Para obtener más información acerca de cómo ejecutar el programa como un servidor local, consulte [sugerencias de depuración](../atl/debugging-tips.md).

## <a name="see-also"></a>Vea también

[Servicios](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)
