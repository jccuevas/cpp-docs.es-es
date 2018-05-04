---
title: Instrucción de expresión | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60879ca8792e3259a69b7a9a3de6cd83dce0d6d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="expression-statement"></a>Expression (Instrucción)
Las instrucciones de expresión hacen que se evalúen las expresiones. No se realiza ninguna transferencia de control o iteración como resultado de una instrucción de expresión.  
  
 La sintaxis de la instrucción de expresión es simplemente  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[expression ] ;  
```  
  
## <a name="remarks"></a>Comentarios  
 Todas las expresiones de una instrucción de expresión se evalúan y se aplican todos los efectos secundarios antes de que se ejecute la siguiente instrucción. Las instrucciones de expresión más comunes son las asignaciones y las llamadas a funciones.  Puesto que la expresión es opcional, un punto y coma solo se considera una instrucción de expresión vacía, que se conoce como el [null](../cpp/null-statement.md) instrucción.  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre las instrucciones de C++](../cpp/overview-of-cpp-statements.md)