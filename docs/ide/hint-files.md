---
title: "Archivos de indicaciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cpp.hint"
  - "vc.hint.file"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivo de detención"
  - "cpp.hint"
  - "archivo de indicaciones"
  - "cpp.stop"
  - "Vista de clases, archivo de indicaciones"
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Archivos de indicaciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un *archivo sugerencia* Ayuda a Visual Studio el entorno de desarrollo integrado (IDE) interprete los identificadores de Visual C++, como los nombres de funciones y macros. Al abrir un proyecto de Visual C++, el IDE *sistema de análisis* analiza el código en cada archivo de origen en el proyecto y recopila información sobre cada identificador. A continuación, el IDE usa dicha información para admitir características como la **la vista de clases** explorador y **barra de navegación**.  
  
 El sistema de análisis, que se introdujo en [!INCLUDE[cpp_dev10_long](../build/includes/cpp_dev10_long_md.md)], entienda la sintaxis de C o C++, pero puede interpretar erróneamente una instrucción que contiene una macro. La instrucción se puede interpretar si la macro hace que el código fuente sea sintácticamente incorrecto al escribirse. La instrucción puede ser sintácticamente correcta cuando se compila el código fuente y el preprocesador reemplaza el [macro identificador](../preprocessor/hash-define-directive-c-cpp.md) con su definición. El sistema de análisis funciona sin necesidad de compilar el proyecto porque usa los archivos de sugerencia para interpretar las macros. Por lo tanto, una exploración de la característica como **la vista de clases** está disponible inmediatamente.  
  
 Un archivo de sugerencia contiene personalizables por el usuario *sugerencias*, que tienen la misma sintaxis que las definiciones de macro de C o C++. Visual C++ incluye un archivo de sugerencia integrado que es suficiente para la mayoría de los proyectos, pero puede crear sus propios archivos de sugerencia para mejorar la forma en que Visual Studio controla los identificadores.  
  
> [!IMPORTANT]
>  Si modifica o agrega un archivo de sugerencia, debe eliminar el archivo .sdf o un archivo de VC.db en la solución en orden para que los cambios surtan efecto.  
  
## <a name="scenario"></a>Escenario  
 Suponga que el código siguiente es un archivo de origen que se examina con el **la vista de clases** explorador. El `STDMETHOD` macro declara un método denominado `myMethod` que toma un parámetro y devuelve un puntero a un **HRESULT**.  
  
```  
// Source code file.  
STDMETHOD(myMethod)(int parameter1);  
```  
  
 Las siguientes definiciones de macro se encuentran en un archivo de encabezado independiente.  
  
```  
// Header file.  
#define STDMETHOD(method) HRESULT (STDMETHODCALLTYPE * method)  
#define STDMETHODCALLTYPE __stdcall  
#define HRESULT void*  
```  
  
 El sistema de análisis no puede interpretar el código fuente porque una función denominada STDMETHOD aparece como declarada y dicha declaración es sintácticamente incorrecta porque tiene dos listas de parámetros. El sistema de análisis no abre el archivo de encabezado para detectar las definiciones de la `STDMETHOD`, `STDMETHODCALLTYPE`, y `HRESULT` macros. Como el sistema de análisis no puede interpretar el `STDMETHOD` (macro), se omite la instrucción al completo y, a continuación, continúa analizando.  
  
 El sistema de análisis no utiliza archivos de encabezado porque el proyecto puede depender de uno o más archivos de encabezado importantes. Si cambia cualquier archivo de encabezado, el sistema de análisis podría tener que volver a examinar todos los archivos de encabezado en el proyecto, lo que reduce el rendimiento del IDE. En su lugar, el sistema de análisis utiliza sugerencias que especifican cómo controlar las `STDMETHOD`, `STDMETHODCALLTYPE`, y `HRESULT` macros.  
  
 ¿Cómo sé que se requiere una sugerencia? ¿Y si necesita una sugerencia, qué tipo debe crear? Es un inicio de sesión que se necesita una sugerencia si la vista de un identificador en **vista de clases** no es coherente con la vista en el **Editor**. Por ejemplo, **la vista de clases** podría no mostrar un miembro de clase que sabe que existe, o el nombre del miembro es incorrecto. ¿Para obtener más información acerca de los tipos de sugerencias que resuelven los problemas comunes, consulte la qué Macros Require A Hint? sección más adelante en este tema.  
  
## <a name="architecture"></a>Arquitectura  
 Archivos de sugerencia pertenecen a los directorios físicos, no a los directorios lógicos mencionados en **el Explorador de soluciones**. No es necesario agregar un archivo de sugerencia a su proyecto para que tenga un efecto en el archivo de sugerencia. El sistema de análisis usa archivos de sugerencia cuando analiza los archivos de origen.  
  
 Cada archivo de sugerencia se denomina **cpp.hint**. Por lo tanto, muchos directorios pueden contener un archivo de sugerencia, pero solo puede ocurrir en un directorio determinado.  
  
 Su proyecto puede verse afectado por cero o más archivos de sugerencia. Si no hay ningún archivo de sugerencia, el sistema de análisis usa técnicas de recuperación de errores para omitir el código fuente. De lo contrario, el sistema de análisis usa la estrategia siguiente para buscar y recopilar sugerencias.  
  
### <a name="search-order"></a>Orden de búsqueda  
 El sistema de análisis busca los directorios de archivos de sugerencia en el orden siguiente.  
  
-   El directorio que contiene el paquete de instalación de Visual C++ (**vcpackages**). Este directorio contiene un archivo de sugerencia integrado que describe los símbolos en archivos del sistema utilizados con frecuencia, como **windows.h**. Por consiguiente, el proyecto hereda automáticamente la mayoría de las sugerencias que necesita.  
  
-   La ruta de acceso del directorio raíz de un archivo de origen en el directorio que contiene el archivo de origen. En un proyecto típico de Visual C++, el directorio raíz contiene el archivo de solución o proyecto.  
  
     La excepción a esta regla es si un *stop archivo* está en la ruta de acceso al archivo de origen. Proporciona control adicional sobre el orden de búsqueda de un archivo de detención y es cualquier archivo que se denomina **cpp.stop**. En lugar de iniciarse desde el directorio raíz, el sistema de análisis realiza las búsquedas de directorio que contiene el archivo de detención en el directorio que contiene el archivo de origen. En un proyecto típico, no necesita un archivo de detención.  
  
### <a name="hint-gathering"></a>Recopilación de sugerencias  
 Un archivo de sugerencia contiene cero o más *sugerencias*. Una sugerencia se define o se elimina como una macro de C o C++. Es decir, el `#define` Directiva de preprocesador crea o vuelve a definir una sugerencia y el `#undef` directiva elimina una sugerencia.  
  
 El sistema de análisis abre cada archivo de sugerencia en el orden de búsqueda descrito anteriormente, acumula las sugerencias de cada archivo en un conjunto de *sugerencias vigentes*, y, a continuación, utiliza las sugerencias vigentes para interpretar los identificadores en el código.  
  
 El sistema de análisis usa las siguientes reglas para acumular las sugerencias.  
  
-   Si la nueva sugerencia especifica un nombre que ya no está definido, la nueva sugerencia agrega el nombre a las sugerencias vigentes.  
  
-   Si la nueva sugerencia especifica un nombre que ya está definido, la nueva sugerencia vuelve a definir la sugerencia existente.  
  
-   Si la nueva sugerencia es una `#undef` la directiva que especifica una sugerencia vigente existente, la nueva sugerencia elimina la existente.  
  
 La primera regla significa que las sugerencias vigentes se heredan de los archivos de sugerencia abiertos previamente. Las dos últimas reglas significan que las sugerencias que aparecen más adelante en el orden de búsqueda pueden invalidar las sugerencias que se produjo anteriormente. Por ejemplo, puede invalidar cualquier sugerencia anterior si crea un archivo de sugerencia en el directorio que contiene un archivo de origen.  
  
 Para obtener una descripción de cómo se recopilan las sugerencias, vea la `Example` más adelante en este tema.  
  
### <a name="syntax"></a>Sintaxis  
 Las sugerencias se crean y eliminan con la misma sintaxis que las directivas de preprocesador que crean y eliminan macros. De hecho, el sistema de análisis usa el preprocesador de C/C ++ para evaluar las sugerencias. Para obtener más información acerca de las directivas de preprocesador, vea [#define (directiva) (C/C ++)](../preprocessor/hash-define-directive-c-cpp.md) y [#undef (directiva) (C/C ++)](../preprocessor/hash-undef-directive-c-cpp.md).  
  
 Los elementos de sintaxis inusuales sólo son el `@<`, `@=`, y `@>` las cadenas de reemplazo. Estos son cadenas de reemplazo específicas del archivo de sugerencia que se usan con sólo *mapa* macros. Un mapa es un conjunto de macros relacionadas con eventos, funciones o datos a otros datos, funciones o controladores de eventos. Por ejemplo, `MFC` se utiliza para crear mapas [mapas de mensajes](../mfc/reference/message-maps-mfc.md), y `ATL` usa para crear [asignaciones de objeto](../atl/reference/object-map-macros.md). Las cadenas de reemplazo específicas del archivo de sugerencia indican los elementos inicial, intermedios y finales de un mapa. Solo el nombre de una macro de mapa es significativo. Por lo tanto, cada cadena de reemplazo oculta intencionalmente la implementación de la macro.  
  
 Las sugerencias usan la sintaxis siguiente.  
  
|Sintaxis|Significado|  
|------------|-------------|  
|`#define` *Sugerencia nombre* *cadena de reemplazo*<br /><br /> `#define` *Sugerencia nombre* `(` *parámetro*, ...`)`*cadena de reemplazo*|Una directiva de preprocesador que define una nueva sugerencia o vuelve a definir una sugerencia existente. Después de la directiva, el preprocesador reemplaza cada aparición de *nombre sugerencia* en código fuente con *cadena de reemplazo*.<br /><br /> El segundo formato de sintaxis define una sugerencia de este tipo. Si se produce una sugerencia de este tipo en el código fuente, el preprocesador reemplaza primero cada aparición de *parámetro* en *cadena de reemplazo* con el argumento correspondiente en el código fuente y, a continuación, reemplaza *Sugerencia nombre* con *cadena de reemplazo*.|  
|`@<`|Un determinado archivo de sugerencia *cadena de reemplazo* que indica el inicio de un conjunto de elementos de mapa.|  
|`@=`|Un determinado archivo de sugerencia *cadena de reemplazo* que indica un elemento de mapa intermedio. Un mapa puede tener varios elementos de mapa.|  
|`@>`|Un determinado archivo de sugerencia *cadena de reemplazo* que indica el final de un conjunto de elementos de mapa.|  
|`#undef` *nombre de sugerencia*|La directiva de preprocesador que elimina una sugerencia existente. El nombre de la sugerencia es proporcionado por el *nombre sugerencia* identificador.|  
|`//` *comentario*|Una línea de comentario.|  
|`/*` *comentario* `*/`|Un comentario de varias líneas.|  
  
## <a name="what-macros-require-a-hint"></a>¿Qué Macros que requieren una sugerencia?  
 Ciertos tipos de macros pueden interferir con el sistema de análisis. Esta sección describe los tipos de macros que pueden suponer un problema y el tipo de sugerencia que se puede crear para solucionar el problema.  
  
### <a name="disruptive-macros"></a>Macros de interrupción  
 Algunas macros que el sistema de análisis interprete incorrectamente el código fuente, pero pueden hacer caso omiso sin perjudicar la experiencia de exploración. Por ejemplo, el lenguaje de anotación de código fuente ([SAL](../c-runtime-library/sal-annotations.md)) macros resolver en los atributos de C++ que le ayudan a buscar errores de programación. Si desea omitir las anotaciones SAL al examinar el código, puede crear un archivo de sugerencia que oculte la anotación.  
  
 En el siguiente código fuente, el parámetro de tipo para el `FormatWindowClassName()` función es `PXSTR`, y el nombre de parámetro es `szBuffer`. Sin embargo, los errores del sistema al analizar el `_Pre_notnull_` y `_Post_z_` anotaciones SAL para el tipo de parámetro o el nombre del parámetro.  
  
 **Código fuente:**  
  
```  
static void FormatWindowClassName(_Pre_notnull__Post_z_ PXSTR szBuffer)  
```  
  
 **Estrategia:** Null definición  
  
 La estrategia en esta situación es tratar las anotaciones SAL como si no existen. Para ello, especifique una sugerencia cuya cadena de reemplazo es null. Por consiguiente, el sistema de análisis omite las anotaciones y el **la vista de clases** explorador no las muestra. (Visual C++ incluye un archivo de sugerencia integrado que oculta la anotación SAL).  
  
 **Archivo de sugerencia:**  
  
```  
#define _Pre_notnull_  
```  
  
### <a name="concealed-cc-language-elements"></a>Elementos del lenguaje C o C++ oculto  
 Una razón común para que el sistema de análisis malinterpreta código fuente es si una macro oculta un C o C++ [signo de puntuación](../cpp/punctuators-cpp.md) o [palabra clave](../cpp/keywords-cpp.md) token. Es decir, una macro puede contener la mitad de un par de signos de puntuación, como `<>`, `[]`, `{}`, y `()`.  
  
 En el siguiente código fuente, la `START_NAMESPACE` macro oculta una llave de apertura sin par (`{`).  
  
 **Código fuente:**  
  
```  
#define START_NAMESPACE namespace MyProject {  
```  
  
 **Estrategia:** copia directos  
  
 Si la semántica de una macro es crítica para la experiencia de exploración, cree una sugerencia que es idéntica a la macro. El sistema de análisis resuelve la macro en la definición del archivo de sugerencia.  
  
 Tenga en cuenta que si la macro en el archivo de origen contiene otras macros, las macros sólo se interpretan si ya están en el conjunto de sugerencias vigentes.  
  
 **Archivo de sugerencia:**  
  
```  
#define START_NAMESPACE namespace MyProject {  
```  
  
### <a name="maps"></a>Asignaciones  
 Una asignación se compone de macros que designan un elemento inicial, el elemento final y cero o más elementos intermedios. El sistema de análisis malinterpreta mapas porque cada macro de mapa oculta elementos del lenguaje C o C++ y la sintaxis de una instrucción de C o C++ completa se distribuye en diversas macros independientes.  
  
 El código fuente siguiente define el `BEGIN_CATEGORY_MAP`, `IMPLEMENTED_CATEGORY`, y `END_CATEGORY_MAP` macros.  
  
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
  
 **Estrategia:** identificar elementos de mapa  
  
 Especifique sugerencias para el inicio, el medio (si existe) y el final elementos de un mapa. Utilice las cadenas de reemplazo especiales para mapas, `@<`, `@=`, y `@>`. Para obtener más información, consulte el `Syntax` en este tema.  
  
 **Archivo de sugerencia:**  
  
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
 Las macros compuestas contienen uno o varios de los tipos de macro que se confunden el sistema de análisis.  
  
 El siguiente código fuente contiene la `START_NAMESPACE` (macro), que especifica el inicio de un ámbito de espacio de nombres, y el `BEGIN_CATEGORY_MAP` macro, que especifica el inicio de un mapa.  
  
 **Código fuente:**  
  
```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP  
```  
  
 **Estrategia:** copia directos  
  
 Crear sugerencias para la `START_NAMESPACE` y `BEGIN_CATEGORY_MAP` macros y, a continuación, cree una sugerencia para el `NSandMAP` macro que es la misma que la mostrada anteriormente para el código fuente. Como alternativa, si una macro compuesta consta de sólo macros perjudiciales y espacio en blanco, puede definir una sugerencia cuya cadena de reemplazo sea una definición nula.  
  
 En este ejemplo, suponga que `START_NAMESPACE` ya tiene una sugerencia como se describe en este tema en el `Concealed C/C++ Language Elements` subtítulo. Y suponga `BEGIN_CATEGORY_MAP` tiene una sugerencia como se describió anteriormente en `Maps`.  
  
 **Archivo de sugerencia:**  
  
```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP  
```  
  
### <a name="inconvenient-macros"></a>Macros no convenientes  
 Algunas macros pueden ser interpretados por el sistema de análisis, pero el código fuente es difícil de leer porque la macro es larga o compleja. Por motivos de legibilidad, puede proporcionar una sugerencia que simplifique la presentación de la macro.  
  
 **Código fuente:**  
  
```  
#define STDMETHOD(methodName) HRESULT (STDMETHODCALLTYPE * methodName)  
```  
  
 **Estrategia:** simplificación  
  
 Crear una sugerencia que se muestra una definición de macro más sencilla.  
  
 **Archivo de sugerencia:**  
  
```  
#define STDMETHOD(methodName) void* methodName  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo se acumulan las sugerencias de los archivos de sugerencia. Archivos de detención no se utilizan en este ejemplo.  
  
 La siguiente ilustración muestra algunos de los directorios físicos de un proyecto de Visual C++. Archivos de sugerencia se encuentran en el `vcpackages`, `Debug`, `A1`, y `A2` directorios.  
  
### <a name="hint-file-directories"></a>Directorios de archivos de sugerencia  
 ![Comunes y Nº 45; & proyecto directorios de archivos de sugerencia específico.](../ide/media/hintfile.png "HintFile")  
  
### <a name="directories-and-hint-file-contents"></a>Directorios y el contenido del archivo de sugerencia  
 La siguiente lista muestra los directorios de este proyecto que contienen archivos de sugerencia y el contenido de dichos archivos. Sólo algunas de las muchas sugerencias en el `vcpackages` aparecen directorios de archivos de sugerencia.  
  
-   vcpackages  
  
    ```  
    // vcpackages (partial list)  
    #define _In_  
    #define _In_opt_  
    #define _In_z_  
    #define _In_opt_z_  
    #define _In_count_(size)  
    ```  
  
-   Depurar  
  
    ```  
    // Debug  
    #undef _In_  
    #define OBRACE {  
    #define CBRACE }  
    #define RAISE_EXCEPTION(x) throw (x)  
    #define START_NAMESPACE namespace MyProject {  
    #define END_NAMESPACE }  
    ```  
  
-   A1  
  
    ```  
    // A1  
    #define START_NAMESPACE namespace A1Namespace {  
    ```  
  
-   A2  
  
    ```  
    // A2  
    #undef OBRACE  
    #undef CBRACE  
    ```  
  
### <a name="effective-hints"></a>Sugerencias vigentes  
 En la tabla siguiente se enumera las sugerencias vigentes para los archivos de origen de este proyecto.  
  
-   Archivo de origen: A1_A2_B.cpp  
  
-   Sugerencias vigentes:  
  
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
  
 Las siguientes notas se aplican a la lista anterior.  
  
-   Las sugerencias vigentes pertenecen a la `vcpackages`, `Debug`, `A1`, y `A2` directorios.  
  
-   El **#undef** la directiva en el `Debug` quitado el archivo de sugerencia el `#define _In_` sugerencia en el `vcpackages` archivo de sugerencia del directorio.  
  
-   El archivo de sugerencia en el `A1` redefine el directorio `START_NAMESPACE`.  
  
-   El `#undef` sugerencia en el `A2` directory quitó las sugerencias para `OBRACE` y `CBRACE` en el `Debug` archivo de sugerencia del directorio.  
  
## <a name="see-also"></a>Vea también  
 [Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Crear y controlar el entorno de Windows](../Topic/Creating%20and%20Controlling%20Environment%20Windows.md)   
 [#define (directiva) (C/C ++)](../preprocessor/hash-define-directive-c-cpp.md)   
 [#undef (directiva) (C/C ++)](../preprocessor/hash-undef-directive-c-cpp.md)   
 [Anotaciones SAL](../c-runtime-library/sal-annotations.md)   
 [Mapas de mensajes](../mfc/reference/message-maps-mfc.md)   
 [Macros de mapa de mensajes](../atl/reference/message-map-macros-atl.md)   
 [Macros de mapa de objeto](../atl/reference/object-map-macros.md)