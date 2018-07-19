---
title: LOCAL (MASM) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Local
dev_langs:
- C++
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed9926d23f2e1e8636f31a6f586609ae22d38acd
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32053576"
---
# <a name="local-masm"></a>LOCAL (MASM)
En la primera directiva, dentro de una macro, **LOCAL** define las etiquetas que son únicas para cada instancia de la macro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      LOCAL localname [[, localname]]...  
LOCAL label [[ [count ] ]] [[:type]] [[, label [[ [count] ]] [[type]]]]...  
```  
  
## <a name="remarks"></a>Comentarios  
 En la segunda directiva, dentro de una definición de procedimiento (**PROC**), **LOCAL** crea variables basada en pilas que existen para la duración del procedimiento. El *etiqueta* puede ser una variable simple o una matriz que contiene *recuento* elementos.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)