---
title: Ejecutar el programa como un servidor Local | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae2e44ba51a878d293ad5b497a1638cc9d7dc76
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848488"
---
# <a name="running-the-program-as-a-local-server"></a>Ejecutar el programa como un servidor Local
Si ejecuta el programa como un servicio es un problema, puede cambiar temporalmente el registro para que el programa se ejecuta como un servidor local normal. Simplemente cambie el nombre del `LocalService` valor bajo el AppID que `_LocalService` y asegúrese del `LocalServer32` clave bajo el CLSID se ha establecido correctamente. (Tenga en cuenta mediante DCOMCNFG para especificar que la aplicación se debe ejecutar en un equipo diferente cambia el nombre que su `LocalServer32` clave a `_LocalServer32`.) Al ejecutar el programa como un servidor local tarda unos segundos más en el inicio porque la llamada a `StartServiceCtrlDispatcher` en `CAtlServiceModuleT::Start` tarda algunos segundos antes de que se produce un error.  
  
## <a name="see-also"></a>Vea también  
 [Sugerencias de depuración](../atl/debugging-tips.md)

