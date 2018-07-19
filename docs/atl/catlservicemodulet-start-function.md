---
title: 'Función CAtlServiceModuleT:: Start | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule.Start
- CServiceModule::Start
dev_langs:
- C++
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ef614f4cbc3f097e6f790a49c0b599817f9b59c
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849190"
---
# <a name="catlservicemoduletstart-function"></a>Función CAtlServiceModuleT:: Start
Cuando se ejecuta el servicio, `_tWinMain` llamadas `CAtlServiceModuleT::WinMain`, que a su vez llama a `CAtlServiceModuleT::Start`.  
  
 `CAtlServiceModuleT::Start` establece una matriz de `SERVICE_TABLE_ENTRY` estructuras que se asignan cada servicio a su función de inicio. Esta matriz, a continuación, se pasa a la función de la API de Win32, [StartServiceCtrlDispatcher](http://msdn.microsoft.com/library/windows/desktop/ms686324). En teoría, un archivo EXE puede controlar varios servicios y la matriz puede tener varias `SERVICE_TABLE_ENTRY` estructuras. Actualmente, sin embargo, un servicio generado con ATL sólo admite un servicio por archivo EXE. Por lo tanto, la matriz tiene una sola entrada que contiene el nombre del servicio y `_ServiceMain` como función de inicio. `_ServiceMain` es una función miembro estática de `CAtlServiceModuleT` que llama a la función miembro no estático, `ServiceMain`.  
  
> [!NOTE]
>  Error de `StartServiceCtrlDispatcher` para conectar con el control de service manager (SCM) probablemente significa que el programa no se está ejecutando como servicio. En este caso, el programa llama a `CAtlServiceModuleT::Run` directamente para que el programa puede ejecutarse como un servidor local. Para obtener más información acerca de cómo ejecutar el programa como un servidor local, consulte [sugerencias de depuración](../atl/debugging-tips.md).  
  
## <a name="see-also"></a>Vea también  
 [Servicios](../atl/atl-services.md)   
 [CAtlServiceModuleT:: Start](../atl/reference/catlservicemodulet-class.md#start)

