---
title: "file_status (Clase) | Microsoft Docs"
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
  - "filesystem/std::tr2::sys::file_status"
  - "filesystem/std::tr2::sys::file_status::perms"
  - "filesystem/std::tr2::sys::file_status::type"
dev_langs: 
  - "C++"
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
caps.latest.revision: 15
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# file_status (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Contiene un [file\_type](../Topic/file_type%20Enumeration.md).  
  
## Sintaxis  
  
```  
class file_status;  
```  
  
## file\_status::file\_status  
  
```  
explicit file_status(file_type ftype = file_type::none,    perms mask = perms::unknown) noexcept;file_status(const file_status&) noexcept = default;file_status(file_status&&) noexcept = default;  
```  
  
## file\_status::operator\=  
  
```  
file_status& operator=(const file_status&) noexcept = default;  
file_status& operator=(file_status&&) nexcept = default;  
```  
  
 Los operadores predeterminados de asignación de miembros se comportan según lo previsto.  
  
## type  
  
```  
file_type type() const noexcept  
void type(file_type _Ftype) noexcept  
```  
  
 Obtiene o establece el elemento file\_type.  
  
## permissions  
  
```  
perms permissions() const noexcept  
void permissions(perms_Prms) noexcept   
```  
  
 Obtiene o establece los permisos de archivo.  
  
 Use el establecedor para definir un archivo como readonly o quitar este atributo.  
  
## Requisitos  
 **Encabezado:** filesystem  
  
 **Espacio de nombres:** std::tr2::sys  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [path \(Clase, biblioteca de plantillas estándar de C\+\+\)](../standard-library/path-class-cpp-standard-template-library.md)   
 [\<filesystem\>](../standard-library/filesystem.md)