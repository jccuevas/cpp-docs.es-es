---
title: Administrar los datos de estado de los módulos MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5c2bced4f7f04cf75c72e68db0f99e0f89d2566
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930521"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>Administrar los datos de estado de los módulos MFC
En este artículo se describe los datos de estado de los módulos MFC y cómo se actualiza este estado cuando el flujo de ejecución (el código de ruta de acceso tiene a través de una aplicación cuando se ejecuta) entra y sale de un módulo. También se describe el cambio de Estados de módulo mediante las macros AFX_MANAGE_STATE y METHOD_PROLOGUE.  
  
> [!NOTE]
>  El término "módulo" aquí hace referencia a un programa ejecutable, o a un archivo DLL (o conjunto de archivos DLL) que funcionan independientemente del resto de la aplicación, pero usa una copia compartida de la DLL de MFC. Un control ActiveX es un ejemplo típico de un módulo.  
  
 Como se muestra en la ilustración siguiente, MFC tiene datos de estado para cada módulo que se utilizan en una aplicación. Ejemplos de estos datos son los identificadores de instancia de Windows (usados para cargar recursos), punteros a actual `CWinApp` y `CWinThread` objetos de una aplicación, recuentos de referencias de módulo OLE así como una variedad de mapas que mantienen las conexiones entre Windows objeto identificadores y las instancias correspondientes de los objetos MFC. Sin embargo, cuando una aplicación utiliza varios módulos, los datos de estado de todos los módulos no están aplicación amplia. En su lugar, cada módulo tiene su propia copia privada de los datos de estado de MFC.  
  
 ![Los datos de un único módulo de estado &#40;aplicación&#41;](../mfc/media/vc387n1.gif "vc387n1")  
Datos de estado de un solo módulo (aplicación)  
  
 Datos de estado de un módulo se encuentran en una estructura y siempre está disponibles a través de un puntero a esa estructura. Cuando el flujo de ejecución entra en un determinado módulo, como se muestra en la siguiente ilustración, estado de ese módulo debe ser el estado "actual" o "efectivo". Por lo tanto, cada objeto de subproceso tiene un puntero a la estructura de estado efectiva de esa aplicación. Mantener este puntero actualizado en todo momento es vital para administrar el estado global de la aplicación y mantiene la integridad del estado de cada módulo. Administración incorrecta del estado global puede provocar un comportamiento impredecible de la aplicación.  
  
 ![Los datos de varios módulos de estado](../mfc/media/vc387n2.gif "vc387n2")  
Datos de estado de varios módulos  
  
 En otras palabras, cada módulo es responsable de cambiar correctamente entre los Estados de módulos en todos sus puntos de entrada. Un "punto de entrada" es cualquier lugar donde el flujo de ejecución puede escribir el código del módulo. Puntos de entrada incluyen:  
  
-   [Funciones exportadas en un archivo DLL](../mfc/exported-dll-function-entry-points.md)  
  
-   [Funciones miembro de interfaces COM](../mfc/com-interface-entry-points.md)  
  
-   [Procedimientos de ventana](../mfc/window-procedure-entry-points.md)  
  
## <a name="see-also"></a>Vea también  
 [Temas generales de MFC](../mfc/general-mfc-topics.md)

