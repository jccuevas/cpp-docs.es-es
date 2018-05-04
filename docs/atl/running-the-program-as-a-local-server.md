---
title: Ejecutar el programa como un servidor Local | Documentos de Microsoft
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
ms.openlocfilehash: c2b8a79978528493e02ac5a272dafe8da6fdc1d9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="running-the-program-as-a-local-server"></a>Ejecutar el programa como un servidor Local
Si ejecuta el programa como un servicio es un problema, puede cambiar temporalmente el registro para que el programa se ejecuta como un servidor local normal. Basta con cambiar el nombre de la `LocalService` valor bajo el AppID a `_LocalService` y asegúrese del `LocalServer32` clave bajo el CLSID está establecida correctamente. (Tenga en cuenta que mediante DCOMCNFG para especificar que la aplicación debe ejecutarse en un equipo diferente cambia el nombre la `LocalServer32` clave a `_LocalServer32`.) Al ejecutar el programa como un servidor local tarda unos segundos más en el inicio porque la llamada a **StartServiceCtrlDispatcher** en `CAtlServiceModuleT::Start` tarda unos segundos antes de que se produce un error.  
  
## <a name="see-also"></a>Vea también  
 [Sugerencias de depuración](../atl/debugging-tips.md)

