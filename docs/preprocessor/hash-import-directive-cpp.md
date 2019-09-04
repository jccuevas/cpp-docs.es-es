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
ms.openlocfilehash: afd05e7380ec3838fe9763be23ccfae338adb4fb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220267"
---
# <a name="import-directive-c"></a>Directiva #import (C++)

**C++Cuestión**

Se utiliza para incorporar información de una biblioteca de tipos. El contenido de la biblioteca de tipos se convierte en clases de C++, que describen fundamentalmente las interfaces COM.

## <a name="syntax"></a>Sintaxis

> **#import** *atributos*"*filename*" \[] \
> **#import**> atributos de nombre dearchivo\[] \<

### <a name="parameters"></a>Parámetros

*extensión*\
Especifica la biblioteca de tipos que se va a importar. El *nombre de archivo* puede ser uno de los siguientes tipos:

- El nombre de un archivo que contiene una biblioteca de tipos, como un archivo .olb, .tlb o .dll. La palabra clave `file:`,, puede preceder a cada nombre de archivo.

- El identificador de programa de un control en la biblioteca de tipos. La palabra clave `progid:`,, puede preceder a cada ProgID. Por ejemplo:

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   Para obtener más información sobre los ProgID, vea [especificar el identificador de localización y el número de versión](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).

   Cuando se usa un compilador cruzado de 32 bits en un sistema operativo de 64 bits, el compilador solo puede leer el subárbol del registro de 32 bits. Es posible que desee utilizar el compilador de 64 bits nativo para compilar y registrar una biblioteca de tipos de 64 bits.

- El identificador de biblioteca de la biblioteca de tipos. La palabra clave `libid:`,, puede preceder a cada identificador de biblioteca. Por ejemplo:

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   `version` Si no especifica ni `lcid`, las [reglas](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) aplicadas a `progid:` también se aplican `libid:`a.

- Un archivo ejecutable (.exe).

- Un archivo de biblioteca (. dll) que contiene un recurso de biblioteca de tipos (como. ocx).

- Un documento compuesto que contiene una biblioteca de tipos.

- Cualquier otro formato de archivo que pueda entender la API **LoadTypeLib** .

*sus*\
Uno o más [atributos de #import](#_predir_the_23import_directive_import_attributes). Separa los atributos con un espacio en blanco o con una coma. Por ejemplo:

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

O bien

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>Comentarios

### <a name="_predir_the_23import_directive_searchorderforfilename"></a>Orden de búsqueda de nombre de archivo

el *nombre de archivo* está precedido opcionalmente por una especificación de directorio. El nombre de archivo debe designar un archivo existente. La diferencia entre las dos formas de sintaxis es el orden en que el preprocesador busca los archivos de biblioteca de tipos cuando no se especifica completamente la ruta de acceso.

|Forma de sintaxis|.|
|-----------------|------------|
|Formato con comillas|Indica al preprocesador que busque primero los archivos de biblioteca de tipos en el directorio del archivo que contiene la instrucción **#import** y, a continuación, en los directorios de los archivos que`#include`incluyan () ese archivo. A continuación, el preprocesador busca en las rutas de acceso que se muestran a continuación.|
|Formato con corchetes angulares|Indica al preprocesador que busque archivos de biblioteca de tipos en las siguientes rutas de acceso:<br /><br /> 1.  La `PATH` lista de rutas de la variable de entorno<br />2.  La `LIB` lista de rutas de la variable de entorno<br />3.  La ruta de acceso especificada por la opción del compilador [/i](../build/reference/i-additional-include-directories.md) , salvo que el compilador busca una biblioteca de tipos a la que se hizo referencia desde otra biblioteca de tipos con el atributo [no_registry](../preprocessor/no-registry.md) .|

### <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>Especificar el identificador de localización y el número de versión

Cuando especifica un identificador de programa, también puede especificar el identificador y el número de versión de localización del identificador de programa. Por ejemplo:

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

Si no especifica un identificador de localización, se elige un ProgID según las siguientes reglas:

- Si solo hay un identificador de localización, se usa uno.

- Si hay más de un identificador de localización, se usa el primero con el número de versión 0, 9 o 409.

- Si hay más de un identificador de localización y ninguno de ellos es 0, 9 o 409, se usa el último.

- Si no especifica un número de versión, se utiliza la versión más reciente.

###  <a name="_predir_the_23import_directive_header_files_created_by_import"></a>Archivos de encabezado creados por la importación

**#import** crea dos archivos de encabezado que reconstruyen el contenido de C++ la biblioteca de tipos en el código fuente. El archivo de encabezado principal es similar al generado por el compilador Lenguaje de definición de interfaz de Microsoft (MIDL), pero con código y datos adicionales generados por el compilador. El [archivo de encabezado principal](#_predir_the_primary_type_library_header_file) tiene el mismo nombre base que la biblioteca de tipos, más una. Extensión de TLH. El archivo de encabezado secundario tiene el mismo nombre base que la biblioteca de tipos, con una extensión .TLI. Contiene implementaciones para funciones miembro generadas por el compilador y se incluye (`#include`) en el archivo de encabezado principal.

Si se importa una propiedad dispinterface que `byref` usa parámetros, **#import** no genera una instrucción [_ _ declspec (Property)](../cpp/property-cpp.md) para la función.

Ambos archivos de encabezado se colocan en el directorio de salida especificado por la opción [/FO (nombre del archivo objeto)](../build/reference/fo-object-file-name.md) . Después, el compilador los Lee y compila como si el archivo de encabezado principal fuera nombrado `#include` por una directiva.

Las siguientes optimizaciones del compilador acompañan a la directiva **#import** :

- El archivo de encabezado, cuando se crea, tiene la misma marca de tiempo que la biblioteca de tipos.

- Cuando se procesa **#import** , el compilador comprueba primero si el encabezado existe y está actualizado. En caso afirmativo, no es necesario volver a crearlo.

La Directiva de **#import** también participa en la recompilación mínima y puede colocarse en un archivo de encabezado precompilado.  Para obtener más información, vea [crear archivos de encabezado](../build/creating-precompiled-header-files.md)precompilados.

### <a name="_predir_the_primary_type_library_header_file"></a>Archivo de encabezado de la biblioteca de tipos principal

El archivo de encabezado principal de la biblioteca de tipos se compone de siete secciones:

- Encabezado reutilizable: Consta de los comentarios `#include` , la instrucción para COMDEF. H (que define algunas macros estándar utilizadas en el encabezado) y otra información de configuración diversa.

- Referencias adelantadas y definiciones de cadena: Consta de declaraciones de estructura como `struct IMyInterface` y definiciones de tipo.

- Declaraciones de puntero inteligente: La clase `_com_ptr_t` de plantilla es un puntero inteligente. Encapsula los punteros de interfaz y elimina la necesidad de llamar `AddRef`a las funciones, `QueryInterface` `Release`y. También oculta la `CoCreateInstance` llamada al crear un nuevo objeto com. En esta sección se utiliza la `_COM_SMARTPTR_TYPEDEF` instrucción de macro para establecer definiciones de tipo de interfaces com como especializaciones de plantilla de la clase de plantilla [_com_ptr_t](../cpp/com-ptr-t-class.md) . Por ejemplo, para la `IMyInterface`interfaz, el. El archivo TLH contendrá:

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   que el compilador expandirá a:

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   El tipo `IMyInterfacePtr` se puede utilizar a continuación en lugar del puntero de interfaz sin formato `IMyInterface*`. Por consiguiente, no es necesario llamar a las diversas `IUnknown` funciones miembro

- Declaraciones de TypeInfo: Se compone principalmente de definiciones de clase y otros elementos que exponen los elementos `ITypeLib:GetTypeInfo`TypeInfo individuales devueltos por. En esta sección, cada typeinfo de la biblioteca de tipos se refleja en el encabezado de forma dependiente de la información de `TYPEKIND`.

- Definición de GUID de estilo antiguo opcional: Contiene inicializaciones de las constantes GUID con nombre. Estos nombres tienen el formato `CLSID_CoClass` y `IID_Interface`, de forma similar a los generados por el compilador de MIDL.

- Instrucción `#include` para el encabezado secundario de la biblioteca de tipos.

- REUTILIZADOR de pie de página: Incluye `#pragma pack(pop)`actualmente.

Todas las secciones, excepto la sección de encabezado reutilizable y de pie de página reutilizable, se incluyen en `library` un espacio de nombres con el nombre especificado por la instrucción en el archivo IDL original. Puede utilizar los nombres del encabezado de la biblioteca de tipos mediante una calificación explícita con el nombre del espacio de nombres. O bien, puede incluir la siguiente instrucción:

```cpp
using namespace MyLib;
```

inmediatamente después de la instrucción **#import** en el código fuente.

El espacio de nombres se puede suprimir mediante el atributo [no_namespace](no-namespace.md)) de la directiva **#import** . Sin embargo, la supresión del espacio de nombres puede dar lugar a conflictos de nombres. También se puede cambiar el nombre del espacio de nombres por el atributo [rename_namespace](rename-namespace.md) .

El compilador proporciona la ruta de acceso completa a cualquier dependencia de biblioteca de tipos necesaria para la biblioteca de tipos que se está procesando actualmente. La ruta de acceso se escribe, en forma de comentarios, en el encabezado de la biblioteca de tipos (.TLH) que el compilador genera para cada biblioteca de tipos procesada.

Si una biblioteca de tipos contiene referencias a tipos definidos en otras bibliotecas de tipos, el archivo .TLH incluirá comentarios del siguiente tipo:

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

El nombre de archivo real en el comentario **#import** es la ruta de acceso completa de la biblioteca de tipos a la que se hace referencia cruzada, tal como se almacena en el registro. Si se producen errores causados por definiciones de tipos que faltan, compruebe los comentarios en el encabezado de. TLH para ver qué bibliotecas de tipos dependientes se deben importar primero. Los errores probables son errores de sintaxis (por ejemplo, C2143, C2146, C2321), C2501 (faltan especificadores decl) o C2433 (“inline” no permitida en la declaración de datos) mientras se compila el archivo .TLI.

Para resolver los errores de dependencia, Determine cuál de los comentarios de dependencia no se proporciona de otro modo para los encabezados del sistema y, a continuación, proporcione una **#import** Directiva en algún momento antes de la directiva **#import** de la biblioteca de tipos dependientes.

### <a name="_predir_the_23import_directive_import_attributes"></a>atributos de #import

**#import** puede incluir opcionalmente uno o más atributos. Estos atributos indican al compilador que modifique el contenido de los encabezados de la biblioteca de tipos. Se puede usar un **\\** símbolo de barra diagonal inversa () para incluir líneas adicionales en una única instrucción **#import** . Por ejemplo:

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

Para obtener más información, vea [atributos de #import](../preprocessor/hash-import-attributes-cpp.md).

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)\
[Compatibilidad con COM del compilador](../cpp/compiler-com-support.md)
