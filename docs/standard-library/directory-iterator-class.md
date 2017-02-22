---
title: "directory_iterator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "filesystem/std::tr2::sys::directory_iterator"
  - "directory_iterator"
  - "filesystem/std::experimental::filesystem::v1::_Directory_iterator::_Directory_iterator"
  - "filesystem/std::experimental::filesystem::v1::directory_iterator"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::directory_iterator"
  - "std::experimental::filesystem::v1::directory_iterator::directory_iterator"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::increment"
  - "std::experimental::filesystem::v1::directory_iterator::increment"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::operator="
  - "std::experimental::filesystem::v1::directory_iterator::operator="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::operator=="
  - "std::experimental::filesystem::v1::directory_iterator::operator=="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::operator!="
  - "std::experimental::filesystem::v1::directory_iterator::operator!="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::operator*"
  - "std::experimental::filesystem::v1::directory_iterator::operator*"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::operator->"
  - "std::experimental::filesystem::v1::directory_iterator::operator->"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::operator++"
  - "std::experimental::filesystem::v1::directory_iterator::operator++"
dev_langs: 
  - "C++"
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# directory_iterator (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un iterador de entrada que establece secuencias en los nombres de archivo en un directorio. En el caso de un iterador X, la expresión \*X se evalúa como un objeto de la clase directory\_entry que contiene el nombre de archivo y cualquier elemento conocido sobre su estado.  
  
 La clase almacena un objeto de tipo path, denominado mydir aquí a efectos de la exposición, que representa el nombre del directorio que se va a secuenciar y un objeto de directory\_entry tipo denominado myentry aquí, que representa el nombre de archivo actual en la secuencia del directorio. Un objeto construido de forma predeterminada de tipo directory\_entry tiene un nombre de ruta de acceso mydir vacío y representa el iterador de final de secuencia.  
  
 Por ejemplo, si tenemos el directorio abc con entradas def y ghi, el código:  
  
 `for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`  
  
 llamará a visit con los argumentos path\("abc\/def"\) y path\("abc\/ghi"\).  
  
 Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos \(C\+\+\)](../standard-library/file-system-navigation.md).  
  
## Sintaxis  
  
```  
class directory_iterator;  
```  
  
## directory\_iterator::directory\_iterator  
  
```cpp  
directory_iterator() noexcept;  
explicit directory_iterator(const path& pval);  
directory_iterator(const path& pval,  
    error_code& ec) noexcept;  
directory_iterator(const directory_iterator&) = default;  
directory_iterator(directory_iterator&&) noexcept = default;  
```  
  
 El primer constructor crea un iterador de final de secuencia. Los constructores segundo y tercero almacenan pval en mydir y luego intentan abrir y leer mydir como un directorio. Si es correcto, almacenan el primer nombre de archivo en el directorio de myentry; de lo contrario, generan un iterador de final de secuencia.  
  
 Los constructores predeterminados se comportan según lo previsto.  
  
## directory\_iterator::increment  
  
```cpp  
directory_iterator& increment(  
    error_code& ec) noexcept;  
```  
  
 La función intenta avanzar al siguiente nombre de archivo del directorio. Si es correcto, almacena ese nombre de archivo en myentry; en caso contrario, produce un iterador de final de secuencia.  
  
## directory\_iterator::operator\!\=  
  
```cpp  
bool operator!=(const directory_iterator& right) const;  
```  
  
 El operador miembro devuelve \!\(\*this \=\= right\).  
  
## directory\_iterator::operator\=  
  
```cpp  
directory_iterator& operator=(const directory_iterator&) = default;  
directory_iterator& operator=(directory_iterator&&) noexcept = default;  
```  
  
 Los operadores predeterminados de asignación de miembros se comportan según lo previsto.  
  
## directory\_iterator::operator\=\=  
  
```cpp  
bool operator==(const directory_iterator& right) const;  
  
```  
  
 El operador miembro solo devuelve true si \*this y right son iteradores de final de secuencia o si ninguno de los dos lo son.  
  
## directory\_iterator::operator\*  
  
```cpp  
const directory_entry& operator*() const;  
```  
  
 El operador miembro devuelve myentry.  
  
## directory\_iterator::operator\-\>  
  
```cpp  
const directory_entry *operator->() const;  
```  
  
 La función miembro devuelve &\*\*this.  
  
## directory\_iterator::operator\+\+  
  
```cpp  
directory_iterator& operator++();  
directory_iterator& operator++(int);  
```  
  
 La primera función miembro llama a increment\(\) y luego devuelve \*this. La segunda función miembro hace una copia del objeto, llama a increment\(\) y luego devuelve la copia.  
  
## Requisitos  
 **Encabezado:** filesystem  
  
 **Espacio de nombres:** std::experimental::filesystem::v1  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem\>](../standard-library/filesystem.md)   
 [Exploración del sistema de archivos \(C\+\+\)](../standard-library/file-system-navigation.md)