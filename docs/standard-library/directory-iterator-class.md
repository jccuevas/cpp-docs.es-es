---
title: directory_iterator (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- filesystem/std::experimental::filesystem::directory_iterator
- directory_iterator
- filesystem/std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator
- FILESYSTEM/std::experimental::filesystem::directory_iterator::directory_iterator
- FILESYSTEM/std::experimental::filesystem::directory_iterator::increment
- FILESYSTEM/std::experimental::filesystem::directory_iterator::operator=
- FILESYSTEM/std::experimental::filesystem::directory_iterator::operator==
- FILESYSTEM/std::experimental::filesystem::directory_iterator::operator!=
- FILESYSTEM/std::experimental::filesystem::directory_iterator::operator*
- FILESYSTEM/std::experimental::filesystem::directory_iterator::operator->
- FILESYSTEM/std::experimental::filesystem::directory_iterator::operator++
dev_langs:
- C++
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
caps.latest.revision: 19
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 4eb80d5309a7749c1374d72be16798dbeea33bdc
ms.lasthandoff: 02/24/2017

---
# <a name="directoryiterator-class"></a>directory_iterator (Clase)
Describe un iterador de entrada que establece secuencias en los nombres de archivo en un directorio. En el caso de un iterador X, la expresión *X se evalúa como un objeto de la clase directory_entry que contiene el nombre de archivo y cualquier elemento conocido sobre su estado.  
  
 La clase almacena un objeto de tipo path, denominado mydir aquí a efectos de la exposición, que representa el nombre del directorio que se va a secuenciar y un objeto de directory_entry tipo denominado myentry aquí, que representa el nombre de archivo actual en la secuencia del directorio. Un objeto construido de forma predeterminada de tipo directory_entry tiene un nombre de ruta de acceso mydir vacío y representa el iterador de final de secuencia.  
  
 Por ejemplo, si tenemos el directorio abc con entradas def y ghi, el código:  
  
 `for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`  
  
 llamará a visit con los argumentos path("abc/def") y path("abc/ghi").  
  
 Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class directory_iterator;  
```  
  
## <a name="directoryiteratordirectoryiterator"></a>directory_iterator::directory_iterator  
  
```  
directory_iterator() noexcept;  
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;  
directory_iterator(const directory_iterator&) = default;  
directory_iterator(directory_iterator&&) noexcept = default;  
```  
  
 El primer constructor crea un iterador de final de secuencia. Los constructores segundo y tercero almacenan pval en mydir y luego intentan abrir y leer mydir como un directorio. Si es correcto, almacenan el primer nombre de archivo en el directorio de myentry; de lo contrario, generan un iterador de final de secuencia.  
  
 Los constructores predeterminados se comportan según lo previsto.  
  
## <a name="directoryiteratorincrement"></a>directory_iterator::increment  
  
```  
directory_iterator& increment(error_code& ec) noexcept;  
```  
  
 La función intenta avanzar al siguiente nombre de archivo del directorio. Si es correcto, almacena ese nombre de archivo en myentry; en caso contrario, produce un iterador de final de secuencia.  
  
## <a name="directoryiteratoroperator"></a>directory_iterator::operator!=  
  
```  
bool operator!=(const directory_iterator& right) const;
```  
  
 El operador miembro devuelve !(*this == right).  
  
## <a name="directoryiteratoroperator"></a>directory_iterator::operator=  
  
```  
directory_iterator& operator=(const directory_iterator&) = default;  
directory_iterator& operator=(directory_iterator&&) noexcept = default;  
```  
  
 Los operadores predeterminados de asignación de miembros se comportan según lo previsto.  
  
## <a name="directoryiteratoroperator"></a>directory_iterator::operator==  
  
```  
bool operator==(const directory_iterator& right) const;
```  
  
 El operador miembro solo devuelve true si *this y right son iteradores de final de secuencia o si ninguno de los dos lo son.  
  
## <a name="directoryiteratoroperator"></a>directory_iterator::operator*  
  
```  
const directory_entry& operator*() const;
```  
  
 El operador miembro devuelve myentry.  
  
## <a name="directoryiteratoroperator-"></a>directory_iterator::operator->  
  
```  
const directory_entry * operator->() const;
```  
  
 La función miembro devuelve &**this.  
  
## <a name="directoryiteratoroperator"></a>directory_iterator::operator++  
  
```  
directory_iterator& operator++();
directory_iterator& operator++(int);
```  
  
 La primera función miembro llama a increment() y luego devuelve *this. La segunda función miembro hace una copia del objeto, llama a increment() y luego devuelve la copia.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<experimental/filesystem>  
  
 **Espacio de nombres:** std::experimental::filesystem  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem>](../standard-library/filesystem.md)   
 [Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md)


