---
title: C2002 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2002
dev_langs:
- C++
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01124fc839d6e788ff2dccae325f01f7d4337f5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164871"
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