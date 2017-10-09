---
title: C2002 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2002
dev_langs:
- C++
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d8f6fc5983a462850581f69ca32dd7c305f9e847
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2002"></a>C2002 de Error del compilador
constante de caracteres anchos no válido  
  
 La constante de caracteres multibyte no es válida.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  La constante de caracteres anchos contiene más bytes de lo esperado.  
  
2.  No se incluye el encabezado estándar STDDEF.h.  
  
3.  Caracteres anchos no se pueden concatenar con literales de cadena ordinarios.  
  
4.  Una constante de caracteres anchos debe ir precedida por el carácter 'L':  
  
    ```  
    L'mbconst'  
    ```  
  
5.  En Microsoft C++, los argumentos de texto de una directiva de preprocesador deben ser ASCII. Por ejemplo, la directiva, `#pragma message(L"string")`, no es válido.
