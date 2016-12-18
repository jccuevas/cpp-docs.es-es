---
title: "&lt;filesystem&gt; | Microsoft Docs"
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
  - "filesystem/std::tr2::sys::directory_entry"
  - "filesystem/std::tr2::sys::recursive_directory_iterator"
  - "filesystem/std::tr2::sys::path"
  - "filesystem/std::tr2::sys::filesystem_error"
  - "filesystem/std::tr2::sys::directory_iterator"
  - "<filesystem>"
dev_langs: 
  - "C++"
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
caps.latest.revision: 27
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;filesystem&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Incluya el encabezado \<filesystem\> para tener acceso a las clases y funciones con las que se manipula y recupera información sobre las rutas de acceso, los archivos y los directorios.  
  
## Sintaxis  
  
```cpp  
#include <filesystem>  
using namespace std::tr2::sys;  
```  
  
> [!IMPORTANT]
>  En C\+\+14, el encabezado \<filesystem\> sigue sin ser estándar de C\+\+, aunque está previsto que se estandarice aproximadamente en su forma actual en el marco de tiempo de C\+\+17.  
  
 Este encabezado admite sistemas de archivos para uno de dos tipos amplios de sistemas operativos host: Microsoft Windows y Posix.  
  
 Mientras que la mayoría de las funciones son comunes a ambos sistemas operativos, en este documento se identifican las diferencias. Por ejemplo:  
  
-   Windows admite varios nombres de raíz, como c: o \\\\network\_name. Así que un sistema de archivos consta de un bosque de árboles, cada uno con su propio directorio raíz; por ejemplo, c:\\ o \\\\network\_name\\ y cada uno con su propio directorio actual, para completar una ruta de acceso relativa \(es decir, una que no es una ruta de acceso absoluta\).  
  
-   Posix admite un único árbol, sin nombre de raíz, el directorio raíz único \/ y un único directorio actual.  
  
 Otra diferencia importante es la representación nativa de rutas de acceso:  
  
-   Windows usa una secuencia terminada en null de wchar\_t, codificada como UTF\-16 \(uno o dos elementos para cada carácter\).  
  
-   Posix usa una secuencia terminada en null de char, codificada como UTF\-8 \(uno o varios elementos para cada carácter\).  
  
-   Un objeto de ruta de acceso de clase almacena la ruta de acceso en forma nativa, pero admite la conversión sencilla entre esta forma almacenada y varias formas externas:  
  
    -   Una secuencia terminada en null de char, codificada según la preferencia del sistema operativo.  
  
    -   Una secuencia terminada en null de char, codificada como UTF\-8.  
  
    -   Una secuencia terminada en null de wchar\_t, codificada según la preferencia del sistema operativo.  
  
    -   Una secuencia terminada en null de char16\_t, codificada como UTF\-16.  
  
    -   Una secuencia terminada en null de char32\_t, codificada como UTF\-32.  
  
 Las interconversiones entre estas representaciones se realizan, según sea necesario, mediante el uso de uno o varios aspectos de codecvt. Si no se designa un objeto de configuración regional específica, estas facetas se obtienen de la configuración regional global.  
  
 Otra diferencia es el detalle con el que cada sistema operativo permite especificar permisos de acceso a archivos o directorios:  
  
1.  Windows registra si un archivo es de solo lectura o editable, un atributo que no tiene sentido en el caso de los directorios.  
  
2.  Posix registra si el propietario, el grupo del propietario o todos los usuarios pueden leer, editar o ejecutar un archivo \(examinar si se trata de un directorio\), además de algunos otros permisos.  
  
 Un aspecto común a ambos sistemas es la estructura impuesta en una ruta de acceso una vez superado el nombre de raíz. Para la ruta de acceso c:\/abc\/xyz\/def.ext:  
  
-   El nombre de raíz es c:.  
  
-   El directorio raíz es \/.  
  
-   La ruta de acceso raíz es c:\/.  
  
-   La ruta de acceso relativa es abc\/xyz\/def.ext.  
  
-   La ruta de acceso principal es c:\/abc\/xyz.  
  
-   El nombre de archivo es def.ext.  
  
-   La raíz es def.  
  
-   La extensión es. ext.  
  
 Una diferencia menor es el **separador preferido**, entre la secuencia de directorios de una ruta de acceso. Ambos sistemas operativos permiten escribir una barra diagonal \/, pero en algunos contextos Windows prefiere una barra diagonal inversa \\.  
  
 Por último, una característica importante de los objetos de ruta de acceso es que pueden usarse cada vez que se necesite un argumento filename en las clases definidas en el encabezado \<fstream\>.  
  
 Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos \(C\+\+\)](../standard-library/file-system-navigation.md).  
  
## Clases  
  
|Nombre|Descripción|  
|------------|-----------------|  
|directory\_entry \(Clase\)|Describe un objeto devuelto por un directory\_iterator o un recursive\_directory\_iterator y contiene información sobre|  
|directory\_iterator \(Clase\)|Describe un iterador de entrada que establece una secuencia por los nombres de archivo en un directorio de sistema de archivos.|  
|filesystem\_error \(Clase\)|Clase base para excepciones que se producen para notificar un desbordamiento de sistema de bajo nivel.|  
|path \(Clase\)|Define una clase que almacena un objeto de tipo de plantilla `String` adecuado para su uso como nombre de archivo.|  
|recursive\_directory\_iterator \(Clase\)|Describe un iterador de entrada que establece una secuencia por los nombres de archivo en un directorio de sistema de archivos. El iterador también puede descender a subdirectorios.|  
|[file\_status \(Clase\)](../standard-library/file-status-class.md)|Ajusta un `file_type`.|  
  
## Estructuras  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[space\_info \(Estructura\)](../standard-library/space-info-structure.md)|Contiene información sobre un volumen.|  
  
## Funciones  
 [Funciones de \<filesystem\>](../standard-library/filesystem-functions.md)  
  
## Operadores  
 [\<filesystem\> \(operadores\)](../standard-library/filesystem-operators.md)  
  
## Enumeraciones  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[copy\_option \(Enumeración\)](../Topic/copy_option%20Enumeration%20%3Cfilesystem%3E.md)|Enumeración que se utiliza con [copy\_file](http://msdn.microsoft.com/es-es/4af7a9b0-8861-45ed-b84e-0307f0669d60) y determina el comportamiento si ya existe un archivo de destino.|  
|[directory\_options \(Enumeración\)](../Topic/directory_options%20Enumeration.md)|Enumeración que especifica las opciones de los iteradores de directorio.|  
|[file\_type \(Enumeración\)](../Topic/file_type%20Enumeration.md)|Enumeración de tipos de archivo.|  
|[Enumeración de permisos](../Topic/perms%20Enumeration.md)|Un tipo de máscara de bits que se usa para transmitir los permisos y las opciones de permisos.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)