---
title: Compilador Error C2011 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2011
dev_langs:
- C++
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 898a724f022a81f590ec1f8165de9752de6c1d0b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33166642"
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