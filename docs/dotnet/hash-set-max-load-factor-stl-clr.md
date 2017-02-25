---
title: "hash_set::max_load_factor (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_set::max_load_factor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_load_factor (miembro) [STL/CLR]"
ms.assetid: 9aef46b1-e7c2-488c-a219-77c1c0de6dc4
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# hash_set::max_load_factor (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene o establece elementos máximos por el depósito.  
  
## Sintaxis  
  
```  
float max_load_factor();  
void max_load_factor(float new_factor);  
```  
  
#### Parámetros  
 new\_factor  
 Nuevo factor de carga máxima a almacenar.  
  
## Comentarios  
 La primera función miembro devuelve el factor de carga máxima almacenado actual.  Se utiliza para determinar el tamaño medio máximo de depósito.  
  
 La segunda función miembro reemplaza el factor de carga máxima de almacén con `new_factor`.  El rehashing no automático aparece hasta una inserción subsiguiente.  
  
## Ejemplo  
  
```  
// cliext_hash_set_max_load_factor.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**bucket\_count\(\) \= 16**  
**load\_factor\(\) \= 0,1875**  
**max\_load\_factor\(\) \= 4**  
**bucket\_count\(\) \= 16**  
**load\_factor\(\) \= 0,1875**  
**max\_load\_factor\(\) \= 0,25**  
**bucket\_count\(\) \= 128**  
**load\_factor\(\) \= 0,0234375**  
**max\_load\_factor\(\) \= 0,25**   
## Requisitos  
 cliext \<\/hash\_set de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set::bucket\_count](../dotnet/hash-set-bucket-count-stl-clr.md)   
 [hash\_set::load\_factor](../dotnet/hash-set-load-factor-stl-clr.md)   
 [hash\_set::rehash](../dotnet/hash-set-rehash-stl-clr.md)