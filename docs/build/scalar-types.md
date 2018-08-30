---
title: Tipos escalares | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 07c9195e-b6c7-4083-8ef0-8a93032e4d1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6af598ec6e27138f4e666007018ce803177697b3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211146"
---
# <a name="scalar-types"></a>Tipos escalares
Aunque el acceso a los datos puede provenir de cualquier alineación, se recomienda que los datos se alineen en su límite natural para evitar la pérdida de rendimiento (o una multiplicidad de ello). Las enumeraciones son enteros constantes y se tratan como enteros de 32 bits. La tabla siguiente describe la definición de tipo y el almacenamiento recomendado para él, ya que pertenece a la alineación con los siguientes valores de alineación:  
  
-   Byte - 8 bits  
  
-   Palabra: 16 bits  
  
-   Palabra doble - 32 bits  
  
-   Word Quad - 64 bits  
  
-   Palabra octal - 128 bits  
  
|||||  
|-|-|-|-|  
|Tipo escalar|Tipo de datos C|Tamaño de almacenamiento (en bytes)|Alineación recomendada|  
|**INT8**|**char**|1|Byte|  
|**UINT8**|**unsigned char**|1|Byte|  
|**INT16**|**short**|2|Palabra|  
|**UINT16**|**unsigned short**|2|Palabra|  
|**INT32**|**int**, **largo**|4|Palabra doble|  
|**UINT32**|**int sin signo, unsigned long**|4|Palabra doble|  
|**INT64**|**__int64**|8|Quadword|  
|**UINT64**|**unsigned __int64**|8|Quadword|  
|**FP32 (precisión simple)**|**float**|4|Palabra doble|  
|**FP64 (precisión doble)**|**double**|8|Quadword|  
|**PUNTERO**|<strong>\*</strong>|8|Quadword|  
|**__m64**|**__m64 (struct)**|8|Quadword|  
|**__m128**|**__m128 struct**|16|Octaword|  
  
## <a name="see-also"></a>Vea también  
 [Tipos y almacenamiento](../build/types-and-storage.md)