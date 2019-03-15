---
title: Estados de módulos de un archivo DLL de MFC estándar vinculados dinámicamente a MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
ms.openlocfilehash: 3ab51ca8097bd5ec27e8e7cfd8b8f19d76195664
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822150"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>Estados de módulos de un archivo DLL de MFC estándar vinculados dinámicamente a MFC

La capacidad para vincular dinámicamente una DLL de MFC normal a la DLL de MFC permite algunas configuraciones que son muy complicados. Por ejemplo, un archivo DLL MFC y el archivo ejecutable que lo usa pueden tanto dinámicamente vincular a la DLL de MFC a los archivos DLL de extensión MFC.

Esta configuración supone un problema con respecto a los datos globales de MFC, como el puntero a la actual `CWinApp` objeto y asignaciones de identificadores.

Antes de la versión 4.0 de MFC, estos datos globales residían en la propia DLL de MFC y se ha compartido por todos los módulos en el proceso. Dado que cada proceso que utiliza un archivo DLL para Win32 obtiene su propia copia de datos del archivo DLL, este esquema proporciona una manera fácil de realizar un seguimiento de los datos de cada proceso. Además, dado que el modelo AFXDLL suponía que podría haber sólo uno `CWinApp` objeto y solo un conjunto de asignaciones en el proceso de identificadores, se podrían realizar el seguimiento de estos elementos en la propia DLL de MFC.

Pero con la capacidad de vincular dinámicamente un archivo DLL MFC de la DLL de MFC, ahora es posible tener dos o más `CWinApp` objetos en un proceso y también dos o más conjuntos de asignaciones de identificadores. ¿Cómo MFC realizar un seguimiento de las que debería usar?

La solución consiste en proporcionar su propia copia de esta información de estado global de cada módulo (aplicación o DLL de MFC normal). Por lo tanto, una llamada a **AfxGetApp** en las tarifas DLL de MFC devuelve un puntero a la `CWinApp` objeto en el archivo DLL, no aparece en el archivo ejecutable. Esta copia por módulo de los datos globales de MFC se conoce como un estado del módulo y se describe en [Nota técnica 58 de MFC](../mfc/tn058-mfc-module-state-implementation.md).

El procedimiento de ventana común de MFC cambia automáticamente al estado de módulo correcto, por lo que no deberá preocuparse en los controladores de mensajes implementados en el archivo DLL MFC. Pero cuando el archivo ejecutable se llama a la DLL de MFC normal, es necesario establecer explícitamente el estado actual del módulo en uno para el archivo DLL. Para ello, use el **AFX_MANAGE_STATE** macro en todas las funciones que se exporta desde la DLL. Esto se realiza mediante la adición de la línea de código siguiente al principio de las funciones exportadas desde el archivo DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Administrar los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Archivos DLL de MFC estándar vinculados dinámicamente a MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Archivos DLL de extensión MFC](extension-dlls-overview.md)

## <a name="see-also"></a>Vea también

[Archivos DLL en Visual C++](dlls-in-visual-cpp.md)
