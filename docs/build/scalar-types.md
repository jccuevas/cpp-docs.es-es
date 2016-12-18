---
title: "Tipos escalares | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 07c9195e-b6c7-4083-8ef0-8a93032e4d1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tipos escalares
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Aunque el acceso de datos se puede derivar de cualquier alineación, se recomienda que los datos se alineen según su límite natural, para evitar una disminución del rendimiento \(o una multiplicidad de ello\).  Las enumeraciones son enteros constantes y se tratan como enteros de 32 bits.  La tabla siguiente describe la definición de tipos y el almacenamiento recomendado para ello según su relación con la alineación utilizando los valores de alineación siguientes:  
  
-   Byte \- 8 bits  
  
-   Palabra \- 16 bits  
  
-   Palabra doble \- 32 bits  
  
-   Palabra cuádruple \- 64 bits  
  
-   Palabra octal \- 128 bits  
  
|||||  
|-|-|-|-|  
|Tipo escalar|Tipo de datos en C|Espacio de almacenamiento \(en bytes\)|Alineación recomendada|  
|**Int8**|`char`|1|Byte|  
|**UInt8**|`unsigned char`|1|Byte|  
|**Int16**|**short**|2|Word|  
|**UInt16**|**unsigned short**|2|Word|  
|**Int32**|**int, long**|4|Doubleword|  
|**UInt32**|**int sin signo, long sin signo**|4|Doubleword|  
|**Int64**|`__int64`|8|Quadword|  
|**UInt64**|**unsigned \_\_int64**|8|Quadword|  
|**FP32 \(precisión sencilla\)**|**float**|4|Doubleword|  
|**FP64 \(precisión doble\)**|**double**|8|Quadword|  
|**POINTER**|**\***|8|Quadword|  
|`__m64`|**struct \_\_m64**|8|Quadword|  
|`__m128`|**struct \_\_m128**|16|Octaword|  
  
## Vea también  
 [Tipos y almacenamiento](../build/types-and-storage.md)