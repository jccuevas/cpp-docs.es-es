---
title: Clases de secciones críticas (ATL) y modelos de subprocesos
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, critical sections
- ATL, multithreading
- threading [ATL], models
- critical sections
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
ms.openlocfilehash: 98db15a1fee2637b9493b538468fa9446015404f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196160"
---
# <a name="threading-models-and-critical-sections-classes"></a>Clases de secciones críticas y modelos de subprocesos

Las clases siguientes definen un subprocesamiento sección crítica y modelo:

- [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md) implementa un servidor COM de subprocesamiento de modelo, agrupadas por subproceso.

- [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md) proporciona métodos para implementar un servidor COM de subprocesamiento de modelo, agrupadas por subproceso.

- [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md) proporciona métodos de subprocesos para aumentar y disminuir una variable. Proporciona una sección crítica.

- [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md) proporciona métodos de subprocesos para aumentar y disminuir una variable. No se proporciona una sección crítica.

- [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md) proporciona métodos para aumentar y disminuir una variable. No se proporciona una sección crítica.

- [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel) determina la clase de modelo de subprocesamiento adecuada para una clase de objeto único.

- [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel) determina la clase de modelo de subprocesamiento adecuada para un objeto que está disponible globalmente.

- [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md) contiene métodos para obtener y liberar una sección crítica. La sección crítica se inicializa automáticamente.

- [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md) contiene métodos para obtener y liberar una sección crítica. Se debe inicializar explícitamente la sección crítica.

- [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md) refleja los métodos de `CComCriticalSection` sin proporcionar una sección crítica. Los métodos de `CComFakeCriticalSection` no hacer nada.

- [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) proporciona la función de creación de un subproceso de CRT. Utilice esta clase si el subproceso va a usar las funciones de CRT.

- [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md) proporciona la función de creación de un subproceso de Windows. Utilice esta clase si el subproceso no va a usar las funciones de CRT.

## <a name="see-also"></a>Vea también

[Información general de clases](../atl/atl-class-overview.md)
