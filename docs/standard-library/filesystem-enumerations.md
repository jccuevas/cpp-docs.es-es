---
title: '&lt;filesystem&gt; (Enumeraciones) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- filesystem/std::filesystem::copy_options
- filesystem/std::experimental::filesystem::copy_options
- filesystem/std::filesystem::directory_options
- filesystem/std::experimental::filesystem::directory_options
- filesystem/std::filesystem::file_type
- filesystem/std::experimental::filesystem::file_type
- filesystem/std::filesystem::perms
- filesystem/std::experimental::filesystem::perms
dev_langs: C++
ms.assetid: 0096c046-d101-464c-8259-b878a48280b0
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f0bb076a2cfd8a97c2a3cfc5dc8f33e5390c27a0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ltfilesystemgt-enumerations"></a>&lt;filesystem&gt; (Enumeraciones)
En este tema, se documentan las enumeraciones del encabezado del sistema de archivos.

## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<experimental/filesystem>    
 **Espacio de nombres:** std::experimental::filesystem  

##  <a name="copy_options"></a>  copy_options
Una enumeración de valores de máscara de bits que se usa con las funciones [copy](http://msdn.microsoft.com/en-us/4af7a9b0-8861-45ed-b84e-0307f0669d60) y [copy_file](http://msdn.microsoft.com/en-us/4af7a9b0-8861-45ed-b84e-0307f0669d60) para especificar el comportamiento.  
  
### <a name="syntax"></a>Sintaxis  
```cpp  
enum class copy_options {      
   none = 0,  
   skip_existing = 1,  
   overwrite_existing = 2,  
   update_existing = 4,  
   recursive = 8,  
   copy_symlinks = 16,  
   skip_symlinks = 32,  
   directories_only = 64,  
   create_symlinks = 128,  
   create_hard_links = 256  
};  
```  
  
### <a name="values"></a>Valores  
  
|`Name`|Descripción|  
|------------|-----------------|  
|`none`|Realice el comportamiento predeterminado de la operación.|  
|`skip_existing`|No copie el archivo si ya existe, no informe de un error.|  
|`overwrite_existing`|Sobrescriba el archivo si ya existe.|  
|`update_existing`|Sobrescriba el archivo si ya existe y es más antiguo que el reemplazo.|  
|`recursive`|Copie de forma recursiva subdirectorios y su contenido.|  
|`copy_symlinks`|Copie vínculos simbólicos como vínculos simbólicos, en lugar de copiar los archivos a los que apuntan.|  
|`skip_symlinks`|Ignore vínculos simbólicos.|  
|`directories_only`|Itere solo en directorios, omita archivos.|  
|`create_symlinks`|Establezca vínculos simbólicos en lugar de copiar archivos. Una ruta de acceso absoluta debe usarse como la ruta de acceso de origen a menos que el destino sea el directorio actual.|  
|`create_hard_links`|Establezca vínculos físicos en lugar de copiar archivos.|  
  

##  <a name="directory_options"></a> directory_options
Especifica si se deben seguir los vínculos simbólicos a directorios o bien si se deben ignorar.  
  
### <a name="syntax"></a>Sintaxis  
```cpp  
enum class directory_options {  
   none = 0,  
   follow_directory_symlink 
};  
```  
  
### <a name="values"></a>Valores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`none`|Comportamiento predeterminado: omitir vínculos simbólicos a directorios. Permiso denegado es un error.|  
|`follow_directory_symlink`|se tratan los vínculos simbólicos a directorios como directorios reales.|  
  
##  <a name="file_type"></a>  file_type
Enumeración de tipos de archivo. Los valores admitidos son normales, el directorio, not_found y desconocido.  
  
### <a name="syntax"></a>Sintaxis  
```cpp  
enum class file_type {
    not_found = -1, 
    none, 
    regular, 
    directory, 
    symlink,
    block, 
    character, 
    fifo, 
    socket, 
    unknown
};  
```  
  
### <a name="values"></a>Valores  
  
|Nombre|Valor|Descripción|  
|----------|-----------|-----------------|  
|`not_found`|-1|Representa un archivo que no existe.|  
|`none`|0|Representa un archivo que no tiene ningún atributo de tipo. (No se admite).|  
|`regular`|1|Representa un archivo de disco convencional.|  
|`directory`|2|Representa un directorio.|  
|`symlink`|3|Representa un vínculo simbólico. (No se admite).|  
|`block`|4|Representa un archivo de bloque especial en sistemas basados en UNIX. (No se admite).|  
|`character`|5|Representa un archivo de carácter especial en sistemas basados en UNIX. (No se admite).|  
|`fifo`|6|Representa un archivo FIFO en sistemas basados en UNIX. (No se admite).|  
|`socket`|7|Representa un socket en sistemas basados en UNIX. (No se admite).|  
|`unknown`|8|Representa un archivo cuyo estado no se puede determinar.|  
  
##  <a name="perms"></a>  perms
Marcas para los permisos de archivo. Los valores admitidos son básicamente “readonly” y all. Para los archivos de solo lectura, no se establece ningún bit *_write. En caso contrario, se establece el bit `all` (0x0777).  
  
### <a name="syntax"></a>Sintaxis  
```cpp  
enum class perms {// names for permissions
   none = 0,
   owner_read = 0400,  // S_IRUSR
   owner_write = 0200, // S_IWUSR
   owner_exec = 0100,  // S_IXUSR
   owner_all = 0700,   // S_IRWXU
   group_read = 040,   // S_IRGRP
   group_write = 020,  // S_IWGRP
   group_exec = 010,   // S_IXGRP
   group_all = 070,    // S_IRWXG
   others_read = 04,   // S_IROTH
   others_write = 02,  // S_IWOTH
   others_exec = 01,   // S_IXOTH
   others_all = 07,    // S_IRWXO
   all = 0777,
   set_uid = 04000,    // S_ISUID
   set_gid = 02000,    // S_ISGID
   sticky_bit = 01000, // S_ISVTX
   mask = 07777,
   unknown = 0xFFFF,
   add_perms = 0x10000,
   remove_perms = 0x20000,
   resolve_symlinks = 0x40000
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem>](../standard-library/filesystem.md)

