---
title: 'Cómo: migrar a-CLR'
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- upgrading Visual C++ applications, /clr compiler option
- compiling native code [C++]
- interoperability [C++], /clr compiler option
- interop [C++], /clr compiler option
- migration [C++], /clr compiler option
- /clr compiler option [C++], porting to
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
ms.openlocfilehash: 337dc69b60537fba8484837981fc6be0971c69cb
ms.sourcegitcommit: 40ffe764244784c715b086c79626ac390b855d47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2019
ms.locfileid: "79544487"
---
# <a name="how-to-migrate-to-clr"></a>Cómo: Migrar a /clr

En este tema se describen los problemas que surgen al compilar código nativo con **/CLR** (consulte [/CLR (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) para obtener más información). **/CLR** permite invocar código nativo C++ y llamarlo desde ensamblados .net además de otro código nativo C++ . Vea [ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md) y la [interoperabilidad nativa y de .net](../dotnet/native-and-dotnet-interoperability.md) para obtener más información sobre las ventajas de la compilación con **/CLR**.

## <a name="known-issues-compiling-library-projects-with-clr"></a>Problemas conocidos al compilar proyectos de biblioteca con /clr

Visual Studio contiene algunos problemas conocidos al compilar proyectos de biblioteca con **/CLR**:

- El código puede consultar tipos en tiempo de ejecución con [CRuntimeClass:: FromName](../mfc/reference/cruntimeclass-structure.md#fromname). Sin embargo, si un tipo está en un archivo MSIL. dll (compilado con **/CLR**), la llamada a `FromName` puede producir un error si se produce antes de que los constructores estáticos se ejecuten en el archivo. dll administrado (no verá este problema si la llamada de FromName tiene lugar después de que se haya ejecutado el código en el archivo. dll administrado). Para solucionar este problema, puede forzar la creación del constructor estático administrado si define una función en el archivo .dll administrado, lo exporta y lo invoca desde la aplicación MFC nativa. Por ejemplo:

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>Compilar con Visual C++

Antes de usar **/CLR** en cualquier módulo del proyecto, primero compile y vincule el proyecto nativo con Visual Studio 2010.

Los pasos siguientes, seguidos en orden, proporcionan la ruta más sencilla a una compilación de **/CLR** . Es importante compilar y ejecutar el proyecto después de cada uno de estos pasos.

### <a name="versions-prior-to-visual-studio-2003"></a>Versiones anteriores a Visual Studio 2003

Si va a actualizar a Visual Studio 2010 desde una versión anterior a Visual Studio 2003, es posible que vea errores de compilador relacionados C++ con la compatibilidad mejorada estándar en visual Studio 2003

### <a name="upgrading-from-visual-studio-2003"></a>Actualizar desde Visual Studio 2003

Los proyectos previamente compilados con Visual Studio 2003 también deben compilarse primero sin **/CLR** , ya que Visual Studio ahora tiene mayor compatibilidad con ANSI/ISO y algunos cambios importantes. El cambio que es probable que requiera la mayor atención a las [características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md). Es muy probable que el código que utiliza CRT genere advertencias sobre elementos desusados. Estas advertencias se pueden suprimir, pero es preferible migrar a las nuevas [versiones de funciones de CRT con seguridad mejorada](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) , ya que proporcionan una mejor seguridad y pueden revelar problemas de seguridad en el código.

### <a name="upgrading-from-managed-extensions-for-c"></a>Actualizar desde Extensiones administradas para C++

A partir de Visual Studio 2005, el código escrito con extensiones C++ administradas para no se compilará en **/CLR**.

## <a name="convert-c-code-to-c"></a>Convertir código de C en código de C++

Aunque Visual Studio compilará archivos de C, es necesario convertirlos en C++ para una compilación de **/CLR** . No es necesario cambiar el nombre de archivo real; puede usar **/TP** (vea [/TC,/TP,/TC,/TP (especificar el tipo de archivo de origen))](../build/reference/tc-tp-tc-tp-specify-source-file-type.md). Tenga en cuenta C++ que, aunque se requieren archivos de código fuente para **/CLR**, no es necesario volver a factorizar el código para utilizar paradigmas orientados a objetos.

Es muy probable que el código de C requiera cambios cuando se compile como un archivo de C++. Las reglas de seguridad de tipos de C++ son estrictas, por lo que las conversiones de tipos se deben realizar de forma explícita. Por ejemplo, malloc devuelve un puntero nulo, pero se puede asignar a un puntero de cualquier tipo de C con una conversión:

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

Los punteros a función también presentan una seguridad de tipos estricta en C++, por lo que el siguiente código de C requiere alguna modificación. En C++, es mejor crear un especificador `typedef` que defina el tipo de puntero a función y, a continuación, utilizar dicho tipo para convertir los punteros de función:

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

C++ también requiere que se creen prototipos de las funciones o se definan totalmente para que se pueda hacer referencia a ellas o se puedan invocar.

Se debe cambiar el nombre de los identificadores utilizados en código C++ de C que se van a incluir palabras clave en (como **virtual**, **New**, **Delete**, **bool**, **true**, **false**, etc.). Esto generalmente se puede hacer con operaciones simples de búsqueda y sustitución.

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>Redefinir la configuración del proyecto

Después de que el proyecto se compila y se ejecuta en Visual Studio 2010, debe crear nuevas configuraciones de proyecto para **/CLR** en lugar de modificar las configuraciones predeterminadas. **/CLR** es incompatible con algunas opciones del compilador y la creación de configuraciones independientes le permite compilar el proyecto como nativo o administrado. Cuando se selecciona **/CLR** en el cuadro de diálogo páginas de propiedades, se deshabilitan los valores de configuración del proyecto que no son compatibles con **/CLR** (y las opciones deshabilitadas no se restauran automáticamente si se anula la selección de **/CLR** posteriormente).

### <a name="create-new-project-configurations"></a>Crear nuevas configuraciones de proyecto

Puede usar la opción **copiar configuración de** en el **cuadro de diálogo Nueva configuración del proyecto** (**compilación** > **Configuration Manager** > **configuración de soluciones activas** > **nuevo**) para crear una configuración de proyecto basada en la configuración del proyecto existente. Haga esto una vez para la configuración de depuración y una vez para la configuración Release. Los cambios subsiguientes se pueden aplicar solo a las configuraciones específicas de **/CLR** , lo que deja intactas las configuraciones de proyecto originales.

Los proyectos que usan reglas de compilación personalizadas pueden requerir más atención.

Este paso tiene implicaciones diferentes para los proyectos que utilizan archivos Make. En este caso, se puede configurar un destino de compilación independiente o se puede crear una versión específica de la compilación **/CLR** a partir de una copia del original.

### <a name="change-project-settings"></a>Cambiar la configuración del proyecto

se puede seleccionar **/CLR** en el entorno de desarrollo siguiendo las instrucciones de [/CLR (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md). Como se mencionó previamente, este paso deshabilitará automáticamente los parámetros de configuración del proyecto en conflicto.

> [!NOTE]
>  Al actualizar un proyecto de biblioteca o servicio web administrado desde Visual Studio 2003, la opción del compilador **/ZL** se agregará a la página de propiedades **línea de comandos** . Esto produce el error LNK2001. Quite **/ZL** de la página de propiedades **línea de comandos** para resolverlo. Vea [/ZL (omitir nombre de biblioteca predeterminada)](../build/reference/zl-omit-default-library-name.md) y [establezca las propiedades del compilador y compilación](../build/working-with-project-properties.md) para obtener más información. O bien, agregue msvcrt. lib y msvcmrt. lib a la propiedad **dependencias adicionales** del enlazador.

En el caso de los proyectos compilados con archivos make, las opciones del compilador incompatibles deben deshabilitarse manualmente una vez que se agregue **/CLR** . Vea/[/CLR Restrictions](../build/reference/clr-restrictions.md) para obtener información sobre las opciones del compilador que no son compatibles con **/CLR**.

### <a name="precompiled-headers"></a>Encabezados precompilados

Los encabezados precompilados se admiten en **/CLR**. Sin embargo, si solo se compilan algunos de los archivos CPP con **/CLR** (compilando el Rest como nativo), se necesitarán algunos cambios porque los encabezados precompilados generados con **/CLR** no son compatibles con los generados sin **/CLR**. Esta incompatibilidad se debe al hecho de que **/CLR** genera y requiere metadatos. Los módulos compilados **/CLR** , por tanto, no pueden usar encabezados precompilados que no incluyen metadatos, y los módulos que no son de **/CLR** no pueden usar archivos de encabezado precompilados que contienen metadatos.

La manera más sencilla de compilar un proyecto en el que algunos módulos se compilan **/CLR** es deshabilitar completamente los encabezados precompilados. (En el cuadro de diálogo Páginas de propiedades del proyecto, abra el nodo C/C++ y seleccione Encabezados precompilados. A continuación, cambie la propiedad Crear/Utilizar encabezado precompilado a "No utilizar encabezados precompilados").

Sin embargo, particularmente para los proyectos grandes, los encabezados precompilados proporcionan una velocidad de compilación mucho mayor, de modo que no es deseable deshabilitar esta característica. En este caso, es mejor configurar los archivos **/CLR** y no **/CLR** para usar encabezados precompilados independientes. Esto puede realizarse en un solo paso mediante la selección múltiple de los módulos que se van a compilar **/CLR** mediante **Explorador de soluciones**, haciendo clic con el botón derecho en el grupo y seleccionando Propiedades. A continuación, cambie las propiedades Crear o utilizar encabezado precompilado a través de archivo y Archivo de encabezado precompilado para utilizar un nombre de archivo de encabezado y un archivo PCH diferentes, respectivamente.

## <a name="fixing-errors"></a>Corregir errores

La compilación con **/CLR** puede producir errores de compilador, vinculador o en tiempo de ejecución. En esta sección se describen los problemas más comunes.

### <a name="metadata-merge"></a>Fusión mediante combinación de metadatos

Las distintas versiones de los tipos de datos pueden hacer que el vinculador produzca un error debido a que los metadatos generados para los dos tipos no coinciden. (Esto suele ocurrir cuando los miembros de un tipo se definen condicionalmente, pero las condiciones no son las mismas para todos los archivos CPP que usan el tipo). En este caso, se produce un error en el vinculador, que solo informa del nombre del símbolo y el nombre del segundo archivo OBJ en el que se definió el tipo. A menudo resulta útil invertir el orden en que se envían los archivos OBJ al vinculador para detectar la ubicación de la otra versión del tipo de datos.

### <a name="loader-lock-deadlock"></a>Interbloqueo de bloqueo del cargador

Se puede producir el "interbloqueo de bloqueo del cargador", pero es determinista y se detecta y se registra en tiempo de ejecución. Vea [inicialización de ensamblados mixtos](../dotnet/initialization-of-mixed-assemblies.md) para obtener información detallada sobre el fondo, las instrucciones y las soluciones.

### <a name="data-exports"></a>Exportaciones de datos

La exportación de datos DLL es propensa a errores y no se recomienda. Esto se debe a que no se garantiza que se inicialice la sección de datos de una DLL hasta que se haya ejecutado alguna parte administrada de la DLL. Metadatos de referencia con [la directiva #using](../preprocessor/hash-using-directive-cpp.md).

### <a name="type-visibility"></a>Visibilidad de tipos

De forma predeterminada, los tipos nativos son privados. Esto puede producir un tipo nativo que no sea visible fuera de la DLL. Para resolver este error, agregue `public` a estos tipos.

### <a name="floating-point-and-alignment-issues"></a>Problemas de punto flotante y alineación

`__controlfp` no se admite en el Common Language Runtime (vea [_control87, _controlfp \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) para obtener más información). CLR tampoco respetará la [alineación](../cpp/align-cpp.md).

### <a name="com-initialization"></a>Inicialización COM

Common Language Runtime inicializa COM automáticamente cuando se inicializa un módulo (cuando se inicializa COM automáticamente, se hace en forma de MTA). Como resultado, la inicialización explícita de COM produce códigos devueltos que indican que COM ya se ha inicializado. El intento de inicializar COM explícitamente con un modelo de subprocesos cuando CLR ya ha inicializado COM en otro modelo de subprocesos puede hacer que la aplicación no funcione correctamente.

El Common Language Runtime inicia COM como MTA de forma predeterminada; Use [/CLRTHREADATTRIBUTE (establecer el atributo de subproceso de CLR)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) para modificarlo.

### <a name="performance-issues"></a>Problemas de rendimiento

Puede que disminuya el rendimiento si los métodos de C++ nativos generados para MSIL se llaman indirectamente (llamadas a funciones virtuales o uso de punteros de función). Para obtener más información al respecto, vea [double thunk](../dotnet/double-thunking-cpp.md).

Al pasar de código nativo a código MSIL, observará un aumento en el tamaño del espacio de trabajo. Esto se debe a que Common Language Runtime proporciona muchas características para garantizar que los programas se ejecuten correctamente. Si la aplicación **/CLR** no se ejecuta correctamente, puede habilitar C4793 (desactivado de forma predeterminada), vea [Advertencia del compilador (nivel 1 y 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) para obtener más información.

### <a name="program-crashes-on-shutdown"></a>El programa se bloquea o se cierra

En algunos casos, CLR puede cerrarse antes de que el código administrado termine de ejecutarse. El uso de `std::set_terminate` y `SIGTERM` puede producir esto. Consulte [constantes de señal](../c-runtime-library/signal-constants.md) y [set_terminate](../c-runtime-library/abnormal-termination.md) para obtener más información.

## <a name="using-new-visual-c-features"></a>Utilizar las nuevas características de Visual C++

Una vez que la aplicación se compila, se vincula y se ejecuta, puede empezar a usar las características de .NET en cualquier módulo compilado con **/CLR**. Para obtener más información, consulta [Component Extensions for Runtime Platforms](../extensions/component-extensions-for-runtime-platforms.md).

Para obtener información sobre la programación de .NET en Visual C++, vea:

- [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)

- [Extensiones de componentes para plataformas de tiempo de ejecución](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>Consulte también

[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)
