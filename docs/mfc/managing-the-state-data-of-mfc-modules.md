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
ms.openlocfilehash: c8e79f54ed586201a7d82327662643a9a241b8f4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357265"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>Administrar los datos de estado de los módulos MFC

En este artículo se describen los datos de estado de los módulos MFC y cómo se actualiza este estado cuando el flujo de ejecución (el código de ruta de acceso pasa a través de una aplicación al ejecutar) entra y sale de un módulo. También se discute cómo cambiar los estados del módulo con las macros AFX_MANAGE_STATE y METHOD_PROLOGUE.

> [!NOTE]
> El término "módulo" aquí hace referencia a un programa ejecutable, o a un archivo DLL (o conjunto de archivos DLL) que funcionan independientemente del resto de la aplicación, pero utiliza una copia compartida del archivo DLL de MFC. Un control ActiveX es un ejemplo típico de un módulo.

Como se muestra en la figura siguiente, MFC tiene datos de estado para cada módulo utilizado en una aplicación. Entre los ejemplos de estos datos se incluyen identificadores `CWinApp` de `CWinThread` instancia de Windows (utilizados para cargar recursos), punteros a los objetos actuales y de una aplicación, recuentos de referencias de módulos OLE y una variedad de asignaciones que mantienen las conexiones entre los identificadores de objetos de Windows y las instancias correspondientes de objetos MFC. Sin embargo, cuando una aplicación utiliza varios módulos, los datos de estado de cada módulo no son de toda la aplicación. En su lugar, cada módulo tiene su propia copia privada de los datos de estado de MFC.

![Datos de estado de un único módulo &#40;aplicación&#41;](../mfc/media/vc387n1.gif "Datos de estado de un único módulo &#40;aplicación&#41;") <br/>
Datos de estado de un solo módulo (aplicación)

Los datos de estado de un módulo están contenidos en una estructura y siempre están disponibles a través de un puntero a esa estructura. Cuando el flujo de ejecución entra en un módulo determinado, como se muestra en la figura siguiente, el estado de ese módulo debe ser el estado "actual" o "eficaz". Por lo tanto, cada objeto de subproceso tiene un puntero a la estructura de estado efectiva de esa aplicación. Mantener este puntero actualizado en todo momento es vital para administrar el estado global de la aplicación y mantener la integridad del estado de cada módulo. La administración incorrecta del estado global puede dar lugar a un comportamiento impredecible de la aplicación.

![Datos de estado de múltiples módulos](../mfc/media/vc387n2.gif "Datos de estado de varios módulos") <br/>
Datos de estado de varios módulos

En otras palabras, cada módulo es responsable de cambiar correctamente entre los estados del módulo en todos sus puntos de entrada. Un "punto de entrada" es cualquier lugar donde el flujo de ejecución puede introducir el código del módulo. Los puntos de entrada incluyen:

- [Funciones exportadas en un archivo DLL](../mfc/exported-dll-function-entry-points.md)

- [Funciones miembro de interfaces COM](../mfc/com-interface-entry-points.md)

- [Procedimientos de ventana](../mfc/window-procedure-entry-points.md)

## <a name="see-also"></a>Consulte también

[Temas generales de MFC](../mfc/general-mfc-topics.md)
