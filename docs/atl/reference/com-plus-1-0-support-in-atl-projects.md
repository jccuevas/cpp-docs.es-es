---
title: Compatibilidad con COM + 1.0 en proyectos ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.MTS
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06a9e6cd4a374f0941b360a3f8f24f61e4b46a6a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763303"
---
# <a name="com-10-support-in-atl-projects"></a>Compatibilidad con COM + 1.0 en proyectos ATL

Puede usar el [Asistente para proyectos ATL](../../atl/reference/creating-an-atl-project.md) para crear un proyecto con compatibilidad básica para los componentes de COM + 1.0.

COM + 1.0 está diseñado para desarrollar aplicaciones distribuidas basadas en componentes. También se proporciona una infraestructura de tiempo de ejecución para implementar y administrar estas aplicaciones.

Si selecciona el **compatibilidad con COM + 1.0** casilla de verificación, el asistente modifica el script de compilación en el paso del vínculo. En concreto, el COM + 1.0 proyecto incluye vínculos a las siguientes bibliotecas:

- Comsvcs.lib.

- Mtxguid.lib

Si selecciona el **compatibilidad con COM + 1.0** casilla de verificación, también puede seleccionar **registrador de componentes de soporte técnico**. El registrador de componentes permite al objeto COM + 1.0 obtener una lista de componentes, registrar componentes o anular el registro de componentes (individualmente o a la vez).

## <a name="see-also"></a>Vea también

[Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
[Programar con ATL y código de tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
[Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)

