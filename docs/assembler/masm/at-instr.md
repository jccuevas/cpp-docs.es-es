---
title: '@InStr | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- '@InStr'
dev_langs:
- C++
helpviewer_keywords:
- '@InStr symbol'
ms.assetid: 980d5b9f-2b88-4306-8955-df6cd2133e68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0fb92987de21f653440d6c4cc23d726ad323b69
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="instr"></a>@InStr
Función de macro que busca la primera aparición de *string2* en *string1*, empezando en *posición* en *string1*. Si *posición* no aparece, la búsqueda comienza en el inicio de *string1*. Devuelve un entero de posición o 0 si *string2* no se encuentra.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
@InStr( [[position]], string1, string2 )  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de símbolos](../../assembler/masm/symbols-reference.md)