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
ms.openlocfilehash: d1bed6f3b0dddf0d4ae5e8309d683e52c9e82410
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52174896"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>Administrar los datos de estado de los módulos MFC

Este artículo describen los datos de estado de los módulos MFC y cómo se actualiza este estado cuando el flujo de ejecución (el código de path toma a través de una aplicación cuando se ejecuta) entra y sale de un módulo. También se trata el cambio de Estados de módulos con las macros AFX_MANAGE_STATE y METHOD_PROLOGUE.

> [!NOTE]
>  El término "módulo" aquí hace referencia a un programa ejecutable, o a un archivo DLL (o conjunto de archivos DLL) que funcionan independientemente del resto de la aplicación, pero usa una copia compartida de la DLL de MFC. Un control ActiveX es un ejemplo típico de un módulo.

Como se muestra en la ilustración siguiente, MFC tiene datos de estado para cada módulo que se usan en una aplicación. Algunos ejemplos de estos datos son los identificadores de instancia de Windows (usados para cargar recursos), punteros a la actual `CWinApp` y `CWinThread` de una aplicación OLE recuentos de referencia de módulo y una variedad de mapas que mantienen las conexiones entre los objetos Windows objeto identificadores y las instancias correspondientes de objetos de MFC. Sin embargo, cuando una aplicación utiliza varios módulos, los datos de estado de cada módulo no están aplicación amplia. En su lugar, cada módulo tiene su propia copia privada de los datos de estado de MFC.

![Los datos de un solo módulo de estado &#40;aplicación&#41;](../mfc/media/vc387n1.gif "los datos de un solo módulo de estado &#40;aplicación&#41;") <br/>
Datos de estado de un solo módulo (aplicación)

Datos de estado de un módulo se encuentran en una estructura y siempre está disponibles a través de un puntero a esa estructura. Cuando el flujo de ejecución entra en un módulo determinado, como se muestra en la siguiente ilustración, estado de ese módulo debe ser el estado "actual" o "eficaces". Por lo tanto, cada objeto de subproceso tiene un puntero a la estructura de estado efectivo de la aplicación. Mantener este puntero actualizado en todo momento es vital para administrar el estado global de la aplicación y mantener la integridad del estado de cada módulo. Administración incorrecta del estado global puede provocar un comportamiento impredecible de la aplicación.

![Los datos de varios módulos de estado](../mfc/media/vc387n2.gif "los datos de varios módulos de estado") <br/>
Datos de estado de varios módulos

En otras palabras, cada módulo es responsable de cambiar correctamente entre los Estados de módulos en todos sus puntos de entrada. Un "punto de entrada" es cualquier lugar donde el flujo de ejecución puede escribir el código del módulo. Puntos de entrada incluyen:

- [Funciones exportadas en un archivo DLL](../mfc/exported-dll-function-entry-points.md)

- [Funciones miembro de las interfaces COM](../mfc/com-interface-entry-points.md)

- [Procedimientos de ventana](../mfc/window-procedure-entry-points.md)

## <a name="see-also"></a>Vea también

[Temas generales de MFC](../mfc/general-mfc-topics.md)
