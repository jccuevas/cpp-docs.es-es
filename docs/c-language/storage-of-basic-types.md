---
title: "Almacenamiento de tipos b&#225;sicos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operaciones aritméticas [C++], tipos"
  - "tipos de datos [C], especificadores"
  - "tipos de datos [C], almacenamiento"
  - "double (tipo de datos), almacenamiento"
  - "números de punto flotante, almacenamiento"
  - "int (tipo de datos)"
  - "tipos enteros"
  - "tipos enteros, almacenamiento"
  - "long double (palabra clave) [C], almacenamiento"
  - "long (palabra clave) [C]"
  - "short (tipo de datos)"
  - "tipos con signo [C++], almacenamiento"
  - "especificadores [C++], tipo"
  - "almacenamiento [C++], tipos"
  - "almacenar tipos [C++]"
  - "especificadores de tipos [C++], tamaños"
  - "tipos [C], aritméticos"
  - "tipos sin signo [C++], almacenamiento"
ms.assetid: bd1f33c1-c6b9-4558-8a72-afb21aef3318
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Almacenamiento de tipos b&#225;sicos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En la tabla siguiente se resume el almacenamiento asociado a cada tipo básico.  
  
### Tamaños de los tipos fundamentales  
  
|Tipo|Almacenamiento|  
|----------|--------------------|  
|`char`, `unsigned char`, **signed char**|1 byte|  
|**short**, **unsigned short**|2 bytes|  
|`int`, `unsigned int`|4 bytes|  
|**long**, `unsigned long`|4 bytes|  
|**float**|4 bytes|  
|**double**|8 bytes|  
|`long double`|8 bytes|  
  
 Los tipos de datos de C entran en categorías generales.  Los “tipos enteros” incluyen `char`, `int`, **short**, **long**, **signed**, `unsigned` y `enum`.  Los “tipos de punto flotante” incluyen **float**, **double** y `long double`.  Los “tipos aritméticos” incluyen todos los tipos de punto flotante y enteros.  
  
## Vea también  
 [Declaraciones y tipos](../c-language/declarations-and-types.md)