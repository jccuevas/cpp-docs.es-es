---
title: "__ptr32, __ptr64 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__ptr32_cpp"
  - "__ptr64_cpp"
  - "__ptr32"
  - "__ptr64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__ptr32 (palabra clave) [C++]"
  - "__ptr64 (palabra clave) [C++]"
  - "_ptr32 (palabra clave) [C++]"
  - "_ptr64 (palabra clave) [C++]"
  - "ptr32 (palabra clave) [C++]"
  - "ptr64 (palabra clave) [C++]"
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __ptr32, __ptr64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 `__ptr32` representa un puntero nativo en un sistema de 32 bits, mientras que `__ptr64` representa un puntero nativo en un sistema de 64 bits.  
  
 En el ejemplo siguiente se muestra cómo declarar cada uno de estos tipos de puntero:  
  
```  
int * __ptr32 p32;  
int * __ptr64 p64;  
```  
  
 En un sistema de 32 bits, un puntero declarado con `__ptr64` se trunca a un puntero de 32 bits.  En un sistema de 64 bits, un puntero declarado con `__ptr32` se convierte a un puntero de 64 bits.  
  
> [!NOTE]
>  No se puede utilizar `__ptr32` o `__ptr64` al compilar con **\/clr:pure**.  De lo contrario se generará `Compiler Error C2472`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo declarar y asignar punteros con las palabras clave `__ptr32` y `__ptr64`.  
  
```  
#include <cstdlib>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    int * __ptr32 p32;  
    int * __ptr64 p64;  
  
    p32 = (int * __ptr32)malloc(4);  
    *p32 = 32;  
    cout << *p32 << endl;  
  
    p64 = (int * __ptr64)malloc(4);  
    *p64 = 64;  
    cout << *p64 << endl;  
}  
```  
  
  **32**  
**64**   
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Tipos fundamentales](../cpp/fundamental-types-cpp.md)