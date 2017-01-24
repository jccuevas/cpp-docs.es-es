---
title: "Pragmas de C | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "pragma (directivas), C/C++"
ms.assetid: 3d6d36b4-d565-4632-a4cd-e39aeaded5ad
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Pragmas de C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Una instrucción "pragma" indica al compilador que realice una acción determinada en tiempo de compilación.  Las instrucciones pragma varían en función del compilador.  Por ejemplo, puede utilizar la instrucción pragma **optimize** para establecer las optimizaciones que desea realizar en su programa.  Las instrucciones pragma de C de Microsoft son:  
  
|||||  
|-|-|-|-|  
|**alloc\_text**|**data\_seg**|**inline\_recursion**|**setlocale**|  
|**auto\_inline**|**function**|**intrinsic**|**warning**|  
|**check\_stack**|**hdrstop**|**message**||  
|**code\_seg**|**include\_alias**|**optimize**||  
|**comment**|**inline\_depth**|**pack**||  
  
 Vea [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md) en la *Referencia del preprocesador* para obtener una descripción de las instrucciones pragma de C de Microsoft.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Archivos de código fuente y programas de origen](../c-language/source-files-and-source-programs.md)