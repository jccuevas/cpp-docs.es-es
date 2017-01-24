---
title: "Clase directory_entry | Microsoft Docs"
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
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator const std::experimental::filesystem::v1::path &"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::directory_entry"
  - "std::experimental::filesystem::v1::directory_entry::directory_entry"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator="
  - "std::experimental::filesystem::v1::directory_entry::operator="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::assign"
  - "std::experimental::filesystem::v1::directory_entry::assign"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::replace_filename"
  - "std::experimental::filesystem::v1::directory_entry::replace_filename"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::path"
  - "std::experimental::filesystem::v1::directory_entry::path"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::status"
  - "std::experimental::filesystem::v1::directory_entry::status"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::symlink_status"
  - "std::experimental::filesystem::v1::directory_entry::symlink_status"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator<"
  - "std::experimental::filesystem::v1::directory_entry::operator<"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator=="
  - "std::experimental::filesystem::v1::directory_entry::operator=="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator!="
  - "std::experimental::filesystem::v1::directory_entry::operator!="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator<="
  - "std::experimental::filesystem::v1::directory_entry::operator<="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator>"
  - "std::experimental::filesystem::v1::directory_entry::operator>"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator>="
  - "std::experimental::filesystem::v1::directory_entry::operator>="
dev_langs: 
  - "C++"
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
caps.latest.revision: 17
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Clase directory_entry
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto devuelto por `*X`, donde *X* es un [directory\_iterator](../standard-library/directory-iterator-class.md) o un [recursive\_directory\_iterator](../standard-library/recursive-directory-iterator-class.md).  
  
## Sintaxis  
  
```  
class directory_entry;  
```  
  
## Comentarios  
 La clase almacena un objeto de tipo [clase path](../standard-library/path-class-cpp-standard-template-library.md).`path` puede ser una [ruta de acceso](../standard-library/path-class-cpp-standard-template-library.md) o un tipo derivado de `path`. También almacena dos valores [file\_type](../Topic/file_type%20Enumeration.md): uno que representa lo que se conoce sobre el estado del nombre del archivo almacenado y otra que representa lo que se conoce sobre el estado del vínculo simbólico del nombre del archivo.  
  
 Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos \(C\+\+\)](../standard-library/file-system-navigation.md).  
  
## assign  
  
```  
void assign(const PFX path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());  
```  
  
 La función miembro asigna pval a mypath, stat a mystat y symstat a mysymstat.  
  
## directory\_entry  
  
```  
directory_entry() = default;  
directory_entry(const directory_entry&) = default;  
directory_entry(directory_entry&&) noexcept = default;  
explicit directory_entry(const PFX path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());  
```  
  
 Los constructores predeterminados se comportan según lo previsto. El cuarto constructor inicializa mypath para pval, mystat para stat\_arg y mysymstat para symstat\_arg.  
  
## operator\!\=  
  
```  
bool operator!=(const directory_entry& right) const noexcept;  
  
```  
  
 La función miembro devuelve \!\(\*this \=\= right\).  
  
## operator\=  
  
```  
directory_entry& operator=(const directory_entry&) = default;  
directory_entry& operator=(directory_entry&&) noexcept = default;  
  
```  
  
 Los operadores predeterminados de asignación de miembros se comportan según lo previsto.  
  
## operator\=\=  
  
```  
bool operator==(const directory_entry& right) const noexcept;  
```  
  
 La función miembro devuelve mypath \=\= right.mypath.  
  
## operator\<  
  
```  
  
bool operator<(const directory_entry& right) const noexcept;  
  
```  
  
 La función miembro devuelve mypath \< right.mypath.  
  
## operator\<\=  
  
```  
bool operator<=(const directory_entry& right) const noexcept;  
```  
  
 La función miembro devuelve \!\(right \< \*this\).  
  
## operator\>  
  
```  
bool operator>(const directory_entry& right) const noexcept;  
```  
  
 La función miembro devuelve right \< \*this.  
  
## operator\>\=  
  
```  
bool operator>=(const directory_entry& right) const noexcept;  
  
```  
  
 La función miembro devuelve \!\(\*this \< right\).  
  
## operator const path\_type&  
  
```  
operator const path&() const; // retained  
```  
  
 El operador miembro devuelve mypath.  
  
## path  
  
```  
const PFX path& path() const noexcept;  
```  
  
 La función miembro devuelve mypath.  
  
## replace\_filename  
  
```  
void replace_filename(const PFX path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());  
```  
  
 La función miembro reemplaza mypath con mypath.parent\_path\(\) \/ pval, mystat con stat\_arg y mysymstat con symstat\_arg  
  
## status  
  
```  
file_status status() const;  
file_status status(  
    error_code& ec) const noexcept;  
Otherwise, mystat = status(mypval).  
  
```  
  
 Ambas funciones miembro devuelven mystat que posiblemente primero se modifica según se muestra a continuación:  
  
1.  Si status\_known\(mystat\), no es necesario hacer nada.  
  
2.  De lo contrario, si \!status\_known\(mysymstat\) && \!is\_symlink\(mysymstat\), entonces mystat \= mysymstat.  
  
## symlink\_status  
  
```  
file_status symlink_status() const;  
file_status symlink_status(  
    error_code& ec) const noexcept;  
```  
  
 Ambas funciones miembro devuelven mysymstat que posiblemente primero se modifica según se muestra a continuación: si status\_known\(mysymstat\), no es necesario hacer nada. En caso contrario, mysymstat \= symlink\_status\(mypval\).  
  
## Requisitos  
 **Encabezado:** filesystem  
  
 **Espacio de nombres:** std::tr2::sys  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem\>](../standard-library/filesystem.md)