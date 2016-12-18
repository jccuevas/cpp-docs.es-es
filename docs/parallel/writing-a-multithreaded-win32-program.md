---
title: "Crear un programa Win32 multiproceso | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "comunicaciones [C++], entre subprocesos"
  - "subprocesamiento múltiple [C++], compartir recursos comunes"
  - "subprocesamiento múltiple [C++], pilas de subprocesos"
  - "mutex [C++]"
  - "exclusión mutua [C++]"
  - "recursos [C++], multithreading"
  - "recursos compartidos [C++]"
  - "pilas [C++]"
  - "pilas de subprocesos [C++]"
  - "subprocesamiento [C++], compartir recursos comunes"
  - "subprocesamiento [C++], pilas de subprocesos"
ms.assetid: 1415f47d-417f-4f42-949b-946fb28aab0e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear un programa Win32 multiproceso
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se escribe un programa con varios subprocesos, es preciso coordinar su comportamiento y su [utilización de los recursos del programa](#_core_sharing_common_resources_between_threads).  También debe asegurarse de que cada subproceso dispone de [su propia pila](#_core_thread_stacks).  
  
##  <a name="_core_sharing_common_resources_between_threads"></a> Compartir recursos comunes entre subprocesos  
  
> [!NOTE]
>  Para obtener una discusión similar desde el punto de vista de MFC, vea [Subprocesamiento múltiple: Sugerencias de programación](../parallel/multithreading-programming-tips.md) y [Subprocesamiento múltiple: Cuándo utilizar las clases de sincronización](../parallel/multithreading-when-to-use-the-synchronization-classes.md).  
  
 Cada subproceso dispone de su propia pila y su propia copia de los registros de la CPU.  Otros recursos, tales como archivos, datos estáticos y memoria dinámica \(montón\) se comparten entre todos los subprocesos del proceso.  Los subprocesos que utilizan estos recursos comunes deben estar sincronizados.  Win32 proporciona varios métodos para sincronizar recursos, entre los que se incluyen semáforos, secciones críticas, eventos y exclusiones mutuas \(mutex\).  
  
 Cuando varios subprocesos obtienen acceso a datos estáticos, el programa debe contemplar y solucionar los posibles conflictos que puedan resultar del acceso a los recursos.  Considere un programa en el que un subproceso actualiza una estructura de datos estática que contiene coordenadas *x*,*y* para elementos que se van a mostrar en pantalla mediante otro subproceso.  Si el subproceso de actualización modifica la coordenada *x* y, a continuación, queda relegado antes de que pueda cambiar la coordenada *y*, el subproceso de presentación en pantalla podría estar programado antes de que se actualice la coordenada *y*.  El elemento se mostraría entonces en una posición incorrecta.  Este problema se puede evitar mediante la utilización de semáforos que controlen el acceso a la estructura.  
  
 Una exclusión mutua \(*mut**ex*\) es un método de comunicación entre subprocesos o procesos que se ejecutan de forma asincrónica entre sí.  Esta comunicación se suele utilizar para coordinar las actividades de varios procesos o subprocesos, normalmente mediante el control del acceso a un recurso compartido, que se realiza bloqueando y desbloqueando el recurso.  Para resolver este problema de actualización de las coordenadas *x*,*y*, el subproceso de actualización establece una exclusión mutua antes de llevar a cabo la actualización, lo que indicaría que la estructura de datos se encuentra en uso.  Posteriormente, después de haber procesado ambas coordenadas, eliminaría la exclusión mutua.  El subproceso de presentación en pantalla debe esperar a que se elimine la exclusión mutua para poder actualizar la presentación.  Este proceso de espera se suele denominar bloqueo en una exclusión mutua, ya que el proceso se bloquea y no puede continuar hasta que la exclusión mutua se elimina.  
  
 El programa Bounce.c mostrado en [Ejemplo de programa multiproceso en C](../parallel/sample-multithread-c-program.md) utiliza una exclusión mutua denominada `ScreenMutex` para coordinar las actualizaciones de pantalla.  Cada vez que uno de los subprocesos de presentación está preparado para escribir en la pantalla, realiza una llamada a **WaitForSingleObject** con el identificador, que apunta a `ScreenMutex`, y la constante **INFINITE**, que indica que la llamada a **WaitForSingleObject** debe bloquearse en la exclusión mutua todo el tiempo que sea necesario.  Cuando se restablece el valor de `ScreenMutex`, la función de espera configura la exclusión mutua, de modo que otros subprocesos no interfieran en la presentación en pantalla y continúa ejecutando el subproceso.  De lo contrario, el subproceso se bloquea hasta que la exclusión mutua se elimina.  Cuando el subproceso completa la actualización en pantalla, libera la exclusión mutua mediante una llamada a **ReleaseMutex**.  
  
 Las escrituras en pantalla y los datos estáticos son sólo dos de los recursos que requieren una cuidadosa administración.  Por ejemplo, el programa puede contener varios subprocesos que tengan acceso al mismo archivo.  Puesto que otro subproceso puede haber desplazado el puntero del archivo, cada subproceso debe restablecer ese puntero antes de leer o escribir.  Además, cada subproceso debe asegurarse de no quedar relegado desde que coloca el puntero hasta que obtiene acceso al archivo.  Para coordinar el acceso al archivo, estos subprocesos utilizarían un semáforo implementado encerrando las instrucciones de acceso al archivo entre las llamadas a **WaitForSingleObject** y **ReleaseMutex**.  El siguiente ejemplo de código muestra esta técnica:  
  
```  
HANDLE    hIOMutex= CreateMutex (NULL, FALSE, NULL);  
  
WaitForSingleObject( hIOMutex, INFINITE );  
fseek( fp, desired_position, 0L );  
fwrite( data, sizeof( data ), 1, fp );  
ReleaseMutex( hIOMutex);  
```  
  
##  <a name="_core_thread_stacks"></a> Pilas de subprocesos  
 Todo el espacio de pila predeterminado de una aplicación se asigna al primer subproceso de ejecución, conocido como subproceso 1.  En consecuencia, deberá especificar qué cantidad de memoria desea asignar para una pila independiente para cada subproceso adicional que necesite el programa.  El sistema operativo asigna espacio de pila adicional para el subproceso \(si es necesario\), pero debe especificar un valor predeterminado.  
  
 El primer argumento de la llamada a `_beginthread` es un puntero a la función **BounceProc**, que ejecuta los subprocesos.  El segundo argumento especifica el tamaño de pila predeterminado para el subproceso.  El último argumento es un número de id. que se pasa a **BounceProc**.  **BounceProc** utiliza el número de identificación como origen para el generador de números aleatorios y para seleccionar el atributo de color y el carácter de presentación para el subproceso.  
  
 Los subprocesos que realizan llamadas a la biblioteca en tiempo de ejecución de C o a la API Win32 deben proporcionar suficiente espacio de pila para la biblioteca y las funciones de la API a las que llaman.  La función `printf` de C requiere más de 500 bytes de espacio de pila, mientras que las llamadas a rutinas de la API Win32 requieren 2K de espacio de pila disponible.  
  
 Como cada subproceso dispone de su propia pila, podrá evitar posibles colisiones entre los datos si utiliza la menor cantidad posible de datos estáticos.  Diseñe el programa de modo que utilice variables automáticas de pila para todos los datos privados de un subproceso.  Las únicas variables globales del programa Bounce.c son las exclusiones mutuas o las variables que no cambian después de su inicialización.  
  
 Win32 también proporciona Almacenamiento local de subprocesos \(Thread Local Storage, TLS\) para almacenar datos para cada subproceso.  Para obtener más información, vea [Almacenamiento local de subprocesos \(TLS\)](../parallel/thread-local-storage-tls.md).  
  
## Vea también  
 [Subprocesamiento múltiple con C y Win32](../parallel/multithreading-with-c-and-win32.md)