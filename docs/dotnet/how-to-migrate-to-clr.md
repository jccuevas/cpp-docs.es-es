---
title: 'Cómo: migrar a - clr | Microsoft Docs'
ms.custom: get-started-article
ms.date: 09/18/2018
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- upgrading Visual C++ applications, /clr compiler option
- compiling native code [C++]
- interoperability [C++], /clr compiler option
- interop [C++], /clr compiler option
- migration [C++], /clr compiler option
- /clr compiler option [C++], porting to
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 210cf8d3183e9fcd94cfa51d875a0b26e4a8fa07
ms.sourcegitcommit: 92c568e9466ffd7346a4120c478c9bdea61c8756
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2018
ms.locfileid: "47029663"
---
# <a name="how-to-migrate-to-clr"></a>Cómo: Migrar a /clr

En este tema se trata los problemas que surgen al compilar el código nativo con **/CLR** (consulte [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md) para obtener más información). **/ CLR** permite que el código de C++ nativa invocar y se pueden invocar desde ensamblados de .NET además de otro código de C++ nativo. Consulte [ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md) y [nativo e interoperabilidad de .NET](../dotnet/native-and-dotnet-interoperability.md) para obtener más información sobre las ventajas de compilar con **/CLR**.

## <a name="known-issues-compiling-library-projects-with-clr"></a>Problemas conocidos al compilar proyectos de biblioteca con /clr

Visual Studio contiene algunos problemas conocidos al compilar proyectos de biblioteca con **/CLR**:

- El código puede consultar los tipos en tiempo de ejecución con [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md#fromname). Sin embargo, si un tipo está en un archivo .dll de MSIL (compilado con **/CLR**), la llamada a `FromName` puede producir un error si se produce antes de que los constructores estáticos se ejecuten en el archivo .dll administrado (no verá este problema si la llamada a FromName se produce una vez que tenga el código ejecutar en el archivo .dll administrado). Para solucionar este problema, puede forzar la creación del constructor estático administrado si define una función en el archivo .dll administrado, lo exporta y lo invoca desde la aplicación MFC nativa. Por ejemplo:

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>Compilar con Visual C++

Antes de usar **/CLR** en cualquier módulo del proyecto, compile y vincule primero el proyecto nativo con Visual Studio 2010.

Los pasos siguientes, realizados por orden, proporcionan la ruta de acceso más fácil para un **/CLR** compilación. Es importante compilar y ejecutar el proyecto después de cada uno de estos pasos.

### <a name="versions-prior-to-visual-c-2003"></a>Versiones anteriores a Visual C++ 2003

Si se actualiza a Visual Studio 2010 desde una versión anterior a Visual C++ 2003, puede que aparezcan errores de compilador relacionados con la conformidad con el estándar C++ mejorado en Visual C++ 2003.

### <a name="upgrading-from-visual-c-2003"></a>Actualizar desde Visual C++ 2003

Los proyectos compilados con Visual C++ 2003 anteriormente también primero se deben compilar sin **/CLR** como Visual Studio ahora tiene mayor compatibilidad con ANSI/ISO y algunos cambios importantes. El cambio que probablemente requiera más atención es [características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md). Es muy probable que el código que utiliza CRT genere advertencias sobre elementos desusados. Estas advertencias se pueden suprimir, pero la migración al nuevo [con seguridad mejorada versiones de las funciones CRT](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) es preferible, ya que proporcionan una mejor seguridad y pueden revelar problemas de seguridad en el código.

### <a name="upgrading-from-managed-extensions-for-c"></a>Actualizar desde Extensiones administradas para C++

A partir de Visual Studio 2005, el código escrito con extensiones administradas para C++ no se compilará bajo **/CLR**.

## <a name="convert-c-code-to-c"></a>Convertir código de C en código de C++

Aunque Visual Studio compilará los archivos de C, es necesario convertirlos a C++ para un **/CLR** compilación. El nombre de archivo real no tiene que cambiarse; Puede usar **/Tp** (consulte [/TC, / TP, / TC, /TP (Especificar tipo de archivo de origen)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md).) Tenga en cuenta que aunque se requieren para archivos de código fuente de C++ **/CLR**, no es necesario refactorizar el código para utilizar paradigmas orientados a objetos.

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

Se debe cambiar el nombre de los identificadores utilizados en el código de C que resulten ser palabras clave en C++ (como `virtual`, `new`, `delete`, `bool`, `true`, `false`, etc.). Esto generalmente se puede hacer con operaciones simples de búsqueda y sustitución.

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>Redefinir la configuración del proyecto

Después de que el proyecto se compila y ejecuta en Visual Studio 2010 debe crear nuevas configuraciones de proyecto para **/CLR** en lugar de modificar las configuraciones predeterminadas. **/ CLR** es incompatible con algunas opciones del compilador y la creación de configuraciones independientes le permite compilar el proyecto como nativo o administrado. Cuando **/CLR** está seleccionado en el cuadro de diálogo páginas de propiedades, la configuración del proyecto no es compatible con **/CLR** están deshabilitadas (y las opciones deshabilitadas no se restauran automáticamente si   **/CLR** se desactiva posteriormente).

### <a name="create-new-project-configurations"></a>Crear nuevas configuraciones de proyecto

Puede usar **Copiar configuración de** opción el **nuevo cuadro de diálogo de configuración de proyecto** (**compilar** > **deConfigurationManager**  >  **Configuración de soluciones activas** > **New**) para crear una configuración de proyecto basada en la configuración del proyecto existente. Haga esto una vez para la configuración de depuración y una vez para la configuración Release. A continuación, se pueden aplicar los cambios posteriores a la **/CLR** -configuraciones específicas, dejando intactas las configuraciones del proyecto original.

Los proyectos que usan reglas de compilación personalizadas pueden requerir más atención.

Este paso tiene implicaciones diferentes para los proyectos que utilizan archivos Make. En este caso se puede configurar un destino de compilación independiente o específica de la versión **/CLR** compilación puede crearse desde una copia del original.

### <a name="change-project-settings"></a>Cambiar la configuración del proyecto

**/ CLR** se pueden seleccionar en el entorno de desarrollo siguiendo las instrucciones de [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md). Como se mencionó previamente, este paso deshabilitará automáticamente los parámetros de configuración del proyecto en conflicto.

> [!NOTE]
>  Al actualizar una biblioteca administrada o un proyecto de servicio web desde Visual C++ 2003, el **/Zl** se de opción del compilador agregado a la **línea de comandos** página de propiedades. Esto produce el error LNK2001. Quitar **/Zl** desde el **línea de comandos** página de propiedades para resolver. Consulte [/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md) y [trabajar con las propiedades del proyecto](../ide/working-with-project-properties.md) para obtener más información. O bien, agregue msvcrt.lib y msvcmrt.lib al vinculador **dependencias adicionales** propiedad.

Para los proyectos generados con archivos MAKE, las opciones del compilador incompatible se deben deshabilitar manualmente una vez **/CLR** se agrega. Ver /[restricciones de /clr](../build/reference/clr-restrictions.md) para obtener información sobre las opciones del compilador que no son compatibles con **/CLR**.

### <a name="precompiled-headers"></a>Encabezados precompilados

Se admiten encabezados precompilados en **/CLR**. Sin embargo, si solo compila algunos de los archivos CPP con **/CLR** (y compila el resto como nativos) algunos cambios será necesarios porque los encabezados precompilados generados con **/CLR** no son compatibles con los genera sin **/CLR**. Esta incompatibilidad es debido al hecho de que **/CLR** genera y requiere metadatos. Módulos compilados **/CLR** , por tanto, no puede utilizar encabezados precompilados que no incluyan metadatos y no **/CLR** módulos no pueden usar archivos de encabezado precompilados que contengan metadatos.

La manera más fácil de compilar un proyecto donde algunos módulos se compilan **/CLR** consiste en deshabilitar completamente los encabezados precompilados. (En el cuadro de diálogo Páginas de propiedades del proyecto, abra el nodo C/C++ y seleccione Encabezados precompilados. A continuación, cambie la propiedad Crear/Utilizar encabezado precompilado a "No utilizar encabezados precompilados").

Sin embargo, particularmente para los proyectos grandes, los encabezados precompilados proporcionan una velocidad de compilación mucho mayor, de modo que no es deseable deshabilitar esta característica. En este caso es mejor configurar el **/CLR** y no **/CLR** archivos para utilizar encabezados precompilados independientes. Esto puede hacerse en un solo paso mediante la selección múltiple los módulos que se compilarán **/CLR** mediante el Explorador de soluciones, con el botón secundario en el grupo y seleccione Propiedades. A continuación, cambie las propiedades Crear o utilizar encabezado precompilado a través de archivo y Archivo de encabezado precompilado para utilizar un nombre de archivo de encabezado y un archivo PCH diferentes, respectivamente.

## <a name="fixing-errors"></a>Corregir errores

Compilar con **/CLR** puede dar lugar a errores del compilador, vinculador o tiempo de ejecución. En esta sección se describen los problemas más comunes.

### <a name="metadata-merge"></a>Combinación de metadatos

Las distintas versiones de los tipos de datos pueden hacer que el vinculador produzca un error debido a que los metadatos generados para los dos tipos no coinciden. (Esto ocurre normalmente cuando los miembros de un tipo se definen condicionalmente, pero las condiciones no son las mismas para todos los archivos CPP que usan dicho tipo). En este caso, el vinculador produce un error y solo notifica el nombre de símbolo y el nombre del segundo archivo OBJ en el que se definió el tipo. A menudo resulta útil invertir el orden en que se envían los archivos OBJ al vinculador para detectar la ubicación de la otra versión del tipo de datos.

### <a name="loader-lock-deadlock"></a>Interbloqueo de bloqueo del cargador

El "interbloqueo de bloqueo del cargador" pueden aparecer, pero es determinista y se detecta y se notifica en tiempo de ejecución. Consulte [inicialización de ensamblados mixtos](../dotnet/initialization-of-mixed-assemblies.md) para información detallada, orientación y soluciones.

### <a name="data-exports"></a>Exportaciones de datos

La exportación de datos DLL es propensa a errores y no se recomienda. Esto se debe a que no se garantiza que se inicialice la sección de datos de una DLL hasta que se haya ejecutado alguna parte administrada de la DLL. Los metadatos de referencia con [#using](../preprocessor/hash-using-directive-cpp.md).

### <a name="type-visibility"></a>Visibilidad de tipos

Tipos nativos son privados de forma predeterminada. Esto puede producir un tipo nativo que no sea visible fuera de la DLL. Para resolver este error, agregue `public` a estos tipos.

### <a name="floating-point-and-alignment-issues"></a>Problemas de punto flotante y alineación

`__controlfp` no es compatible con common language runtime (vea [_control87, _controlfp, \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) para obtener más información). CLR tampoco respetará [alinear](../cpp/align-cpp.md).

### <a name="com-initialization"></a>Inicialización COM

Common Language Runtime inicializa COM automáticamente cuando se inicializa un módulo (cuando se inicializa COM automáticamente, se hace en forma de MTA). Como resultado, la inicialización explícita de COM produce códigos devueltos que indican que COM ya se ha inicializado. El intento de inicializar COM explícitamente con un modelo de subprocesos cuando CLR ya ha inicializado COM en otro modelo de subprocesos puede hacer que la aplicación no funcione correctamente.

Common language runtime inicia COM de MTA de forma predeterminada; usar [/CLRTHREADATTRIBUTE (Establecer atributo de subproceso de CLR)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) para modificar este comportamiento.

### <a name="performance-issues"></a>Problemas de rendimiento

Puede que disminuya el rendimiento si los métodos de C++ nativos generados para MSIL se llaman indirectamente (llamadas a funciones virtuales o uso de punteros de función). Para obtener más información sobre esto, vea [doble thunk](../dotnet/double-thunking-cpp.md).

Al pasar de código nativo a código MSIL, observará un aumento en el tamaño del espacio de trabajo. Esto se debe a que Common Language Runtime proporciona muchas características para garantizar que los programas se ejecuten correctamente. Si su **/CLR** aplicación no se ejecuta correctamente, puede habilitar C4793 (desactivado de forma predeterminada), consulte [advertencia del compilador (nivel 1 y 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) para obtener más información.

### <a name="program-crashes-on-shutdown"></a>El programa se bloquea o se cierra

En algunos casos, CLR puede cerrarse antes de que el código administrado termine de ejecutarse. El uso de `std::set_terminate` y `SIGTERM` puede producir esto. Consulte [signal (constantes)](../c-runtime-library/signal-constants.md) y [set_terminate](../c-runtime-library/abnormal-termination.md) para obtener más información.

## <a name="using-new-visual-c-features"></a>Utilizar las nuevas características de Visual C++

Después de la aplicación compila, vínculos y se ejecuta, puede empezar a usar las características de .NET en cualquier módulo compilado con **/CLR**. Para obtener más información, vea [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md).

Si utilizó las Extensiones administradas para C++, puede convertir el código para usar la nueva sintaxis. Para obtener más información sobre la conversión de extensiones administradas para C++, vea [C++ / c++ / CLI Migration Primer](../dotnet/cpp-cli-migration-primer.md).

Para obtener información sobre la programación de .NET en Visual C++, vea:

- [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)

- [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>Vea también

[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)
