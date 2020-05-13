---
title: '#import (Directiva) (C++)'
ms.date: 08/29/2019
f1_keywords:
- '#import'
helpviewer_keywords:
- .tlh files
- '#import directive'
- import directive (#import)
- tlh files
- tlbid switch
- preprocessor, directives
- COM, type library header file
ms.assetid: 787d1112-e543-40d7-ab15-a63d43f4030a
ms.openlocfilehash: 9cdfef091b659151f427c381e386f0e83396e741
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332064"
---
# <a name="import-directive-c"></a>Directiva #import (C++)

**Específicos de C++**

Se utiliza para incorporar información de una biblioteca de tipos. El contenido de la biblioteca de tipos se convierte en clases de C++, que describen fundamentalmente las interfaces COM.

## <a name="syntax"></a>Sintaxis

> **#import** " nombre \[de*archivo*" *atributos*]
> **#import** \<*atributos* *de nombre de archivo*> \[]

### <a name="parameters"></a>Parámetros

*Nombre*\
Especifica la biblioteca de tipos que se va a importar. El nombre de *archivo* puede ser uno de los siguientes tipos:

- El nombre de un archivo que contiene una biblioteca de tipos, como un archivo .olb, .tlb o .dll. La palabra `file:`clave , , puede preceder a cada nombre de archivo.

- El identificador de programa de un control en la biblioteca de tipos. La palabra `progid:`clave , , puede preceder a cada progid. Por ejemplo:

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   Para obtener más información sobre progids, consulte [Especificación del ID](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)de localización y el número de versión .

   Cuando se usa un compilador cruzado de 32 bits en un sistema operativo de 64 bits, el compilador solo puede leer el subárbol del Registro de 32 bits. Es posible que desee utilizar el compilador de 64 bits nativo para compilar y registrar una biblioteca de tipos de 64 bits.

- El identificador de biblioteca de la biblioteca de tipos. La palabra `libid:`clave , , puede preceder a cada identificador de biblioteca. Por ejemplo:

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   Si no `version` especifica o `lcid`, las `progid:` [reglas](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) aplicadas `libid:`también se aplican a .

- Un archivo ejecutable (.exe).

- Un archivo de biblioteca (.dll) que contiene un recurso de biblioteca de tipos (por ejemplo, un archivo .ocx).

- Un documento compuesto que contiene una biblioteca de tipos.

- Cualquier otro formato de archivo que pueda entender la API **LoadTypeLib.**

*Atributos*\
Uno o más [atributos #import](#_predir_the_23import_directive_import_attributes). Separa los atributos con un espacio en blanco o con una coma. Por ejemplo:

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

O bien

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>Observaciones

### <a name="search-order-for-filename"></a><a name="_predir_the_23import_directive_searchorderforfilename"></a>Orden de búsqueda para el nombre de archivo

*nombre de archivo* está precedido opcionalmente por una especificación de directorio. El nombre de archivo debe designar un archivo existente. La diferencia entre las dos formas de sintaxis es el orden en que el preprocesador busca los archivos de biblioteca de tipos cuando no se especifica completamente la ruta de acceso.

|Forma de sintaxis|Acción|
|-----------------|------------|
|Formato con comillas|Indica al preprocesador que busque primero los archivos de biblioteca de tipos en el directorio del archivo`#include`que contiene la instrucción #import y, **a** continuación, en los directorios de los archivos que incluyan ( ) ese archivo. A continuación, el preprocesador busca en las rutas de acceso que se muestran a continuación.|
|Formato con corchetes angulares|Indica al preprocesador que busque archivos de biblioteca de tipos en las siguientes rutas de acceso:<br /><br /> 1. `PATH` La lista de rutas de variables de entorno<br />2. `LIB` La lista de rutas de variables de entorno<br />3. La ruta de acceso especificada por la opción del compilador [/I,](../build/reference/i-additional-include-directories.md) excepto que el compilador está buscando una biblioteca de tipos a la que se hizo referencia desde otra biblioteca de tipos con el atributo [no_registry.](../preprocessor/no-registry.md)|

### <a name="specify-the-localization-id-and-version-number"></a><a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>Especifique el ID de localización y el número de versión

Cuando especifica un identificador de programa, también puede especificar el identificador y el número de versión de localización del identificador de programa. Por ejemplo:

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

Si no especifica un ID de localización, se elige un progid de acuerdo con las siguientes reglas:

- Si solo hay un identificador de localización, se usa ese.

- Si hay más de un identificador de localización, se utiliza el primero con el número de versión 0, 9 o 409.

- Si hay más de un identificador de localización y ninguno de ellos es 0, 9 o 409, se usa el último.

- Si no especifica un número de versión, se utiliza la versión más reciente.

### <a name="header-files-created-by-import"></a><a name="_predir_the_23import_directive_header_files_created_by_import"></a>Archivos de encabezado creados por importación

**#import** crea dos archivos de encabezado que reconstruyen el contenido de la biblioteca de tipos en el código fuente de C++. El archivo de encabezado principal es similar al generado por el compilador de lenguaje de definición de interfaz de Microsoft (MIDL), pero con datos y código generados por el compilador adicionales. El archivo de [encabezado principal](#_predir_the_primary_type_library_header_file) tiene el mismo nombre base que la biblioteca de tipos, además de un archivo . Extensión TLH. El archivo de encabezado secundario tiene el mismo nombre base que la biblioteca de tipos, con una extensión .TLI. Contiene implementaciones para funciones miembro generadas por el compilador y se incluye (`#include`) en el archivo de encabezado principal.

Si importa una propiedad dispinterface que utiliza `byref` parámetros, **#import** no genera una instrucción [__declspec(property)](../cpp/property-cpp.md) para la función.

Ambos archivos de encabezado se colocan en el directorio de salida especificado por la opción [/Fo (archivo](../build/reference/fo-object-file-name.md) de objeto de nombre). A continuación, el compilador los lee y compila como si `#include` el archivo de encabezado principal fuera nombrado por una directiva.

Las siguientes optimizaciones del compilador vienen con la directiva **#import:**

- El archivo de encabezado, cuando se crea, tiene la misma marca de tiempo que la biblioteca de tipos.

- Cuando se procesa **#import,** el compilador comprueba primero si el encabezado existe y está actualizado. En caso afirmativo, no es necesario volver a crearlo.

La directiva **#import** también participa en la reconstrucción mínima y se puede colocar en un archivo de encabezado precompilado.  Para obtener más información, consulte Creación de archivos de [encabezado precompilados.](../build/creating-precompiled-header-files.md)

### <a name="primary-type-library-header-file"></a><a name="_predir_the_primary_type_library_header_file"></a>Archivo de encabezado de biblioteca de tipo principal

El archivo de encabezado principal de la biblioteca de tipos se compone de siete secciones:

- Encabezado reutilizable: consta de los comentarios, la instrucción `#include` para COMDEF.H (que define algunas macros estándar utilizadas en el encabezado) y otro tipo de información de instalación.

- Definiciones de tipo y referencias adelantadas: consta de declaraciones de estructura como `struct IMyInterface` y definiciones de tipo.

- Declaraciones de puntero inteligente: la clase `_com_ptr_t` de plantilla es un puntero inteligente. Encapsula punteros de interfaz y elimina `AddRef`la `Release`necesidad `QueryInterface` de llamar a , , y funciones. También oculta la `CoCreateInstance` llamada al crear un nuevo objeto COM. En esta sección `_COM_SMARTPTR_TYPEDEF` se utiliza la instrucción macro para establecer typedefs de interfaces COM como especializaciones de plantilla de la clase de plantilla [_com_ptr_t.](../cpp/com-ptr-t-class.md) Por ejemplo, `IMyInterface`para la interfaz , el archivo . El archivo TLH contendrá:

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   que el compilador expandirá a:

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   El tipo `IMyInterfacePtr` se puede utilizar a continuación en lugar del puntero de interfaz sin formato `IMyInterface*`. Por lo tanto, no hay necesidad `IUnknown` de llamar a las diversas funciones miembro

- Declaraciones Typeinfo: consiste principalmente en definiciones de clase y `ITypeLib:GetTypeInfo`otros elementos que exponen los elementos typeinfo individuales devueltos por . En esta sección, cada typeinfo de la biblioteca de tipos se refleja en el encabezado de forma dependiente de la información de `TYPEKIND`.

- Definición de GUID de estilo anterior opcional: contiene inicializaciones de las constantes de GUID con nombre. Estos nombres tienen `CLSID_CoClass` `IID_Interface`el formulario y , similares a los generados por el compilador MIDL.

- Instrucción `#include` para el encabezado secundario de la biblioteca de tipos.

- Sección del pie de página reutilizable: actualmente incluye `#pragma pack(pop)`.

Todas las secciones, excepto la sección de encabezado reutilizable y de pie de `library` página reutilizable, se incluyen en un espacio de nombres con su nombre especificado por la instrucción en el archivo IDL original. Puede usar los nombres del encabezado de biblioteca de tipos mediante una calificación explícita mediante el nombre del espacio de nombres. O bien, puede incluir la siguiente declaración:

```cpp
using namespace MyLib;
```

inmediatamente después de la **#import** instrucción en el código fuente.

El espacio de nombres se puede suprimir mediante el atributo [no_namespace](no-namespace.md)) de la directiva **#import.** Sin embargo, la supresión del espacio de nombres puede dar lugar a conflictos de nombres. El atributo [rename_namespace](rename-namespace.md) también puede cambiar el nombre del espacio de nombres.

El compilador proporciona la ruta de acceso completa a cualquier dependencia de biblioteca de tipos requerida por la biblioteca de tipos que está procesando actualmente. La ruta de acceso se escribe, en forma de comentarios, en el encabezado de la biblioteca de tipos (.TLH) que el compilador genera para cada biblioteca de tipos procesada.

Si una biblioteca de tipos contiene referencias a tipos definidos en otras bibliotecas de tipos, el archivo .TLH incluirá comentarios del siguiente tipo:

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

El nombre de archivo real en el **#import** comentario es la ruta de acceso completa de la biblioteca de tipos de referencia cruzada, tal como se almacena en el registro. Si encuentra errores causados por definiciones de tipo que faltan, compruebe los comentarios en la cabecera del archivo . TLH para ver qué bibliotecas de tipos dependientes pueden necesitar importarse primero. Los errores probables son errores de sintaxis (por ejemplo, C2143, C2146, C2321), C2501 (faltan especificadores decl) o C2433 (“inline” no permitida en la declaración de datos) mientras se compila el archivo .TLI.

Para resolver errores de dependencia, determine cuáles de los comentarios de dependencia no se proporcionan de otro modo por los encabezados del sistema y, a continuación, proporcione una directiva **#import** en algún momento antes de la directiva **#import** de la biblioteca de tipos dependiente.

### <a name="import-attributes"></a><a name="_predir_the_23import_directive_import_attributes"></a>atributos #import

**#import** puede incluir opcionalmente uno o varios atributos. Estos atributos indican al compilador que modifique el contenido de los encabezados de la biblioteca de tipos. Se puede**\\**utilizar un símbolo de barra diagonal inversa ( ) para incluir líneas adicionales en una sola instrucción **#import.** Por ejemplo:

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

Para obtener más información, consulte [#import atributos](../preprocessor/hash-import-attributes-cpp.md).

**Específicos de C++: END**

## <a name="see-also"></a>Consulte también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)\
[Soporte COM del compilador](../cpp/compiler-com-support.md)
