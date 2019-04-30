---
title: Restricciones de las DLL de carga retrasada
ms.date: 11/04/2016
helpviewer_keywords:
- constraints [C++], delayed loading of DLLs
- delayed loading of DLLs, constraints
- DLLs [C++], constraints
ms.assetid: 0097ff65-550f-4a4e-8ac3-39bf6404f926
ms.openlocfilehash: e37890fcd757a52ddeff0ccd79289bbc0c35e042
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344166"
---
# <a name="constraints-of-delay-loading-dlls"></a>Restricciones de las DLL de carga retrasada

Hay ciertas restricciones relacionadas con la carga retrasada de importaciones.

- No se pueden admitir las importaciones de datos. Una solución alternativa consiste en administrar uno mismo la importación de datos de forma explícita con `LoadLibrary` (o `GetModuleHandle` después de saber que el asistente de carga retrasada cargó la DLL) y `GetProcAddress`.

- No se admite la carga retrasada de Kernel32.dll. Esta DLL es necesaria para que las rutinas del asistente de carga retrasada lleven a cabo la carga retrasada.

- [Enlace](binding-imports.md) de entrada no se admite los puntos que se reenvían.

- Es posible que la carga retrasada de una DLL no tenga como resultado el mismo comportamiento del proceso si hay inicializaciones por procesos que se producen en el punto de entrada de la DLL de carga retrasada. Otros casos incluyen estático TLS (almacenamiento local de subproceso), declarado mediante [__declspec (Thread)](../../cpp/thread.md), que no se controla al cargar la DLL a través de `LoadLibrary`. El TLS dinámico, con `TlsAlloc`, `TlsFree`, `TlsGetValue` y `TlsSetValue`, sigue disponible para su uso en DLL estáticas o de carga retrasada.

- Los punteros de función estáticos (globales) se deben reinicializar a las funciones importadas después de la primera llamada a la función, porque el primer uso del puntero de función apuntará al código thunk.

- Actualmente, con el mecanismo de importación normal, no hay ninguna manera de retrasar la carga de procedimientos específicos de una DLL solamente.

- No se admiten las convenciones de llamada personalizadas (como, por ejemplo, el uso de códigos de condición en las arquitecturas x86). Además, los registros de punto flotante no se guardan en ninguna plataforma. Si la rutina del asistente personalizada o las rutinas de enlace utilizan tipos de punto flotante, tendrán que guardar y restaurar por completo el estado de punto flotante en las máquinas con convenciones de llamada de registro con parámetros de punto flotante. Tenga cuidado al realizar la carga retrasada de la DLL de CRT si llama a funciones de CRT que tomen parámetros de punto flotante en una pila de procesador de datos numéricos (NDP) en la función de ayuda.

## <a name="see-also"></a>Vea también

[Compatibilidad del vinculador con las DLL de carga retrasada](linker-support-for-delay-loaded-dlls.md)<br/>
[LoadLibrary (función)](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya)<br/>
[GetModuleHandle (función)](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulehandlea)<br/>
[GetProcAddress (función)](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress)<br/>
[Función TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc)<br/>
[Función TlsFree](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsfree)<br/>
[Función TlsGetValue](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)<br/>
[Función TlsSetValue](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlssetvalue)
