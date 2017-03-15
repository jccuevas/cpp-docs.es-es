---
title: Compatibilidad con COM + 1.0 en proyectos ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.MTS
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 7521c1dae6fd29b8b951d23fe33c91179d4b46ed
ms.lasthandoff: 02/24/2017

---
# <a name="com-10-support-in-atl-projects"></a>Compatibilidad con COM + 1.0 en proyectos ATL
Puede usar el [Asistente para proyectos ATL](../../atl/reference/creating-an-atl-project.md) para crear un proyecto con compatibilidad básica para los componentes de COM + 1.0.  
  
 COM + 1.0 está diseñado para desarrollar aplicaciones distribuidas basadas en componentes. También proporciona una infraestructura en tiempo de ejecución para implementar y administrar estas aplicaciones.  
  
 Si selecciona el **compatibilidad con COM + 1.0** casilla de verificación, el asistente modifica el script de compilación en el paso de vinculación. En concreto, el COM + 1.0 de proyectos vincula a las siguientes bibliotecas:  
  
-   Comsvcs.lib.  
  
-   Mtxguid.lib  
  
 Si selecciona el **compatibilidad con COM + 1.0** casilla de verificación, también puede seleccionar **admitir registro de componentes**. El registrador de componentes permite al objeto COM + 1.0 obtener una lista de componentes, registrar componentes o eliminar componentes del registro (individualmente o todos a la vez).  
  
## <a name="see-also"></a>Vea también  
 [Fundamentos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
 [Programar con ATL y el código de tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Configuraciones predeterminadas de proyecto ATL](../../atl/reference/default-atl-project-configurations.md)


