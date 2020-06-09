---
title: Administrar los datos de estado de los módulos MFC
ms.date: 11/19/2018
helpviewer_keywords:
- global state [MFC]
- data management [MFC], MFC modules
- window procedure entry points [MFC]
- exported interfaces and global state [MFC]
- module states [MFC], saving and restoring
- data management [MFC]
- MFC, managing state data
- multiple modules [MFC]
- module state restored [MFC]
ms.assetid: 81889c11-0101-4a66-ab3c-f81cf199e1bb
ms.openlocfilehash: 64888b8ab53ebd80f328e1efe79df6256f30f9b6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622569"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>Administrar los datos de estado de los módulos MFC

En este artículo se describen los datos de estado de los módulos MFC y cómo se actualiza este estado cuando el flujo de ejecución (el código de ruta de acceso pasa a través de una aplicación cuando se ejecuta) entra y sale de un módulo. También se describe cómo cambiar los Estados del módulo con las macros AFX_MANAGE_STATE y METHOD_PROLOGUE.

> [!NOTE]
> El término "módulo" se refiere a un programa ejecutable, o a un archivo DLL (o un conjunto de archivos dll) que funcionan independientemente del resto de la aplicación, pero usa una copia compartida del archivo DLL de MFC. Un control ActiveX es un ejemplo típico de un módulo.

Como se muestra en la siguiente ilustración, MFC tiene datos de estado para cada módulo que se usa en una aplicación. Algunos ejemplos de estos datos son los identificadores de instancia de Windows (que se usan para cargar recursos), los punteros a los `CWinApp` objetos y actuales `CWinThread` de una aplicación, los recuentos de referencias del módulo OLE y una variedad de asignaciones que mantienen las conexiones entre los identificadores de objetos de Windows y las instancias correspondientes de objetos MFC. Sin embargo, cuando una aplicación usa varios módulos, los datos de estado de cada módulo no son de toda la aplicación. En su lugar, cada módulo tiene su propia copia privada de los datos de estado de MFC.

![Datos de estado de un solo módulo &#40;aplicación&#41;](../mfc/media/vc387n1.gif "Datos de estado de un solo módulo &#40;aplicación&#41;") <br/>
Datos de estado de un solo módulo (aplicación)

Los datos de estado de un módulo están contenidos en una estructura y siempre están disponibles a través de un puntero a esa estructura. Cuando el flujo de ejecución entra en un módulo determinado, como se muestra en la ilustración siguiente, el estado de ese módulo debe ser el estado "actual" o "efectivo". Por consiguiente, cada objeto de subproceso tiene un puntero a la estructura de Estado efectivo de esa aplicación. Mantener este puntero actualizado en todo momento es fundamental para administrar el estado global de la aplicación y mantener la integridad del estado de cada módulo. Una administración incorrecta del estado global puede provocar un comportamiento impredecible de la aplicación.

![Datos de estado de varios módulos](../mfc/media/vc387n2.gif "Datos de estado de varios módulos") <br/>
Datos de estado de varios módulos

En otras palabras, cada módulo es responsable de cambiar correctamente entre Estados de módulos en todos sus puntos de entrada. Un "punto de entrada" es cualquier lugar donde el flujo de ejecución puede entrar en el código del módulo. Los puntos de entrada incluyen:

- [Funciones exportadas en un archivo DLL](exported-dll-function-entry-points.md)

- [Funciones miembro de interfaces COM](com-interface-entry-points.md)

- [Procedimientos de ventana](window-procedure-entry-points.md)

## <a name="see-also"></a>Consulte también

[Temas generales de MFC](general-mfc-topics.md)
