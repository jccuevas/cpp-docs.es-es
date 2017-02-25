---
title: "Matriz de par&#225;metros y puntos suspensivos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sobrecarga de funciones, coincidencia de argumentos"
ms.assetid: 492e3f6c-1c4c-4e0c-a358-72f2d39c30be
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Matriz de par&#225;metros y puntos suspensivos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La prioridad de la matriz de parámetros para resolver las llamadas a funciones sobrecargadas ha cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 En Extensiones administradas y en la nueva sintaxis, no hay ninguna compatibilidad explícita para la matriz de parámetros que C\# y [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] admiten.  En su lugar, una matriz ordinaria se marca con un atributo, del modo siguiente:  
  
```  
void Trace1( String* format, [ParamArray]Object* args[] );  
void Trace2( String* format, Object* args[] );  
```  
  
 Aunque ambos parezcan iguales, el atributo `ParamArray` etiqueta esto para C\# u otros lenguajes de CLR como una matriz que acepta un número variable de elementos con cada invocación.  El cambio en el comportamiento de los programas entre Extensiones administradas y la nueva sintaxis está en la resolución de una función sobrecargada configurada en la que una instancia declara puntos suspensivos y una segunda declara un atributo `ParamArray`, como en el ejemplo siguiente proporcionado por Artur Laksberg.  
  
```  
int fx(...); // 1  
int fx( [ParamArray] Int32[] ); // 2  
```  
  
 En Extensiones administradas, los puntos suspensivos tenían prioridad sobre el atributo lo que era razonable ya que el atributo no constituye un aspecto formal del lenguaje.  No obstante, en la nueva sintaxis, la matriz de parámetros se admite ahora directamente dentro del lenguaje y tiene prioridad sobre los puntos suspensivos porque está fuertemente tipada.  Así, en Extensiones administradas, la llamada  
  
```  
fx( 1, 2 );  
```  
  
 se resuelve como `fx(…)` mientras que en la nueva sintaxis, se resuelve como la instancia `ParamArray`.  En caso de que el comportamiento del programa dependa más de la invocación de la instancia de puntos suspensivos que la de `ParamArray`, deberá modificar la firma o la llamada.  
  
## Vea también  
 [Cambio general en el lenguaje](../dotnet/general-language-changes-cpp-cli.md)