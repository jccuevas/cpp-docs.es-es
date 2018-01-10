---
title: Pragmas de C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: pragmas, C/C++
ms.assetid: 3d6d36b4-d565-4632-a4cd-e39aeaded5ad
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 01fbd345daa6243a0385d556dd7cb6642a881de7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c-pragmas"></a>Pragmas de C
**Específicos de Microsoft**  
  
 Una instrucción "pragma" indica al compilador que realice una acción determinada en tiempo de compilación. Las instrucciones pragma varían en función del compilador. Por ejemplo, puede utilizar la instrucción pragma **optimize** para establecer las optimizaciones que desea realizar en su programa. Las instrucciones pragma de C de Microsoft son:  
  
|||||  
|-|-|-|-|  
|**alloc_text**|**data_seg**|**inline_recursion**|**setlocale**|  
|**auto_inline**|**function**|**intrinsic**|**warning**|  
|**check_stack**|**hdrstop**|**message**||  
|**code_seg**|**include_alias**|**optimize**||  
|**comment**|**inline_depth**|**pack**||  
  
 Vea [Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md) en la *Referencia del preprocesador* para obtener una descripción de las instrucciones pragma del compilador de C de Microsoft.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Archivos de código fuente y programas origen](../c-language/source-files-and-source-programs.md)