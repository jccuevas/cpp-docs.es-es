---
title: directory_entry (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- FILESYSTEM/std::experimental::filesystem::directory_entry::directory_entry
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator=
- FILESYSTEM/std::experimental::filesystem::directory_entry::assign
- FILESYSTEM/std::experimental::filesystem::directory_entry::replace_filename
- FILESYSTEM/std::experimental::filesystem::directory_entry::path
- FILESYSTEM/std::experimental::filesystem::directory_entry::status
- FILESYSTEM/std::experimental::filesystem::directory_entry::symlink_status
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator<
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator==
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator!=
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator<=
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator>
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator>=
dev_langs:
- C++
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 0bd6b73c99eccffc7661cc4b43f97ab46890c5ee
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="directoryentry-class"></a>directory_entry (Clase)
Describe un objeto devuelto por `*X`, donde *X* es un [directory_iterator](../standard-library/directory-iterator-class.md) o un [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class directory_entry;  
```  
  
## <a name="remarks"></a>Comentarios  
 La clase almacena un objeto de tipo [path](../standard-library/path-class.md). La `path` almacenada puede ser una instancia de la [path (Clase)](../standard-library/path-class.md) o de un tipo que se deriva de `path`. También almacena dos valores [file_type](../standard-library/filesystem-enumerations.md#file_type): uno que representa lo que se conoce sobre el estado del nombre de archivo almacenado y otra que representa lo que se conoce sobre el estado del vínculo simbólico del nombre de archivo.  
  
 Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md).  
  
## <a name="assign"></a>assign  
  
```  
void assign(const std::experimental::filesystem::path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());
```  
  
 La función miembro asigna pval a mypath, stat a mystat y symstat a mysymstat.  
  
## <a name="directoryentry"></a>directory_entry  
  
```  
directory_entry() = default;  
directory_entry(const directory_entry&) = default;  
directory_entry(directory_entry&&) noexcept = default;  
explicit directory_entry(const std::experimental::filesystem::path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());
```  
  
 Los constructores predeterminados se comportan según lo previsto. El cuarto constructor inicializa mypath para pval, mystat para stat_arg y mysymstat para symstat_arg.  
  
## <a name="operator"></a>operator!=  
  
```  
bool operator!=(const directory_entry& right) const noexcept;  
```  
  
 La función miembro devuelve !(*this == right).  
  
## <a name="operator"></a>operator=  
  
```  
directory_entry& operator=(const directory_entry&) = default;  
directory_entry& operator=(directory_entry&&) noexcept = default;  
```  
  
 Los operadores predeterminados de asignación de miembros se comportan según lo previsto.  
  
## <a name="operator"></a>operator==  
  
```  
bool operator==(const directory_entry& right) const noexcept;  
```  
  
 La función miembro devuelve mypath == right.mypath.  
  
## <a name="operator"></a>operator<  
  
```  
 
bool operator<(const directory_entry& right) const noexcept;  
```  
  
 La función miembro devuelve mypath < right.mypath.  
  
## <a name="operator"></a>operator<=  
  
```  
bool operator<=(const directory_entry& right) const noexcept;  
```  
  
 La función miembro devuelve !(right \< *this).  
  
## <a name="operator"></a>operator>  
  
```  
bool operator>(const directory_entry& right) const noexcept;  
```  
  
 La función miembro devuelve right \< *this.  
  
## <a name="operator"></a>operator>=  
  
```  
bool operator>=(const directory_entry& right) const noexcept;  
```  
  
 La función miembro devuelve !(*this < right).  
  
## <a name="operator-const-pathtype"></a>operator const path_type&  
  
``` 
 operator const std::experimental::filesystem::path&() const; 
```  
  
 El operador miembro devuelve mypath.  
  
## <a name="path"></a>ruta de acceso  
  
```  
const std::experimental::filesystem::path& path() const noexcept;  
```  
  
 La función miembro devuelve mypath.  
  
## <a name="replacefilename"></a>replace_filename  
  
```  
void replace_filename(
    const std::experimental::filesystem::path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());
```  
  
 La función miembro reemplaza mypath con mypath.parent_path() / pval, mystat con stat_arg y mysymstat con symstat_arg  
  
## <a name="status"></a>status  
  
```  
file_status status() const; 
file_status status(error_code& ec) const noexcept;  
```  
  
 Ambas funciones miembro devuelven mystat que posiblemente primero se modifica según se muestra a continuación:  
  
1.  Si status_known(mystat), no es necesario hacer nada.  
  
2.  De lo contrario, si !status_known(mysymstat) && !is_symlink(mysymstat), entonces mystat = mysymstat.  
  
## <a name="symlinkstatus"></a>symlink_status  
  
```  
file_status symlink_status() const; 
file_status symlink_status(error_code& ec) const noexcept;  
```  
  
 Ambas funciones miembro devuelven mysymstat que posiblemente primero se modifica según se muestra a continuación: si status_known(mysymstat), no es necesario hacer nada. En caso contrario, mysymstat = symlink_status(mypval).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<experimental/filesystem>  
  
 **Espacio de nombres:** std::experimental::filesystem  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem>](../standard-library/filesystem.md)


