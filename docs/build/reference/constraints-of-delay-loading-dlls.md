---
title: Restricciones de las DLL de carga retrasada
ms.date: 11/04/2016
helpviewer_keywords:
- constraints [C++], delayed loading of DLLs
- delayed loading of DLLs, constraints
- DLLs [C++], constraints
ms.assetid: 0097ff65-550f-4a4e-8ac3-39bf6404f926
ms.openlocfilehash: be5e5eb360f80e0b2ea9682f38f6787044cd3c63
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493070"
---
# <a name="constraints-of-delay-loading-dlls"></a>Restricciones de las DLL de carga retrasada

Hay ciertas restricciones relacionadas con la carga retrasada de importaciones.

- No se pueden admitir las importaciones de datos. Una solución alternativa consiste en administrar uno mismo la importación de datos de forma explícita con `LoadLibrary` (o `GetModuleHandle` después de saber que el asistente de carga retrasada cargó la DLL) y `GetProcAddress`.

- No se admite la carga retrasada de Kernel32.dll. Esta DLL es necesaria para que las rutinas del asistente de carga retrasada lleven a cabo la carga retrasada.

- No se admite el [enlace](binding-imports.md) de puntos de entrada que se reenvían.

- Es posible que la carga retrasada de una DLL no tenga como resultado el mismo comportamiento del proceso si hay inicializaciones por procesos que se producen en el punto de entrada de la DLL de carga retrasada. Otros casos incluyen TLS estático (almacenamiento local para el subproceso), declarado mediante [_ _ declspec (subproceso)](../../cpp/thread.md), que no se controla `LoadLibrary`cuando el archivo dll se carga a través de. El TLS dinámico, con `TlsAlloc`, `TlsFree`, `TlsGetValue` y `TlsSetValue`, sigue disponible para su uso en DLL estáticas o de carga retrasada.

- Los punteros de función estáticos (globales) se deben reinicializar a las funciones importadas después de la primera llamada a la función, porque el primer uso del puntero de función apuntará al código thunk.

- Actualmente, con el mecanismo de importación normal, no hay ninguna manera de retrasar la carga de procedimientos específicos de una DLL solamente.

- No se admiten las convenciones de llamada personalizadas (como, por ejemplo, el uso de códigos de condición en las arquitecturas x86). Además, los registros de punto flotante no se guardan en ninguna plataforma. Si la rutina del asistente personalizada o las rutinas de enlace utilizan tipos de punto flotante, tendrán que guardar y restaurar por completo el estado de punto flotante en las máquinas con convenciones de llamada de registro con parámetros de punto flotante. Tenga cuidado al realizar la carga retrasada de la DLL de CRT si llama a funciones de CRT que tomen parámetros de punto flotante en una pila de procesador de datos numéricos (NDP) en la función de ayuda.

## <a name="see-also"></a>Vea también

[Compatibilidad del vinculador con las DLL de carga retrasada](linker-support-for-delay-loaded-dlls.md)<br/>
[LoadLibrary (función)](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)<br/>
[GetModuleHandle función)](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlew)<br/>
[GetProcAddress (función)](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)<br/>
[TlsAlloc (función)](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)<br/>
[TlsFree (función)](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsfree)<br/>
[TlsGetValue función)](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)<br/>
[TlsSetValue función)](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlssetvalue)
