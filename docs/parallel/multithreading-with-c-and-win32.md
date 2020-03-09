---
title: Subprocesamiento múltiple con C y Win32
ms.date: 08/09/2019
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
ms.openlocfilehash: 1764561e0b2b43b8a89d8a1eb2e85d84ce33c4fc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867058"
---
# <a name="multithreading-with-c-and-win32"></a>Subprocesamiento múltiple con C y Win32

El compiladorC++ de Microsoft C/(MSVC) proporciona compatibilidad para la creación de aplicaciones multiproceso. Considere la posibilidad de usar más de un subproceso si la aplicación necesita realizar operaciones costosas que harían que la interfaz de usuario dejara de responder.

Con MSVC, hay varias maneras de programar con varios subprocesos: puede usar C++/WinRT y la biblioteca de Windows Runtime, la biblioteca de Microsoft Foundation Class (MFC C++),/CLI y el tiempo de ejecución de .net, o la biblioteca en tiempo de ejecución de C y la API de Win32. Este artículo trata sobre el multithreading en C. Para ver un ejemplo de código, vea [programa multiproceso de ejemplo en C](sample-multithread-c-program.md).

## <a name="multithread-programs"></a>Programas multiproceso

Un subproceso es básicamente una ruta de ejecución a través de un programa. También es la unidad más pequeña de ejecución que programa Win32. Un subproceso consta de una pila, el estado de los registros de la CPU y una entrada en la lista de ejecución del programador del sistema. Cada subproceso comparte todos los recursos del proceso.

Un proceso se compone de uno o más subprocesos y el código, los datos y otros recursos de un programa en la memoria. Los recursos de programa típicos son archivos abiertos, semáforos y memoria asignada dinámicamente. Un programa se ejecuta cuando el programador del sistema proporciona un control de ejecución de subprocesos. Scheduler determina los subprocesos que deben ejecutarse y cuándo deben ejecutarse. Los subprocesos de menor prioridad podrían tener que esperar mientras los subprocesos de mayor prioridad completan sus tareas. En equipos con varios procesadores, el programador puede trasladar subprocesos individuales a distintos procesadores para equilibrar la carga de la CPU.

Cada subproceso de un proceso funciona de forma independiente. A menos que los haga visibles entre sí, los subprocesos se ejecutan individualmente y no son conscientes de los demás subprocesos de un proceso. Sin embargo, los subprocesos que comparten recursos comunes deben coordinar su trabajo mediante el uso de semáforos u otro método de comunicación entre procesos. Para obtener más información acerca de la sincronización de subprocesos, vea [escribir un programa Win32 multiproceso](#writing-a-multithreaded-win32-program).

## <a name="library-support-for-multithreading"></a>Compatibilidad de bibliotecas con el subprocesamiento múltiple

Todas las versiones de CRT admiten ahora multithreading, con la excepción de las versiones sin bloqueo de algunas funciones. Para obtener más información, vea rendimiento de las [bibliotecas multiproceso](../c-runtime-library/multithreaded-libraries-performance.md). Para obtener información sobre las versiones de CRT disponibles para vincular con el código, vea características de la [biblioteca CRT](../c-runtime-library/crt-library-features.md).

## <a name="include-files-for-multithreading"></a>Archivos de inclusión para el subprocesamiento múltiple

Los archivos de inclusión CRT estándar declaran las funciones de la biblioteca en tiempo de ejecución de C tal como se implementan en las bibliotecas. Si las opciones del compilador especifican las convenciones de llamada [__fastcall o __vectorcall](../build/reference/gd-gr-gv-gz-calling-convention.md) , el compilador supone que se debe llamar a todas las funciones mediante la Convención de llamada Register. Las funciones de la biblioteca en tiempo de ejecución usan la Convención de llamada de C y las declaraciones de los archivos de inclusión estándar indican al compilador que genere referencias externas correctas a estas funciones.

## <a name="crt-functions-for-thread-control"></a>Funciones de CRT para el control de subprocesos

Todos los programas Win32 contienen al menos un subproceso. Cualquier subproceso puede crear subprocesos adicionales. Un subproceso puede completar su trabajo rápidamente y después terminar, o bien puede permanecer activo durante toda la vida del programa.

Las bibliotecas de CRT proporcionan las siguientes funciones para la creación y terminación de subprocesos: [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md), [_endthread y _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md).

Las funciones `_beginthread` y `_beginthreadex` crean un nuevo subproceso y devuelven un identificador del subproceso si la operación se ha realizado correctamente. El subproceso finaliza automáticamente si finaliza la ejecución. O bien, se puede finalizar con una llamada a `_endthread` o `_endthreadex`.

> [!NOTE]
> Si llama a rutinas en tiempo de ejecución de C desde un programa compilado con libcmt. lib, debe iniciar los subprocesos con la función `_beginthread` o `_beginthreadex`. No utilice las funciones `ExitThread` y `CreateThread` de Win32. La utilización de `SuspendThread` puede producir un interbloqueo cuando existe más de un subproceso bloqueado en espera de que el subproceso suspendido complete su acceso a una estructura de datos en tiempo de ejecución de C.

### <a name="_core_the__beginthread_function"></a>Las funciones _beginthread y _beginthreadex

Las funciones `_beginthread` y `_beginthreadex` crean un nuevo subproceso. Un subproceso comparte los segmentos de código y de datos de un proceso con otros subprocesos del proceso pero dispone de sus propios y únicos valores de registros, espacio de pila y dirección de la instrucción actual. El sistema asigna tiempo de CPU a cada subproceso, de modo que todos los subprocesos de un proceso puedan ejecutarse de forma simultánea.

`_beginthread` y `_beginthreadex` son similares a la función [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) de la API Win32, pero tiene estas diferencias:

- Inicializan ciertas variables de la biblioteca en tiempo de ejecución de C. Esto solo es importante si usa la biblioteca en tiempo de ejecución de C en los subprocesos.

- `CreateThread` ayuda a proporcionar control sobre los atributos de seguridad. Esta función se puede utilizar para iniciar un subproceso que se encontraba en un estado suspendido.

`_beginthread` y `_beginthreadex` devuelven un identificador al nuevo subproceso si se han realizado correctamente o un código de error si se produjo un error.

### <a name="_core_the__endthread_function"></a>Las funciones _endthread y _endthreadex

La función [_endthread](../c-runtime-library/reference/endthread-endthreadex.md) termina un subproceso creado por `_beginthread` (y, de forma similar, `_endthreadex` finaliza un subproceso creado por `_beginthreadex`). Los subprocesos terminan automáticamente cuando finalizan. `_endthread` y `_endthreadex` son útiles para la terminación condicional desde un subproceso. Por ejemplo, un subproceso dedicado a procesar las comunicaciones puede terminar si es incapaz de obtener el control del puerto de comunicaciones.

## <a name="writing-a-multithreaded-win32-program"></a>Crear un programa Win32 multiproceso

Al escribir un programa con varios subprocesos, debe coordinar su comportamiento y [el uso de los recursos del programa](#_core_sharing_common_resources_between_threads). Además, asegúrese de que cada subproceso recibe [su propia pila](#_core_thread_stacks).

### <a name="_core_sharing_common_resources_between_threads"></a>Compartir recursos comunes entre subprocesos

> [!NOTE]
> Para obtener una explicación similar desde el punto de vista de MFC, vea [multithreading: sugerencias de programación](multithreading-programming-tips.md) y [multithreading: Cuándo utilizar las clases de sincronización](multithreading-when-to-use-the-synchronization-classes.md).

Cada subproceso dispone de su propia pila y su propia copia de los registros de la CPU. Otros recursos, tales como archivos, datos estáticos y memoria dinámica (montón) se comparten entre todos los subprocesos del proceso. Los subprocesos que utilizan estos recursos comunes deben estar sincronizados. Win32 proporciona varios métodos para sincronizar recursos, entre los que se incluyen semáforos, secciones críticas, eventos y exclusiones mutuas (mutex).

Cuando varios subprocesos obtienen acceso a datos estáticos, el programa debe contemplar y solucionar los posibles conflictos que puedan resultar del acceso a los recursos. Considere un programa en el que un subproceso actualiza una estructura de datos estática que contiene coordenadas *x*,*y* para los elementos que se van a mostrar en otro subproceso. Si el subproceso de actualización modifica la coordenada *x* y se adelanta antes de que pueda cambiar la coordenada *y* , el subproceso de presentación podría programarse antes de que se actualice la coordenada *y* . El elemento se mostraría entonces en una posición incorrecta. Este problema se puede evitar mediante la utilización de semáforos que controlen el acceso a la estructura.

Una exclusión mutua (abreviatura de *MUT*UAL *ex*clusion) es una manera de comunicarse entre subprocesos o procesos que se ejecutan de forma asincrónica entre sí. Esta comunicación se puede usar para coordinar las actividades de varios subprocesos o procesos, normalmente mediante el control del acceso a un recurso compartido mediante el bloqueo y desbloqueo del recurso. Para resolver este problema de actualización de la coordenada *x*,*y* , el subproceso de actualización establece una exclusión mutua que indica que la estructura de datos está en uso antes de realizar la actualización. Posteriormente, después de haber procesado ambas coordenadas, eliminaría la exclusión mutua. El subproceso de presentación en pantalla debe esperar a que se elimine la exclusión mutua para poder actualizar la presentación. Este proceso de espera a una exclusión mutua a menudo se denomina *bloqueo* en una exclusión mutua, porque el proceso está bloqueado y no puede continuar hasta que la exclusión mutua no se borra.

El programa Bounce. c que se muestra en el [programa multiproceso de ejemplo de c](sample-multithread-c-program.md) usa una exclusión mutua denominada `ScreenMutex` para coordinar las actualizaciones de la pantalla. Cada vez que uno de los subprocesos para mostrar está listo para escribir en la pantalla, llama a `WaitForSingleObject` con el identificador de `ScreenMutex` y infinito constante para indicar que la llamada a `WaitForSingleObject` debe bloquearse en la exclusión mutua y no agotar el tiempo de espera. Si `ScreenMutex` está desactivada, la función wait establece la exclusión mutua para que otros subprocesos no interfieran con la presentación y continúe ejecutando el subproceso. De lo contrario, el subproceso se bloquea hasta que la exclusión mutua se elimina. Cuando el subproceso completa la actualización de pantalla, libera la exclusión mutua mediante una llamada a `ReleaseMutex`.

Las escrituras en pantalla y los datos estáticos son sólo dos de los recursos que requieren una cuidadosa administración. Por ejemplo, el programa puede contener varios subprocesos que tengan acceso al mismo archivo. Puesto que otro subproceso puede haber desplazado el puntero del archivo, cada subproceso debe restablecer ese puntero antes de leer o escribir. Además, cada subproceso debe asegurarse de que no se ha adelantado entre el momento en que coloca el puntero y el momento en que tiene acceso al archivo. Estos subprocesos deben usar un semáforo para coordinar el acceso al archivo entre corchetes en cada acceso de archivo con llamadas `WaitForSingleObject` y `ReleaseMutex`. El siguiente ejemplo de código muestra esta técnica:

```C
HANDLE    hIOMutex = CreateMutex (NULL, FALSE, NULL);

WaitForSingleObject( hIOMutex, INFINITE );
fseek( fp, desired_position, 0L );
fwrite( data, sizeof( data ), 1, fp );
ReleaseMutex( hIOMutex);
```

### <a name="_core_thread_stacks"></a>Pilas de subprocesos

Todo el espacio de pila predeterminado de una aplicación se asigna al primer subproceso de ejecución, conocido como subproceso 1. En consecuencia, deberá especificar qué cantidad de memoria desea asignar para una pila independiente para cada subproceso adicional que necesite el programa. El sistema operativo asigna espacio de pila adicional para el subproceso (si es necesario), pero debe especificar un valor predeterminado.

El primer argumento de la llamada a `_beginthread` es un puntero a la función `BounceProc`, que ejecuta los subprocesos. El segundo argumento especifica el tamaño de pila predeterminado para el subproceso. El último argumento es un número de identificación que se pasa a `BounceProc`. `BounceProc` usa el número de identificación para inicializar el generador de números aleatorios y seleccionar el atributo de color y el carácter de visualización del subproceso.

Los subprocesos que realizan llamadas a la biblioteca en tiempo de ejecución de C o a la API Win32 deben proporcionar suficiente espacio de pila para la biblioteca y las funciones de la API a las que llaman. La función `printf` de C requiere más de 500 bytes de espacio de pila, y debe tener 2K bytes de espacio de pila disponible al llamar a rutinas de la API Win32.

Como cada subproceso dispone de su propia pila, podrá evitar posibles colisiones entre los datos si utiliza la menor cantidad posible de datos estáticos. Diseñe el programa de modo que utilice variables automáticas de pila para todos los datos privados de un subproceso. Las únicas variables globales del programa Bounce. c son las exclusiones mutuas o las variables que nunca cambian después de inicializarse.

Win32 también proporciona almacenamiento local de subprocesos (TLS) para almacenar los datos por subproceso. Para obtener más información, vea [almacenamiento local para el subproceso (TLS)](thread-local-storage-tls.md).

## <a name="avoiding-problem-areas-with-multithread-programs"></a>Evitar áreas de riesgo en programas multiproceso

Hay varios problemas que pueden surgir al crear, vincular o ejecutar un programa de C multiproceso. En la tabla siguiente se describen algunos de los problemas más comunes. (Para obtener una explicación similar desde el punto de vista de MFC, vea [multithreading: sugerencias de programación](multithreading-programming-tips.md)).

|Problema|Causa probable|
|-------------|--------------------|
|Aparece un cuadro de mensaje que indica que el programa ha provocado una infracción de protección.|Muchos errores de programación de Win32 causan infracciones de protección. Una causa común de infracciones de protección es la asignación indirecta de datos a punteros nulos. Dado que el programa intenta tener acceso a la memoria que no le pertenece, se emite una infracción de protección.<br /><br /> Una manera sencilla de detectar la causa de una infracción de protección es compilar el programa con información de depuración y, a continuación, ejecutarlo a través del depurador en el entorno de Visual Studio. Cuando se produce un error de protección, Windows transfiere el control al depurador y el cursor se coloca en la línea que causó el problema.|
|El programa genera numerosos errores de compilación y vinculación.|Puede eliminar muchos problemas potenciales si establece el nivel de advertencia del compilador en uno de sus valores más altos y tiene en cuentan los mensajes de advertencia. Mediante el uso de las opciones de nivel de advertencia de nivel 3 o nivel 4, puede detectar conversiones de datos involuntarias, los prototipos de función que faltan y el uso de características no ANSI.|

## <a name="see-also"></a>Consulte también

[Compatibilidad con multithreading para código anterior ( C++visual)](multithreading-support-for-older-code-visual-cpp.md)\
[Programa multiproceso de ejemplo en C](sample-multithread-c-program.md)\
\ de [almacenamiento local para el subproceso (TLS)](thread-local-storage-tls.md)
[Simultaneidad y operaciones asincrónicas con C++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency)\
[Multithreading con C++ y MFC](multithreading-with-cpp-and-mfc.md)
