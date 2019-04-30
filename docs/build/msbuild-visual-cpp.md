---
title: MSBuild en la línea de comandos - C++
ms.date: 12/12/2018
f1_keywords:
- MSBuild
helpviewer_keywords:
- MSBuild
ms.assetid: 7a1be7ff-0312-4669-adf2-5f5bf507d560
ms.openlocfilehash: 565b1c47b4476fa7cb830e15b978b389f4344ee1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273318"
---
# <a name="msbuild-on-the-command-line---c"></a>MSBuild en la línea de comandos - C++

En general, se recomienda que use Visual Studio para establecer las propiedades del proyecto e invocar el sistema MSBuild. Sin embargo, puede usar el **MSBuild** herramienta directamente desde el símbolo del sistema. El proceso de compilación se controla mediante la información en un archivo de proyecto (.vcxproj) que puede crear y editar. El archivo de proyecto especifica opciones de compilación basadas en fases, condiciones y eventos de compilación. Además, puede especificar cero o más de línea de comandos *opciones* argumentos.

> **msbuild.exe** [ *project_file* ] [ *options* ]

Use la **/target** (o **/t**) y **/Property** (o **/p**) opciones de línea de comandos para invalidar los destinos y propiedades específicas Si se especifica en el archivo de proyecto.

Es una función esencial del archivo del proyecto especificar un *destino*, que es una operación determinada aplicada a su proyecto y las entradas y salidas que son necesarios para realizar esa operación. Un archivo de proyecto puede especificar uno o varios destinos, que pueden incluir un destino predeterminado.

Cada destino consta de una secuencia de uno o varios *tareas*. Cada tarea se representa mediante una clase de .NET Framework que contiene un comando ejecutable. Por ejemplo, el [CL (tarea)](/visualstudio/msbuild/cl-task) contiene el [cl.exe](reference/compiling-a-c-cpp-program.md) comando.

Un *parámetro de tarea* es una propiedad de la tarea de la clase y que normalmente representa una opción de línea de comandos del comando ejecutable. Por ejemplo, el `FavorSizeOrSpeed` parámetro de la `CL` tarea corresponde a la **/Os** y **/Ot** opciones del compilador.

Parámetros de tarea adicionales admiten la infraestructura de MSBuild. Por ejemplo, el `Sources` parámetro de tarea Especifica un conjunto de tareas que pueden usarse en otras tareas. Para obtener más información acerca de las tareas de MSBuild, vea [referencia de tareas](/visualstudio/msbuild/msbuild-task-reference).

Mayoría de las tareas requiere entradas y salidas, como cadena, numéricos o booleanos parámetros, las rutas de acceso y nombres de archivo. Por ejemplo, una entrada habitual es el nombre de un archivo de código fuente .cpp para compilar. Un parámetro de entrada importante es una cadena que especifica la configuración de compilación y plataforma, por ejemplo, "depurar\|Win32". Las entradas y salidas se especifican mediante uno o varios XML definido por el usuario `Item` elementos contenidos en un `ItemGroup` elemento.

También puede especificar un archivo de proyecto definido por el usuario *propiedades* y `ItemDefinitionGroup` *elementos*. Las propiedades y los elementos forman pares de nombre/valor que se pueden usar como variables en la compilación. El componente de nombre de un par define una *macro*, y el componente de valor declara el *el valor de macro*. Se tiene acceso a una macro de propiedad mediante el uso de $(*nombre*) notación y una macro de elemento que se accede mediante %(*nombre*) notación.

Otros elementos XML en un archivo de proyecto pueden probar las macros y, a continuación, condicionalmente establezca el valor de una macro o controlar la ejecución de la compilación. Los nombres de macro y cadenas literales se pueden concatenar para generar estructuras como un ruta de acceso y nombre de archivo. En la línea de comandos, el **/Property** opción establece o invalida una propiedad de proyecto. No se pueden hacer referencia a elementos en la línea de comandos.

El sistema MSBuild puede ejecutar condicionalmente un destino antes o después de otro destino. Además, el sistema puede crear un destino en función de si los archivos que usa el destino son más recientes que los archivos que emite.

Para obtener más información acerca de MSBuild, vea:

- [MSBuild](/visualstudio/msbuild/msbuild) conceptos de información general de MSBuild.

- [Referencia de MSBuild](/visualstudio/msbuild/msbuild-reference) hacen referencia a información sobre el sistema MSBuild.

- [Referencia de esquema de archivo de proyecto](/visualstudio/msbuild/msbuild-project-file-schema-reference) se enumeran los elementos de esquema XML de MSBuild, junto con sus atributos y elementos primarios y secundarios. Observe especialmente el [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild), [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild), [destino](/visualstudio/msbuild/target-element-msbuild), y [tarea](/visualstudio/msbuild/task-element-msbuild) elementos.

- [Referencia de línea de comandos](/visualstudio/msbuild/msbuild-command-line-reference) se describen los argumentos de línea de comandos y opciones que puede utilizar con msbuild.exe.

- [Referencia de tareas](/visualstudio/msbuild/msbuild-task-reference) las tareas de MSBuild describe. Tenga en cuenta especialmente estas tareas, que son específicas de Visual C++: [Tarea BscMake](/visualstudio/msbuild/bscmake-task), [CL (tarea)](/visualstudio/msbuild/cl-task), [CPPClean (tarea)](/visualstudio/msbuild/cppclean-task), [LIB (tarea)](/visualstudio/msbuild/lib-task), [Vincular tarea](/visualstudio/msbuild/link-task), [MIDL (tarea)](/visualstudio/msbuild/midl-task), [MT (tarea)](/visualstudio/msbuild/mt-task), [tarea RC](/visualstudio/msbuild/rc-task), [SetEnv (tarea)](/visualstudio/msbuild/setenv-task), [VCMessage (tarea)](/visualstudio/msbuild/vcmessage-task)

## <a name="in-this-section"></a>En esta sección

|Término|Definición|
|----------|----------------|
|[Tutorial: Uso de MSBuild para crear un proyecto de Visual C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|Muestra cómo crear un proyecto de Visual C++ mediante **MSBuild**.|
|[Cómo: Usar de eventos de compilación en proyectos de MSBuild](how-to-use-build-events-in-msbuild-projects.md)|Muestra cómo especificar una acción que se produce en una fase concreta de la compilación: antes de que empiece la compilación; antes de iniciar el paso de vínculo; o bien, una vez finalizada la compilación.|
|[Cómo: Agregar un paso personalizado de compilación a proyectos de MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)|Muestra cómo agregar una fase definido por el usuario a la secuencia de compilación.|
|[Cómo: Agregar herramientas personalizadas de compilación a proyectos de MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)|Muestra cómo asociar una herramienta de compilación con un archivo determinado.|
|[Cómo: Integrar herramientas personalizadas en las propiedades del proyecto](how-to-integrate-custom-tools-into-the-project-properties.md)|Muestra cómo agregar las opciones para una herramienta personalizada para las propiedades del proyecto.|
|[Cómo: Modificar la plataforma de destino y el conjunto de herramientas de la plataforma](how-to-modify-the-target-framework-and-platform-toolset.md)|Muestra cómo compilar un proyecto para varios marcos de trabajo o conjuntos de herramientas.|

## <a name="see-also"></a>Vea también

[Uso del conjunto de herramientas MSVC desde la línea de comandos](building-on-the-command-line.md)
