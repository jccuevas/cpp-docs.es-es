---
title: "Clase filesystem_error | Microsoft Docs"
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
  - "filesystem/std::tr2::sys::filesystem_error"
dev_langs: 
  - "C++"
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
caps.latest.revision: 13
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Clase filesystem_error
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una base para todas las excepciones que se producen para notificar un desbordamiento de sistema de bajo nivel.  
  
## Sintaxis  
  
```  
class filesystem_error    : public system_error;  
```  
  
## Comentarios  
 Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un error de las funciones \<filesystem\>. Almacena un objeto de tipo string, denominado mymesg aquí a efectos de la exposición. También almacena dos objetos de tipo path, denominados mypval1 y mypval2.  
  
## filesystem\_error::filesystem\_error  
  
```  
filesystem_error(const string& what_arg, error_code ec);  
filesystem_error(const string& what_arg,  
    const path& pval1, error_code ec);  
filesystem_error(const string& what_arg,  
    const path& pval1, const path& pval2, error_code ec);  
```  
  
 El primer constructor crea su propio mensaje a partir de what\_arg y ec. El segundo constructor también crea su propio mensaje a partir de pval1 y lo almacena en mypval1. El tercer constructor también crea su propio mensaje a partir de pval1, que almacena en mypval1, y a partir de pval2, que almacena en mypval2.  
  
## filesystem\_error::path1  
  
```  
const path& path1() const noexcept;  
  
```  
  
 La función miembro devuelve mypval1.  
  
## filesystem\_error::path2  
  
```  
const path& path2() const noexcept;  
  
```  
  
 La función miembro devuelve mypval2.  
  
## filesystem\_error::what  
  
```  
const char *what() const noexcept;  
```  
  
 La función miembro devuelve un puntero a un NTBS, preferiblemente creado a partir de runtime\_error::what\(\), system\_error::what\(\), mymesg, mypval1.native\_string\(\) y mypval2.native\_string\(\).  
  
## Requisitos  
 **Encabezado:** filesystem  
  
 **Espacio de nombres:** std::tr2::sys  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [system\_error \(Clase\)](../standard-library/system-error-class.md)   
 [\<filesystem\>](../standard-library/filesystem.md)   
 [\<exception\>](../standard-library/exception.md)