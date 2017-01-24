---
title: "#import (Directiva) (C++) | Microsoft Docs"
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
  - "#import"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#import (directiva)"
  - ".tlh (archivos)"
  - "COM, archivo de encabezado de biblioteca de tipos"
  - "directiva de importación (#import)"
  - "preprocesador, directivas"
  - "tlbid (modificador)"
  - "tlh (archivos)"
ms.assetid: 787d1112-e543-40d7-ab15-a63d43f4030a
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #import (Directiva) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Se utiliza para incorporar información de una biblioteca de tipos.  El contenido de la biblioteca de tipos se convierte en clases de C\+\+, que describen fundamentalmente las interfaces COM.  
  
## Sintaxis  
  
```  
#import "filename" [attributes]  
#import <filename> [attributes]  
```  
  
#### Parámetros  
 *filename*  
 Especifica la biblioteca de tipos que se va a importar.  El elemento `filename` puede ser uno de los siguientes:  
  
-   El nombre de un archivo que contiene una biblioteca de tipos, como un archivo .olb, .tlb o .dll.  La palabra clave, **file:**, puede preceder a cada nombre de archivo.  
  
-   El identificador de programa de un control en la biblioteca de tipos.  La palabra clave, **progid:**, puede preceder a cada identificador de programa.  Por ejemplo:  
  
    ```  
    #import "progid:my.prog.id.1.5"  
    ```  
  
     Para obtener más información sobre los identificadores de programa, vea [Especificar el identificador y el número de versión de localización](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).  
  
     Tenga en cuenta que al compilar con un compilador cruzado en un sistema operativo de 64 bits, el compilador podrá leer únicamente el subárbol del Registro de 32 bits.  Es posible que desee utilizar el compilador de 64 bits nativo para compilar y registrar una biblioteca de tipos de 64 bits.  
  
-   El identificador de biblioteca de la biblioteca de tipos.  La palabra clave, **libid:**, puede preceder a cada identificador de biblioteca.  Por ejemplo:  
  
    ```  
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")  
    ```  
  
     Si no especifica la versión o el lcid, las [reglas](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) que se aplican a **progid:** también se aplican a **libid:**.  
  
-   Un archivo ejecutable \(.exe\).  
  
-   Un archivo de biblioteca \(.dll\) que contiene un recurso de biblioteca de tipos \(como .ocx\).  
  
-   Un documento compuesto que contiene una biblioteca de tipos.  
  
-   Cualquier otro formato de archivo que API **LoadTypeLib** pueda comprender.  
  
 `attributes`  
 Uno o más [atributos \#import](#_predir_the_23import_directive_import_attributes).  Separa los atributos con un espacio en blanco o con una coma.  Por ejemplo:  
  
```  
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only  
```  
  
 O bien  
  
```  
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only  
```  
  
## Comentarios  
  
##  <a name="_predir_the_23import_directive_searchorderforfilename"></a> Orden de búsqueda de nombre de archivo  
 *filename* va precedido opcionalmente por una especificación de directorio.  El nombre de archivo debe designar un archivo existente.  La diferencia entre las dos formas de sintaxis es el orden en que el preprocesador busca los archivos de biblioteca de tipos cuando no se especifica completamente la ruta de acceso.  
  
|Forma de sintaxis|Acción|  
|-----------------------|------------|  
|Formato con comillas|Indica al preprocesador que busque archivos de biblioteca de tipos primero en el directorio del archivo que contiene la instrucción `#import` y, después, en los directorios de los archivos que incluyen \(`#include`\) ese archivo.  A continuación, el preprocesador busca en las rutas de acceso que se muestran a continuación.|  
|Formato con corchetes angulares|Indica al preprocesador que busque archivos de biblioteca de tipos en las siguientes rutas de acceso:<br /><br /> 1.  La lista de rutas de acceso de la variable de entorno **PATH**<br />2.  La lista de rutas de acceso de la variable de entorno **LIB**<br />3.  La ruta de acceso especificada por la opción de compilador \/I \(directorios de inclusión adicionales\), excepto si el compilador busca una biblioteca de tipos a la que se hizo referencia desde otra biblioteca de tipos con el atributo [no\_registry](../preprocessor/no-registry.md).|  
  
##  <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a> Especificar el identificador y el número de versión de localización  
 Cuando especifica un identificador de programa, también puede especificar el identificador y el número de versión de localización del identificador de programa.  Por ejemplo:  
  
```  
#import "progid:my.prog.id" lcid("0") version("4.0)  
```  
  
 Si no especifica un identificador de localización, se elige un identificador de programa de acuerdo con las reglas siguientes:  
  
-   Si solo hay un identificador de localización, es el que se utiliza.  
  
-   Si hay más de un identificador de localización, se usa el primero con el número de versión 0, 9 o 409.  
  
-   Si hay más de un identificador de localización y ninguno de ellos es 0, 9 o 409, se utiliza el último.  
  
-   Si no especifica un número de versión, se utiliza la versión más reciente.  
  
##  <a name="_predir_the_23import_directive_header_files_created_by_import"></a> Archivos de encabezado creados por la directiva de importación  
 `#import` crea dos archivos de encabezado que reconstruyen el contenido de la biblioteca de tipos en código fuente de C\+\+.  El archivo de encabezado principal es similar al generado por el compilador de Lenguaje de definición de interfaz de Microsoft \(MIDL\), pero con código y datos adicionales generados por el compilador.  El [archivo de encabezado principal](#_predir_the_primary_type_library_header_file) tiene el mismo nombre base que la biblioteca de tipos, más una extensión .TLH.  El archivo de encabezado secundario tiene el mismo nombre base que la biblioteca de tipos, con una extensión .TLI.  Contiene implementaciones para funciones miembro generadas por el compilador y se incluye \(`#include`\) en el archivo de encabezado principal.  
  
 Si se importa una propiedad dispinterface que utilice parámetros byref, \#import no generará la instrucción \_\_declspec\([propiedad](../cpp/property-cpp.md)\) para la función.  
  
 Ambos archivos de encabezado se colocan en el directorio de resultados especificado por la opción \/Fo \(asignar nombre al archivo objeto\).  Después, el compilador los lee y compila como si una directiva `#include` denominase el archivo de encabezado principal.  
  
 Las optimizaciones del compilador siguientes se incluyen en la directiva `#import`:  
  
-   El archivo de encabezado, cuando se crea, tiene la misma marca de tiempo que la biblioteca de tipos.  
  
-   Cuando se procesa `#import`, el compilador comprueba primero si el encabezado existe y está actualizado.  En caso afirmativo, no necesita volver a crearlo.  
  
 La directiva `#import` también participa en la recompilación mínima y puede colocarse en un archivo de encabezado precompilado.  Vea [Crear archivos de encabezado precompilados](../build/reference/creating-precompiled-header-files.md) para obtener más información.  
  
###  <a name="_predir_the_primary_type_library_header_file"></a> Archivo de encabezado principal de la biblioteca de tipos  
 El archivo de encabezado principal de la biblioteca de tipos se compone de siete secciones:  
  
-   Encabezado reutilizable: consta de los comentarios, la instrucción `#include` para COMDEF.H \(que define algunas macros estándar utilizadas en el encabezado\) y otro tipo de información de instalación.  
  
-   Definiciones de tipo y referencias adelantadas: consta de declaraciones de estructura como `struct IMyInterface` y definiciones de tipo.  
  
-   Declaraciones de puntero inteligente: la clase de plantilla `_com_ptr_t` es una implementación de puntero inteligente que encapsula punteros de interfaz y elimina la necesidad de llamar a funciones `AddRef`, **Release**, `QueryInterface`.  Además, oculta la llamada de `CoCreateInstance` al crear un nuevo objeto COM.  En esta sección se utiliza la instrucción de macro **\_COM\_SMARTPTR\_TYPEDEF** para establecer definiciones de tipo de interfaces COM para que sean especializaciones de plantilla de la clase de plantilla [\_com\_ptr\_t](../cpp/com-ptr-t-class.md).  Por ejemplo, para la interfaz **IMyInterface**, el archivo .TLH contendrá:  
  
    ```  
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
    ```  
  
     que el compilador expandirá a:  
  
    ```  
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;  
    ```  
  
     El tipo `IMyInterfacePtr` se puede utilizar a continuación en lugar del puntero de interfaz sin formato `IMyInterface*`.  Por consiguiente, no es necesario llamar a las diversas funciones miembro de **IUnknown**  
  
-   Declaraciones de Typeinfo: principalmente consta de definiciones de clase y otros elementos que exponen los elementos individuales de typeinfo devueltos por **ITypeLib:GetTypeInfo**.  En esta sección, cada typeinfo de la biblioteca de tipos se refleja en el encabezado de forma dependiente de la información de `TYPEKIND`.  
  
-   Definición de GUID de estilo anterior opcional: contiene inicializaciones de las constantes de GUID con nombre.  Son nombres de forma **CLSID\_CoClass** e **IID\_Interface**, similares a los generados por el compilador MIDL.  
  
-   Instrucción `#include` para el encabezado secundario de la biblioteca de tipos.  
  
-   Sección del pie de página reutilizable: actualmente incluye `#pragma pack(pop)`.  
  
 Todas las secciones, excepto la sección del encabezado reutilizable y del pie de página reutilizable, se incluyen en un espacio de nombres con el nombre especificado por la instrucción **library** en el archivo IDL original.  Puede utilizar los nombres del encabezado de la biblioteca de tipos, ya sea mediante una calificación explícita con el nombre del espacio de nombres o incluyendo la siguiente instrucción:  
  
```  
using namespace MyLib;  
```  
  
 inmediatamente después de la instrucción de `#import` en el código fuente.  
  
 El espacio de nombres se puede suprimir utilizando el atributo [no\_namespace](#_predir_no_namespace) de la directiva `#import`.  Sin embargo, la supresión del espacio de nombres puede dar lugar a conflictos de nombres.  También se puede cambiar el nombre del espacio de nombres mediante el atributo [rename\_namespace](#_predir_rename_namespace).  
  
 El compilador proporciona la ruta de acceso completa a cualquier dependencia de la biblioteca de tipos necesaria para la biblioteca de tipos que está actualmente en procesamiento.  La ruta de acceso se escribe, en forma de comentarios, en el encabezado de la biblioteca de tipos \(.TLH\) que el compilador genera para cada biblioteca de tipos procesada.  
  
 Si una biblioteca de tipos contiene referencias a tipos definidos en otras bibliotecas de tipos, el archivo .TLH incluirá comentarios del siguiente tipo:  
  
```  
//  
// Cross-referenced type libraries:  
//  
//  #import "c:\path\typelib0.tlb"  
//  
```  
  
 El nombre de archivo real en el comentario de `#import` es la ruta de acceso completa de la biblioteca de tipos a la que se hace referencia cruzada, almacenada en el Registro.  Si detecta errores que se deben a la falta de definiciones de tipo, compruebe los comentarios en el encabezado del archivo .TLH para ver qué bibliotecas de tipos dependientes han de importarse primero.  Los errores probables son errores de sintaxis \(por ejemplo, C2143, C2146, C2321\), C2501 \(faltan especificadores decl\) o C2433 \(“inline” no permitida en la declaración de datos\) mientras se compila el archivo .TLI.  
  
 Debe determinar los comentarios de dependencia que, de otro modo, los encabezados de sistema no proporcionarían, e indicar una directiva `#import` en algún momento antes de la directiva `#import` de la biblioteca de tipos dependiente para resolver los errores.  
  
 Para obtener más información, vea el artículo referente a la posibilidad de que los métodos contenedores \#import provoquen una infracción de acceso \(Q242527\) o el referente a los errores del compilador al usar \#import con XML \(Q269194\) de Knowledge Base.  Encontrará artículos de Knowledge Base en los elementos multimedia de MSDN Library o en la dirección [http:\/\/support.microsoft.com\/support\/](http://support.microsoft.com/support/).  
  
##  <a name="_predir_the_23import_directive_import_attributes"></a> Atributos \#import  
 `#import` puede incluir opcionalmente uno o varios atributos.  Estos atributos indican al compilador que modifique el contenido de los encabezados de la biblioteca de tipos.  Se puede utilizar un símbolo de barra diagonal inversa \(**\\**\) para incluir líneas adicionales en una única instrucción `#import`.  Por ejemplo:  
  
```  
#import "test.lib" no_namespace \  
   rename("OldName", "NewName")  
```  
  
 Para obtener más información, vea [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md).  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)   
 [Compatibilidad con COM del compilador](../cpp/compiler-com-support.md)