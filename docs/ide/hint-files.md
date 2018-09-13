---
title: Archivos de indicaciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- cpp.hint
- vc.hint.file
dev_langs:
- C++
helpviewer_keywords:
- stop file
- cpp.hint
- hint file
- cpp.stop
- Class View, hint file
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dca97238310c42b9a537baa4056563b25c20c617
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895232"
---
# <a name="hint-files"></a>Archivos de indicaciones

Un *archivo de indicaciones* ayuda al entorno de desarrollo integrado (IDE) de Visual Studio a interpretar los identificadores de Visual C++, como los nombres de funciones y macros. Al abrir un proyecto de Visual C++, el *sistema de análisis* del IDE analiza el código de todos los archivos de código fuente del proyecto y recopila información sobre todos los identificadores. Después, el IDE usa esa información para admitir características como el explorador de la **Vista de clases** y la **Barra de navegación**.

El sistema de análisis, que se introdujo en Visual C++ 2010, entiende la sintaxis de C y C++, pero puede interpretar de manera incorrecta una instrucción que contiene una macro. La instrucción se puede interpretar de manera incorrecta si la macro hace que el código fuente sea sintácticamente incorrecto al escribirse. La instrucción puede ser sintácticamente correcta cuando se compila el código fuente y el preprocesador reemplaza el [identificador de macro](../preprocessor/hash-define-directive-c-cpp.md) con su definición. El sistema de análisis funciona sin necesidad de compilar el proyecto porque usa los archivos de indicaciones para interpretar las macros. Por tanto, una característica de exploración como **Vista de clases** está disponible de inmediato.

Un archivo de indicaciones contiene *indicaciones* personalizables por el usuario, que tienen la misma sintaxis que las definiciones de macro de C o C++. Visual C++ incluye un archivo de indicaciones integrado que es suficiente para la mayoría de los proyectos, pero puede crear sus propios archivos de indicaciones para mejorar la forma en que Visual Studio controla los identificadores.

> [!IMPORTANT]
> Si modifica o agrega un archivo de indicaciones, debe eliminar el archivo .sdf o un archivo VC.db en la solución para que los cambios surtan efecto.

## <a name="scenario"></a>Escenario

Suponga que el código siguiente está en un archivo de código fuente que se examina con el explorador **Vista de clases**. La macro `STDMETHOD` declara un método denominado `myMethod` que toma un parámetro y devuelve un puntero a un **HRESULT**.

```cpp
// Source code file.
STDMETHOD(myMethod)(int parameter1);
```

Las definiciones de macro siguientes se encuentran en un archivo de encabezado independiente.

```cpp
// Header file.
#define STDMETHOD(method) HRESULT (STDMETHODCALLTYPE * method)  
#define STDMETHODCALLTYPE __stdcall
#define HRESULT void*  
```

El sistema de análisis no puede interpretar el código fuente porque una función denominada `STDMETHOD` aparece como declarada, y esa declaración es sintácticamente incorrecta porque tiene dos listas de parámetros. El sistema de análisis no abre el archivo de encabezado para detectar las definiciones de las macros `STDMETHOD`, `STDMETHODCALLTYPE` y `HRESULT`. Como el sistema de análisis no puede interpretar la macro `STDMETHOD`, ignora toda la instrucción y, después, continúa el análisis.

El sistema de análisis no usa archivos de encabezado porque es posible que el proyecto dependa de uno o varios archivos de encabezado importantes. Si cambia cualquier archivo de encabezado, es posible que el sistema de análisis tenga que volver a examinar todos los archivos de encabezado del proyecto, lo que reduce el rendimiento del IDE. En su lugar, el sistema de análisis usa indicaciones que especifican cómo controlar las macros `STDMETHOD`, `STDMETHODCALLTYPE` y `HRESULT`.

¿Cómo se sabe si se necesita una indicación? Y si se necesita una indicación, ¿qué tipo se debe crear? Una señal de que se necesita una indicación es si la vista de un identificador en la **Vista de clases** no es coherente con la vista en el **Editor**. Por ejemplo, es posible que en la **Vista de clases** no se muestre un miembro de clase que sabe que existe, o bien que el nombre del miembro sea incorrecto. Para obtener más información sobre los tipos de indicaciones que resuelven problemas comunes, vea la sección "¿Qué macros requieren una indicación?" más adelante en este tema.

## <a name="architecture"></a>Arquitectura

Los archivos de indicaciones pertenecen a los directorios físicos, no a los directorios lógicos que se representan en el **Explorador de soluciones**. No es necesario agregar un archivo de indicaciones al proyecto para que surta efecto. El sistema de análisis solo usa los archivos de indicaciones cuando analiza los archivos de código fuente.

Todos los archivos de indicaciones se denominan **cpp.hint**. Por tanto, muchos directorios pueden contener un archivo de indicaciones pero solo puede aparecer uno en un directorio determinado.

El proyecto puede verse afectado por cero o más archivos de indicaciones. Si no hay archivos de indicaciones, el sistema de análisis usa técnicas de recuperación de errores para ignorar el código fuente que no se puede descifrar. En caso contrario, el sistema de análisis usa la estrategia siguiente para buscar y recopilar indicaciones.

### <a name="search-order"></a>Orden de búsqueda

El sistema de análisis busca los archivos de indicaciones en directorios en el orden siguiente.

- El directorio que contiene el paquete de instalación de Visual C++ (**vcpackages**). Este directorio contiene un archivo de indicaciones integrado que describe símbolos en los archivos del sistema que se usan con frecuencia, como **windows.h**. Por tanto, el proyecto hereda de manera automática la mayoría de las indicaciones que necesita.

- La ruta de acceso del directorio raíz de un archivo de código fuente al directorio que contiene el propio archivo de código fuente. En un proyecto típico de Visual C++, el directorio raíz contiene el archivo de solución o del proyecto.

   La excepción a esta regla es si hay un *archivo de detención* en la ruta de acceso al archivo de código fuente. Un archivo de detención proporciona control adicional sobre el orden de búsqueda y es cualquier archivo con el nombre **cpp.stop**. En lugar de iniciarse desde el directorio raíz, el sistema de análisis busca desde el directorio que contiene el archivo de detención hasta el directorio que contiene el archivo de código fuente. En un proyecto típico, no se necesita un archivo de detención.

### <a name="hint-gathering"></a>Recopilación de indicaciones

Un archivo de indicaciones contiene cero o más *indicaciones*. Un indicación se define o elimina igual que una macro de C o C++. Es decir, la directiva de preprocesador `#define` crea o vuelve a definir una indicación, y la directiva `#undef` la elimina.

El sistema de análisis abre cada archivo de indicaciones en el orden de búsqueda descrito anteriormente, acumula las indicaciones de cada archivo en un conjunto de *indicaciones vigentes* y, después, usa las indicaciones vigentes para interpretar los identificadores en el código.

El sistema de análisis usa las reglas siguientes para acumular las indicaciones.

- Si la indicación nueva especifica un nombre que todavía no está definido, agrega el nombre a las indicaciones vigentes.

- Si la indicación nueva especifica un nombre que ya está definido, vuelve a definir la indicación existente.

- Si la indicación nueva es una directiva `#undef` que especifica una indicación vigente existente, la indicación nueva elimina la existente.

La primera regla significa que las indicaciones vigentes se heredan de los archivos de indicaciones abiertos previamente. Las dos últimas reglas significan que las indicaciones que se producen después en el orden de búsqueda pueden invalidar las que se produce antes. Por ejemplo, puede invalidar cualquier indicación anterior si crea un archivo de indicaciones en el directorio que contiene un archivo de código fuente.

Para obtener una descripción de cómo se recopilan las indicaciones, vea la sección `Example` más adelante en este tema.

### <a name="syntax"></a>Sintaxis

Las indicaciones se crean y eliminan con la misma sintaxis que las directivas de preprocesador que crean y eliminan macros. De hecho, el sistema de análisis usa el preprocesador de C/C ++ para evaluar las indicaciones. Para obtener más información sobre las directivas de preprocesador, vea [#define (directiva) (C/C ++)](../preprocessor/hash-define-directive-c-cpp.md) y [#undef (directiva) (C/C ++)](../preprocessor/hash-undef-directive-c-cpp.md).

Los únicos elementos de sintaxis inusuales son las cadenas de reemplazo `@<`, `@=` y `@>`. Son cadenas de reemplazo específicas de archivo de indicaciones que solo se usan con macros *map*. Un mapa es un conjunto de macros que relacionan datos, funciones o eventos con otros datos, funciones o controladores de eventos. Por ejemplo, `MFC` usa los mapas para crear [mapas de mensajes](../mfc/reference/message-maps-mfc.md), y `ATL` para crear [mapas de objetos](../atl/reference/object-map-macros.md). Las cadenas de reemplazo específicas de archivos de indicaciones indican los elementos inicial, intermedio y final de un mapa. Solo el nombre de una macro de mapa es significativo. Por tanto, todas las cadenas de reemplazo ocultan intencionadamente la implementación de la macro.

Las indicaciones usan la sintaxis siguiente.

|Sintaxis|Significado|
|------------|-------------|
|`#define` *nombre_de_la_indicación* *cadena_de_reemplazo*<br /><br /> `#define` *nombre_de_la_indicación* `(` *parámetro*, ...`)`*cadena_de_reemplazo*|Una directiva de preprocesador que define una indicación nueva o vuelve a definir una indicación existente. Después de la directiva, el preprocesador reemplaza cada aparición de *nombre_de_la_indicación* en el código fuente con *cadena_de_reemplazo*.<br /><br /> El segundo formato de sintaxis define una indicación similar a una función. Si en el código fuente aparece una indicación de tipo de función, en primer lugar el preprocesador reemplaza cada aparición de *parámetro* en *cadena_de_reemplazo* con el argumento correspondiente en el código fuente y, después, reemplaza *nombre_de_la_indicación* con *cadena_de_reemplazo*.|
|`@<`|Una *cadena_de_reemplazo* específica del archivo de indicaciones que indica el inicio de un conjunto de elementos de mapa.|
|`@=`|Una *cadena_de_reemplazo* específica del archivo de indicaciones que indica un elemento de mapa intermedio. Un mapa puede tener varios elementos de mapa.|
|`@>`|Una *cadena_de_reemplazo* específica del archivo de indicaciones que indica el final de un conjunto de elementos de mapa.|
|`#undef` *nombre_de_la_indicación*|La directiva de preprocesador que elimina una indicación existente. El nombre de la indicación lo proporciona el identificador de *nombre_de_la_indicación*.|
|`//` *comentario*|Un comentario de una sola línea.|
|`/*` *comentario* `*/`|Un comentario multilínea.|

## <a name="what-macros-require-a-hint"></a>¿Qué macros requieren una indicación?

Ciertos tipos de macros pueden interferir con el sistema de análisis. En esta sección se describen los tipos de macros que pueden causar un problema y el tipo de indicación que se puede crear para solucionarlo.

### <a name="disruptive-macros"></a>Macros problemáticas

Algunas macros hacen que el sistema de análisis interprete de manera incorrecta el código fuente, pero se pueden ignorar sin perjudicar la experiencia de exploración. Por ejemplo, las macros del lenguaje de anotación de código fuente ([SAL](../c-runtime-library/sal-annotations.md)) se resuelven en atributos de C++ que ayudan a buscar errores de programación. Si quiere omitir las anotaciones SAL al examinar el código, puede crear un archivo de indicaciones que oculte la anotación.

En el código fuente siguiente, el tipo de parámetro para la función `FormatWindowClassName()` es `PXSTR`, y el nombre de parámetro es `szBuffer`. Pero el sistema de análisis confunde las anotaciones SAL `_Pre_notnull_` y `_Post_z_` para el tipo de parámetro o el nombre del parámetro.

**Código fuente:**  

```  
static void FormatWindowClassName(_Pre_notnull__Post_z_ PXSTR szBuffer)  
```  

**Estrategia:** definición NULL

En esta situación, la estrategia consiste en tratar las anotaciones SAL como si no existieran. Para ello, especifique una indicación cuya cadena de reemplazo sea NULL. Por tanto, el sistema de análisis ignora las anotaciones y no se muestran en el explorador **Vista de clases**. (Visual C++ incluye un archivo de indicaciones integrado que oculta la anotación SAL).  

**Archivo de indicaciones:**  

```  
#define _Pre_notnull_
```  

### <a name="concealed-cc-language-elements"></a>Elementos ocultos del lenguaje C o C++

Una razón común por la que el sistema de análisis malinterpreta el código fuente es si una macro oculta un token de [signo de puntuación](../cpp/punctuators-cpp.md) o [palabra clave](../cpp/keywords-cpp.md) de C o C++. Es decir, es posible que una macro contenga la mitad de un par de signos de puntuación, como `<>`, `[]`, `{}` y `()`.

En el código fuente siguiente, la macro `START_NAMESPACE` oculta una llave de apertura sin emparejar (`{`).

**Código fuente:**  

```  
#define START_NAMESPACE namespace MyProject {
```  

**Estrategia:** copia directa

Si la semántica de una macro es fundamental para la experiencia de exploración, cree una indicación que sea idéntica a la macro. El sistema de análisis resuelve la macro en la definición del archivo de indicaciones.

Tenga en cuenta que si la macro en el archivo de código fuente contiene otras macros, solo se interpretarán si ya están en el conjunto de indicaciones vigentes.

**Archivo de indicaciones:**  

```  
#define START_NAMESPACE namespace MyProject {
```  

### <a name="maps"></a>Asignaciones

Un mapa se compone de macros que designan un elemento inicial, un elemento final y cero o más elementos intermedios. El sistema de análisis malinterpreta los mapas porque las macros de mapa ocultan elementos del lenguaje C o C++, y la sintaxis de una instrucción de C o C++ completa se distribuye entre diversas macros independientes.

En el código fuente siguiente se definen las macros `BEGIN_CATEGORY_MAP`, `IMPLEMENTED_CATEGORY` y `END_CATEGORY_MAP`.

**Código fuente:**  

```  
#define BEGIN_CATEGORY_MAP(x)\
static const struct ATL::_ATL_CATMAP_ENTRY* GetCategoryMap() throw() {\
static const struct ATL::_ATL_CATMAP_ENTRY pMap[] = {
#define IMPLEMENTED_CATEGORY( catid ) { _ATL_CATMAP_ENTRY_IMPLEMENTED, &catid },
#define END_CATEGORY_MAP()\
   { _ATL_CATMAP_ENTRY_END, NULL } };\
   return( pMap ); }
```  

**Estrategia:** identificar los elementos de mapa

Especifique indicaciones para los elementos inicial, intermedio (si existe) y final de un mapa. Use las cadenas de reemplazo de mapas especiales (`@<`, `@=` y `@>`). Para obtener más información, vea la sección `Syntax` de este tema.

**Archivo de indicaciones:**  

```  
// Start of the map.
#define BEGIN_CATEGORY_MAP(x) @<
// Intermediate map element.
#define IMPLEMENTED_CATEGORY( catid ) @=
// Intermediate map element.
#define REQUIRED_CATEGORY( catid ) @=
// End of the map.
#define END_CATEGORY_MAP() @>
```  

### <a name="composite-macros"></a>Macros compuestas

Las macros compuestas contienen uno o varios de los tipos de macro que confunden al sistema de análisis.

El código fuente siguiente contiene la macro `START_NAMESPACE`, que especifica el inicio de un ámbito de espacio de nombres, y la macro `BEGIN_CATEGORY_MAP`, que especifica el inicio de un mapa.

**Código fuente:**  

```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP
```  

**Estrategia:** copia directa

Cree indicaciones para las macros `START_NAMESPACE` y `BEGIN_CATEGORY_MAP`, y después cree una indicación para la macro `NSandMAP` que tenga el mismo valor que se muestra anteriormente para el código fuente. O bien, si una macro compuesta solo está formada por macros problemáticas y espacio en blanco, puede definir una indicación cuya cadena de reemplazo sea una definición nula.

En este ejemplo, suponga que `START_NAMESPACE` ya tiene una indicación, como se describe en el subtítulo `Concealed C/C++ Language Elements` de este tema. Y suponga que `BEGIN_CATEGORY_MAP` tiene una indicación, como se describió anteriormente en `Maps`.

**Archivo de indicaciones:**  

```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP
```  

### <a name="inconvenient-macros"></a>Macros no convenientes

El sistema de análisis puede interpretar algunas macros, pero el código fuente es difícil de leer porque la macro es larga o compleja. Para mejorar la legibilidad, puede proporcionar una indicación que simplifique la presentación de la macro.

**Código fuente:**  

```  
#define STDMETHOD(methodName) HRESULT (STDMETHODCALLTYPE * methodName)  
```  

**Estrategia:** simplificación

Cree una indicación que muestre una definición de macro más sencilla.

**Archivo de indicaciones:**  

```  
#define STDMETHOD(methodName) void* methodName
```  

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo se acumulan las indicaciones de los archivos de indicaciones. En este ejemplo no se usan archivos de detención.

En la ilustración siguiente se muestran algunos de los directorios físicos de un proyecto de Visual C++. Los archivos de indicaciones se encuentran en los directorios `vcpackages`, `Debug`, `A1` y `A2`.

### <a name="hint-file-directories"></a>Directorios de archivos de indicaciones

![Directorios de archivos de indicaciones comunes y específicos del proyecto.](../ide/media/hintfile.png "HintFile")  

### <a name="directories-and-hint-file-contents"></a>Directorios y contenido del archivo de indicaciones

En la lista siguiente se muestran los directorios de este proyecto que contienen archivos de indicaciones y el contenido de esos archivos. Solo se enumeran algunas de las muchas indicaciones del archivo de indicaciones del directorio `vcpackages`.

- vcpackages

    ```  
    // vcpackages (partial list)  
    #define _In_
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)  
    ```  

- Depuración

    ```  
    // Debug
    #undef _In_
    #define OBRACE {
    #define CBRACE }
    #define RAISE_EXCEPTION(x) throw (x)  
    #define START_NAMESPACE namespace MyProject {
    #define END_NAMESPACE }
    ```  

- A1

    ```  
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    ```  

- A2

    ```  
    // A2
    #undef OBRACE
    #undef CBRACE
    ```  

### <a name="effective-hints"></a>Indicaciones vigentes

En la tabla siguiente se enumeran las indicaciones vigentes para los archivos de código fuente de este proyecto.

- Archivo de código fuente: A1_A2_B.cpp

- Indicaciones vigentes:

    ```  
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

Las notas siguientes se aplican a la lista anterior.

- Las sugerencias vigentes pertenecen a los directorios `vcpackages`, `Debug`, `A1` y `A2`.

- La directiva **#undef** del archivo de indicaciones `Debug` quitó la indicación `#define _In_` del archivo de indicaciones del directorio `vcpackages`.

- El archivo de indicaciones del directorio `A1` redefine `START_NAMESPACE`.

- La indicación `#undef` del directorio `A2` quitó las indicaciones para `OBRACE` y `CBRACE` del archivo de indicaciones del directorio `Debug`.

## <a name="see-also"></a>Vea también

[Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)    
[#define (directiva) (C/C++)](../preprocessor/hash-define-directive-c-cpp.md)   
[#undef (directiva) (C/C++)](../preprocessor/hash-undef-directive-c-cpp.md)   
[Anotaciones SAL](../c-runtime-library/sal-annotations.md)   
[Mapas de mensajes](../mfc/reference/message-maps-mfc.md)   
[Macros de mapa de mensajes](../atl/reference/message-map-macros-atl.md)   
[Macros de mapa de objetos](../atl/reference/object-map-macros.md)