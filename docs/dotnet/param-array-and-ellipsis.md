---
title: Matriz de parámetros y los puntos suspensivos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- function overloading, argument matching
ms.assetid: 492e3f6c-1c4c-4e0c-a358-72f2d39c30be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 20d13f327abe3e864007c4941af2ce9fd03ea05d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33158526"
---
# <a name="param-array-and-ellipsis"></a>Matriz de parámetros y puntos suspensivos
Prioridad de la matriz de parámetros para resolver llamadas a funciones sobrecargadas ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 En extensiones administradas y la nueva sintaxis, no hay ninguna compatibilidad explícita para la matriz de parámetros que admiten C# y Visual Basic. En su lugar, una matriz ordinaria marca con un atributo, como se indica a continuación:  
  
```  
void Trace1( String* format, [ParamArray]Object* args[] );  
void Trace2( String* format, Object* args[] );  
```  
  
 Aunque ambos parezcan iguales, la `ParamArray` atributo esto etiquetas para C# u otros lenguajes CLR como una matriz que acepta un número variable de elementos con cada invocación. El cambio de comportamiento de programas entre extensiones administradas y la nueva sintaxis está en la resolución de una función sobrecargada configurada en la que una instancia declara puntos suspensivos y una segunda declara un `ParamArray` atributo, como en el ejemplo siguiente proporcionado Artur Laksberg.  
  
```  
int fx(...); // 1  
int fx( [ParamArray] Int32[] ); // 2  
```  
  
 En extensiones administradas, los puntos suspensivos tiene prioridad sobre el atributo que es razonable, ya que el atributo no es un aspecto formal del lenguaje. Sin embargo, en la nueva sintaxis, la matriz de parámetros se admite ahora directamente dentro del lenguaje y tiene prioridad sobre los puntos suspensivos porque es más inflexible. Por lo tanto, en extensiones administradas, la llamada  
  
```  
fx( 1, 2 );  
```  
  
 se resuelve como `fx(...)` mientras esté en la nueva sintaxis, se resuelve como el `ParamArray` instancia. En caso de que el comportamiento del programa depende de la invocación de la instancia de puntos suspensivos a través de la `ParamArray`, deberá modificar la firma o la llamada.  
  
## <a name="see-also"></a>Vea también  
 [Cambios generales en el lenguaje (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)