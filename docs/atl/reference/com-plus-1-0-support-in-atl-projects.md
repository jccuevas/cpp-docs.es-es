---
title: Compatibilidad con COM + 1.0 en ATL (proyectos) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.appwiz.ATL.MTS
dev_langs: C++
helpviewer_keywords: ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 33b93084a99154aea671c877aae7d80e48485202
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="com-10-support-in-atl-projects"></a>Compatibilidad con COM + 1.0 en ATL (proyectos)
Puede usar el [Asistente para proyectos ATL](../../atl/reference/creating-an-atl-project.md) para crear un proyecto con compatibilidad básica para los componentes de COM + 1.0.  
  
 COM + 1.0 está diseñado para desarrollar aplicaciones distribuidas basadas en componentes. También proporciona una infraestructura de tiempo de ejecución para implementar y administrar estas aplicaciones.  
  
 Si selecciona el **compatibilidad con COM + 1.0** casilla de verificación, el asistente modifica el script de compilación en el paso de vinculación. En concreto, el COM + 1.0 proyecto incluye vínculos a las bibliotecas siguientes:  
  
-   Comsvcs.lib.  
  
-   Mtxguid.lib  
  
 Si selecciona el **compatibilidad con COM + 1.0** casilla de verificación, también puede seleccionar **admitir registro de componentes**. El registrador de componentes permite al objeto COM + 1.0 obtener una lista de componentes, registrar componentes o anular el registro de componentes (individualmente o a la vez).  
  
## <a name="see-also"></a>Vea también  
 [Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
 [Programar con ATL y el código de tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)

