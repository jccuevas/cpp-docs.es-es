---
title: '#Importar directiva) (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#import'
dev_langs:
- C++
helpviewer_keywords:
- .tlh files
- '#import directive'
- import directive (#import)
- tlh files
- tlbid switch
- preprocessor, directives
- COM, type library header file
ms.assetid: 787d1112-e543-40d7-ab15-a63d43f4030a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5bb62a61762c2c4e042777376f4d2b9f3ffc747e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429752"
---
# <a name="import-directive-c"></a>#import (Directiva) (C++)
**Específicos de C++**  
  
Se utiliza para incorporar información de una biblioteca de tipos. El contenido de la biblioteca de tipos se convierte en clases de C++, que describen fundamentalmente las interfaces COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#import "filename" [attributes]  
#import <filename> [attributes]  
```  
  
### <a name="parameters"></a>Parámetros  
*filename*  
Especifica la biblioteca de tipos que se va a importar. *nombre de archivo* puede ser uno de los siguientes:  
  
- El nombre de un archivo que contiene una biblioteca de tipos, como un archivo .olb, .tlb o .dll. La palabra clave, **archivo:**, puede preceder a cada nombre de archivo.  
  
- El identificador de programa de un control en la biblioteca de tipos. La palabra clave, **progid:**, puede preceder a cada identificador de programa. Por ejemplo:  
  
    ```  
    #import "progid:my.prog.id.1.5"  
    ```  
  
     Para obtener más información sobre los ProgID, consulte [especificando el identificador de localización y el número de versión](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).  
  
     Tenga en cuenta que al compilar con un compilador cruzado en un sistema operativo de 64 bits, el compilador podrá leer únicamente el subárbol del Registro de 32 bits. Es posible que desee utilizar el compilador de 64 bits nativo para compilar y registrar una biblioteca de tipos de 64 bits.  
  
- El identificador de biblioteca de la biblioteca de tipos. La palabra clave, **libid:**, puede preceder a cada identificador de biblioteca. Por ejemplo:  
  
    ```  
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")  
    ```  
  
     Si no especifica versión o el lcid, el [reglas](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) que se aplican a **progid:** también se aplican a **libid:**.  
  
- Un archivo ejecutable (.exe).  
  
- Un archivo de biblioteca (.dll) que contiene un recurso de biblioteca de tipos (como .ocx).  
  
- Un documento compuesto que contiene una biblioteca de tipos.  
  
- Cualquier otro formato de archivo que pueda entender el **LoadTypeLib** API.  
  
*Atributos*  
Uno o varios [atributos #import](#_predir_the_23import_directive_import_attributes). Separa los atributos con un espacio en blanco o con una coma. Por ejemplo:  
  
```  
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only  
```  
  
O bien  
  
```  
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only  
```  
  
## <a name="remarks"></a>Comentarios  
  
##  <a name="_predir_the_23import_directive_searchorderforfilename"></a> Orden de búsqueda de nombre de archivo  

*nombre de archivo* va precedido opcionalmente por una especificación de directorio. El nombre de archivo debe designar un archivo existente. La diferencia entre las dos formas de sintaxis es el orden en que el preprocesador busca los archivos de biblioteca de tipos cuando no se especifica completamente la ruta de acceso.  
  
|Forma de sintaxis|Acción|  
|-----------------|------------|  
|Formato con comillas|Indica al preprocesador que busque archivos de biblioteca de tipos primero en el directorio del archivo que contiene el **#import** instrucción y, a continuación, en los directorios de los archivos que incluyen (`#include`) ese archivo. A continuación, el preprocesador busca en las rutas de acceso que se muestran a continuación.|  
|Formato con corchetes angulares|Indica al preprocesador que busque archivos de biblioteca de tipos en las siguientes rutas de acceso:<br /><br /> 1.  El `PATH` lista de la ruta de la variable de entorno<br />2.  El `LIB` lista de la ruta de la variable de entorno<br />3.  La ruta de acceso especificada por el /I (más directorios de inclusión) la opción del compilador, excepto que el compilador busca una biblioteca de tipos que se hace referencia desde otra biblioteca de tipos con el [no_registry](../preprocessor/no-registry.md) atributo.|  
  
##  <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a> Especifica el identificador de localización y el número de versión  

Cuando especifica un identificador de programa, también puede especificar el identificador y el número de versión de localización del identificador de programa. Por ejemplo:  
  
```  
#import "progid:my.prog.id" lcid("0") version("4.0)  
```  
  
Si no especifica un identificador de localización, se elige un identificador de programa de acuerdo con las reglas siguientes:  
  
- Si solo hay un identificador de localización, es el que se utiliza.  
  
- Si hay más de un identificador de localización, se usa el primero con el número de versión 0, 9 o 409.  
  
- Si hay más de un identificador de localización y ninguno de ellos es 0, 9 o 409, se utiliza el último.  
  
- Si no especifica un número de versión, se utiliza la versión más reciente.  
  
##  <a name="_predir_the_23import_directive_header_files_created_by_import"></a> Archivos de encabezado creados con la importación  

**#import** crea dos archivos de encabezado que reconstruyen el contenido de la biblioteca de tipos en código fuente de C++. El archivo de encabezado principal es similar al generado por el compilador de Lenguaje de definición de interfaz de Microsoft (MIDL), pero con código y datos adicionales generados por el compilador. El [archivo de encabezado principal](#_predir_the_primary_type_library_header_file) tiene el mismo nombre base que la biblioteca de tipos, más una. Extensión TLH. El archivo de encabezado secundario tiene el mismo nombre base que la biblioteca de tipos, con una extensión .TLI. Contiene implementaciones para funciones miembro generadas por el compilador y se incluye (`#include`) en el archivo de encabezado principal.  
  
Si importa una propiedad dispinterface que utilice parámetros byref, #import no generará __declspec ([propiedad](../cpp/property-cpp.md)) instrucción para la función.  
  
Ambos archivos de encabezado se colocan en el directorio de resultados especificado por la opción /Fo (asignar nombre al archivo objeto). Después, el compilador los lee y compila como si una directiva `#include` denominase el archivo de encabezado principal.  
  
Las siguientes optimizaciones del compilador vienen con el **#import** directiva:  
  
- El archivo de encabezado, cuando se crea, tiene la misma marca de tiempo que la biblioteca de tipos.  
  
- Cuando **#import** está procesado, el compilador comprueba primero si el encabezado existe y está actualizado. En caso afirmativo, no necesita volver a crearlo.  
  
El **#import** directiva también participa en la recompilación mínima y puede colocarse en un archivo de encabezado precompilado. Consulte [crear archivos de encabezado precompilado](../build/reference/creating-precompiled-header-files.md) para obtener más información.  
  
###  <a name="_predir_the_primary_type_library_header_file"></a> Archivo de encabezado de biblioteca de tipos principal  
El archivo de encabezado principal de la biblioteca de tipos se compone de siete secciones:  
  
- Encabezado reutilizable: consta de los comentarios, la instrucción `#include` para COMDEF.H (que define algunas macros estándar utilizadas en el encabezado) y otro tipo de información de instalación.  
  
- Definiciones de tipo y referencias adelantadas: consta de declaraciones de estructura como `struct IMyInterface` y definiciones de tipo.  
  
- Declaraciones de puntero inteligente: la clase de plantilla `_com_ptr_t` es una implementación de puntero inteligente que encapsula punteros de interfaz y elimina la necesidad de llamar a `AddRef`, `Release`, `QueryInterface` funciones. Además, oculta la llamada de `CoCreateInstance` al crear un nuevo objeto COM. En esta sección utiliza la instrucción de macro `_COM_SMARTPTR_TYPEDEF` para establecer definiciones de tipos de interfaces COM que sean especializaciones de plantilla de la [_com_ptr_t](../cpp/com-ptr-t-class.md) clase de plantilla. Por ejemplo, para la interfaz `IMyInterface`, el. Archivo TLH contendrá:  
  
    ```  
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
    ```  
  
     que el compilador expandirá a:  
  
    ```  
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;  
    ```  
  
     El tipo `IMyInterfacePtr` se puede utilizar a continuación en lugar del puntero de interfaz sin formato `IMyInterface*`. Por lo tanto, no hay ninguna necesidad de llamar a las diversas `IUnknown` funciones miembro  
  
- Las declaraciones de TypeInfo: principalmente consta de definiciones de clase y otros elementos que exponen los elementos individuales de typeinfo devueltos por `ITypeLib:GetTypeInfo`. En esta sección, cada typeinfo de la biblioteca de tipos se refleja en el encabezado de forma dependiente de la información de `TYPEKIND`.  
  
- Definición de GUID de estilo anterior opcional: contiene inicializaciones de las constantes de GUID con nombre. Estos son los nombres de la forma `CLSID_CoClass` y `IID_Interface`, similares a los generados por el compilador MIDL.  
  
- Instrucción `#include` para el encabezado secundario de la biblioteca de tipos.  
  
- Sección del pie de página reutilizable: actualmente incluye `#pragma pack(pop)`.  
  
Todas las secciones, excepto la sección de código reutilizable encabezado reutilizable y pie de página, se incluyen en un espacio de nombres con el nombre especificado por el `library` instrucción en el archivo IDL original. Puede utilizar los nombres del encabezado de la biblioteca de tipos, ya sea mediante una calificación explícita con el nombre del espacio de nombres o incluyendo la siguiente instrucción:  
  
```  
using namespace MyLib;  
```  
  
inmediatamente después de la **#import** instrucción en el código fuente.  
  
El espacio de nombres se puede suprimir utilizando el [no_namespace](#_predir_no_namespace) atributo de la **#import** directiva. Sin embargo, la supresión del espacio de nombres puede dar lugar a conflictos de nombres. El espacio de nombres también se puede cambiar el nombre por el [rename_namespace](#_predir_rename_namespace) atributo.  
  
El compilador proporciona la ruta de acceso completa a cualquier dependencia de la biblioteca de tipos necesaria para la biblioteca de tipos que está actualmente en procesamiento. La ruta de acceso se escribe, en forma de comentarios, en el encabezado de la biblioteca de tipos (.TLH) que el compilador genera para cada biblioteca de tipos procesada.  
  
Si una biblioteca de tipos contiene referencias a tipos definidos en otras bibliotecas de tipos, el archivo .TLH incluirá comentarios del siguiente tipo:  
  
```  
//  
// Cross-referenced type libraries:  
//  
//  #import "c:\path\typelib0.tlb"  
//  
```  
  
El nombre de archivo real en el **#import** comentario es la ruta de acceso completa de la biblioteca de tipos de referencia cruzada, tal como está almacenado en el registro. Si detecta errores que se deben a la falta de definiciones de tipo, compruebe los comentarios en el encabezado del archivo .TLH para ver qué bibliotecas de tipos dependientes han de importarse primero. Los errores probables son errores de sintaxis (por ejemplo, C2143, C2146, C2321), C2501 (faltan especificadores decl) o C2433 (“inline” no permitida en la declaración de datos) mientras se compila el archivo .TLI.  
  
Debe determinar cuál de la dependencia de comentarios no se proporcionan en caso contrario para con encabezados de sistema y, a continuación, proporcionan un **#import** la directiva en algún momento antes de la **#import** la directiva del dependiente biblioteca de tipos para resolver los errores.  
  
Para obtener más información, vea el artículo referente a la posibilidad de que los métodos contenedores #import provoquen una infracción de acceso (Q242527) o el referente a los errores del compilador al usar #import con XML (Q269194) de Knowledge Base. Puede encontrar artículos de Knowledge Base en el medio de MSDN Library o en [Microsoft Support](https://support.microsoft.com/).  
  
##  <a name="_predir_the_23import_directive_import_attributes"></a> atributos #import  
 
**#import** puede incluir opcionalmente uno o varios atributos. Estos atributos indican al compilador que modifique el contenido de los encabezados de la biblioteca de tipos. Una barra diagonal inversa (**\\**) símbolo puede usarse para incluir líneas adicionales en una sola **#import** instrucción. Por ejemplo:  
  
```  
#import "test.lib" no_namespace \  
   rename("OldName", "NewName")  
```  
  
Para obtener más información, consulte [atributos #import](../preprocessor/hash-import-attributes-cpp.md).  
  
**FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)<br/>
[Compatibilidad con COM del compilador](../cpp/compiler-com-support.md)