---
title: REGISTRO (MASM) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- RECORD
dev_langs:
- C++
helpviewer_keywords:
- RECORD directive
ms.assetid: c83db394-0fe3-468f-813f-13302cdc862d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dcad460e914cadbc45eeeeea87461b7082e25635
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="record-masm"></a>RECORD (MASM)
Declara un tipo de registro que consta de los campos especificados. *FieldName* nombres de campo, *ancho* especifica el número de bits, y *expresión* da como resultado su valor inicial.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
   recordname RECORD fieldname:width [[= expression]]   
[[, fieldname:width [[= expression]]]]...  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)