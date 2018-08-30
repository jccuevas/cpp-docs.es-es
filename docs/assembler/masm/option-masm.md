---
title: OPCIÓN (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- option
dev_langs:
- C++
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a2dcbc55d6a2d033cde3b6189618afd67bdc3fb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221514"
---
# <a name="option-masm"></a>OPTION (MASM)
Habilita y deshabilita las características del ensamblador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
OPTION   
optionlist  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Las opciones disponibles incluyen:  
  
|||||  
|-|-|-|-|  
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**EMULADOR**|  
|**NOEMULATOR**|**EPÍLOGO**|**EXPR16**|**EXPR32**|  
|**IDIOMA**|**LJMP**|**NOLJMP**|**M510**|  
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**OFFSET**|  
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|  
|**PROC**|**PRÓLOGO**|**READONLY**|**NOREADONLY**|  
|**EL ÁMBITO**|**NOSCOPED**|**SEGMENT**|**SETIF2**.|  
  
 La sintaxis de LENGUAJE es **opción LANGUAGE:**<em>x</em>, donde *x* es uno de C, SYSCALL, STDCALL, PASCAL, FORTRAN o BASIC.  SYSCALL, PASCAL, FORTRAN y BASIC no se admiten con utilizado con [. MODELO](../../assembler/masm/dot-model.md) sin formato.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)