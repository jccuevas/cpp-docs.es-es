---
title: Archivos de indicaciones
ms.date: 02/26/2019
f1_keywords:
- cpp.hint
- vc.hint.file
helpviewer_keywords:
- stop file
- cpp.hint
- hint file
- cpp.stop
- Class View, hint file
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
ms.openlocfilehash: de299f17686d68956e9847d47743d8931734d4ad
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075204"
---
# <a name="hint-files"></a>Archivos de indicaciones

Un *archivo de indicaciones* contiene macros que de otra manera provocarían que el analizador de bases de datos de navegación de C++ omitiera ciertas regiones del código. Al abrir un proyecto de C++ de Visual Studio, el analizador analiza el código de todos los archivos de código fuente del proyecto y genera una base de datos con información sobre todos los identificadores. Después, el IDE usa esa información para admitir características de navegación por el código, como el explorador **Vista de clases** y la **Barra de navegación**.

El analizador de bases de datos de navegación de C++ es un analizador por aproximación que puede analizar grandes cantidades de código en poco tiempo. Una de las causas de su rapidez es el hecho de que omite el contenido de bloques. Por ejemplo, solo registra la ubicación y los parámetros de una función, mientras que omite su contenido. Algunas macros pueden provocar problemas con la heurística usada para determinar el inicio y final de un bloque. Estos problemas provocan que ciertas regiones de código se registren incorrectamente.

Las regiones omitidas pueden manifestarse de varias maneras:

- La falta de tipos y funciones en la **Vista de clases**, **Ir a** y la **Barra de navegación**.

- La existencia de ámbitos incorrectos en la **Barra de navegación**.

- Sugerencias para **crear una declaración o definición** para las funciones que ya se han definido.

Un archivo de indicaciones contiene indicaciones personalizables por el usuario, que tienen la misma sintaxis que las definiciones de macro de C o C++. Visual C++ incluye un archivo de indicaciones integrado que resulta suficiente para la mayoría de los proyectos. Pero puede crear sus propios archivos de indicaciones para mejorar el analizador específicamente para su proyecto.

> [!IMPORTANT]
> Si modifica o agrega un archivo de indicaciones, deberá realizar pasos adicionales para que los cambios surtan efecto:
> - En versiones anteriores a la versión 15,6 de Visual Studio 2017: Elimine el archivo. sdf o el archivo VC. dB de la solución para todos los cambios.
> - En Visual Studio 2017 versión 15,6 y versiones posteriores: cierre y vuelva a abrir la solución después de agregar nuevos archivos de sugerencia.

## <a name="scenario"></a>Escenario

```cpp
#define NOEXCEPT noexcept
void Function() NOEXCEPT
{
}
```

Sin un archivo de indicaciones, `Function` no se mostrará en la **Vista de clases**, **Ir a** ni la **Barra de navegación**. Tras agregar un archivo de indicaciones con esta definición de macro, el analizador ahora identifica y sustituye la macro `NOEXCEPT`, lo que permite que analice correctamente la función:

```cpp.hint
#define NOEXCEPT
```

## <a name="disruptive-macros"></a>Macros problemáticas

Existen dos categorías de macros que interrumpen el analizador:

- Macros que encapsulan las palabras clave que decoran una función

   ```cpp
   #define NOEXCEPT noexcept
   #define STDMETHODCALLTYPE __stdcall
   ```

   Para estos tipos de macros, solo se requiere el nombre de la macro en el archivo de indicaciones:

   ```cpp.hint
   #define NOEXCEPT
   #define STDMETHODCALLTYPE
   ```

- Macros que contienen corchetes desequilibrados

   ```cpp
   #define BEGIN {
   ```

   Para estos tipos de macros, se requiere tanto el nombre de la macro como su contenido en el archivo de indicaciones:

   ```cpp.hint
   #define BEGIN {
   ```

## <a name="editor-support"></a>Compatibilidad con el editor

A partir de la versión 15.8 de Visual Studio 2017, hay varias características para identificar las macros problemáticas:

- Se resaltan las macros que forman parte de las regiones omitidas por el analizador.

- Hay una acción rápida para crear un archivo de indicaciones que incluye la macro resaltada. En el caso de que ya haya un archivo de indicaciones, la acción rápida permite agregar la macro al archivo de indicaciones.

![Macro resaltada.](media/hint-squiggle-and-actions.png "Sugerencia y acciones rápidas en zigzag")

Después de ejecutar una acción rápida, el analizador vuelve a analizar los archivos afectados por el archivo de indicaciones.

De forma predeterminada, se resalta la macro de problema como una sugerencia. El resaltado se puede cambiar a un elemento más visible, como un subrayado ondulado de color rojo o verde. Use la opción **Macros de regiones de navegación omitidas** en la sección **Subrayados ondulados de código**, que encontrará en **Herramientas** > **Opciones** > **Editor de texto** > **C/C++**  > **Ver**.

![Macros en la opción regiones de exploración omitidas.](media/skipped-regions-squiggle-option.png "Se omitió la opción en zigzag de regiones.")

## <a name="display-browsing-database-errors"></a>Visualizar errores de la base de datos de exploración

El comando de menú **Proyecto** > **Visualizar errores de la base de datos de exploración** permite visualizar todas las regiones que no se pudieron analizar en la **Lista de errores**. Este comando está pensado para simplificar la creación del archivo de indicaciones inicial. Pero el analizador no puede determinar si la causa del error es una macro problemática, por lo que debe evaluar cada error. Ejecute el comando **Visualizar errores de la base de datos de exploración** y navegue a cada error para cargar el archivo afectado en el editor. Una vez cargado el archivo, se resaltarán las macros que formen parte de la región. Puede invocar las acciones rápidas para agregarlas a un archivo de indicaciones. Después de actualizar el archivo de indicaciones, la lista de errores se actualizará automáticamente. Si quiere modificar el archivo de indicaciones manualmente, también puede usar el comando **Volver a analizar la solución** para desencadenar una actualización.

## <a name="architecture"></a>Architecture

Los archivos de indicaciones están relacionados con los directorios físicos, no con los directorios lógicos que se muestran en el **Explorador de soluciones**. No es necesario agregar un archivo de indicaciones al proyecto para que surta efecto. El sistema de análisis solo usa los archivos de indicaciones cuando analiza los archivos de código fuente.

Todos los archivos de indicaciones se denominan **cpp.hint**. Muchos directorios pueden contener un archivo de indicaciones, pero solo puede aparecer uno en un directorio determinado.

El proyecto puede verse afectado por cero o más archivos de indicaciones. Si no hay archivos de indicaciones, el sistema de análisis usa técnicas de recuperación de errores para ignorar el código fuente que no se puede descifrar. En caso contrario, el sistema de análisis usa la estrategia siguiente para buscar y recopilar indicaciones.

### <a name="search-order"></a>Orden de búsqueda

El sistema de análisis busca los archivos de indicaciones en directorios en el orden siguiente.

- El directorio que contiene el paquete de instalación de Visual C++ (**vcpackages**). Este directorio contiene un archivo de indicaciones integrado que describe símbolos en los archivos del sistema que se usan con frecuencia, como **windows.h**. Por tanto, el proyecto hereda de manera automática la mayoría de las indicaciones que necesita.

- La ruta de acceso del directorio raíz de un archivo de código fuente al directorio que contiene el propio archivo de código fuente. En un proyecto típico de C++ de Visual Studio, el directorio raíz contiene el archivo de la solución o del proyecto.

   La excepción a esta regla es si hay un *archivo de detención* en la ruta de acceso al archivo de código fuente. Un archivo de detención es cualquier archivo con el nombre **cpp.stop**. Un archivo de detención proporciona control adicional sobre el orden de búsqueda. En lugar de iniciarse desde el directorio raíz, el sistema de análisis busca desde el directorio que contiene el archivo de detención hasta el directorio que contiene el archivo de código fuente. En un proyecto típico, no se necesita ningún archivo de detención.

### <a name="hint-gathering"></a>Recopilación de indicaciones

Un archivo de indicaciones contiene cero o más *indicaciones*. Un indicación se define o elimina igual que una macro de C o C++. Es decir, la directiva de preprocesador `#define` crea o vuelve a definir una indicación, y la directiva `#undef` la elimina.

El sistema de análisis abre cada archivo de indicaciones en el orden de búsqueda descrito anteriormente. Acumula las indicaciones de cada archivo en un conjunto de *indicaciones vigentes* y, después, usa las indicaciones vigentes para interpretar los identificadores en el código.

El sistema de análisis usa estas reglas para acumular las indicaciones:

- Si la indicación nueva especifica un nombre que todavía no está definido, agrega el nombre a las indicaciones vigentes.

- Si la indicación nueva especifica un nombre que ya está definido, vuelve a definir la indicación existente.

- Si la indicación nueva es una directiva `#undef` que especifica una indicación vigente existente, la indicación nueva elimina la existente.

La primera regla significa que las indicaciones vigentes se heredan de los archivos de indicaciones abiertos previamente. Las dos últimas reglas implican que las indicaciones posteriores en el orden de búsqueda pueden invalidar las anteriores. Por ejemplo, puede invalidar cualquier indicación anterior si crea un archivo de indicaciones en el directorio que contiene un archivo de código fuente.

Para obtener una descripción de cómo se recopilan las indicaciones, vea la sección [Ejemplo](#example).

### <a name="syntax"></a>Sintaxis

Puede crear y eliminar indicaciones con la misma sintaxis que las directivas de preprocesador para crear y eliminar macros. De hecho, el sistema de análisis usa el preprocesador de C/C ++ para evaluar las indicaciones. Para obtener más información sobre las directivas de preprocesador, vea [#define (directiva) (C/C ++)](../../preprocessor/hash-define-directive-c-cpp.md) y [#undef (directiva) (C/C ++)](../../preprocessor/hash-undef-directive-c-cpp.md).

Los únicos elementos de sintaxis inusuales son las cadenas de reemplazo `@<`, `@=` y `@>`. Son cadenas de reemplazo específicas de archivo de indicaciones que solo se usan con macros *map*. Un mapa es un conjunto de macros que relacionan datos, funciones o eventos con otros datos, funciones o controladores de eventos. Por ejemplo, `MFC` usa los mapas para crear [mapas de mensajes](../../mfc/reference/message-maps-mfc.md), y `ATL` para crear [mapas de objetos](../../atl/reference/object-map-macros.md). Las cadenas de reemplazo específicas de archivos de indicaciones indican los elementos inicial, intermedio y final de un mapa. Solo el nombre de una macro de mapa es significativo. Por tanto, todas las cadenas de reemplazo ocultan intencionadamente la implementación de la macro.

Las sugerencias usan esta sintaxis:

|Sintaxis|Significado|
|------------|-------------|
|`#define` *Hint-Name* *-cadena de reemplazo*<br /><br /> `#define` *Hint-name* `(` *parámetro*,...`)` *-cadena de reemplazo*|Una directiva de preprocesador que define una indicación nueva o vuelve a definir una indicación existente. Después de la directiva, el preprocesador reemplaza cada aparición de *nombre_de_la_indicación* en el código fuente con *cadena_de_reemplazo*.<br /><br /> El segundo formato de sintaxis define una indicación similar a una función. Si en el código fuente aparece una indicación de tipo de función, en primer lugar el preprocesador reemplaza cada aparición de *parámetro* en *cadena_de_reemplazo* con el argumento correspondiente en el código fuente y, después, reemplaza *nombre_de_la_indicación* con *cadena_de_reemplazo*.|
|`@<`|Una *cadena_de_reemplazo* específica del archivo de indicaciones que indica el inicio de un conjunto de elementos de mapa.|
|`@=`|Una *cadena_de_reemplazo* específica del archivo de indicaciones que indica un elemento de mapa intermedio. Un mapa puede tener varios elementos de mapa.|
|`@>`|Una *cadena_de_reemplazo* específica del archivo de indicaciones que indica el final de un conjunto de elementos de mapa.|
|`#undef` *Hint-Name*|La directiva de preprocesador que elimina una indicación existente. El nombre de la indicación lo proporciona el identificador de *nombre_de_la_indicación*.|
|`//` *Comentario*|Comentario en una sola línea.|
|`/*` *comentario* `*/`|Un comentario multilínea.|

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo se acumulan las sugerencias de los archivos de indicaciones. En este ejemplo no se usa ningún archivo de detención.

En la ilustración se muestran algunos de los directorios físicos de un proyecto de C++ de Visual Studio. Hay archivos de indicaciones en los directorios `vcpackages`, `Debug`, `A1` y `A2`.

### <a name="hint-file-directories"></a>Directorios de archivos de indicaciones

![Directorios de archivos&#45;de sugerencia comunes y específicos del proyecto.](media/hintfile.png "HintFile")

### <a name="directories-and-hint-file-contents"></a>Directorios y contenido del archivo de indicaciones

En esta lista se muestran los directorios de este proyecto que contienen archivos de indicaciones y el contenido de esos archivos. Solo se enumeran algunas de las muchas indicaciones del archivo de indicaciones del directorio `vcpackages`:

- vcpackages

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    ```

- Depurar

    ```cpp.hint
    // Debug
    #undef _In_
    #define OBRACE {
    #define CBRACE }
    #define RAISE_EXCEPTION(x) throw (x)
    #define START_NAMESPACE namespace MyProject {
    #define END_NAMESPACE }
    ```

- A1

    ```cpp.hint
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    ```

- A2

    ```cpp.hint
    // A2
    #undef OBRACE
    #undef CBRACE
    ```

### <a name="effective-hints"></a>Indicaciones vigentes

En esta tabla se enumeran las indicaciones vigentes para los archivos de código fuente de este proyecto:

- Archivo de código fuente: A1_A2_B.cpp

- Indicaciones vigentes:

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    // Debug...
    #define RAISE_EXCEPTION(x) throw (x)
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    // ...Debug
    #define END_NAMESPACE }
    ```

Estas notas se aplican a la lista anterior:

- Las sugerencias vigentes pertenecen a los directorios `vcpackages`, `Debug`, `A1` y `A2`.

- La directiva **#undef** del archivo de indicaciones `Debug` quitó la indicación `#define _In_` del archivo de indicaciones del directorio `vcpackages`.

- El archivo de indicaciones del directorio `A1` redefine `START_NAMESPACE`.

- La indicación `#undef` del directorio `A2` quitó las indicaciones para `OBRACE` y `CBRACE` del archivo de indicaciones del directorio `Debug`.

## <a name="see-also"></a>Consulte también

[Tipos de archivos creados para proyectos de C++ de Visual Studio](file-types-created-for-visual-cpp-projects.md)<br>
[#define (directiva) (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)<br>
[#undef (directiva) (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br>
[Anotaciones SAL](../../c-runtime-library/sal-annotations.md)<br>
