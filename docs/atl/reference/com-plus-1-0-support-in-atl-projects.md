---
title: Compatibilidad con COM + 1.0 en proyectos ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.MTS
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
ms.openlocfilehash: 39a3597b8df833d89942e31b361f791b14ceb8c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278480"
---
# <a name="com-10-support-in-atl-projects"></a>Compatibilidad con COM + 1.0 en proyectos ATL

Puede usar el [Asistente para proyectos ATL](../../atl/reference/creating-an-atl-project.md) para crear un proyecto con compatibilidad básica para los componentes de COM + 1.0.

COM + 1.0 está diseñado para desarrollar aplicaciones distribuidas basadas en componentes. También se proporciona una infraestructura de tiempo de ejecución para implementar y administrar estas aplicaciones.

Si selecciona el **compatibilidad con COM + 1.0** casilla de verificación, el asistente modifica el script de compilación en el paso del vínculo. En concreto, el COM + 1.0 proyecto incluye vínculos a las siguientes bibliotecas:

- comsvcs.lib

- Mtxguid.lib

Si selecciona el **compatibilidad con COM + 1.0** casilla de verificación, también puede seleccionar **registrador de componentes de soporte técnico**. El registrador de componentes permite al objeto COM + 1.0 obtener una lista de componentes, registrar componentes o anular el registro de componentes (individualmente o a la vez).

## <a name="see-also"></a>Vea también

[Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programar con ATL y código en tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)
