---
title: "hash_multiset::max_load_factor (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multiset::max_load_factor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_load_factor (miembro) [STL/CLR]"
ms.assetid: ca0a6e8e-b889-47e4-9edd-c5a321fdeb8f
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# hash_multiset::max_load_factor (STL/CLR)
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
// cliext_hash_multiset_max_load_factor.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
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
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::bucket\_count](../dotnet/hash-multiset-bucket-count-stl-clr.md)   
 [hash\_multiset::load\_factor](../dotnet/hash-multiset-load-factor-stl-clr.md)   
 [hash\_multiset::rehash](../dotnet/hash-multiset-rehash-stl-clr.md)