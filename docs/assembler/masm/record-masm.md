---
title: REGISTRO (MASM) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- RECORD
dev_langs:
- C++
helpviewer_keywords:
- RECORD directive
ms.assetid: c83db394-0fe3-468f-813f-13302cdc862d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e726053a9146cf88ed4e84045118d19b7094ed37
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057269"
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