---
title: Crear un programa Win32 multiproceso
ms.date: 11/04/2016
helpviewer_keywords:
- thread stacks [C++]
- resources [C++], multithreading
- stacks [C++]
- shared resources [C++]
- threading [C++], sharing common resources
- multithreading [C++], thread stacks
- multithreading [C++], sharing common resources
- mutual exclusion [C++]
- communications [C++], between threads
- mutex [C++]
- threading [C++], thread stacks
ms.assetid: 1415f47d-417f-4f42-949b-946fb28aab0e
ms.openlocfilehash: c7d9790cfee39fbddd9ab545d48fa375d56f3a05
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561335"
---
# <a name="writing-a-multithreaded-win32-program"></a>Crear un programa Win32 multiproceso

Al escribir un programa con varios subprocesos, debe coordinar su comportamiento y [el uso de los recursos del programa](#_core_sharing_common_resources_between_threads). También debe asegurarse de que cada subproceso recibe [su propia pila](#_core_thread_stacks).

##  <a name="_core_sharing_common_resources_between_threads"></a> Compartir recursos comunes entre subprocesos

> [!NOTE]
>  Para obtener una discusión similar desde el punto de vista MFC, vea [Multithreading: sugerencias de programación](multithreading-programming-tips.md) y [Multithreading: cuándo usar las clases de sincronización](multithreading-when-to-use-the-synchronization-classes.md).

Cada subproceso dispone de su propia pila y su propia copia de los registros de la CPU. Otros recursos, tales como archivos, datos estáticos y memoria dinámica (montón) se comparten entre todos los subprocesos del proceso. Los subprocesos que utilizan estos recursos comunes deben estar sincronizados. Win32 proporciona varios métodos para sincronizar recursos, entre los que se incluyen semáforos, secciones críticas, eventos y exclusiones mutuas (mutex).

Cuando varios subprocesos obtienen acceso a datos estáticos, el programa debe contemplar y solucionar los posibles conflictos que puedan resultar del acceso a los recursos. Considere la posibilidad de un programa que un subproceso actualiza una estructura de datos estáticos que contiene *x*,*y* coordenadas para los elementos que se mostrará por otro subproceso. Si el subproceso de actualización modifica la *x* coordinar y es relegado antes de que puede cambiar el *y* coordenadas, el subproceso de presentación podría estar programado antes el *y* coordenada es se actualizó. El elemento se mostraría entonces en una posición incorrecta. Este problema se puede evitar mediante la utilización de semáforos que controlen el acceso a la estructura.

Una exclusión mutua (abreviatura de *mut*ual *ex*clusion) es una forma de comunicación entre subprocesos o procesos que se ejecutan de forma asincrónica entre sí. Esta comunicación se suele utilizar para coordinar las actividades de varios procesos o subprocesos, normalmente mediante el control del acceso a un recurso compartido, que se realiza bloqueando y desbloqueando el recurso. Para resolver este problema *x*,*y* problema de actualización de las coordenadas, el subproceso de actualización establece una exclusión mutua que indica que la estructura de datos está en uso antes de realizar la actualización. Posteriormente, después de haber procesado ambas coordenadas, eliminaría la exclusión mutua. El subproceso de presentación en pantalla debe esperar a que se elimine la exclusión mutua para poder actualizar la presentación. Este proceso de espera se suele denominar bloqueo en una exclusión mutua, ya que el proceso se bloquea y no puede continuar hasta que la exclusión mutua se elimina.

El programa Bounce.c mostrado en [ejemplo programa multiproceso en C](sample-multithread-c-program.md) usa una exclusión mutua denominada `ScreenMutex` para coordinar las actualizaciones de pantalla. Cada vez que uno de los subprocesos de presentación está preparado para escribir en la pantalla, llama `WaitForSingleObject` con el identificador de `ScreenMutex` y INFINITE constante para indicar que el `WaitForSingleObject` llamada debe bloquearse en la exclusión mutua y el tiempo de espera. Cuando se restablece el valor de `ScreenMutex`, la función de espera configura la exclusión mutua, de modo que otros subprocesos no interfieran en la presentación en pantalla y continúa ejecutando el subproceso. De lo contrario, el subproceso se bloquea hasta que la exclusión mutua se elimina. Cuando el subproceso finalice la actualización en pantalla, libera la exclusión mutua mediante una llamada a `ReleaseMutex`.

Las escrituras en pantalla y los datos estáticos son sólo dos de los recursos que requieren una cuidadosa administración. Por ejemplo, el programa puede contener varios subprocesos que tengan acceso al mismo archivo. Puesto que otro subproceso puede haber desplazado el puntero del archivo, cada subproceso debe restablecer ese puntero antes de leer o escribir. Además, cada subproceso debe asegurarse de no quedar relegado desde que coloca el puntero hasta que obtiene acceso al archivo. Estos subprocesos utilizarían un semáforo para coordinar el acceso al archivo encerrando cada acceso de archivo con `WaitForSingleObject` y `ReleaseMutex` llamadas. El siguiente ejemplo de código muestra esta técnica:

```
HANDLE    hIOMutex= CreateMutex (NULL, FALSE, NULL);

WaitForSingleObject( hIOMutex, INFINITE );
fseek( fp, desired_position, 0L );
fwrite( data, sizeof( data ), 1, fp );
ReleaseMutex( hIOMutex);
```

##  <a name="_core_thread_stacks"></a> Pilas de subprocesos

Todo el espacio de pila predeterminado de una aplicación se asigna al primer subproceso de ejecución, conocido como subproceso 1. En consecuencia, deberá especificar qué cantidad de memoria desea asignar para una pila independiente para cada subproceso adicional que necesite el programa. El sistema operativo asigna espacio de pila adicional para el subproceso (si es necesario), pero debe especificar un valor predeterminado.

El primer argumento de la `_beginthread` llamada es un puntero a la `BounceProc` función, que ejecuta los subprocesos. El segundo argumento especifica el tamaño de pila predeterminado para el subproceso. El último argumento es un número de identificación que se pasa a `BounceProc`. `BounceProc` el número de identificador se usa para inicializar el generador de números aleatorios y para seleccionar el atributo de color del subproceso y mostrar caracteres.

Los subprocesos que realizan llamadas a la biblioteca en tiempo de ejecución de C o a la API Win32 deben proporcionar suficiente espacio de pila para la biblioteca y las funciones de la API a las que llaman. La función `printf` de C requiere más de 500 bytes de espacio de pila, mientras que las llamadas a rutinas de la API Win32 requieren 2K de espacio de pila disponible.

Como cada subproceso dispone de su propia pila, podrá evitar posibles colisiones entre los datos si utiliza la menor cantidad posible de datos estáticos. Diseñe el programa de modo que utilice variables automáticas de pila para todos los datos privados de un subproceso. Las únicas variables globales del programa Bounce.c son las exclusiones mutuas o las variables que no cambian después de su inicialización.

Win32 también proporciona Almacenamiento local de subprocesos (Thread Local Storage, TLS) para almacenar datos para cada subproceso. Para obtener más información, consulte [almacenamiento Local de subprocesos (TLS)](thread-local-storage-tls.md).

## <a name="see-also"></a>Vea también

[Multithreading con C y Win32](multithreading-with-c-and-win32.md)