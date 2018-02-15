---
title: "¿Dónde encaja la automatización remota? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Remote Automation, DCOM
ms.assetid: 4c4c8176-cfc0-44f7-bc87-b690f069ad2f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9ad6eef0bbaad7860e7f4310ce283efe18c668eb
ms.sourcegitcommit: fa7a6dccddce3747389c91277a53e296f905305c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="where-does-remote-automation-fit-in"></a>¿Dónde encaja la automatización remota?
DCOM se lanzó en 1996 y está disponible con plataformas de 32 bits y 64 bits. El equipo de Visual Basic de Microsoft siempre ha visto Visual Basic como utilizando la automatización para permitir que sus componentes para comunicarse. La falta de una versión distribuida limitó en gran medida el uso de estas capacidades en entornos empresariales, por lo que el equipo de desarrollo de Visual Basic 4.0 Enterprise Edition decidió investigar la creación de su propio conjunto de componentes de acceso remoto para la automatización partes de OLE y COM. Claramente, un objetivo fundamental era para asegurarse de que el resultado sería compatible con y se podría reemplazar DCOM cuando empezó a estar disponible. Así, se implementaron para implementar automatización remota (RA) para plataformas de Windows de 16 bits y 32 bits.  
  
 Automatización remota no está asociada a ningún lenguaje específico, pero hasta el lanzamiento de Visual C++ 4.2 Enterprise Edition, sólo se incluía en Visual Basic 4.0. Tenga en cuenta que DCOM reemplaza completamente la automatización remota. Si tiene la oportunidad de usar DCOM en lugar de automatización remota en sus aplicaciones, debería hacerlo. No obstante, hay escenarios donde la automatización remota es más apropiada:  
  
-   Si tienen clientes de 16 bits.  
  
-   Si su organización no ha puesto aún una versión habilitada para DCOM de Windows NT o Windows 95.  
  
-   Si va a actualizar un conjunto de aplicaciones que usa la automatización remota para componentes de C++ en lugar de uno o más componentes de Visual Basic.  
  
 No debe haber ninguna diferencia entre los programas creados para utilizar automatización remota y los creados para utilizar automatización a través de DCOM, y las utilidades de configuración permiten de forma muy sencilla cambiar la operación entre la automatización remota y DCOM. Por lo tanto, no es difícil actualizar una aplicación de automatización remota a DCOM cuando la infraestructura está en su lugar.  
  
## <a name="see-also"></a>Vea también  
 [¿Qué proporciona la automatización remota](what-does-remote-automation-provide-q.md)   
 [Historial de DCOM](../mfc/history-of-dcom.md)
