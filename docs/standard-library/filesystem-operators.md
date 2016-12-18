---
title: "&lt;filesystem&gt; (operadores) | Microsoft Docs"
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
  - "FILESYSTEM/std::experimental::filesystem::v1::operator=="
  - "std::experimental::filesystem::v1::operator=="
  - "FILESYSTEM/std::experimental::filesystem::v1::operator!="
  - "std::experimental::filesystem::v1::operator!="
  - "FILESYSTEM/std::experimental::filesystem::v1::operator<"
  - "std::experimental::filesystem::v1::operator<"
  - "FILESYSTEM/std::experimental::filesystem::v1::operator<="
  - "std::experimental::filesystem::v1::operator<="
  - "FILESYSTEM/std::experimental::filesystem::v1::operator>"
  - "std::experimental::filesystem::v1::operator>"
  - "FILESYSTEM/std::experimental::filesystem::v1::operator>="
  - "std::experimental::filesystem::v1::operator>="
  - "FILESYSTEM/std::experimental::filesystem::v1::operator/"
  - "std::experimental::filesystem::v1::operator/"
  - "FILESYSTEM/std::experimental::filesystem::v1::operator<<"
  - "std::experimental::filesystem::v1::operator<<"
  - "FILESYSTEM/std::experimental::filesystem::v1::operator>>"
  - "std::experimental::filesystem::v1::operator>>"
dev_langs: 
  - "C++"
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
caps.latest.revision: 12
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;filesystem&gt; (operadores)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los operadores realizan una comparación léxica de dos rutas de acceso como cadenas. Use la función **equivalent** para determinar si dos rutas de acceso \(por ejemplo, una relativa y una absoluta\) hacen referencia al mismo archivo o directorio del disco.  
  
```  
C:\root > D:\root: false  
C:\root > C:\root\sub: false  
C:\root > C:\roo: true  
  
```  
  
 Para obtener más información, vea [Exploración del sistema de archivos \(C\+\+\)](../standard-library/file-system-navigation.md).  
  
## operator\=\=  
  
```  
bool operator==(const path& left, const path& right) noexcept;  
```  
  
 La función devuelve left.native\(\) \=\= right.native\(\).  
  
## operator\!\=  
  
```  
bool operator!=(const path& left, const path& right) noexcept;  
```  
  
 La función devuelve \!\(left \=\= right\).  
  
## operator\<  
  
```  
bool operator<(const path& left, const path& right) noexcept;  
```  
  
 La función devuelve left.native\(\) \< right.native\(\).  
  
## operator\<\=  
  
```  
bool operator<=(const path& left, const path& right) noexcept;  
```  
  
 La función devuelve \!\(right \< left\).  
  
## operator\>  
  
```  
bool operator>(const path& left, const path& right) noexcept;  
```  
  
 La función devuelve right \< left.  
  
## operator\>\=  
  
```  
bool operator>=(const path& left, const path& right) noexcept;  
```  
  
 La función devuelve \!\(left \< right\).  
  
## operator\/  
  
```  
path operator/(const path& left, const path& right);  
```  
  
 La función ejecuta lo siguiente:  
  
```  
basic_string<Elem, Traits> str;  
path ans = left;  
return (ans /= right);  
  
```  
  
## operator\<\<  
  
```  
template<class Elem, class Traits>    basic_ostream<Elem, Traits>&    operator<<(basic_ostream<Elem, Traits>& os, const path& pval);  
```  
  
 La función devuelve os \<\< pval.string\<Elem, Traits\>\(\).  
  
## operator\>\>  
  
```  
template<class Elem, class Traits>    basic_istream<Elem, Traits>&    operator<<(basic_istream<Elem, Traits>& is, const path& pval);  
```  
  
 La función ejecuta lo siguiente:  
  
```  
basic_string<Elem, Traits> str;  
is >> str;  
pval = str;  
return (is);  
  
```  
  
## operator\=\=  
  
```  
bool operator==(const path& left, const path& right) noexcept;  
```  
  
 La función devuelve left.native\(\) \=\= right.native\(\).  
  
## Vea también  
 [path \(Clase, biblioteca de plantillas estándar de C\+\+\)](../standard-library/path-class-cpp-standard-template-library.md)   
 [Exploración del sistema de archivos \(C\+\+\)](../standard-library/file-system-navigation.md)   
 [\<filesystem\>](../standard-library/filesystem.md)