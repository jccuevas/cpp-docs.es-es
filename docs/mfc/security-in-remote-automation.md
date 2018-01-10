---
title: "Seguridad de la automatización remota | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- AllowRemoteActivation [MFC]
- Remote Automation [MFC], security
- activating objects [MFC]
- security [MFC]
- Automation objects [MFC], security options
- object activation [MFC]
- security [MFC], Remote Automation
ms.assetid: 276b300d-c0b5-4bd8-8bf5-0270994b9cfa
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e535fac6330d6268629e8e3681fec47c7b0d65d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="security-in-remote-automation"></a>Seguridad de la automatización remota
Automatización remota es compatible con un nivel básico de seguridad para permitir que un escritor de la aplicación de servidor (o, en su lugar, su administrador) especificar cómo un objeto específico puede activarse de manera remota. Todos los objetos de automatización en un sistema determinado pueden establecerse globalmente a "no permitir activación remota" o "Permitir activación remota". Además y con más frecuencia, los objetos individuales pueden recibir estas capacidades. Automatización remota utiliza una clave en la configuración de registro de cada objeto, **AllowRemoteActivation**, para determinar si un servidor determinado puede activarse de manera remota. Si la configuración de todo el sistema usa este modo, a continuación, puede asignarse a cada objeto en el registro de esta clave y el estado individual de cada uno de ellos puede establecerse en "Sí" o "no", según corresponda.  
  
 Si el sistema de servidor está ejecutando Windows NT o Windows 2000, se permite una forma alternativa de seguridad. En este caso, la automatización remota utiliza la lista de control de acceso (ACL) de NT para especificar qué usuarios o grupo o grupos de usuarios pueden activar de forma remota un servidor determinado.  
  
 Tenga en cuenta que las opciones de seguridad se aplican a todo el objeto; no es posible establecer atributos de una interfaz específica, o de propiedades o métodos individuales en ese objeto.  
  
 Todas las opciones de seguridad se pueden establecer a través del Administrador de conexiones de automatización remota (RAC).  
  
## <a name="see-also"></a>Vea también  
 [Automatización remota](../mfc/remote-automation.md)

