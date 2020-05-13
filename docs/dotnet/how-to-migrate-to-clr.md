---
title: 'Cómo: Migrar a -clr'
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
ms.openlocfilehash: 339b1f3172d8b82ece3e98f117f53ed399cbd4e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376079"
---
# <a name="how-to-migrate-to-clr"></a>Cómo: Migrar a /clr

En este tema se describen los problemas que surgen al compilar código nativo con **/clr** (vea [/clr (compilación](../build/reference/clr-common-language-runtime-compilation.md) de Common Language Runtime) para obtener más información). **/clr** permite que el código C++ nativo se invoque y se invoque desde ensamblados de .NET además de otro código C++ nativo. Consulte [Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md) e [Interoperabilidad nativa y .NET](../dotnet/native-and-dotnet-interoperability.md) para obtener más información sobre las ventajas de compilar con **/clr**.

## <a name="known-issues-compiling-library-projects-with-clr"></a>Problemas conocidos al compilar proyectos de biblioteca con /clr

Visual Studio contiene algunos problemas conocidos al compilar proyectos de biblioteca con **/clr:**

- El código puede consultar tipos en tiempo de ejecución con [CRuntimeClass::FromName](../mfc/reference/cruntimeclass-structure.md#fromname). Sin embargo, si un tipo está en un archivo .dll `FromName` de MSIL (compilado con **/clr**), la llamada puede producir un error si se produce antes de que los constructores estáticos se ejecuten en el archivo .dll administrado (no verá este problema si la llamada FromName se produce después de que se haya ejecutado el código en el archivo .dll administrado). Para solucionar este problema, puede forzar la creación del constructor estático administrado si define una función en el archivo .dll administrado, lo exporta y lo invoca desde la aplicación MFC nativa. Por ejemplo:

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>Compilar con Visual C++

Antes de usar **/clr** en cualquier módulo del proyecto, primero compile y vincule el proyecto nativo con Visual Studio 2010.

Los pasos siguientes, seguidos en orden, proporcionan la ruta de acceso más fácil a una compilación **/clr.** Es importante compilar y ejecutar el proyecto después de cada uno de estos pasos.

### <a name="versions-prior-to-visual-studio-2003"></a>Versiones anteriores a Visual Studio 2003

Si va a actualizar a Visual Studio 2010 desde una versión anterior a Visual Studio 2003, es posible que vea errores del compilador relacionados con la conformidad estándar mejorada de C++ en Visual Studio 2003

### <a name="upgrading-from-visual-studio-2003"></a>Actualización desde Visual Studio 2003

Los proyectos compilados anteriormente con Visual Studio 2003 también deben compilarse primero sin **/clr,** ya que Visual Studio ahora ha aumentado el cumplimiento de ANSI/ISO y algunos cambios importantes. El cambio que es probable que requiera la mayor atención es las características de [seguridad en el CRT.](../c-runtime-library/security-features-in-the-crt.md) Es muy probable que el código que utiliza CRT genere advertencias sobre elementos desusados. Estas advertencias se pueden suprimir, pero se prefiere migrar a las nuevas [versiones de seguridad mejorada de funciones de CRT,](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) ya que proporcionan una mejor seguridad y pueden revelar problemas de seguridad en el código.

### <a name="upgrading-from-managed-extensions-for-c"></a>Actualizar desde Extensiones administradas para C++

A partir de Visual Studio 2005, el código escrito con Extensiones administradas para C++ no se compilará en **/clr**.

## <a name="convert-c-code-to-c"></a>Convertir código de C en código de C++

Aunque Visual Studio compilará archivos C, es necesario convertirlos a C++ para una compilación **/clr.** No es posible cambiar el nombre de archivo real; puede utilizar **/Tp** (consulte [/Tc, /Tp, /TC, /TP (Especificar tipo](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)de archivo de origen) .) Tenga en cuenta que aunque los archivos de código fuente de C++ son necesarios para **/clr**, no es necesario volver a factorizar el código para usar paradigmas orientados a objetos.

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

Los identificadores utilizados en el código C que resultan ser palabras clave en C+ (como **virtual**, **new**, **delete**, **bool**, **true**, **false**, etc.) deben cambiarse de nombre. Esto generalmente se puede hacer con operaciones simples de búsqueda y sustitución.

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>Redefinir la configuración del proyecto

Después de compilar y ejecutar el proyecto en Visual Studio 2010, debe crear nuevas configuraciones de proyecto para **/clr** en lugar de modificar las configuraciones predeterminadas. **/clr** es incompatible con algunas opciones del compilador y la creación de configuraciones independientes le permite compilar el proyecto como nativo o administrado. Cuando se selecciona **/clr** en el cuadro de diálogo de páginas de propiedades, la configuración del proyecto no es compatible con **/clr** se deshabilita (y las opciones deshabilitadas no se restauran automáticamente si **/clr** no está seleccionado posteriormente).

### <a name="create-new-project-configurations"></a>Crear nuevas configuraciones de proyecto

Puede usar la opción **Copiar configuración de** en el cuadro de diálogo Nueva configuración del **proyecto** **(Configuración** > de la**solución** > activa del**Administrador** > de configuración de compilación**nuevo**) para crear una configuración de proyecto basada en la configuración del proyecto existente. Haga esto una vez para la configuración de depuración y una vez para la configuración Release. Los cambios posteriores solo se pueden aplicar a las configuraciones específicas de **/clr,** dejando intactas las configuraciones del proyecto original.

Los proyectos que usan reglas de compilación personalizadas pueden requerir más atención.

Este paso tiene implicaciones diferentes para los proyectos que utilizan archivos Make. En este caso, se puede configurar un destino de compilación independiente o se puede crear una versión específica de la compilación **/clr** a partir de una copia del original.

### <a name="change-project-settings"></a>Cambiar la configuración del proyecto

**/clr** se puede seleccionar en el entorno de desarrollo siguiendo las instrucciones [de /clr (Compilación](../build/reference/clr-common-language-runtime-compilation.md)de Common Language Runtime) . Como se mencionó previamente, este paso deshabilitará automáticamente los parámetros de configuración del proyecto en conflicto.

> [!NOTE]
> Al actualizar una biblioteca administrada o un proyecto de servicio web desde Visual Studio 2003, la opción del compilador **/Zl** se agregará a la página de propiedades línea de **comandos.** Esto produce el error LNK2001. Quite **/Zl** de la página de propiedades Línea de **comandos** para resolver. Consulte [/Zl (Omitir nombre](../build/reference/zl-omit-default-library-name.md) de biblioteca predeterminado) y [Establecer propiedades del compilador y compilación](../build/working-with-project-properties.md) para obtener más información. O bien, agregue msvcrt.lib y msvcmrt.lib a la propiedad **Dependencias adicionales** del vinculador.

Para los proyectos compilados con makefiles, las opciones del compilador incompatibles deben deshabilitarse manualmente una vez que se agrega **/clr.** Consulte[/ /clr Restricciones](../build/reference/clr-restrictions.md) para obtener información sobre las opciones del compilador que no son compatibles con **/clr**.

### <a name="precompiled-headers"></a>Encabezados precompilados

Los encabezados precompilados se admiten en **/clr**. Sin embargo, si solo compila algunos de los archivos CPP con **/clr** (compilar el resto como nativo) se necesitarán algunos cambios porque los encabezados precompilados generados con **/clr** no son compatibles con los generados sin **/clr**. Esta incompatibilidad se debe al hecho de que **/clr** genera y requiere metadatos. Por lo tanto, los módulos compilados **/clr** no pueden usar encabezados precompilados que no incluyan metadatos y los módulos no **/clr** no pueden usar archivos de encabezado precompilados que contengan metadatos.

La forma más fácil de compilar un proyecto donde se compilan algunos módulos **/clr** es deshabilitar los encabezados precompilados por completo. (En el cuadro de diálogo Páginas de propiedades del proyecto, abra el nodo C/C++ y seleccione Encabezados precompilados. A continuación, cambie la propiedad Crear/Utilizar encabezado precompilado a "No utilizar encabezados precompilados").

Sin embargo, particularmente para los proyectos grandes, los encabezados precompilados proporcionan una velocidad de compilación mucho mayor, de modo que no es deseable deshabilitar esta característica. En este caso, es mejor configurar los archivos **/clr** y non **/clr** para usar encabezados precompilados independientes. Esto se puede hacer en un paso seleccionando varios los módulos que se van a compilar **/clr** mediante el **Explorador**de soluciones , haciendo clic con el botón derecho en el grupo y seleccionando Propiedades. A continuación, cambie las propiedades Crear o utilizar encabezado precompilado a través de archivo y Archivo de encabezado precompilado para utilizar un nombre de archivo de encabezado y un archivo PCH diferentes, respectivamente.

## <a name="fixing-errors"></a>Corregir errores

La compilación con **/clr** puede dar lugar a errores del compilador, del vinculador o del tiempo de ejecución. En esta sección se describen los problemas más comunes.

### <a name="metadata-merge"></a>Fusión mediante combinación de metadatos

Las distintas versiones de los tipos de datos pueden hacer que el vinculador produzca un error debido a que los metadatos generados para los dos tipos no coinciden. (Esto suele producirse cuando los miembros de un tipo se definen condicionalmente, pero las condiciones no son las mismas para todos los archivos CPP que utilizan el tipo.) En este caso, el vinculador falla, notificando solo el nombre del símbolo y el nombre del segundo archivo OBJ donde se definió el tipo. A menudo resulta útil invertir el orden en que se envían los archivos OBJ al vinculador para detectar la ubicación de la otra versión del tipo de datos.

### <a name="loader-lock-deadlock"></a>Interbloqueo de bloqueo del cargador

El "interbloqueo de bloqueo del cargador" puede producirse, pero es determinista y se detecta y notifica en tiempo de ejecución. Consulte [Inicialización de ensamblados mixtos](../dotnet/initialization-of-mixed-assemblies.md) para obtener información detallada sobre fondo, orientación y soluciones.

### <a name="data-exports"></a>Exportaciones de datos

La exportación de datos DLL es propensa a errores y no se recomienda. Esto se debe a que no se garantiza que se inicialice la sección de datos de una DLL hasta que se haya ejecutado alguna parte administrada de la DLL. Metadatos de referencia con [#using Directiva](../preprocessor/hash-using-directive-cpp.md).

### <a name="type-visibility"></a>Visibilidad de tipos

Los tipos nativos son privados de forma predeterminada. Esto puede producir un tipo nativo que no sea visible fuera de la DLL. Para resolver este error, agregue `public` a estos tipos.

### <a name="floating-point-and-alignment-issues"></a>Problemas de punto flotante y alineación

`__controlfp`no se admite en Common Language Runtime (consulte [_control87, _controlfp _control87_2 \_](../c-runtime-library/reference/control87-controlfp-control87-2.md) para obtener más información). El CLR tampoco respetará [la alineación](../cpp/align-cpp.md).

### <a name="com-initialization"></a>Inicialización COM

Common Language Runtime inicializa COM automáticamente cuando se inicializa un módulo (cuando se inicializa COM automáticamente, se hace en forma de MTA). Como resultado, la inicialización explícita de COM produce códigos devueltos que indican que COM ya se ha inicializado. El intento de inicializar COM explícitamente con un modelo de subprocesos cuando CLR ya ha inicializado COM en otro modelo de subprocesos puede hacer que la aplicación no funcione correctamente.

Common Language Runtime inicia COM como MTA de forma predeterminada; use [/CLRTHREADATTRIBUTE (Set CLR Thread Attribute)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) para modificarlo.

### <a name="performance-issues"></a>Problemas de rendimiento

Puede que disminuya el rendimiento si los métodos de C++ nativos generados para MSIL se llaman indirectamente (llamadas a funciones virtuales o uso de punteros de función). Para obtener más información sobre esto, consulte [Double Thunking](../dotnet/double-thunking-cpp.md).

Al pasar de código nativo a código MSIL, observará un aumento en el tamaño del espacio de trabajo. Esto se debe a que Common Language Runtime proporciona muchas características para garantizar que los programas se ejecuten correctamente. Si la aplicación **/clr** no se está ejecutando correctamente, es posible que desee habilitar C4793 (desactivado de forma predeterminada), consulte [Advertencia del compilador (nivel 1 y 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) para obtener más información.

### <a name="program-crashes-on-shutdown"></a>El programa se bloquea o se cierra

En algunos casos, CLR puede cerrarse antes de que el código administrado termine de ejecutarse. El uso de `std::set_terminate` y `SIGTERM` puede producir esto. Consulte [constantes](../c-runtime-library/signal-constants.md) y [set_terminate](../c-runtime-library/abnormal-termination.md) de señal para obtener más información.

## <a name="using-new-visual-c-features"></a>Utilizar las nuevas características de Visual C++

Después de compilar, vínculos y ejecuciones de la aplicación, puede empezar a usar características de .NET en cualquier módulo compilado con **/clr**. Para obtener más información, vea [Extensiones de componentes para plataformas de tiempo de ejecución](../extensions/component-extensions-for-runtime-platforms.md).

Para obtener información sobre la programación de .NET en Visual C++, vea:

- [Programación de .NET con C+/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)

- [Extensiones de componentes para plataformas de tiempo de ejecución](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>Consulte también

[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)
