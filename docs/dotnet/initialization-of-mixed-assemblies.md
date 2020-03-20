---
title: Inicialización de ensamblados mixtos
ms.date: 03/09/2018
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
ms.openlocfilehash: 35dd47bd87c278d60fc616dca854bf843acc7c57
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544517"
---
# <a name="initialization-of-mixed-assemblies"></a>Inicialización de ensamblados mixtos

Los desarrolladores de Windows siempre deben tener cuidado del bloqueo del cargador cuando se ejecuta código durante la `DllMain`. Sin embargo, hay algunos problemas adicionales que se deben tener en C++cuenta al tratar con los ensamblados de modo mixto de/CLR.

El código de [DllMain](/windows/win32/Dlls/dllmain) no debe tener acceso a Common Language Runtime (CLR) de .net. Esto significa que `DllMain` no debe hacer llamadas a funciones administradas, directa o indirectamente; no se debe declarar ni implementar código administrado en `DllMain`; y ninguna recolección de elementos no utilizados o carga de biblioteca automática debe tener lugar dentro de `DllMain`.

## <a name="causes-of-loader-lock"></a>Causas del bloqueo del cargador

Con la introducción de la plataforma .NET, hay dos mecanismos diferentes para cargar un módulo de ejecución (EXE o DLL): uno para Windows, que se usa para módulos no administrados, y otro para el CLR, que carga ensamblados .NET. El problema de carga de DLL mixtas se centra en el cargador del sistema operativo Microsoft Windows.

Cuando un ensamblado que solo contiene construcciones de .NET se carga en un proceso, el cargador de CLR puede realizar por sí mismo todas las tareas de carga e inicialización necesarias. Pero, en el caso de los ensamblados mixtos, también debe usarse el cargador de Windows porque pueden contener datos y código nativo.

El cargador de Windows garantiza que ningún código pueda tener acceso al código o a los datos de esa DLL antes de que se haya inicializado y que ningún código pueda cargar el archivo DLL de forma redundante mientras se inicializa parcialmente. Para ello, el cargador de Windows usa una sección crítica global del proceso (a menudo denominada "bloqueo del cargador") que impide el acceso no seguro durante la inicialización del módulo. Como resultado, el proceso de carga es vulnerable a muchos escenarios clásicos de interbloqueo. En el caso de los ensamblados mixtos, los dos escenarios siguientes aumentan el riesgo de interbloqueo:

- En primer lugar, si los usuarios intentan ejecutar funciones compiladas en el lenguaje intermedio de Microsoft (MSIL) cuando se mantiene el bloqueo del cargador (desde `DllMain` o en inicializadores estáticos, por ejemplo), puede producirse un interbloqueo. Considere el caso en el que la función MSIL hace referencia a un tipo de un ensamblado que no se ha cargado. El CLR intentará cargar automáticamente ese ensamblado, lo que puede requerir que el cargador de Windows se bloquee en un bloqueo del cargador. Se produce un interbloqueo, ya que el código anterior ya contiene el bloqueo del cargador en la secuencia de llamada. Sin embargo, la ejecución de MSIL en el bloqueo del cargador no garantiza que se produzca un interbloqueo, lo que dificulta el diagnóstico y la corrección de este escenario. En algunas circunstancias, como cuando la DLL del tipo al que se hace referencia no contiene construcciones nativas y todas sus dependencias no contienen construcciones nativas, no es necesario que el cargador de Windows cargue el ensamblado .NET del tipo al que se hace referencia. Además, otro código podría haber cargado el ensamblado necesario o sus dependencias de .NET/nativas mixtas. En consecuencia, el interbloqueo puede ser difícil de predecir y puede variar según la configuración del equipo de destino.

- En segundo lugar, al cargar las dll en las versiones 1,0 y 1,1 del .NET Framework, el CLR presupone que no se mantuvo el bloqueo del cargador y realiza varias acciones que no son válidas en el bloqueo del cargador. Suponiendo que el bloqueo del cargador no se mantiene es una suposición válida para las DLL puramente de .NET, pero, dado que las DLL mixtas ejecutan rutinas de inicialización nativas, necesitan el cargador nativo de Windows y, por tanto, el bloqueo del cargador. Por lo tanto, incluso si el desarrollador no intentaba ejecutar funciones MSIL durante la inicialización de la DLL, existía una pequeña posibilidad de que se produjera un interbloqueo no determinante con las versiones 1.0 y 1.1 de .NET Framework.

Se ha quitado toda la falta de determinación del proceso de carga de DLL mixtas. Se logró con estos cambios:

- El CLR ya no hace suposiciones falsas al cargar las DLL mixtas.

- La inicialización administrada y no administrada se realiza en dos fases diferentes e independientes. La inicialización no administrada tiene lugar primero (a través de DllMain) y la inicialización administrada tiene lugar después, a través de un. Construcción de `.cctor` compatible con .net. Esta última es completamente transparente para el usuario, a menos que se use **/Zl** o **/NODEFAULTLIB** . Para obtener más información, vea[/NODEFAULTLIB (Ignore Libraries)](../build/reference/nodefaultlib-ignore-libraries.md) y [/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md) .

Todavía puede producirse el bloqueo del cargador, pero ahora tiene lugar de forma reproducible y es posible detectarlo. Si `DllMain` contiene instrucciones MSIL, el compilador genera la advertencia [del compilador Warning (nivel 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md). Además, CRT o CLR intentarán detectar e informar de los intentos de ejecutar MSIL en un bloqueo del cargador. La detección de CRT genera el error en tiempo de ejecución R6033 de C del diagnóstico del tiempo de ejecución.

En el resto de este documento se describen los demás escenarios para los que se puede ejecutar MSIL en un bloqueo del cargador, las soluciones del problema en cada uno de estos escenarios y las técnicas de depuración.

## <a name="scenarios-and-workarounds"></a>Escenarios y soluciones

Hay varias situaciones en las que el código de usuario puede ejecutar MSIL en un bloqueo del cargador. El desarrollador debe asegurarse de que la implementación del código de usuario no intente ejecutar instrucciones MSIL en ninguna de estas circunstancias. En las siguientes subsecciones se describen todas las posibilidades con una explicación de cómo resolver los problemas en los casos más comunes.

### <a name="dllmain"></a>DllMain

La función `DllMain` es un punto de entrada definido por el usuario para un archivo DLL. A menos que el usuario especifique lo contrario, se invoca `DllMain` cada vez que un proceso o subproceso se adjunte o se desasocie de la DLL que lo contiene. Dado que esta invocación se puede producir mientras se mantiene el bloqueo del cargador, no se debe compilar en MSIL ninguna función `DllMain` proporcionada por el usuario. Además, no se puede compilar en MSIL ninguna función en el árbol de llamadas con raíz en `DllMain` . Para resolver los problemas en este caso, el bloque de código que define `DllMain` debe modificarse con #pragma `unmanaged`. Debe hacer lo mismo con cada función a la que `DllMain` llame.

En los casos en los que estas funciones deben llamar a una función que requiere una implementación MSIL para otros contextos de llamada, se puede usar una estrategia de duplicación mediante la cual se crean una versión .NET y una versión nativa de la misma función.

Como alternativa, si no se requiere `DllMain` o si no es necesario ejecutarlo en un bloqueo del cargador, se puede quitar la implementación de `DllMain` proporcionada por el usuario, lo que eliminará el problema.

Si DllMain intenta ejecutar MSIL directamente, tendrá como resultado [Compiler Warning (level 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) . Pero el compilador no puede detectar los casos en los que DllMain llama a una función en otro módulo que a su vez intenta ejecutar MSIL.

Para obtener más información sobre este escenario, vea [impedimentos para el diagnóstico](#impediments-to-diagnosis).

### <a name="initializing-static-objects"></a>Inicializar objetos estáticos

La inicialización de objetos estáticos puede producir un interbloqueo si se requiere un inicializador dinámico. En casos sencillos, como cuando se asigna una variable estática a un valor conocido en tiempo de compilación, no se requiere la inicialización dinámica, por lo que no hay ningún riesgo de interbloqueo. Pero las variables estáticas inicializadas mediante llamadas a funciones, invocaciones de constructores o expresiones que no se pueden evaluar en tiempo de compilación requieren que se ejecute código durante la inicialización del módulo.

El código siguiente muestra ejemplos de inicializadores estáticos que requieren inicialización dinámica: una llamada a función, una construcción de objetos y una inicialización de puntero. (Estos ejemplos no son estáticos, pero se supone que se definen en el ámbito global, lo que tiene el mismo efecto).

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

Este riesgo de interbloqueo depende de si el módulo contenedor se compila con **/clr** y de si se ejecutará MSIL. En concreto, si la variable estática se compila sin **/clr** (o si reside en un bloque #pragma `unmanaged` ) y el inicializador dinámico requerido para inicializarla provoca la ejecución de instrucciones MSIL, se puede producir el interbloqueo. Se debe a que, en el caso de los módulos compilados sin **/CLR**, DllMain realiza la inicialización de variables estáticas. En cambio, las variables estáticas compiladas con **/CLR** se inicializan mediante el `.cctor`, una vez que se ha completado la fase de inicialización no administrada y se ha liberado el bloqueo del cargador.

Hay una serie de soluciones para el interbloqueo causado por la inicialización dinámica de variables estáticas (ordenadas según el tiempo necesario para corregir el problema):

- El archivo de código fuente que contiene la variable estática se puede compilar con **/clr**.

- Todas las funciones a las que llama la variable estática se pueden compilar en código nativo mediante la directiva #pragma `unmanaged` .

- Clone manualmente el código del que depende la variable estática. Para ello, proporcione una versión .NET y una versión nativa con nombres diferentes. Después, los desarrolladores podrán llamar a la versión nativa desde inicializadores estáticos nativos y llamar a la versión de .NET en otra parte.

### <a name="user-supplied-functions-affecting-startup"></a>Funciones proporcionadas por el usuario que afectan al inicio

Hay varias funciones proporcionadas por el usuario de las que dependen las bibliotecas para la inicialización durante el inicio. Por ejemplo, al sobrecargar los operadores globalmente C++ en, como los operadores `new` y `delete`, las versiones proporcionadas por el usuario se usan en C++ todas partes, incluidas en la inicialización y la destrucción de la biblioteca estándar. Como resultado, C++ la biblioteca estándar y los inicializadores estáticos proporcionados por el usuario invocarán cualquier versión proporcionada por el usuario de estos operadores.

Si las versiones proporcionadas por el usuario se compilan en MSIL, estos inicializadores tratarán de ejecutar instrucciones MSIL mientras se mantiene el bloqueo del cargador. Un `malloc` proporcionado por el usuario tiene las mismas consecuencias. Para resolver este problema, estas sobrecargas o definiciones proporcionadas por el usuario deben implementarse como código nativo mediante la directiva #pragma `unmanaged` .

Para obtener más información sobre este escenario, vea [impedimentos para el diagnóstico](#impediments-to-diagnosis).

### <a name="custom-locales"></a>Configuraciones regionales personalizadas

Si el usuario proporciona una configuración regional global personalizada, esta configuración regional se usará para inicializar todas las transmisiones de e/s futuras, incluidas las secuencias que se inicializan estáticamente. Si este objeto de configuración regional global se compila en MSIL, las funciones miembro de objeto de configuración regional compiladas en MSIL pueden invocarse mientras se mantiene el bloqueo del cargador.

Hay tres opciones para solucionar este problema:

Los archivos de código fuente que contienen todas las definiciones de transmisión de E/S globales se pueden compilar mediante la opción **/clr** . Impide que sus inicializadores estáticos se ejecuten en un bloqueo del cargador.

Las definiciones de la función de configuración regional personalizada se pueden compilar en código nativo mediante la directiva #pragma `unmanaged` .

Evite establecer la configuración regional personalizada como configuración regional global hasta que se haya liberado el bloqueo del cargador. Después, configure explícitamente las transmisiones de E/S creadas durante la inicialización con la configuración regional personalizada.

## <a name="impediments-to-diagnosis"></a>Impedimentos para la realización del diagnóstico

En algunos casos, es difícil detectar el origen de los interbloqueos. En las siguientes subsecciones se describen estos escenarios y las maneras de solucionar estos problemas.

### <a name="implementation-in-headers"></a>Implementación en encabezados

En determinados casos, las implementaciones de funciones en archivos de encabezado pueden complicar el diagnóstico. Las funciones insertadas y el código de plantilla requieren que las funciones se especifiquen en un archivo de encabezado.  El lenguaje C++ especifica la Regla de una definición, que obliga a que todas las implementaciones de funciones con el mismo nombre sean semánticamente equivalentes. Por lo tanto, no es necesario que el vinculador de C++ tenga en cuenta ninguna consideración especial al combinar archivos objeto que tengan implementaciones duplicadas de una función determinada.

Antes de Visual Studio 2005, el vinculador simplemente elige el mayor de estas definiciones semánticamente equivalentes, para dar cabida a las declaraciones adelantadas y escenarios en los que se usan diferentes opciones de optimización para los distintos archivos de código fuente. Crea un problema para las DLL mixtas o nativas de .net.

Como los C++ archivos con **/CLR** habilitado y deshabilitado pueden incluir el mismo encabezado, o bien se puede ajustar un #include dentro de un bloque de `#pragma unmanaged`, es posible tener tanto código MSIL como versiones nativas de las funciones que proporcionan implementaciones en encabezados. Las implementaciones MSIL y nativas tienen semánticas diferentes con respecto a la inicialización en un bloqueo del cargador, lo que efectivamente infringe la Regla de una definición. Por lo tanto, cuando el vinculador elige la mayor implementación, puede elegir la versión MSIL de una función, aunque se haya compilado explícitamente en código nativo en otro lugar mediante la directiva #pragma unmanaged. Para asegurarse de que nunca se llame a una versión MSIL de una plantilla o función insertada en el bloqueo del cargador, todas las definiciones de cada una de estas funciones llamadas en el bloqueo del cargador deben modificarse con la Directiva `#pragma unmanaged`. Si el archivo de encabezado es de terceros, la forma más fácil de hacer este cambio es enviar y extraer la Directiva de `#pragma unmanaged` en torno a la Directiva #include para el archivo de encabezado infractor. (Vea [administrado, no administrado](../preprocessor/managed-unmanaged.md) para obtener un ejemplo). Sin embargo, esta estrategia no funcionará para los encabezados que contienen otro código que debe llamar directamente a las API de .NET.

Para la comodidad de los usuarios que se encuentran ante un bloqueo del cargador, el vinculador elegirá la implementación nativa frente a la administrada cuando se le presenten ambas. Este valor predeterminado evita los problemas anteriores. Hay dos excepciones a esta regla en esta versión debido a dos problemas sin resolver del compilador:

- La llamada a una función insertada se realiza a través de un puntero de función estático global. Este escenario es importante porque se llama a las funciones virtuales a través de punteros de función globales. Por ejemplo,

```cpp
#include "definesmyObject.h"
#include "definesclassC.h"

typedef void (*function_pointer_t)();

function_pointer_t myObject_p = &myObject;

#pragma unmanaged
void DuringLoaderlock(C & c)
{
    // Either of these calls could resolve to a managed implementation,
    // at link-time, even if a native implementation also exists.
    c.VirtualMember();
    myObject_p();
}
```

### <a name="diagnosing-in-debug-mode"></a>Diagnóstico en modo de depuración

Todos los diagnósticos de problemas del bloqueo del cargador deben realizarse con compilaciones de depuración. Las compilaciones de versión podrían no generar diagnósticos y las optimizaciones efectuadas en modo de versión podrían enmascarar parte de MSIL en los escenarios de bloqueo del cargador.

## <a name="how-to-debug-loader-lock-issues"></a>Cómo depurar problemas de bloqueo del cargador

El diagnóstico que CLR genera cuando se invoca una función MSIL hace que CLR suspenda la ejecución. A su vez, esto hace que C++ el depurador de modo mixto visual se suspenda al ejecutar el depurado en proceso. Sin embargo, al asociarse al proceso, no es posible obtener una pila de llamadas administrada para el depurado mediante el depurador mixto.

Para identificar la función MSIL específica a la que se llamó en un bloqueo del cargador, los desarrolladores deben seguir los pasos siguientes:

1. Asegúrese de que hay símbolos disponibles para mscoree.dll y mscorwks.dll.

   Puede hacer que los símbolos estén disponibles de dos maneras. En primer lugar, los archivos PDB para mscoree.dll y mscorwks.dll pueden agregarse a la ruta de acceso de búsqueda de símbolos. Para agregarlos, abra el cuadro de diálogo Opciones de ruta de acceso de búsqueda de símbolos. (En el menú **herramientas** , elija **Opciones**. En el panel izquierdo del cuadro de diálogo **Opciones** , abra el nodo **depuración** y elija **símbolos**. Agregue la ruta de acceso a los archivos de PDB Mscoree. dll y mscorwks. dll a la lista de búsqueda. Estos archivos PDB se instalan en %VSINSTALLDIR%\SDK\v2.0\symbols. Elija **Aceptar**.

   En segundo lugar, los archivos PDB para mscoree.dll y mscorwks.dll pueden descargarse desde el Servidor de símbolos de Microsoft. Para configurar el Servidor de símbolos, abra el diálogo de opciones de la ruta de acceso de búsqueda de símbolos. (En el menú **herramientas** , elija **Opciones**. En el panel izquierdo del cuadro de diálogo **Opciones** , abra el nodo **depuración** y elija **símbolos**. Agregue esta ruta de búsqueda a la lista de búsqueda: `https://msdl.microsoft.com/download/symbols`. Agregue un directorio de caché de símbolos al cuadro de texto de caché del servidor de símbolos. Elija **Aceptar**.

1. Establezca el modo del depurador en modo solo nativo.

   Abra la cuadrícula de **propiedades** del proyecto de inicio en la solución. Seleccione **propiedades de configuración** > **depuración**. Establezca el **tipo de depurador** en **solo nativo**.

1. Inicie el depurador (F5).

1. Cuando se genere el diagnóstico **/CLR** , elija **Reintentar** y, a continuación, elija **interrumpir**.

1. Abra la ventana Pila de llamadas. (En la barra de menús, elija **Depurar** > **pila de llamadas**de **Windows** > ). El `DllMain` infractor o el inicializador estático se identifican con una flecha verde. Si no se identifica la función incorrecta, deben llevarse a cabo los pasos siguientes para encontrarla.

1. Abra la ventana **inmediato** (en la barra de menús, elija **depurar** > **Windows** > **inmediato**).

1. Escriba `.load sos.dll` en la ventana **inmediato** para cargar el servicio de depuración de SOS.

1. Escriba `!dumpstack` en la ventana **inmediato** para obtener una lista completa de la pila **/CLR** interna.

1. Busque la primera instancia (más cercana a la parte inferior de la pila) de _CorDllMain (si `DllMain` causa el problema) o _VTableBootstrapThunkInitHelperStub o GetTargetForVTableEntry (si un inicializador estático causa el problema). La entrada de la pila justo debajo de esta llamada es la invocación de la función implementada por MSIL que intentó ejecutarse en el bloqueo del cargador.

1. Vaya al archivo de código fuente y al número de línea identificados en el paso anterior y corrija el problema mediante los escenarios y las soluciones que se describen en la sección escenarios.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el ejemplo siguiente se muestra cómo evitar el bloqueo del cargador moviendo código desde `DllMain` al constructor de un objeto global.

En este ejemplo, hay un objeto administrado global cuyo constructor contiene el objeto administrado originalmente en `DllMain`. La segunda parte de este ejemplo hace referencia al ensamblado y crea una instancia del objeto administrado para invocar el constructor del módulo que realiza la inicialización.

### <a name="code"></a>Código

```cpp
// initializing_mixed_assemblies.cpp
// compile with: /clr /LD
#pragma once
#include <stdio.h>
#include <windows.h>
struct __declspec(dllexport) A {
   A() {
      System::Console::WriteLine("Module ctor initializing based on global instance of class.\n");
   }

   void Test() {
      printf_s("Test called so linker does not throw away unused object.\n");
   }
};

#pragma unmanaged
// Global instance of object
A obj;

extern "C"
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved) {
   // Remove all managed code from here and put it in constructor of A.
   return true;
}
```

En este ejemplo se muestran los problemas de inicialización de ensamblados mixtos:

```cpp
// initializing_mixed_assemblies_2.cpp
// compile with: /clr initializing_mixed_assemblies.lib
#include <windows.h>
using namespace System;
#include <stdio.h>
#using "initializing_mixed_assemblies.dll"
struct __declspec(dllimport) A {
   void Test();
};

int main() {
   A obj;
   obj.Test();
}
```

Este código genera el siguiente resultado:

```Output
Module ctor initializing based on global instance of class.

Test called so linker does not throw away unused object.
```

## <a name="see-also"></a>Consulte también

[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)
