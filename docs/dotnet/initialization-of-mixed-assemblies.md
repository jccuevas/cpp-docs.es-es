---
title: Inicialización de ensamblados mixtos | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ba9f3143fb110b25f384e462e7dfcd69c0140802
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439580"
---
# <a name="initialization-of-mixed-assemblies"></a>Inicialización de ensamblados mixtos

Los desarrolladores de Windows siempre deben ser precavido a la hora de bloqueo del cargador cuando se ejecuta código durante `DllMain`. Sin embargo, hay algunas consideraciones adicionales que entran en juego cuando se trabaja con C / c++ / clr ensamblados de modo mixto.

Código de [DllMain](/windows/desktop/Dlls/dllmain) no debe tener acceso al CLR. Esto significa que `DllMain` no debe hacer llamadas a funciones administradas directa o indirectamente; no se debe declarar ni implementar código administrado en `DllMain`; y no se debe producir la recolección de elementos no usados ni la carga automática de bibliotecas dentro de `DllMain`.

## <a name="causes-of-loader-lock"></a>Causas del bloqueo del cargador

Con la introducción de la plataforma .NET, hay dos mecanismos diferentes para cargar un módulo de ejecución (EXE o DLL): uno para Windows, que se usa para módulos no administrados, y otro para Common Language Runtime (CLR) de .NET, que carga ensamblados .NET. El problema de carga de DLL mixtas se centra en el cargador del sistema operativo Microsoft Windows.

Cuando un ensamblado que solo contiene construcciones de .NET se carga en un proceso, el cargador de CLR puede realizar por sí mismo todas las tareas de carga e inicialización necesarias. Pero, en el caso de los ensamblados mixtos, también debe usarse el cargador de Windows porque pueden contener datos y código nativo.

El cargador de Windows garantiza que el código no pueda tener acceso al código o a los datos de esa DLL antes de que se haya inicializado y que no pueda cargar innecesariamente la DLL mientras esté parcialmente inicializada. Para ello, el cargador de Windows usa una sección crítica global del proceso (a menudo denominada "bloqueo del cargador") que impide el acceso no seguro durante la inicialización del módulo. Como resultado, el proceso de carga es vulnerable a muchos escenarios clásicos de interbloqueo. En el caso de los ensamblados mixtos, los dos escenarios siguientes aumentan el riesgo de interbloqueo:

- En primer lugar, si los usuarios intentan ejecutar funciones compiladas en Lenguaje intermedio de Microsoft (MSIL) cuando se mantiene el bloqueo del cargador (desde `DllMain` o en inicializadores estáticos, por ejemplo), esto puede causar un interbloqueo. Considere el caso en el que la función MSIL hace referencia a un tipo de un ensamblado que no se ha cargado. El CLR intentará cargar automáticamente ese ensamblado, lo que puede requerir que el cargador de Windows se bloquee en un bloqueo del cargador. Como el bloqueo del cargador ya se mantiene mediante el código anterior en la secuencia de llamada, se produce un interbloqueo. Pero la ejecución de MSIL en un bloqueo del cargador no garantiza que se produzca un interbloqueo, lo que dificulta el diagnóstico y la corrección de este escenario. En algunas circunstancias, como cuando la DLL del tipo al que se hace referencia no contiene construcciones nativas y ninguna de sus dependencias contiene construcciones nativas, no se requiere que el cargador de Windows cargue el ensamblado de .NET del tipo al que se hace referencia. Además, otro código podría haber cargado el ensamblado necesario o sus dependencias de .NET/nativas mixtas. En consecuencia, el interbloqueo puede ser difícil de predecir y puede variar según la configuración del equipo de destino.

- En segundo lugar, al cargar las DLL en las versiones 1.0 y 1.1 de .NET Framework, el CLR daba por supuesto que el bloqueo del cargador no se había mantenido y realizaba varias acciones que no son válidas en un bloqueo del cargador. El hecho de dar por supuesto que el bloqueo del cargador no se mantiene es una suposición válida para las DLL puramente de .NET pero, dado que las DLL mixtas ejecutan rutinas de inicialización nativas, necesitan el cargador nativo de Windows y, por lo tanto, el bloqueo del cargador. Por lo tanto, incluso si el desarrollador no intentaba ejecutar funciones MSIL durante la inicialización de la DLL, existía una pequeña posibilidad de que se produjera un interbloqueo no determinante con las versiones 1.0 y 1.1 de .NET Framework.

Se ha quitado toda la falta de determinación del proceso de carga de DLL mixtas. Esto se ha logrado a través de estos cambios:

- El CLR ya no hace suposiciones falsas al cargar las DLL mixtas.

- La inicialización administrada y no administrada se realiza en dos fases diferentes e independientes. Se produce primero la inicialización no administrada (a través de DllMain) y después tiene lugar la inicialización administrada, a través de una construcción compatible con NET denominada *.cctor*. Esta última es completamente transparente para el usuario, a menos que se use **/Zl** o **/NODEFAULTLIB** . Para obtener más información, vea[/NODEFAULTLIB (Ignore Libraries)](../build/reference/nodefaultlib-ignore-libraries.md) y [/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md) .

Todavía puede producirse el bloqueo del cargador, pero ahora tiene lugar de forma reproducible y es posible detectarlo. Si `DllMain` contiene instrucciones MSIL, el compilador genera la advertencia [advertencia del compilador (nivel 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md). Además, CRT o CLR intentarán detectar e informar de los intentos de ejecutar MSIL en un bloqueo del cargador. La detección de CRT genera el error en tiempo de ejecución R6033 de C del diagnóstico del tiempo de ejecución.

En el resto de este documento se describen los demás escenarios para los que se puede ejecutar MSIL en un bloqueo del cargador, las soluciones del problema en cada uno de estos escenarios y las técnicas de depuración.

## <a name="scenarios-and-workarounds"></a>Escenarios y soluciones

Hay varias situaciones en las que el código de usuario puede ejecutar MSIL en un bloqueo del cargador. El desarrollador debe asegurarse de que la implementación del código de usuario no intente ejecutar instrucciones MSIL en ninguna de estas circunstancias. En las siguientes subsecciones se describen todas las posibilidades con una explicación de cómo resolver los problemas en los casos más comunes.

### <a name="dllmain"></a>DllMain

La función `DllMain` es un punto de entrada definido por el usuario para una DLL. A menos que el usuario especifique lo contrario, se invoca `DllMain` cada vez que un proceso o subproceso se adjunte o se desasocie de la DLL que lo contiene. Dado que esta invocación se puede producir mientras se mantiene el bloqueo del cargador, no se debe compilar en MSIL ninguna función `DllMain` proporcionada por el usuario. Además, no se puede compilar en MSIL ninguna función en el árbol de llamadas con raíz en `DllMain` . Para resolver los problemas en este caso, el bloque de código que define `DllMain` debe modificarse con #pragma `unmanaged`. Debe hacer lo mismo con cada función a la que `DllMain` llame.

En los casos en los que estas funciones deben llamar a una función que requiere una implementación MSIL para otros contextos de llamada, se puede usar una estrategia de duplicación mediante la cual se crean una versión .NET y una versión nativa de la misma función.

Como alternativa, si no se requiere `DllMain` o si no es necesario ejecutarlo en un bloqueo del cargador, se puede quitar la implementación de `DllMain` proporcionada por el usuario, lo que eliminará el problema.

Si DllMain intenta ejecutar MSIL directamente, tendrá como resultado [Compiler Warning (level 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) . Pero el compilador no puede detectar los casos en los que DllMain llama a una función en otro módulo que a su vez intenta ejecutar MSIL.

Para obtener más información sobre este escenario, vea "Impedimentos para la realización del diagnóstico".

### <a name="initializing-static-objects"></a>Inicializar objetos estáticos

La inicialización de objetos estáticos puede producir un interbloqueo si se requiere un inicializador dinámico. En casos sencillos, como cuando simplemente se asigna una variable estática a un valor conocido en tiempo de compilación, no se requiere la inicialización dinámica, por lo que no hay riesgo de interbloqueo. Pero las variables estáticas inicializadas mediante llamadas a funciones, invocaciones de constructores o expresiones que no se pueden evaluar en tiempo de compilación requieren que se ejecute código durante la inicialización del módulo.

El código siguiente muestra ejemplos de inicializadores estáticos que requieren inicialización dinámica: una llamada a función, una construcción de objetos y una inicialización de puntero. (Estos ejemplos no son estáticos, pero se supone que se definen en el ámbito global, lo que tiene el mismo efecto).

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

Este riesgo de interbloqueo depende de si el módulo contenedor se compila con **/clr** y de si se ejecutará MSIL. En concreto, si la variable estática se compila sin **/clr** (o si reside en un bloque #pragma `unmanaged` ) y el inicializador dinámico requerido para inicializarla provoca la ejecución de instrucciones MSIL, se puede producir el interbloqueo. Esto se debe a que, en el caso de los módulos compilados sin **/clr**, la inicialización de variables estáticas se lleva a cabo mediante DllMain. En cambio, las variables estáticas compiladas con **/clr** se inicializan mediante .cctor, una vez que se ha completado la fase de inicialización no administrada y se ha liberado el bloqueo del cargador.

Hay una serie de soluciones para el interbloqueo causado por la inicialización dinámica de variables estáticas (ordenadas según el tiempo necesario para corregir el problema):

- El archivo de código fuente que contiene la variable estática se puede compilar con **/clr**.

- Todas las funciones a las que llama la variable estática se pueden compilar en código nativo mediante la directiva #pragma `unmanaged` .

- Clone manualmente el código del que depende la variable estática. Para ello, proporcione una versión .NET y una versión nativa con nombres diferentes. Después, los desarrolladores podrán llamar a la versión nativa desde inicializadores estáticos nativos y llamar a la versión de .NET en otra parte.

### <a name="user-supplied-functions-affecting-startup"></a>Funciones proporcionadas por el usuario que afectan al inicio

Hay varias funciones proporcionadas por el usuario de las que dependen las bibliotecas para la inicialización durante el inicio. Por ejemplo, cuando todo el mundo, como la sobrecarga de operadores en C++ el `new` y `delete` operadores, las versiones proporcionadas por el usuario se utilizan en todas partes, incluidos en la inicialización de la biblioteca estándar de C++ y la destrucción. Como resultado, biblioteca estándar de C++ y los inicializadores estáticos proporcionados por el usuario invocarán cualquier versión proporcionada por el usuario de estos operadores.

Si las versiones proporcionadas por el usuario se compilan en MSIL, estos inicializadores tratarán de ejecutar instrucciones MSIL mientras se mantiene el bloqueo del cargador. Proporcionado por el usuario `malloc` tiene las mismas consecuencias. Para resolver este problema, estas sobrecargas o definiciones proporcionadas por el usuario deben implementarse como código nativo mediante la directiva #pragma `unmanaged` .

Para obtener más información sobre este escenario, vea "Impedimentos para la realización del diagnóstico".

### <a name="custom-locales"></a>Configuraciones regionales personalizadas

Si el usuario proporciona una configuración regional global personalizada, dicha configuración se usará para inicializar todas las transmisiones de E/S posteriores, incluidas las que se inicializan estáticamente. Si este objeto de configuración regional global se compila en MSIL, las funciones miembro de objeto de configuración regional compiladas en MSIL pueden invocarse mientras se mantiene el bloqueo del cargador.

Hay tres opciones para solucionar este problema:

Los archivos de código fuente que contienen todas las definiciones de transmisión de E/S globales se pueden compilar mediante la opción **/clr** . Esto evitará que sus inicializadores estáticos se ejecuten en un bloqueo del cargador.

Las definiciones de la función de configuración regional personalizada se pueden compilar en código nativo mediante la directiva #pragma `unmanaged` .

Evite establecer la configuración regional personalizada como configuración regional global hasta que se haya liberado el bloqueo del cargador. Después, configure explícitamente las transmisiones de E/S creadas durante la inicialización con la configuración regional personalizada.

## <a name="impediments-to-diagnosis"></a>Impedimentos para la realización del diagnóstico

En algunos casos es difícil detectar el origen de los interbloqueos. En las siguientes subsecciones se describen estos escenarios y las maneras de solucionar estos problemas.

### <a name="implementation-in-headers"></a>Implementación en encabezados

En determinados casos, las implementaciones de funciones en archivos de encabezado pueden complicar el diagnóstico. Las funciones insertadas y el código de plantilla requieren que las funciones se especifiquen en un archivo de encabezado.  El lenguaje C++ especifica la Regla de una definición, que obliga a que todas las implementaciones de funciones con el mismo nombre sean semánticamente equivalentes. Por lo tanto, no es necesario que el vinculador de C++ tenga en cuenta ninguna consideración especial al combinar archivos objeto que tengan implementaciones duplicadas de una función determinada.

Antes de Visual Studio 2005, el vinculador se limita a elegir el mayor de estas definiciones semánticamente equivalentes para dar cabida a escenarios y declaraciones adelantadas cuando se usan opciones de optimización diferentes para archivos de origen diferentes. Esto crea un problema en el caso de las DLL de .NET/nativas mixtas.

Dado que puede ser el mismo encabezado incluyen archivos de C++ con **/CLR** habilitados y deshabilitados, o un #include puede colocarse dentro de #pragma `unmanaged` bloque, es posible tener MSIL y las versiones nativas de funciones que proporcionan implementaciones en encabezados. Las implementaciones MSIL y nativas tienen semánticas diferentes con respecto a la inicialización en un bloqueo del cargador, lo que efectivamente infringe la Regla de una definición. Por lo tanto, cuando el vinculador elige la mayor implementación, puede elegir la versión MSIL de una función, aunque se haya compilado explícitamente en código nativo en otro lugar mediante la directiva #pragma unmanaged. Para asegurarse de que nunca se llame a una versión MSIL de una plantilla o función insertada en un bloqueo del cargador, todas las definiciones de cada función de ese tipo llamadas en un bloqueo del cargador deben modificarse con la directiva #pragma `unmanaged` . Si el archivo de encabezado es de terceros, la forma más sencilla de lograrlo es insertar y extraer la directiva #pragma unmanaged en torno a la directiva #include para el archivo de encabezado incorrecto. (Consulte [managed, unmanaged](../preprocessor/managed-unmanaged.md) para obtener un ejemplo.) En cambio, esta estrategia no funcionará para los encabezados que contengan otro código que deba llamar directamente a API de .NET.

Para la comodidad de los usuarios que se encuentran ante un bloqueo del cargador, el vinculador elegirá la implementación nativa frente a la administrada cuando se le presenten ambas. Esto evita los problemas mencionados anteriormente. Hay dos excepciones a esta regla en esta versión debido a dos problemas sin resolver del compilador:

- La llamada a una función insertada se realiza a través de un puntero de función estático global. Este escenario es especialmente importante, ya que las llamadas a funciones virtuales se realizan a través de punteros de función globales. Por ejemplo,

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

## <a name="how-to-debug-loader-lock-issues"></a>Cómo depurar los problemas del bloqueo del cargador

El diagnóstico que CLR genera cuando se invoca una función MSIL hace que CLR suspenda la ejecución. A su vez, esto hace que se suspenda el depurador de modo mixto de Visual C++, incluso cuando se ejecuta el depurado en proceso. En cambio, al asociarse al proceso, no es posible obtener una pila de llamadas administrada para el depurado mediante el depurador mixto.

Para identificar la función MSIL específica a la que se llamó en un bloqueo del cargador, los desarrolladores deben seguir los pasos siguientes:

1. Asegúrese de que hay símbolos disponibles para mscoree.dll y mscorwks.dll.

   Esto se puede llevar a cabo de dos maneras. En primer lugar, los archivos PDB para mscoree.dll y mscorwks.dll pueden agregarse a la ruta de acceso de búsqueda de símbolos. Para ello, abra el diálogo de opciones de la ruta de acceso de búsqueda de símbolos. (Desde el **herramientas** menú, elija **opciones**. En el panel izquierdo de la **opciones** cuadro de diálogo, abra el **depuración** nodo y elija **símbolos**.) Agregue a la lista de búsqueda la ruta de acceso a los archivos PDB mscoree.dll y mscorwks.dll. Estos archivos PDB se instalan en %VSINSTALLDIR%\SDK\v2.0\symbols. Elija **Aceptar**.

   En segundo lugar, los archivos PDB para mscoree.dll y mscorwks.dll pueden descargarse desde el Servidor de símbolos de Microsoft. Para configurar el Servidor de símbolos, abra el diálogo de opciones de la ruta de acceso de búsqueda de símbolos. (Desde el **herramientas** menú, elija **opciones**. En el panel izquierdo de la **opciones** cuadro de diálogo, abra el **depuración** nodo y elija **símbolos**.) Agregue la siguiente ruta de acceso de búsqueda a la lista de búsqueda: http://msdl.microsoft.com/download/symbols. Agregue un directorio de caché de símbolos al cuadro de texto de caché del servidor de símbolos. Elija **Aceptar**.

1. Establezca el modo del depurador en modo solo nativo.

   Para ello, abra el **propiedades** cuadrícula para el proyecto de inicio de la solución. Seleccione **propiedades de configuración** > **depuración**. Establecer el **el tipo de depurador** a **sólo nativo**.

1. Inicie al depurador (F5).

1. Cuando el **/CLR** se genera el diagnóstico, elija **vuelva a intentar** y, a continuación, elija **interrumpir**.

1. Abra la ventana Pila de llamadas. (En la barra de menús, elija **depurar** > **Windows** > **pila de llamadas**.) Los infractores `DllMain` o inicializador estático se identifica con una flecha verde. Si no se identifica la función incorrecta, deben llevarse a cabo los pasos siguientes para encontrarla.

1. Abra el **inmediato** ventana (en la barra de menús, elija **depurar** > **Windows** > **inmediato**.)

1. Escriba .load sos.dll en el **inmediato** ventana para cargar el servicio de depuración de SOS.

1. Escriba! dumpstack en la **inmediato** ventana para obtener una lista completa de interno **/CLR** pila.

1. Busque la primera instancia (cerca de la parte inferior de la pila) de _CorDllMain (si `DllMain` hace que el problema) o _VTableBootstrapThunkInitHelperStub o GetTargetForVTableEntry (si un inicializador estático causa el problema). La entrada de la pila justo debajo de esta llamada es la invocación de la función implementada por MSIL que intentó ejecutarse en el bloqueo del cargador.

1. Vaya al archivo de origen y la línea número identificado en el paso anterior y corrija el problema con los escenarios y soluciones que se describe en la sección de escenarios.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

El ejemplo siguiente muestra cómo evitar el bloqueo del cargador pasando código de `DllMain` al constructor de un objeto global.

En este ejemplo, hay un objeto administrado global cuyo constructor contiene el objeto administrado que estaba originalmente en `DllMain`. La segunda parte de este ejemplo hace referencia al ensamblado. Para ello, crea una instancia del objeto administrado para invocar el constructor del módulo que realiza la inicialización.

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

En este ejemplo se muestra a los problemas de inicialización de ensamblados mixtos:

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

## <a name="see-also"></a>Vea también

[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)
