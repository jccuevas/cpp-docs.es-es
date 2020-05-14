---
title: 'MSBuild en la línea de comandos: C++'
ms.date: 12/12/2018
helpviewer_keywords:
- MSBuild
ms.assetid: 7a1be7ff-0312-4669-adf2-5f5bf507d560
ms.openlocfilehash: e95d99cf5c63c824bb9bade8e76bc3ca99079669
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220565"
---
# <a name="msbuild-on-the-command-line---c"></a>MSBuild en la línea de comandos: C++

En general, se recomienda usar Visual Studio para establecer las propiedades del proyecto e invocar el sistema MSBuild. Pero se puede usar la herramienta **MSBuild** directamente desde el símbolo del sistema. El proceso de compilación se controla mediante la información de un archivo del proyecto (.vcxproj) que se puede crear y editar. En el archivo del proyecto se especifican las opciones de compilación en función de fases, condiciones y eventos de compilación. Además, puede especificar cero o más argumentos *opciones* de la línea de comandos.

> **msbuild.exe** [ *archivo_del_proyecto* ] [ *opciones* ]

Use las opciones de línea de comandos **/target** (o **/t**) y **/property** (o **/p**) para invalidar propiedades y destinos concretos que se especifican en el archivo del proyecto.

Una función esencial del archivo del proyecto es especificar un *destino*, que es una operación determinada que se aplica al proyecto, y las entradas y salidas necesarias para realizar esa operación. Un archivo del proyecto puede especificar uno o varios destinos, que pueden incluir un destino predeterminado.

Cada destino consta de una secuencia de una o varias *tareas*. Cada tarea se representa mediante una clase de .NET Framework que contiene un comando ejecutable. Por ejemplo, la tarea [CL](/visualstudio/msbuild/cl-task) contiene el comando [cl.exe](reference/compiling-a-c-cpp-program.md).

Un *parámetro de tarea* es una propiedad de la tarea de clase y normalmente representa una opción de línea de comandos del comando ejecutable. Por ejemplo, el parámetro `FavorSizeOrSpeed` de la tarea `CL` se corresponde a las opciones del compilador **/Os** y **/Ot**.

Los parámetros de tarea adicionales admiten la infraestructura de MSBuild. Por ejemplo, el parámetro de tarea `Sources` especifica un conjunto de tareas que pueden consumir otras tareas. Para obtener más información sobre las tareas de MSBuild, vea [Referencia de tareas](/visualstudio/msbuild/msbuild-task-reference).

La mayoría de las tareas requieren entradas y salidas, como nombres de archivo, rutas de acceso y parámetros de cadena, numéricos o booleanos. Por ejemplo, una entrada común es el nombre de un archivo de código fuente .cpp que se va a compilar. Un parámetro de entrada importante es una cadena que especifica la configuración de compilación y la plataforma, por ejemplo, "Debug\|Win32". Las entradas y salidas se especifican mediante uno o varios elementos `Item` XML definidos por el usuario incluidos en un elemento `ItemGroup`.

Un archivo del proyecto también puede especificar *propiedades* definidas por el usuario y *elementos* `ItemDefinitionGroup`. Las propiedades y los elementos forman pares de nombre/valor que se pueden usar como variables en la compilación. El componente de nombre de un par define una *macro* y el componente de valor declara el *valor de la macro*. Para acceder a una macro de propiedad se usa la notación $(*nombre*) y para acceder a una macro de elemento, la notación %(*nombre*).

Otros elementos XML de un archivo del proyecto pueden probar macros y, después, establecer de forma condicional el valor de cualquier macro o controlar la ejecución de la compilación. Los nombres de macro y las cadenas literales se pueden concatenar para generar construcciones como una ruta de acceso y un nombre de archivo. En la línea de comandos, la opción **/property** establece o invalida una propiedad del proyecto. No se puede hacer referencia a los elementos en la línea de comandos.

El sistema MSBuild puede ejecutar condicionalmente un destino antes o después de otro destino. Además, el sistema puede compilar un destino en función de si los archivos que el destino consume son más recientes que los que emite.

Para obtener más información sobre MSBuild, vea:

- [MSBuild](/visualstudio/msbuild/msbuild) Información general sobre los conceptos de MSBuild.

- [Referencia de MSBuild](/visualstudio/msbuild/msbuild-reference) Información de referencia sobre el sistema MSBuild.

- [Referencia de esquema de archivo de proyecto](/visualstudio/msbuild/msbuild-project-file-schema-reference) Enumera los elementos de esquema XML de MSBuild, junto con sus atributos y elementos primarios y secundarios. En especial, tenga en cuenta los elementos [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild), [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild), [Target](/visualstudio/msbuild/target-element-msbuild) y [Task](/visualstudio/msbuild/task-element-msbuild).

- [Referencia de la línea de comandos](/visualstudio/msbuild/msbuild-command-line-reference) Describe los argumentos y las opciones de la línea de comandos que puede usar con msbuild.exe.

- [Referencia de tareas](/visualstudio/msbuild/msbuild-task-reference) Describe las tareas de MSBuild. En especial, tenga en cuenta las tareas siguientes, que son específicas de Visual C++: [Tarea BscMake](/visualstudio/msbuild/bscmake-task), [Tarea CL](/visualstudio/msbuild/cl-task), [Tarea CPPClean](/visualstudio/msbuild/cppclean-task), [Tarea LIB](/visualstudio/msbuild/lib-task), [Tarea Link](/visualstudio/msbuild/link-task), [Tarea MIDL](/visualstudio/msbuild/midl-task), [Tarea MT](/visualstudio/msbuild/mt-task), [Tarea RC](/visualstudio/msbuild/rc-task), [Tarea SetEnv](/visualstudio/msbuild/setenv-task) y [Tarea VCMessage](/visualstudio/msbuild/vcmessage-task).

## <a name="in-this-section"></a>En esta sección

|Término|Definición|
|----------|----------------|
|[Tutorial: Uso de MSBuild para crear un proyecto de C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|Se muestra cómo crear un proyecto de C++ en Visual Studio mediante **MSBuild**.|
|[Cómo: Usar de eventos de compilación en proyectos de MSBuild](how-to-use-build-events-in-msbuild-projects.md)|Se muestra cómo especificar una acción que se produce en una fase concreta de la compilación: antes de que se inicie la compilación, antes de que se inicie el paso de vínculo, o bien después de que finalice la compilación.|
|[Cómo: Agregar un paso personalizado de compilación a proyectos de MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)|Se muestra cómo agregar una fase definida por el usuario a la secuencia de compilación.|
|[Cómo: Agregar herramientas personalizadas de compilación a proyectos de MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)|Se muestra cómo asociar una herramienta de compilación a un archivo concreto.|
|[Cómo: Integrar herramientas personalizadas en las propiedades del proyecto](how-to-integrate-custom-tools-into-the-project-properties.md)|Se muestra cómo agregar opciones para una herramienta personalizada a las propiedades del proyecto.|
|[Cómo: Modificar la plataforma de destino y el conjunto de herramientas de la plataforma](how-to-modify-the-target-framework-and-platform-toolset.md)|Se muestra cómo compilar un proyecto para varios marcos de trabajo o conjuntos de herramientas.|

## <a name="see-also"></a>Vea también

[Uso del conjunto de herramientas MSVC desde la línea de comandos](building-on-the-command-line.md)
