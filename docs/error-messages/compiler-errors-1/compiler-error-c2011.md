---
title: Compilador Error C2011 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2011
dev_langs:
- C++
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c599d6add1fa51c6aae7f04019eacdc94f11bb15
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2011"></a>C2011 de Error del compilador
'identifier': nueva definición del tipo 'type'  
  
 El identificador ya se ha definido como `type`. Busque nuevas definiciones del identificador.  
  
 También puede generarse el error C2011 si se importa varias veces un archivo de encabezado o una biblioteca de tipos al mismo archivo. Para evitar inclusiones múltiples de los tipos definidos en un archivo de encabezado, utilice #include guards o un `#pragma` [una vez](../../preprocessor/once.md) la directiva en el archivo de encabezado.  
  
 Si necesita encontrar la declaración del tipo redefinido inicial, puede utilizar el [/P](../../build/reference/p-preprocess-to-a-file.md) marca de compilador para generar el resultado preprocesado que se pasó al compilador. Con las herramientas de búsqueda de texto, puede buscar instancias del identificador redefinido en el archivo de salida.  
  
 El ejemplo siguiente genera el error C2011 y muestra cómo corregirlo:  
  
```  
// C2011.cpp  
// compile with: /c  
struct S;  
union S;   // C2011  
union S2;   // OK  
```