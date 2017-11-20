---
title: Error de compilador un error C2026 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2026
dev_langs: C++
helpviewer_keywords: C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 97937579c12730fecfa89c69d9e7cf51229b5c6c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2026"></a>Error de C2026 de Error de compilador
cadena demasiado grande, caracteres finales truncados  
  
 La cadena era mayor que el límite de 16380 caracteres de un solo byte.  
  
 Antes de la concatenación de cadenas adyacentes, una cadena no puede tener más de 16380 caracteres de byte único.  
  
 Una cadena Unicode de alrededor de la mitad de esta longitud generaría también este error.  
  
 Si tiene una cadena que se define como sigue, genera un error C2026:  
  
```  
char sz[] =  
"\  
imagine a really, really \  
long string here\  
";  
```  
  
 Puede dividirla como sigue:  
  
```  
char sz[] =  
"\  
imagine a really, really "  
"long string here\  
";  
```  
  
 Puede que desee almacenar los literales de cadena excepcionalmente grande (32 KB o más) en un recurso personalizado o un archivo externo. Vea [crear un recurso de datos o personalizado nuevo](../../windows/creating-a-new-custom-or-data-resource.md) para obtener más información.